### What you know about Git and Linux ?
- Git commands and Linux commands.
- Permissions in linux.
- User management
- Process management
- Package management
- Service management
- Giving admin access or limited access to the users

### How do you check the size of a folder in linux ?
du -sh <folder-path>

### How to check if a port is open ?
netstat -lntp

### How do you check running logs ?
tail -f /path/to/logs

### What is swap memory in linux ?
Swap memory is extra space in your computer hard drive that works like a backup RAM, when your computer runs out of RAM, it temporarily moves less used data to this space, so your system doesnt slow down or crash.

### How to check IP address of a linux server ?
ifconfig

### What is the purpose of a chmod ?
Is used to change the permissions of a file or folder. We can set permissions to RWX permissions to owner, group and others

### How to reboot the server when reboot command is not responding ?
We can use the shutdown command with the reboot option ---> "sudo shutdown -r -f now"

### What is the difference between Git and Github ?
Git is a distributed version control used to track code changes in local and manage the versions. Github is a cloud based platform we can hosts our Git repositories, Providing collaboration features like PR, issue tracking etc.

### Explain the difference between git merge and git rebase ?
git merge combines two branches and creating a new merge commit-id and also preserving the history, so that we can track who did what changes. It is used for better collaboration. rebase moves on top of another branch which creates a linear history.

### How do you resolve a merge conflict in Git ?
- Identify the conflicted files "git status"
- Open files and manually resolve conflicts (Look for <<<<<< markers).
- Mark as resolved "git add <file>"
- Commit "git commit -m "Resolved merge conflict"

### What is the difference between fork and clone in GitHub ?
- Fork: Creates a personal copy of someone else’s repository on GitHub (Used for contribution).
- Clone: Downloads a repository to your local machine to start development.

### How can you revert a commit that has already been pushed to a shared branch ?
git revert <commit_hash>

### What are GitHub Actions, and how have you used them ?
- GitHub Actions is a CI/CD tool that automates workflows on GitHub (Build, Test, Deploy).
- Example: Automating code build and deployment to AWS S3 or EC2 on push or pull request events.

### How do you check disk usage on a Linux server ?
df -hT

### How do you check the currently running processes and resource usage ?
top ; ps -ef ; free -h

### Explain the difference between cron and at ?
- cron: Schedules recurring jobs (Daily backups)
- at: Schedules a one-time job (Run a script tomorrow at 2 PM)

### How do you find which process is using a particular port ?
netstat -lntp

### What is the difference between Symlink and Hardlink ?
- Hard link: Points directly to file inode (Memory location, its a number) in hard disk. File data exists even if original is deleted.
- Symlink: Points to file path. Becomes broken if original is deleted.

### How would you monitor logs on a Linux server in real-time ?
tail -f /var/log/syslog  

### How do you manage services in Linux (Start, Stop, Restart) ?
- systemctl start <service>
- systemctl stop <service>
- systemctl restart <service>
- systemctl status <service>

### Explain file permission notation in Linux ?
- r → read, w → write, x → execute.
- Example: -rwxr-xr--
- Owner: read, write, execute
- Group: read, execute
- Others: read

### How do you check if a process is consuming high CPU or memory ?
- top → Sort by %CPU or %MEM.
- ps aux --sort=-%cpu | head -n 10 → Top 10 CPU-consuming processes.
- ps aux --sort=-%mem | head -n 10 → Top 10 memory-consuming processes.

### How to kill a process ?
- kill -9 PID ---> Force kill
- kill PID

### Have you worked on any automation scripts recently ?
Yes we have few applications running on VM, i was asked to write resources monitoring scripts, so i wrote for Disk Utilization. I developed this script and scheduled through crontab for every 15 min and i configured it to send alerts in email and team channels and also i wrote log cleanup script, since our application creates logs every day in our servers, for example "user-05-06-2024.log"

### Can you write a simple shellscript to list all S3 buckets ?
    #!/bin/bash
    R="\e[31m"
    G="\e[32m"
    Y="\e[33m"
    N="\e[0m"
    
    echo "Fetching the list of S3 buckets...."
    aws sts get-caller-identity
    if [ $? -ne 0 ]
    then 
        echo -e "$R AWS_CLI is not configured properly. Run aws configure first $N"
        exit 1
    fi 
    aws s3 ls 
    echo "Done"
    
