### Permissions in Linux
Important concept we use this heavily. Make sure do this in server to get required result. To practice the permissions create one server in aws and connect to it through keypair in gitbash, in that take any file (or) create a file using touch then try "ls -l" you have a file with some notation like below.

        - rw- rw- r--
        
         -             rw-            rw-            r--
        file          user          group          others
                       u              g              o

We have three permissions like R, W, X (Read, Write, Execution). Execution access is used to run the scripts and commands. In linux when you create a user a group with same name will be created.
- To give execution permission to user then "chmod u+x <file-name>"
- Only for owner then "chmod g-rw <file-name>" removing read,write to group
- To give read access to all users to all groups then "chmod ugo+r <file-name>"
- To remove write access to a group and inside folder also then "chmod g-w -R <group-name>"

### Notations of Different Permissions
- R ---> 4 
- W ---> 2
- X ---> 1

### Example of notations to a File
- u ---> RWX (User should have Read,Write,Execute access)
- g ---> R (Group should have only Read access)
- o ---> 0 (Others should have zero access) and Usage ===> "chmod 740 <file-name>"

### User management
Creating Users and giving access to the servers we have two methods
- Password authentication mechanism
- SSH access authentication mechanism

### Password authentication mechanism
Example Ramesh joined in DevOps team
- Create user by "useradd <user-name>", Here you will get permission denied so add with root user by
  "sudo su -" (or) "sudo useradd <ramesh>"
- Create password for ramesh by "passwd ramesh", to check whether user is created or not we can check all
  user entries in "cat /etc/passwd" here UserID is the first number and second number is the groupID and
  third number is othergroupsID (or) to get clear details just "id ramesh", to get groups ---> "getent
  group", to get only a particular group then "getent group <group-name>. If this ramesh wants to connect to
  the server using IPaddress we need to change a configuration by going to "vim /etc/ssh/sshd_config" in
  gitbash only, Here by default linux is disabled for login through password authentication no, So make this
  yes, then "systemctl restart sshd". Must restart the service then only user will get access
- sshd -t ---> Will know any mistakes have done in the previous command, checks syntax of file
- So now how will ramesh login(connect) to the server ? ---> "ssh ramesh@IP"

### SSH access authentication mechanism
- Create raheem user and give access through Privatekey authentication mechanism
- I will ask the raheem to give his Public key through mail
- cd /home/raheem/ enter this command in gitbash after connecting to the server, here we will create folder
  "mkdir .ssh" and then "chmod -R 700 .ssh" here only User(raheem) has RWX(7) access and others have zero
  access, and also make the .ssh folder to raheem ownership by "chown -R raheem:raheem(group) .ssh" now
  create a file inside .ssh folder "vim authorized_key" paste the raheem public key here, ask him to create
  keypair for this. Then change modification to "chmod 400 authorized_key" so that raheem can only read, he
  cant write because it is better to put read only to protect the file.
- 7 --> RWX , 0 --> group , 0 --> others ===> "chmod -R 700 .ssh" to .ssh folder
- Now we will tell raheem that your username is configured and we will give him the IPaddress then raheem
  will login using this command "ssh -i raheem raheem@IP" Here first raheem is his Privatekey and second
  reheem is Username

### Group (groupadd group-name)
- groupadd <group-name> ---> Usage ===> groupadd DevOps
- Add ramesh to the DevOps group by "usermod -g DevOps ramesh" 
   [Note:- Every user will have a Primary group and Secondary group]
- chown ---> Even file owner also cannot run this command, only sudo user can change the ownership, so how
  to change the ownership, below are the commands
          "chown <user>:<group> <file-name>" ---> For file
          "chown <user>:<group> -R <folder-name>" ---> For folder
- We will create testing group(Temperory) and give ramesh access to testing group by
  "usermod -gG testing ramesh" a = appending ; g = Primary group ; G = Secondary group (Used for giving
  temperory access)
- After his work is done then remove ramesh by "gpasswd -d testing ramesh" deletes ramesh from testing group,
  if ramesh exit from the company then make sure he logout from the server and delete from the group
  "groupdel ramesh" ---> Deleting the group
- useradd --help
- Whole process is done manually, we can also do this by automation using shellscript
- This all process may be done by devops but generally we have dedicated linux admin they will take care of
  this user creations etc.

### Process management (37:59 to 54:09)
- ps -ef
- To know if any particular process is running (or) not "ps -ef | grep jenkins"
- When process struck kill the process ---> "kill PID" do not kill parent process id 1st is PID second one is
  parent id. If even kill cannot kill then forcefull terminate "kill -9 PID"

### Package management
- To install packages get sudo access first "sudo su -"
- "yum" command is used to install packages which we can see in RHEL,fedora,centos,awslinux etc. But 
  aws linux added onemore command that is "amazon-linux-extras" we can use both.

### Usages of package management
- "yum install <package-name>"
- "yum list installed" shows all installed,to grep anything particular "yum list installed | grep git"
- "yum list available" (or) to get wordcount "yum list available | wc -l"
- "yum search <package-name>"
- "yum remove <package-name> -y"
- To install nginx "yum install nginx -y" (or) "amazon-linux-extras install nginx1 -y"

### Points to remember
- ps -ef | grep jenkins
- yum and dnf command used to install packages
- Configuration file will be in vim /etc/ssh/sshd_config
