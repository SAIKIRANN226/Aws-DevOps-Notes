### Importance of .gitignore in terraform
Dont forget to put ".gitignore" file in the terraform root folder, not only in terraform root folder, for example if you are creating any other new folder to work, and if you want .gitignore there also you can put, but it is not mandatory. Keeping in root folder is enough, when you hit "terraform init" then terraform will download the provider in ".terraform" folder and this provider memory is almost 350mb. Here github is only to store code not softwares (or) .exe files, then github will automatically reject, so that is why .gitignore is important here (or) A .gitignore file tells to Git which files or directories to ignore (i.e., not to track or commit) in your repository, so that we can 
- Avoid committing sensitive files (e.g., credentials)
- Skip auto-generated local files.
- Keep the repository clean and portable.

### Terraform.tfvars, instance_type = "t3.small" 
- terraform.tfvars will overwrite the value in variables.tf file
- We can also give from the command prompt "terraform plan -var="instance_type=t3.medium"
- Here terraform.tfvars name is not mandatory we can use any name like "saikiran.tfvars" and this will become
  file and we can pass variable file by using "terraform plan -var-file="saikiran.tfvars"

### Variable preferences in terraform
1. command line ---> terraform plan -var="instance_type=t3.small"
2. -var-file ---> terraform plan -var-file="saikiran.tfvars"
3. terraform.tfvars 
4. Environment variable.

### Conditions in terraform
Go through the conditions example in VS. We have one line condition also. Terraform will follow this only.
Expression ? "this will run if true" : "this will run if false"

### Loops are two types
1. Count based loop --> To iterate list
2. For_each loop --> To iterate maps

### Functions - VS
It will do some work, if we give some input and it will take this input and give us output. Here in 
terraform we cannot create our own functions, but terraform itself has some functions we need to use that only. Example:- max(5,12,23) max is the function and we are giving inputs 5,12,23 then terraform will give output that is 23, similarly we have other functions also, and we have used length function like this "length(var.instance_names)" this will calculate the length in list automatically.

### Syntax of output in terraform
	output "instance_info" {
	     value = "aws_instance.web"
	}
### Points to remember
- You need to see the output.tf also in count folder |VS|, output is nothing but attributes reference, we can
  see this in terraform document, like for example you have created ec2 instance but we need to know few
  outputs like what is PublicIP or PrivateIP etc. Output block is used to print the output of the resources in
  the terminal.
- Important point is that you must save all files of terraform then only run the terraform commands.
- How to see Git directory size ? "du -sh .git" useful when it is slow while pushing to the github but still i
  dont get it need to know this later.