### How do you write a shellscript to backup a directory everyday ?
    #!/bin/bash
    R="\e[31m"
    G="\e[32m"
    Y="\e[33m"
    N="\e[0m"
    
    SOURCE_DIR="/path/to/your/data"
    BACKUP_DIR="/path/to/your/backups"
    DATE=$(date)
    BACKUP_NAME="Backup-$DATE.tar.gz"

    echo "Backing up $SOURCE_DIR to $BACKUP_DIR/$BACKUP_NAME.."
    mkdir -p "$BACKUP_DIR"
    tar -czf "$BACKUP_DIR/$BACKUP_NAME" "$SOURCE_DIR"

    if [ $? -ne 0 ]
    then 
      echo -e "$R Backup is failed $N"
    else 
      echo -e "$G Backup is success $N"
    fi 
    
Here .tar means It’s a single file that contains many files/folders bundled together — kind of like putting everything into one big box, but without compression and .gz means After making the .tar archive, it is compressed with the gzip algorithm to make it smaller. This results in a .tar.gz file — a compressed archive. Think of it like putting all your files in a box (.tar) and then shrinking the box (.gz) so it takes less space. tar -czf ---> -c → Create a new archive file. -z → Compress it with gzip (so the file becomes .tar.gz).
-f → File name to write the archive to (the argument right after this is the archive file’s name).In shell scripting, archiving a file or directory refers to the process of combining multiple files and directories into a single file, known as an archive file. This single archive file then contains the original files and their associated metadata, such as file permissions, ownership and timestamps.

### How do you pass arguments to the shellscript ?
I will pass arguments to the shellscript while executing the script, for example "sh greetings.sh morning" i receive the args inside the script through special variables like $1,$2,$3...$N. Number of args "$#" All args special variable is like "$@"

### What is the difference between "$@" and "$*" in bash scripts ?
Both are used to access all the arguments passed to the bash script. "$@" expand each argument individually. "$*" Joins all arguments as one string.

    #!/bin/bash
    echo "Using $@"
    for arg in "$@"
    do 
        echo "$arg"
    done

    echo "Using $*"
    for arg in "$*"
    do 
        echo "$arg"
    done 

    sh saikiran.sh "arg one" "arg two" 
    Using $@: 
    arg one
    arge two

    Using $*:
    arge one arg two

### How do you handle errors in shellscript (or) How do you debug a shellscript ?
Shellscript will not exit when it faces errors, it will continue to run, we need to check every command using exit-status "$?" we can also "set -e" after shibang, but it will not work most of the times.

### What’s the difference between > and >> in shell scripting ?
Greaterthan symbol > means overwrites the file and >> means appends the file.

### How do you read a file line-by-line in bash ?
            
        while IFS= read -r line
        do
          echo "$line"
        done < file.txt
        
### Explain the difference between soft link and hard link ?
Soft link (symbolic link) Points to the file path, can link across file systems, breaks if the original is deleted. Hard link Points directly to the inode, must be on the same file system, remains valid even if the original is deleted.

### How do you check if a process is running in a shell script ?

        if pgrep -x "nginx" > /dev/null
        then
          echo "Running"
        else
          echo "Not running"
        fi

### How do you replace all occurrences of a string in a file using shell commands ?
Using Stream line editor ---> sed -i 's/old_text/new_text/g' file.txt

### How do you find the number of lines, words, and characters in a file ?
Using word count ---> wc file.txt

### Write a script that reads usernames from a file and checks if they exist in the system ?

        #!/bin/bash
        while read -r user
        do
          if id "$user" &>/dev/null
          then
            echo "$user exists"
          else
            echo "$user not found"
          fi
        done < users.txt

Here &>/dev/null ---> &> → Redirect both standard output (stdout) and standard error (stderr).
/dev/null ---> The “black hole” of Linux — anything sent here is discarded. That means Run the id command 
for $user, but throw away all output (whether it’s normal output or error messages).
        
### Write a script to read a file and print only lines that contain the word "ERROR" ?

        #!/bin/bash
        LOG_FILE="/var/log/messages"
        grep "ERROR" "$LOG_FILE"

