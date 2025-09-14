### What is crontab and why it is useful ?
Instead of logging manually and deleting old log files with .log extensions, we can delete using crontab. Crontab is used for scheduling the scripts and it will trigger to delete the old log files everyday in our servers. Crontab will target a particular directory inside the script, which consist of more than 14 days old with ".log" extension only, so crontab has a particular syntax, which consist of 5 stars like "5 4 * * *" go and check crontab guru website and you can see the examples provided in the website itself, just see the crontab linux example in the same website.

### Usage of crontab and giving the script location
- Just type "crontab -e" in server in CD location (-e is editor), then enter the below line.
- "* * * * * sh /home/centos/shell-script/15.delete-old-logs.sh" (Give only absolute path)
- Save using :wq!
- To see the logs "tail -f /var/log/cron"

### Shellscript Optargs (Optional arguments) 18-greetings.sh
- General arguments to the script ---> 01-install-packages.sh git mysql net-tools nginx
- Optargs to the script ---> 01-install-packages.sh -n <sai_kiran> -w <good_morning>
- Optargs are extra inputs you can give when running the script but they’re not required but useful.
- We can control the script behaviour. We use "getops" tool to control this behaviour.

### Shellscript as Native Linux Command
If you want to run shellscript as Native linux command instead of "sh 18-greetings.sh" we have a path for every operating system that is "echo $PATH (Caps)" nothing but if you install any softwares in these PATHS then, automatically windows (or) linux will pick up from this PATHS, so you need to keep your script in that PATH, generally if you put your script in "/usr/local/bin" then you NO need to give ".sh" while running the script. So "sudo cp 18-greetings.sh /usr/local/bin/greeting (Copied as a greeting name) and give executive access "sudo chmod +x /usr/local/bin/greeting" now if you are in any folder otherthan the script folder also, just run by using name "greeting" (or) greeting -n sai -w good evening.

### Automating the creation of aws instances and route53 records
- Till now we have created ec2 instances and route53_records manually by logging into aws console.
- If web then PublicIP, if not web then PrivateIP right ? 
- And also if mongodb, mysql, shipping then t3.small & remaining t2.micro.
- We can now create using aws CLI "aws command line" to automate.
- In every server we have aws command line, you can check using "aws help" in server.
- So we need to write a script to automate using "aws command line"

### Authentication and Authorization
- Authentication --> You have Username/Password, you can go to any common area in your company. Here User
  is a person and he has Username/Password (or) KEY.
- Authorization --> You need to prove your authorization to enter in to the project bays, in other words like
  permissions. Different permissions for TL, Manager, Sr.Engineer etc. We call these as ROLES, these roles
  will be changing every year (or) few years after and Persmissions are tagged to these roles, below is the
  example. We need to check what is the role of user ? and what are the Persmissions attached to that role.
  
1. Team Manager --> Has super admin
2. Team Lead --> Has admin
3. Senior Engineers --> Normal access
4. Trainee --> Just read access

### Permissions
- We have nouns and verbs.
- We have resources in aws --> Ec2, vpc, route53, cdn, IAM etc. In this resources we have nouns & verbs.
- Nouns --> web, catalogue, cart, hostedzone etc.
- Verbs (or) actions --> create resource, update, delete nothing but CRUD.

### We can give authorization like below
- Sivakumar(Trainee) --> EC2(resource) --> Web(instance) --> READ access only.
- Manish(Junior DevOps) --> EC2(resource) --> Web(instance) --> READ and UPDATE access only.
- Raju(Senior Engineer) --> EC2(resource) --> Web(instance) --> READ and "CRU" access not delete.
- Mass(Team Lead) --> EC2(resource) --> All instances --> READ and "CRU" access only not delete.
- Suman(Team manager) --> EC2(resource) --> All instances --> READ and "CRUD" including delete.

### Similarly we have "Roles to Resources"
- Not only for persons, resources should also have access to access another resource, for that we have Roles
  to Resources like for example if you have created one EC2 and this EC2 instance should go and create other
  new instances (or) route53 records.
- So we need to give role to the EC2 by going to IAM/roles/create role/select EC2 as use case/next/admin
  access (or) amazonEc2fullaccess/route53 full access/give any name to the role.
- Now select the already created instance & Actions/Security/Modify IAM role/Select your created role.
- If you got any error remove the old credentials, which was created for aws console in .aws folder
  by using rm -rf command.

### Command to create instance with tags
- aws ec2 run-instances --image-id ami-xxxxxxxx --count 1 --instance-type t2.micro --security-group-ids sg-
  903004f8 --tag-specifications 'ResourceType=instance,Tags=[{Key=Name,Value=Saikiran_instance}]'
- Use this command to list instances and find the one with your specific Name tag. aws ec2 describe-instances
  --filters "Name=tag:Name,Values=MyInstanceName" --query
  "Reservations[].Instances[].InstanceId" --output text
- aws ec2 terminate-instances --instance-ids i-0abc123456def7890
- If you get error "Unable to locate credentials, you can configure by "aws configure"
- Before "aws configure" you need to create Administrator user. By going to IAM, Users, Create user, Attach
  policies directly, Administrator access, Click on the created user, Security credentials, Create accesskey,
  select CLI.
- Here if it is a person, he can keep Access_key & Secret_keys safely, will EC2 can keep these credentials
  secretly ? If anybody has access to this EC2, he can able to see these credentials using ls -la in cd .aws/
  because these keys are saved in .aws/ folder only. Thats why created roles in IAM.

### Go through the "roboshop.sh" file in Roboshop-Shellscript
- This file will create all instances and route53 records from the CLI without logging into the aws.

### We can improve the script like below
- If web, get PublicIP and create records.
- Check if records already exists, if exists update, if not exists then create.

### Points to remember
- To see the logs of crontab "tail -f /var/log/cron" 
- Go through "roboshop.sh" in VS.
- Tag specifications is used to give the names of the instances automatically.
- --query is to get the PrivateIP of the instances nothing but query from the existing resource.
- Important point, So overall create any one instance and give a role to it, so that it will create multiple
  instances from this instance only, you need to clone the "roboshop-shellscript" in this server and run the
  "roboshop.sh" script.
- UPSERT means if the record exists, update (or) edit it, if it doesn’t exist, it will create.
