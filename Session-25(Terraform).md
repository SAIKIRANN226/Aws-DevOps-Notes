### Terraform is a Popular Infrastructure as Code - IaC
Terraform is an Open-source tool developed by HashiCorp. Instead of going into AWS console and manually creating an EC2 instance (or) any other resources, we can create by writing terraform code. Till now we configured our project Manually, also using Shellscript and Ansible, but we prefer Ansible (Controller Machine) as Configuration Management, if it is large project. Because ansible can connect to more number of servers easily from one single ansible server. Why we din't prefer manual configuration ? Because manually logging in every servers is a timetaking process and also we get more human errors.

### Advantages of terraform
- Version Control
- Consistent Infra
- Automated Infra CRUD
- Inventory Management
- Cost Optimisation
- Automatic Dependency Management
- Modular Infra
- Hybrid Cloud

### Version Control
Since it is code, we can maintain in Git to control version. We can completely maintain the history of infra and collaboration is easy. We can also rollback to the previous version incase of any production failure.

### Consistent Infrastructure
Often we face the problem of different configurations in different environments like DEV, QA, PROD. Using terraform we can create similar infra in multiple environments with more reliability (or) Same code will work in all environments like DEV, QA, PROD. Real time scenario like code is working in DEV (or) UAT (or) PRE PROD but not working in PROD, to solve this issue we use terraform.

### Automated Infrastructure - CRUD
Basically CRUD over the infrastructure. Using terraform we can create entire infra in minutes reducing the human errors and deleting infra in minutes if not required and updating infra using terraform is also easy. Create the infra, Read the infra, Update the infra, Delete the infra.

### Inventory Management
When you login to aws console, we have lot of services like multiple vpc, route53, ec2, lb, cdn, s3 etc. If client ask for the full information about the whole infrastructure, we cannot show it in the aws console by navigating to each and every service and taking notes and then showing to the client and that is also not a good practice. But in terraform you can easily take notes and give reports because we have separate folders for every resources like vpc, sg, vpn, databases, app-alb, web-alb, cdn etc.

### Cost Optimization
- Create Infra when required, Delete Infra when not required to save the cost.
- Automatic dependency management, for example if we need to create route53 records, ec2 servers should be in   the running state, and take those IP and paste in the route53, that means route53 is depending on ec2
  servers, so we can create resources and terraform will takecare of the dependencies.
- Terraform Modules, you can create terraform code as modules, so that other projects can also use it without
  writing from the scratch.
- Terraform is also a Hybrid Cloud, you can create infra in aws, azure, gcp not only cloud, it can also
  work with any other popular tools available in the market, you can see in the terraform providers website,
  it can work with many other providers (or) you can write your own module and connect with the terrform
  also. Not only resources, we can also create repos, branches etc. in github by writing terraform code.

The above all are the terraform understanding (Interview Question). It is a declarative way of creating infrastructure, what is declarative ? whatever you write you get it, if you write correct syntax, and it is easy syntax and NO need to follow the sequence in the code. If anybody edit manually in the aws console, and we find it is very difficult to trace who did it, but in terraform if anybody did changes and we can restore the infrastructure immediately by just one command, then we can discuss who did it later.

### Terraform installation and setup
- Download terraform from google mostly AMD64 windows and if you extract you will get .exe file
- Move that .exe file in your desired location.
- Take that downloaded path and give it in the "system environment variable"
- Edit the system environment variables/environment variables/select or click on the path in the system
  variables/edit/new/paste it here.
- If you give the terraform command, it will check all the paths you have given in the env variables, if it
  is available then terraform command will work.
- Install "hashicorp terraform extension" to get colors.

We write code in VS ---> Then we push to github ---> Then we push to the aws, but in order to push we need authentication, for that we need to download "awsCLI install" from google and select windows to install, not linux or macos. Just run shown commands in "cmd" then test "aws --version" in cmd aswel as in gitbash, wether it is installed or not. Then to connect to aws, we need to create a terraform user or administrator user by going to IAM/Users/Create(next)/Attach policies directly and select administrator access then click on your created_user/security_credentials/create access_key/click on command line interface (CLI)/copy the access_key and secret_key then configure user in your laptop by using this command "aws configure" in gitbash. These credentials will be saved in windowsC/users/user/.aws folder

### Syntax of terraform to create resources

      resource "what resource" "name of your resource" {
      
      }

- This syntax we call HCL (Hashicorp Configuration Language) 
- Here also we have variables/conditions/loops/functions/datatypes
- So rightnow we are using terraform for aws, so search terraform providers, select aws provider, if you
  dont give the provider, terraform will not know to work with which provider ? and .tf is the extension.
- Just go through session-01 in VS.
- Where to run the terraform commands ? Where ever .tf files exists.

### Terraform commands
- terraform init --> Initialize the provider, it will download the provider in ".terraform" folder is
  automatically created when you do terraform init.
- terraform plan --> Terraform will calculate the full details and show it (or) it is just a plan it will not
  create, it will show the preview of the changes (or) Terraform compares the infra between declared and
  existing.
- terraform apply --> Now it will create
- terraform apply -auto-approve --> Not ask for the prompt
- terraform destroy -auto-approve --> Not ask for the prompt
- All the above commands should be run in the gitbash.

### Variables syntax

        variable "name-of-variable" {
             type = datatype
             default = "default value"
        }

Terraform will automatically consider which datatype is, so no need to give the data-type but for practice we need to give data-type.

### Points to remember
- https://registry.terraform.io/providers/hashicorp/aws/3.34.0/docs/resources/security_group
- Just go through the "README" file in the sivagithub terraform "https://github.com/daws-76s/terraform"
- In provider also we can give access_key and secret_key under region to authenticate to aws, but when you
  push to github then github will send emails to notify, but it is not recommended because anyone can use
  your aws account and they can create anything in aws. So thats why we downloaded awsCLI to authenticate
  aws account which is a secure way.
- Important point to remember, you "NO" need to push to the github, you can directly save the terraform file
  and run the terraform commands in gitbash and later you can push to the github to save the files. Later
  green colour will change to the normal colour. But saving the file is mandatory.
- Dont push the access_key and secret_key to the github (or) internet for safety reasons.