### Write a script to check if a service is running; if not, start it ?

        #!/bin/bash
        SERVICE="nginx"
        
        if ! pgrep -x "$SERVICE" > /dev/null
        then
          echo "$SERVICE is not running. Starting..."
          systemctl start "$SERVICE"
        else
          echo "$SERVICE is running."
        fi

### What is configuration management in ansible ?
Configuration management is the way of configuring the servers for consistency, scalability, reliability. This is master-node architecture. For example we have ansible server and ansible is installed in it. Then ansible will connect to servers (or) nodes using SSH connection. We write ansible playbooks that are version control in Git. Ansible can run these playbooks against nodes and also it connects to multiple servers at a time to achieve scalability. Since it is configuration as code, same code will work in multiple environments for consistency. Any changes in the configuration, it will immediately run the playbooks and it will reflect in the nodes.

### What are the ansible advantages over shell ?
Linux distributions, Scalability, Error handling, Readability, External systems, Sensitive information, Rich in modules, Easy to understand through YAML format.

### What are handlers in ansible ?
When there is a change in task, we can run another task through handlers. For example if there is a change in nginx configuration, then it will notify another task called restarting nginx.

### What is the significance of become keyword in ansible playbook ?
Become provide the sudo access to the playbook, so that it can install any thing in the server.

### How does ansible handle Idempotence and why it is important in ansible configuration ?
Providing same results irrespective of the number of executions is called idempotence. For example if user exist, it will not create, if not exist then it will create.

### How do you handle errors and exceptions in ansible playbooks ?
When there is an error in ansible playbook, bydefault it will exit the program. But we can manage errors in ansible through Ignore_errors: true, this option allows the playbook to continue even it faces any errors.

### Describe the structure of ansible playbook ?
Just write ansible playbook to install nginx and run the nginx.

### How do you configure inventory files in ansible ?
Inventory file is where we manage the hosts, group of hosts, group of groups that ansible can manage. We can also mention group level variables, host level variables inside the inventory.ini

### How can you store sensitive information such as passwords in ansible ?
We use ansible-vault feature to encrypt the sensitive information like passwords and usernames. Command to create ansible vault is "ansible-vault create secrets.yaml" while executing the playbook, we use the command like "ansible-playbook saikiran.yaml --ask-vault-pass" (or) we can keep "ask_vault_pass = True" in inventory.ini

### You need to manage a dynamic inventory where servers are frequently added or removed. How would you configure ansible to work with such a dynamic inventory ?
We have a plugin called "aws_ec3" it can pull the hosts based on region and filters.

### What are roles in ansible ?
Ansible roles is a proper directory structure to create and manage ansible playbooks. It contains vars, tasks, templates, handlers etc.

### How do you run a specific tasks in ansible ?
We can make use of tags in ansible. We can tag each task with tag value and include them while executing the playbook.

### What modules you have used in ansible ?
We have used many modules in our project like package, service, unarchive, get_url, copy, template, file, command, shell, systemd, import_role etc.

### How is Ansible different from other automation tools like Puppet or Chef ?
Ansible is agentless and uses SSH to connect to nodes and it is a PUSH based model.

### What is an Ansible Inventory ?
An inventory is a file (INI, YAML, or dynamic) that defines the list of hosts and groups where Ansible will run tasks. For example ini format is [webservers] web1.example.com web2.example.com

### What are Ansible Playbooks ?
Playbooks are YAML files containing plays. Each play maps a group of hosts to tasks.

### How do you run an Ansible playbook on a specific host from an inventory group ?
ansible-playbook -i inventory.ini playbook.yml --limit web1.example.com

### What is the difference between command and shell module in Ansible ?
Shell ---> It is like you login inside the server and run the command, Environment variables and redirections (Symbols) will work here. Command ---> It is like running the command outside the server, Environment variables and redirections (Symbols) will not work here.

### What is Idempotency in Ansible ?
If you run program multiple times, that can create samething multiple times, where as in ansible, if the user does not exist then it will create, if exist it will ignore, that means even if you run the program infinite times also, it will not create any damage. Providing same results irrespective of the number of executions is called idempotence.

