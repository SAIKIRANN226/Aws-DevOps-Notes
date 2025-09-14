### How to create multiple environments with terraform in 3 ways
1. Terraform.tfvars
2. Workspaces 
3. Different Repos for different Environments

### 1. Terraform.tfvars method
This method is used to overwrite the default values in variables.tf, For example we want
- web-dev/mongodb-dev/catalogue-dev/redis-dev/user-dev/cart-dev etc.
- web-qa/mongodb-qa/catalogue-qa/redis-qa/user-qa/cart-qa etc.
- web-uat/mongodb-uat/catalogue-uat/redis-uat/user-uat/cart-uat etc.
- web-prod/mongodb-prod/catalogue-prod/redis-prod/user-prod/cart-prod etc.
- Domain names are "web-dev.megacitysai.fun", "mongodb-qa.megacitysai.fun", etc.

Same code but with different configuration, we only need to control using variables for different env's by using tfvars. Different buckets to maintain states and creating different folders in VS "dev,prod". We can also use one bucket for both dev and prod, but make sure other evn's should not get disturbed. How do we maintain different buckets ? By creating two buckets for dev and prod in "AWSconsole" and also create dynamodb tables for dev and prod to lock the buckets.

### Controlling environments using variables
So we have web-dev, web-qa, web-uat, web-prod. How to control this ?
- If key starts with web then we can write a condition using terraform inbuilt function that is
  startswith(each.key, "web")
- When you do terraform init ---> Backend will also be there, so here you have multiple environments, so use
  "terraform init -backend-config=dev/backend.tf"
- terraform plan -var-file=dev/dev.tfvars ---> If you dont mention the file name, it will load default vars.
- terraform apply -var-file=dev/dev.tfvars -auto-approve
- terraform destory -var-file=dev/dev.tfvars -auto-approve

So when you do for the next one prod (or) other env then you need to reconfigure (or) when you are switching from one env to another you must reinitialize by using this command. "terraform init -reconfigure -backend-config=prod/backend.tf". Note:- when you forget to give the -var-file then terraform will take default variables which is in variables.tf, if you now comment out the default variables then terraform will prompt for the values, so you will get know that you forgot to give varfile.

### 2. Workspaces method
We can manage multiple environments using single code (or) same code, only few backends will support this, s3 is one of them. If you want to know workspace commands just "terraform workspace". How to create workspace ? "terraform workspace new dev" do it in gitbash. When you are using terraform it has default variable that is "terraform.workspace", so if you are in dev then the value of terraform.workspace will becomes "dev", if you are in prod then the value of terraform.workspace will becomes "prod". So you need to write lookup function, this function works as, if you pass a KEY we can get that value. In tfvars example there are two separate buckets were created like dev/prod, but in workspaces there is only one default bucket "env:/" and inside this env folder terraform will automatically create dev/prod workspaces.

### 3. Creating different repos for different environments
Nothing but creating different repositories for different environments, better to go this method, if it is a large project in your company.

### First approach is best ?
- Pros ---> same code
- Cons ---> same code for multiple environments, you need to be very careful because whatever changes you do
  that will apply to all env's also
### Second approach is best ?
- Pros ---> same code
- Cons ---> same code for multiple environments, you need to be very careful because whatever changes you do
  that will apply to all env's also. Terraform is also maintaining same bucket that may cause errors and
  difficult to maintain variables.
### Third approach is best ?
- Pros ---> since everything is different you no need to worry
- Cons ---> you need to maintain code duplication 2 repos, if it is big project or crucial project better to
  go for this method, or we can go for either of remaining 2 methods.

### Provisioners (2types) is only for Ec2 instances
Local-exec ---> This provisioner in terraform is a specific block with in the resource that let you run the local shell commands on your local machine (laptop) at the time of resource is created or destroyed. This will run the command from your local machine, not on the server, when the resource is created. It's part of the Terraform configuration, not what you type manually. Below is the example of how the provisioner block is written (or) syntax of a local-exec provisioner with in the resource.
   
         resource "aws_instance" "example" {
           ami           = "ami-123456"
           instance_type = "t2.micro"

           provisioner "local-exec" {
             command = "echo Instance ${self.id} created"
           }
         }

local-exec ---> This provisioner run the commands or scripts on the local machine where Terraform is executed (i.e., the machine running the terraform apply command). It does not interact directly with the remote resource being provisioned. (or) local is where you are running terraform command (laptop) is nothing but gitbash, then local is your current laptop, if you run terraform command from the linux server. What will be the local here ? local will be the linux server. Note:- local-exec will run only one time, to run again you need to destroy first (or) The local-exec provisioner in Terraform allows you to run a local shell command on the machine where Terraform is being run (not the remote EC2 or server). It's commonly used for tasks like calling scripts, triggering tools, or debugging.

Remote-exec ---> This provisioner is used to run commands on a remote server (like a virtual machine or EC2 machine) after it's been created, typically over SSH (for Linux) or WinRM (for Windows). Suppose you provision an EC2 instance using Terraform. You want to install nginx on it automatically after it's created. That's where remote-exec helps. Below is the example of remote-exec and syntax of a remote-exec provisioner with in the resource.

         resource "aws_instance" "web" {
            ami           = "ami-0c55b159cbfafe1f0"
            instance_type = "t2.micro"
        
            provisioner "remote-exec" {
              inline = [
                "sudo apt-get update",
                "sudo yum install nginx -y"
              ]
            }
      
            connection {
              type        = "ssh"
              user        = "centos"
              private_key = file("~/.ssh/my-key.pem")
              host        = self.public_ip
            }
        }

This will run inside the server, first you should connect to the server, then you can run anything inside the server (or) remote-exec provisioner in Terraform, which runs commands on the remote resource (like an EC2 instance) after it's created. Provisioners are useful to integrate terraform with configuration management tools like ansible to get end to end automation, and also enable a keyword called "self"

### Key-points of local-exec and remote-exec
- Local-exec ---> Run on your local machine ---> Use case is to notify,trigger local scripts etc. ---> No
  remote access is need.
- Remote-exec ---> Runs on your remote-resource(ec2) ---> Use case is to install softwares,configure ec2 post
  setup ---> Need SSH/WinRM to access remote host.

### What is difference between Terraform and Ansible ?
Ansible ---> Is intended for configuration management, what is the main input for the configuration management ? server must be created, so if you have server available, wether it is onpremise or in cloud, then we can use ansible to configure the server, server configuration is nothing but configuration management.

Terraform ---> Responsibility is to create server nothing but infrastructure creation. So server created then we handover the server IPaddress to ansible, it will takecare of the provisioning or configuration management, if you integrate terraform and ansible you will get end-end automation using provisioners. Note:- We can also create ec2 instances using ansbile but it does not have state file as terraform does, that is why terraform is perfect for creation of infrastructure only.

### Creation time and Destroy time
- Creation time ---> This local exec will run right after the server is created when we apply.
- Destroy time ---> At the time of destory.
Why we use this Creation time and Destroy time ? To trigger other systems like sending emails, when servers created (or) destoryed.

### Points to remember
- Use different key names in s3 bucket like in the previous you have used different key "foreach" you can use   as per your wish but not with the same key names because it will merge all.
- If you are facing any error in pushing the code to the github use the below command
  "git remote set-url origin <URL>"
- If the code in VS is in full green colour that means the repository is not yet ready in the github, when
  repo is ready then it will turn to normal colour after pushing to git.
- We can write multiple provisioners also like for example "on_failure = continue" nothing but same as ignore   errors in ansible.
