### Locals in terraform
Count.index will not have access in the locals, because count is used to create multiple instances and also to reference the current iteration index. The locals block does not support iteration constructs like for_loops or count directly in locals. As a result, there’s no mechanism to access count.index in locals. We can only put expressions,conditions and functions inside the locals and use it anywhere.

### Syntax of locals
      locals {
         name = "saikrian"
         trainer = "kumar"
         instance_type = var.isProd ? "t3.small" : "t2.micro"
      }
How to call a local ? "local.name" (or) "local.trainer" (or) "local.instance_type"

### Data-Sources - VS
Terraform is connecting to lot of providers like aws,azure,gcp and everything. So these providers contains lot of data like regions,availability_zones,ec2,ami etc. All these are changing dynamically, so data-source is used to query the data dynamically from the providers, for example:- AMI ID's are changing when ever there is a new patch released by the aws, so to fetch ami automatically we use data-source. Just search in the google "Terraform query ami". If anybody created resources manually, then by taking this resource information, we can create another resource also by using data-source or by using terraform query. So that means data-source is useful to query the dynamic data from the providers aswel as from the existing resource information, using this information we can create another resource.

### Types of loops
1. Conditions ---> Mostly to iterate list, for list we used count and count.index (special variable)
2. For_each ---> Mostly to iterate maps, for maps we used "for_each" (special variable)
3. Dynamic loop ---> For creating multiple instances along with the route53_records, we used count and
   for_each loop example. So similarly in the securitygroup if you want to add a new rule or multiple ports
   likes 80,443,22 in ingress (or) egress blocks, that means a block is repeating as many rules you want
   to add. If a block is repeating more times you can keep that block in a variable and you can call by using
   dynamic loop (VS). Nothing but if a block is repeating with in the resource then we need to use it.

### Terraform State (State and Remote state)
What is the terraform responsibility ? Whatever we write it will create, nothing but a Declarative.
- Declarative state is = Our desired state
- Current state is whatever terraform has created that will be in "terraform.tfstate"
- Desired state == Current state (should be equal)
- If you do terraform apply again, then terraform will check current state, if Current state = Desired state,
  then it will not take any action.
- If Current state is not equal to Desired state then it will create.
- While terraform is doing any changes (nothing but after apply) then terraform will create a file called
  ".terraform.lock.hcl" to lock the "terraform.tfstate" file, so that nobody will touch the terraform.tfstate
  file while terraform is doing changes, because terraform is using that file at the time of doing changes.
- terraform.tfstate is in my laptop and iam pushing it to the github, another devops engineer also cloned my
  repo and run it again, devops engineer also have terraform.tfstate and both have no connection, then
  terraform will compare my state and devops person state. If both are running terraform apply, so here
  duplicates may come and some may get error as already exists. So for this issue we have central state file to
  check wether the infra already exists or not ? that is remote state (s3 bucket).
- terraform.tfstate is a crucial file, should not delete.
- We have two disadvantages one is "Collaboration environment" like terraform will have no idea about infra
  created, if multiple persons are working on same infra, it will try to create duplicates or errors may also
  come and another one is "Security" tfstate is a crucial file, if you keep it in local, it may be updated or
  deleted by mistake, for this we have a central state that is "s3 bucket" Remote Storage.

### Creating an s3 bucket and locking the bucket
- Bucket name should be unique.
- By using "dynamodb" ---> Create table to lock the bucket and make sure partition key should be in the 
  following format only "LockID"
- But right now we need remote state, we can also use "terraform cloud" but it is chargeable or we can also
  use s3 bucket from aws which is more popular or for every cloud like gcp also we have option for central
  state file. So now we use terraform s3 remote state for that, Just type in google terraform s3 remote state
  and take that configuration and put inside the provider or we can call as backend also.

### Points to remember
- If you are facing push error in the github you can forcefull push by using "git push -f origin master"
- Configuration is nothing but a script or code, if we write more lines of script we say configuration 
  is increasing.
- Interview question ? We are using s3bucket with dynamodb locking, here local state will not work because it
  will create duplicates and errors, security will not be there inside the local. so that is why we have to
  keep it safely in the remote storage like s3 bucket it will provide better collaboration among the team
  members.
- S3 buckets are chargeable in aws, so delete after practice.