### How do you debug Ansible playbooks ?
Use debug module -v, -vv or -vvv

### How do you connect Ansible with AWS ?
Install boto3 and AWS CLI. Use dynamic inventory scripts (aws_ec2 plugin). Create playbooks using AWS modules like ec2_instance, s3_bucket.

### You need to run a playbook on only those hosts where a service is down. How would you handle it ?
Use the when condition with service_facts:

### A production deployment failed midway due to a network issue. How do you ensure Ansible resumes from where it left off ?
Use --start-at-task option, like ansible-playbook deploy.yml --start-at-task="Install dependencies"

### You need to dynamically add newly launched AWS EC2 instances to your Ansible runs.
Use the aws_ec2 dynamic inventory plugin --> plugin: aws_ec2

### Default Ansible inventory file location ?
/etc/ansible/hosts

### Which file sets Ansible’s default configurations ?
ansible.cfg

### How do you repeat a task for multiple items ?
Using loops 

### What is terraform and why we use it ?
It is an Open-Source tool, developed by hashicorp. Terraform is popular IaC. It is best in the market rightnow because of its advantages like V, C, A, I, C, A, M, H

### Ansible vs Terraform when to use ? What is the purpose ?
Ansible is a popular configuration management tool and Open-source tool. It is only intended for configuration management and application deployment using playbooks and these playbooks are version controlled in Git, since our source code is also Git. Ansible can also create infra but it is not recommended because ansible does not have a state file while terraform does. So thats why terraform is best for creating infra and ansible is best in configuration management. So we integrate terraform with ansible. Once terraform create servers, it can handover to ansible and ansible will takecare of the configuring servers.

### Explain terraform commands ?
We have commands like terraform init, plan, apply, destroy.

### What is the state in terraform ?
Terraform uses state file to compare desired infra with the existing infra which is in current state (terraform.tfstate) if desired state == current state then terraform will not take any action, if desired state is ==/== current state, then terraform will create the infra. So terraform responsibility is to match desired infra with actual infra.

### What is the remote state in terraform ?
Saving state in locally is not recommended because in a collaborative envionment if multiple persons are working on the same infra there is high chances of duplicates and errors like already exist, so we have to keep it safely in the remote storage like s3 bucket and locking this bucket with dynamodb, so that nobody will do any changes.

        backend "s3" {
          bucket = "saikiran"
          key = "msk"
          region = "us-east-1"
          dynamodb_table = "sai-table"
        }

### Explain variables in terraform ?
Variables are used to parameterize the infrastructure. We have types of variables like list, string, map, bool, number. However data-types are no that much important, because terraform will automatically consider which data-type is.

### What is Tfvars in terraform ?
It is a file which has key-value pair, these values will override the default values in variables.tf file. We can use different tfvars like dev.tfvars (or) prod.tfvars to provision the infra in multiple environments. We should use -var-file tag to pass tfvars file to the terraform command.

### What is count and count.index in terraform ?
We use count parameter to create multiple instances and route53 records based on a specific count. We use length function here so that it will calculate the length of the list automatically. Count.index is used to refer the index from 0

### What are outputs in terraform ?
When we create resources in terraform, it will give us attributes of the resource it created. These output values are useful in creating another resources. Module developers expose output values, module users will use it to create another resources

### What are data-sources in terraform ?
Terraform is connecting to providers like aws cloud and we have lot of information in it which are changing dynamically, so we query that data dynamically using data-source and use them to creat another resources.

### What are locals in terraform ?
Locals are also a type of variables. It is a key-value pair and we can use it anywhere we want. It has extra capabilities like keeping expressions, conditions, functions inside the local, variable values can be overridden but locals cannot be overidden.

### What are functions in terraform and name few of them ?
Basically when we give some input to the function, it will give us few ouputs like we have used length, lookup (To find the value of a key in a map), join, split, slice, file

### How do you manage credentials in terraform ?
We need to be careful while handling credentials. Best practices are setting the env variables before we plan and apply the infra. Once it is applied we can unset. We can store the credentials in jenkins credentials if we are following CICD.

### Explain the concept of workspace ?
Terraform workspace is used to create multiple envs using same code. Terraform will give us a special variable terraform.workspace. If you are in dev then the value of terraform.workspace will become dev, same for prod also. We can control envs using lookup function.

