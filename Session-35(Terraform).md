### 3-Tier architecture diagram
![infra](https://github.com/user-attachments/assets/747c7e17-2f4a-4aa6-b2d1-bf8bbf363371)
Start a project "Roboshop-infra-Dev" in VS, this is for Dev environment, as this is multi-env, you have three options like Tfvars-method, Workspaces-method and Different repos for different env, present siva is now creating using different repos for different env method. Every method has pros and cons, you can tell this in interview. We also need to create for SIT, UAT, PROD also. So any project starts with VPC. Go through the resources in VS.

### Create Databases (04-databases in VS)
Now we are creating Databases using ansible PULL strategy, ansible disadvantage when compared to PULL based ? Once we pushed the configuration from the ansible server to the nodes, and if the configuration is disturbed, or anybody changes, we dont have any idea, so ansible implemented PULL architecture aswel, we can schedule a crontab to PULL the configuration periodically from Git not from the ansible-server and run it, since ansible is idempotence in nature, even if it runs the program multiple times nothing will happen. So go through the code of "Roboshop-ansible-roles-Terraform" in VS.

Every platform like azure, gcp or aws cloud platform will have its own solution to maintain configuration and secrets, in aws cloud we have more resources like ec2, dynamodb, lb etc. So for every service you may use passwords or any other secrets in the configuration at some point of time like in mysql we have password Roboshop@, so we have SSM Parameter store, services will refer this. For example in aws cloud, EC2 is a service and if this EC2 wants to retrieve the configuration or passwords which are present in the SSM Parameter, then this EC2 must have access to that SSM right ? for that only we give roles to the EC2 in IAM. Second thing is here we are using ansible to provision servers, so ansible should pull the configuration or passwords whatever present in the SSM Parameter, which is present in aws, then ansible should connect to the aws first, that means ansible should download "boto3 and botocore python" modules. Third thing is ansible-server should also have IAM role (or) IAM policy to PULL the configuration or passwords from the AWS. If these 3 things are there, we can implement vault. IAM role we have given in the code is "iam_instance_profile = role-name", present this role has full admin access, later we can restrict in IAM concepts.

So first store the password in SSM Paramater, for example we have root_password in mysql right ? so store that and naming should be "roboshop/dev/msql_root_pass" and use "secure string" and value should be the password itself "Roboshop@1", so here ansible should retrieve this password, for that we have a syntax called "lookup" put this syntax in the ansible-roles, where ever this password is there.

### Web and App tier (If traffic increases, auto-scaling will create instances)
- When new instance is created, use "user-data" or "provisioner" with ansible to configure the server, this
  may take 5mins of time.
- When you are deploying while website is in running state.
   1. First we create one instance
   2. Provision the instance using ansible or shell
   3. Stop the instance
   4. Take the AMI
   5. Upate auto-scaling using new AMI, that means slowly old instances will replace by new instances. In
      future if traffic increases, auto-scaling uses AMI to create the instances.
Which approach is better 1st or 2nd ? 2nd one is better because there will be less downtime, while website is running. This is VM based approach, later we move to the containerized approach.

### Points to remember
- Auto-scaling is only for web and app tier apps, for Database we use RDS, DynamoDB etc.
- Keeping "sg.yaml" file is just to understand the how the connections are given.
- Ansible PUSH ---> ansible-server itself pushing the configuration to the nodes.
- Ansible PULL ---> nodes itself PULL the configuration by going to the ansible server.
- We have one disadvantage in PUSH approach that it is if anybody disturb the configuration by logging
  manually. We cannot find out who did it. So we can use ansible PULL here.
- Do we know wether the user-data is success or not ? without seeing logs ? NO! because of this disadvantage
  we use terraform provisioners, so that we can able to see in the terminal, we have "null resource". So that
  we can clearly see wether the bootstrap is happening or not ?
- Note that without vpn connection, you cannot connect to the private instances.
- In project we store values or passwords in SSM Parameter manually, not automated
- If you go manuall like "ansible.builtin.command/shell" there is one disadvantage, that is there will be no
  idempotence behaviour, thats why mostly use module only. If there is no official modules from ansible, we
  can use community modules.