### How does terraform manages updates to existing resources ?
Terraform always try to match the desired infra with current infra which is in terraform.tfstate, if current state is equal to desired state, it will not take any action, if not equal then it will create the infra.

### Create an ec2 instance in aws ?
Use provider.tf, variables.tf, data.tf etc. Dont simple write resource block.

### How to store sensitive data in terraform ?
Previously we used ansible vault, recently we migrated to SSM Parameter store, since our whole infra is in SSM Parameter store. We integrate ansible with SSM instead of depending ansible and ansible vault commands.

### Does terraform supports multi provider deployments ?
Yes, we can define multiple providers.

### If i lose the state file how can i recover ?
First of all its a serious issue because terraform uses this file to track the infra. We have to follow some best practices to keep the file safely and in a position to recover. We must use remote state and locking mechanism like S3 bucket and Dynamodb table. We must use data replication, anytime a state file is changed in a bucket, it will make another copy of it in different bucket in different region. Implement proper IAM roles to access state file so that nobody will update or delete. Still if there is a loss, we have to restore it manually.

### What is null resource in terraform ?
It will not create any resources but we can use this to make use of provisioners like remote-exec and local-exec, file provisioners, triggers etc.

### What are modules in terraform ?
We can create terraform code as modules. It is like Dry concept dont repeat yourself, that can be used by others also instead of writing code for the infra from the scratch.

### What is the difference between ansible and terraform ?
Terraform is IaC tool and ansible is configuration management tool. Even though ansible can create infra but ansible dont have state mechanism while terraform does. So thats why terraform is best for creating infra and ansible is best for configuration. We can integrate ansible with terraform to get end-to-end automation. Terraform will create instance and handover to ansible for configuration of servers.

### Terraform vs cloudformation ?
Terraform can be used for multi cloud providers. CF is only used for AWS infra. Terraform has a state functionality while CF uses stacks.

### Once you create ec2 instance using terraform, after that you added one tag manually then what will terraform do ?
First terraform will do refresh operation. It can find the changes happened outside the terraform and alert us. If you apply now then terraform will remove those manuall changes and try to match the desired infra with the current infra.

### How do you deploy your infra code into different environments ?
Tfvars, Workspaces, Different repos for different env

### What are provisioners in terraform ?
We have local-exec and remote-exec and what will do these ?

### Terraform apply fails due to a state lock file issue. How would you resolve it ?
State locking occurs when previous executing is not releasing the lock, we can either use force unlock using LOCK_ID command or we can go to dynamodb table and manually delete entry with LOCK_ID

### Your terraform deployment has created infra but some resources are not deleting even after destroying ?
This majorly happens when there is a dependency on resources. For example we cant delete the SG when it is attached to EC2. So first we make sure to delete dependent resources are deleted and then delete the next resource. Another reason is access issues.

### What is terraform and why we use it ?
It is an Open-Source tool, developed by hashicorp. Terraform is popular IaC. It is best in the market rightnow because of its advantages like V, C, A, I, C, A, M, H

### Ansible vs Terraform when to use ? What is the purpose ?
Ansible is a popular configuration management tool and Open-source tool. It is only intended for configuration management and application deployment using playbooks and these playbooks are version controlled in Git, since our source code is also Git. Ansible can also create infra but it is not recommended because ansible does not have a state file while terraform does. So thats why terraform is best for creating infra and ansible is best in configuration management. So we integrate terraform with ansible. Once terraform create servers, it can handover to ansible and ansible will takecare of the configuring servers.

### Explain terraform commands ?
We have commands like terraform init, plan, apply, destroy.

### What is the state in terraform ?
Terraform uses state file to compare desired infra with the existing infra which is in current state (terraform.tfstate) if desired state == current state then terraform will not take any action, if desired state is ==/== current state, then terraform will create the infra. So terraform responsibility is to match desired infra with actual infra.

### What is the remote state in terraform ?
Saving state in locally is not recommended because in a collaborative envionment if multiple persons are working on the same infra there is high chances of duplicates and errors like already exist, so we have to keep it safely in the remote storage like s3 bucket and locking this bucket with dynamodb, so that nobody will do any changes.

        backend "s3" {
          bucket = "saikiran"
          key = "msk"
          region = "us-east-1"
          dynamodb_table = "sai-table"
        }

### Explain variables in terraform ?
Variables are used to parameterize the infrastructure. We have types of variables like list, string, map, bool, number. However data-types are no that much important, because terraform will automatically consider which data-type is.

### What is Tfvars in terraform ?
It is a file which has key-value pair, these values will override the default values in variables.tf file. We can use different tfvars like dev.tfvars (or) prod.tfvars to provision the infra in multiple environments. We should use -var-file tag to pass tfvars file to the terraform command.

### What is count and count.index in terraform ?
We use count parameter to create multiple instances and route53 records based on a specific count. We use length function here so that it will calculate the length of the list automatically. Count.index is used to refer the index from 0

### What are outputs in terraform ?
When we create resources in terraform, it will give us attributes of the resource it created. These output values are useful in creating another resources. Module developers expose output values, module users will use it to create another resources

### What are data-sources in terraform ?
Terraform is connecting to providers like aws cloud and we have lot of information in it which are changing dynamically, so we query that data dynamically using data-source and use them to creat another resources.

### What are locals in terraform ?
Locals are also a type of variables. It is a key-value pair and we can use it anywhere we want. It has extra capabilities like keeping expressions, conditions, functions inside the local, variable values can be overridden but locals cannot be overidden.

### What are functions in terraform and name few of them ?
Basically when we give some input to the function, it will give us few ouputs like we have used length, lookup (To find the value of a key in a map), join, split, slice, file

### How do you manage credentials in terraform ?
We need to be careful while handling credentials. Best practices are setting the env variables before we plan and apply the infra. Once it is applied we can unset. We can store the credentials in jenkins credentials if we are following CICD.

### Explain the concept of workspace ?
Terraform workspace is used to create multiple envs using same code. Terraform will give us a special variable terraform.workspace. If you are in dev then the value of terraform.workspace will become dev, same for prod also. We can control envs using lookup function.

### How does terraform manages updates to existing resources ?
Terraform always try to match the desired infra with current infra which is in terraform.tfstate, if current state is equal to desired state, it will not take any action, if not equal then it will create the infra.

### Create an ec2 instance in aws ?
Use provider.tf, variables.tf, data.tf etc. Dont simple write resource block.

### How to store sensitive data in terraform ?
Previously we used ansible vault, recently we migrated to SSM Parameter store, since our whole infra is in SSM Parameter store. We integrate ansible with SSM instead of depending ansible and ansible vault commands.

### Does terraform supports multi provider deployments ?
Yes, we can define multiple providers.

### If i lose the state file how can i recover ?
First of all its a serious issue because terraform uses this file to track the infra. We have to follow some best practices to keep the file safely and in a position to recover. We must use remote state and locking mechanism like S3 bucket and Dynamodb table. We must use data replication, anytime a state file is changed in a bucket, it will make another copy of it in different bucket in different region. Implement proper IAM roles to access state file so that nobody will update or delete. Still if there is a loss, we have to restore it manually.

### What is null resource in terraform ?
It will not create any resources but we can use this to make use of provisioners like remote-exec and local-exec, file provisioners, triggers etc.

### What are modules in terraform ?
We can create terraform code as modules. It is like Dry concept dont repeat yourself, that can be used by others also instead of writing code for the infra from the scratch.

### What is the difference between ansible and terraform ?
Terraform is IaC tool and ansible is configuration management tool. Even though ansible can create infra but ansible dont have state mechanism while terraform does. So thats why terraform is best for creating infra and ansible is best for configuration. We can integrate ansible with terraform to get end-to-end automation. Terraform will create instance and handover to ansible for configuration of servers.

### Terraform vs cloudformation ?
Terraform can be used for multi cloud providers. CF is only used for AWS infra. Terraform has a state functionality while CF uses stacks.

### Once you create ec2 instance using terraform, after that you added one tag manually then what will terraform do ?
First terraform will do refresh operation. It can find the changes happened outside the terraform and alert us. If you apply now then terraform will remove those manuall changes and try to match the desired infra with the current infra.

### How do you deploy your infra code into different environments ?
Tfvars, Workspaces, Different repos for different env

### What are provisioners in terraform ?
We have local-exec and remote-exec and what will do these ?

### Terraform apply fails due to a state lock file issue. How would you resolve it ?
State locking occurs when previous executing is not releasing the lock, we can either use force unlock using LOCK_ID command or we can go to dynamodb table and manually delete entry with LOCK_ID

### Your terraform deployment has created infra but some resources are not deleting even after destroying ?
This majorly happens when there is a dependency on resources. For example we cant delete the SG when it is attached to EC2. So first we make sure to delete dependent resources are deleted and then delete the next resource. Another reason is access issues.

### What is jenkins and why it is used ?
Jenkins is an open-source automation tool used for CICD. It allows developers to automatically build, test and deploy the code. In DevOps it reduce manual work and integrate with tools like Git and provide pipeline as code for automation.

### Explain the difference between Freestyle Jobs & Pipeline Jobs in Jenkins ?
Freestyle job is nothing but creating job in jenkins console, here anybody can do the changes and we dont have any idea about that. Pipeline job is a code based creation in jenkins console like using groovy script. Here also anybody can do the changes. Nobody is using freestyle now, everybody is using "Pipeline script from SCM"

### How do you configure Jenkins to integrate with GitHub ?
Using WebHook, we can configure jenkins to integrate with Github and we select GitSCM as source while creating job.

### What is a Jenkinsfile and what are its types ?
We have Scripted pipeline and Declarative pipeline. Both the syntax is same, but in Scripted pipeline is old one and groovy will not work in scripted but in Declarative everything will work and the syntax starts with pipeline {}

### How do you handle secrets in Jenkins ?
We use jenkins credentials plugin to securely store passwords, API tokens, SSH keys. We keep this in jobs in environment section to avoid hard coding and can be used anywhere in the stages.

### Can you explain Jenkins Master-Slave (Agent) architecture ?
- Master (Controller) Handles scheduling jobs, managing configurations, UI, and reporting.
- Slave (Agent) Executes build tasks. Multiple agents can run in parallel on different environments.
- This architecture improves scalability, as builds can be distributed across multiple nodes (Linux, Windows,
  Docker, Kubernetes).

### How do you trigger a Jenkins job automatically ?
- SCM Polling, Jenkins polls Git repo periodically.
- Webhooks, GitHub/GitLab sends an event trigger to Jenkins (preferred).
- Cron Syntax, Scheduled jobs (H/15 * * * * for every 15 minutes).
- Parameterized Trigger, Trigger job from another job with parameters.

### How do you integrate Jenkins with Docker and Kubernetes ?
- Use Docker plugin to build images inside Jenkins.
- Run builds inside Docker containers for isolation.
- Push built images to Docker Hub/ECR.
- Use Jenkins Kubernetes plugin to dynamically spin up build agents as pods.
- Deploy applications directly into Kubernetes clusters using kubectl or Helm inside Jenkins pipelines.

### What are Jenkins Shared Libraries ?
Shared Libraries allow teams to create reusable pipeline code (Groovy scripts) stored in a Git repository. Instead of duplicating code across Jenkinsfiles, you import the shared library and reuse predefined functions.

### How do you troubleshoot a failed Jenkins build ?
- Check the Console Output logs for errors.
- Verify job configuration (SCM URL, credentials, plugins).
- Ensure correct build tools (Maven, Gradle, Node, etc.) are installed.
- If running on an agent, confirm agent connectivity.

### How do you implement parallel stages in Jenkins pipeline ?
Using a parallel key word in stages

### What are Jenkins Plugins you frequently use ?
- Pipeline utility steps plugin
- AnsiColor plugin
- Git Plugin (SCM)
- Docker & Kubernetes Plugins
- SonarQube Plugin (code quality)

### How do you integrate Jenkins with AWS ?
- Install AWS CLI and configure IAM credentials in Jenkins.
- Use AWS CodeDeploy, CodePipeline, or S3 plugins.
- Store artifacts in S3 and deploy using CodeDeploy/CloudFormation/Terraform.
- Jenkins pipeline can push Docker images to Amazon ECR and deploy to EKS or ECS.


