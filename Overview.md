### Sessions (1-11)
- What is computer and what characterstics does computer hold ? What are the use cases of Server, TV, Phone ?
- What is Client-Server architecture ? Transferring media from Phone to Laptop (Viceversa)
- How does Operating system works ? For example windows OS ? We have 2 types of OS Linux and Windows.
- What is the difference between Linux (Servers world) and Windows operating systems ?
- How to connect to Linux server (Node) ? Box ---> Server, Lock ---> Public key, Key ---> Private key
- What are the authentication mechanisms to connect to linux server ?
- Generate (or) create a link between LOCK and KEY ? 'ssh-keygen -f <file_name>' You can directly generate keys in .ssh folder
- How to enable extensions in control panel ? File explorer, view, unhide extenions for known files.
- What is the syntax of Public key ? ssh-rsa {code} Laptop-name
- What is the syntax of Private key ? BEGIN OPENSSH PRIVATE KEY {code} END OPENSSH PRIVATE KEY
- Now create a server in AWS and connect to that server using Public and Private keys.
- Import keypair in AWS by going to --> Network and security options --> Keypairs --> Actions and Import key pair (Publickey) without any gaps.
- Create a SG (Firewall) for inbound. All traffic 0.0.0.0/0 (Representation of internet)
- Launch instance with keypairs and take Amazon Linux 2AMI (HVM). Make sure the key pair name while you are creating in server should match the key pair in Network and Security.
- How to connect to server then ? 'ssh -i saikiran.pem ec2-user@IP' ---> In pwd location (User directory).
- Amazon Linux / Amazon Linux 2 ---> Default user name is 'ec2-user'
- Ubuntu ---> Default user name is 'ubuntu'
- Centos ---> Default user name is 'centos'
- Debian ---> Default user name is 'admin (or) debian'
- RHEL ---> Default user name is 'ec2-user (or) root'
- Cheapest region is us-east-1 ---> Latency is somewhat slow which is negligible.
- What is Absolute path and Relative path ? An absolute path is the complete path to a file or directory starting from the root. Relative path is relative to current directory.
- HTTP --> 80 Hypertext Transfer Protocol (Unencrypted web traffic)
- HTTPS --> 443 Hypertext Transfer Protocol Secure (Encrypted web traffic)
- SSH --> 22 Secureshell (For secure remote login and file transfer)
- SMTP --> 25 Simple Mail Transfer Protocol (Sending email)
- DNS --> 53 Domain Name System (Resolving domain names to IP addresses)
- Gitbash ---> Is an SSH client and also a mini linux.
- Protocol ---> We have different protocols like HTTP, HTTPS, SSH, SMTP, DNS etc.
- $ ---> Normal user ; # ---> Root user (Sudo su -) to exit from root just type exit.
- Pwd ---> Present working directory you will be directly land in /c/users/saikiran
- <command_name> --help ---> Get help from that particular command.
- What are the basic Git commands ? https://dzone.com/articles/top-35-git-commands-with-examples-and-bonus
- Everything is CRUD in software industry (Example of facebook)
- How to update a file with content, save, read ? Just press enter then ctrl+d
- Removing file and folder commands ? rm, rmdir, rm -r <folder_name>
- How to use copy and move commands in linux ? If you use mv command with in the same folder, it works as rename also.
- Grep command in linux is a case sensitive. Linux will treat DevOps and DEVOPS as different. So to make this case insensitive (i) use grep -i ---> 'grep -i DevOps' another example to find a package ---> 'ps -ef | grep -i nginx'
- Piping symbol | ---> One command output will become the input to another command.
- Difference between Wget and Curl commands ?
- What is Cut and Awk commands in linux ? We use cut to quickly extract what we require from the text using delimiters. We use awk when we need more advanced processing like filtering rows or formatting output.
- What are Head and Tail commands in linux ? Head is used to view the first few lines of a file while tail is used to view the last few lines. Both are useful for quickly inspecting logs or large files while 'tail -f' allows real time log monitoring.
- What is VIM in linux ? Is used for creating and editing files. Keys are i, :wq, :q!, :q, :set nu, :set nonu, :noh
- You cannot go directly from 'colon/command' mode to 'insert' mode, you need to go to the 'esc' mode first.
- Different types of search in a file in server ? :/, :?, shift+G, gg, n
- How to search a word and replace in a file ? '%s/sbin/SBIN/g' ---> g means all occurances. If you want any particular line then ':2s' s=substitute. Where ever your cursor is just press 'yy' it will copy. Just press 'p' to paste, 'u' to undo, 10p will copy 10 times.
- We have Read, Write, Execution permissions in Linux ? And file notation is R(4), W(2), X(1). Why execution is used in linux ?
- In linux when you create a user, a group with same name will be created.
- For example to give execution permission to user then 'chmod u+x' and to remove read, write access to group 'chmod g-rw'
- To give read access to all users to all groups then 'chmod ugo+r'
- To remove write access to a group and inside folder also then 'chmod g-w -R'
- User management like creating users and giving access to the servers in 2 methods.
- Password authentication mechanism and SSH access authentication mechanism.
- Create a User and Password for saikiran in server ---> 'sudo useradd saikiran' and 'passwd saikiran and all user entries will be in 'cat /etc/passwd' location. 'sudo userdel saikiran' to delete any user.
- To know userid just enter 'id saikiran' ---> 1st (uid) ; 2nd (gid) ; 3rd (other groups id). To get groups 'getent group'
- If this saikiran wants to connect to the server using IP address, we need to change a configuration in 'vim /etc/ssh/sshd_config' in gitbash. Here by default linux is disabled for login through password authentication as no, so make this yes then 'systemctl restart sshd' then saikiran will connect to server using 'ssh saikiran@IP'
- Now raheem joined and how to give SSH authentication (or) using Private key ? 'sudo useradd raheem' No need to create password for raheem because we are giving access to him using private key which is SSH.
- I will ask raheem to give his public key through mail. He should create key-pair of this.
- Sudo cd /home/raheem/ enter this command in gitbash after connecting to the server, here we will create a folder 'mkdir .ssh' now create a file inside .ssh folder 'vim authorized_key' paste raheem public key here.
- Now we will tell raheem that your username is configured and we will give him the IP address then raheem will login using this command 'ssh -i raheem raheem@IP' Here 1st raheem is his Privatekey and 2nd reheem is Username.
- The process of creating users and groups is done by linux admin team but just know how to create users and groups, adding users into groups, giving permissions to users etc.
- What is process management in linux ? Nothing but how the OS creates, monitor and terminate processes. Each process has unique id. We can monitor processes using 'ps' and 'top' commands and control them with 'kill <pid>' or 'kill -9 <pid>' commands.
- When process stuck kill the process ---> 'kill PID' do not kill parent process id 1st is PID, 2nd one is parent id. If even kill cannot kill then forceful terminate 'kill -9 PID'
- What is Package management in linux ? How the software is installed, updated or removed on the system. We use yum command ; yum list installed ; yum install <package> -y ; yum remove -y
- Algorithm for connecting to any instance ?
- What is Service management in linux ? Is about starting, stopping, monitoring and configuring background services like web servers or databases. We use tools like 'systemctl' to control them.
- Systemctl start nginx ---> This is how to make a package into service.
- Systemctl status nginx ---> To know if it is running or not (or) we can also check with process 'ps -ef | grep -i nginx'
- Systemctl stop nginx ---> To stop the service.
- Systemctl enable nginx ---> Automatically services will run.
- Systemctl disable nginx ---> Will disable nginx.
- What is Network managment in linux ? How do you check port and process running ? 'netstat -lntp' In every system we have 0-65,535 ports.
- What are the general trouble shooting process you do ?
- How to give admin access (or) any other access to linux users ? Example two types of users. Linux admin team should have Full admin access ; DevOps team should have Limited sudo access.
- Generally to give sudo access we have one file 'vim /etc/sudoers' It is not recommended to open this file because it is crucial, so linux has given one command to open then file safely that is 'visudo'
- Ramesh ---> Give Admin full access, under wheelgroup and enter %admin ALL=(ALL) ALL
- Suresh limited access ---> %devops ALL=(ALL) /usr/bin/yum,/usr/bin/systemctl
- For ramesh we have given full admin access but for suresh we can give only few limited access like 'yum' command (To know where this command is installed 'which yum' (or) 'which systemctl' (or) 'which <command-name>'
- Everytime opening 'visudo' is also a risky. Linux has given one location 'vim /etc/sudoers.d'
- vim /etc/sudoers.d/DevOps (Created folder) --> %devops ALL=(ALL) /usr/bin/yum,/usr/bin/systemctl
- vim /etc/sudoers.d/Admin (Created folder) --> %admin ALL=(ALL) ALL
- What is 3 Tier architecture ? Frontend, Backend, Database servers.
- In previous session how do we connected to servers in gitbash ?
- Then how do we connect to servers using putty and super putty (Extension for putty) ?
- In gitbash we call Privatekey as '.pem' but in putty we call it as '.ppk' (Putty privatekey)
- How to create this putty private key ? Load '.pem' file in puttygen and save with .ppk extension
- Open putty --> connection --> ssh --> auth --> credentials --> load your saved .ppk file
- Connection --> data --> username (ec2-user) --> then go to session and save (Important)
- Create a server in AWS and take the public IP and paste it in putty (Hostname) click on load to connect.
- To change the font open putty --> appearence --> change and then save to make effect in superputty also.
- What is the Linux file system structure ?
- When putty stucks (or) unable to enter any command then open putty first load your session then go to connection and give 30 in seconds then go to session and save. Generally we have value 0 you need to give any value like 30 that means every 30 seconds connection will be alive, you can give maximum 300 seconds.
- What is Inode ? For example we have a hard disk and inside the HD, we have some memory locations like a number, when you create file in HD, it will be saved in any of the memory location in HD, this file will point to memory location (A number) that is nothing but Inode. Inode is the representation of file or folder inside the memory, it is a number. How to get that number ? ls -li
- What is Symlink and Hardlink ? Symlink will point to the actual file location not to the inode while Hardlink will point directly to the inode not to the actual file location. Symlink has its own Inode.
- How to create a Symlink for a file ? First create a file hello and add content in it using cat command then create symlink 'ln -s /home/ec2-user/hello /tmp/hello-soft' you can give obsolute path or relative path.
- How to create a Hardlink for a file ? 'ln /home/ec2-user/hello /tmp/hello-hard'
- We use NGINX as frontend servers because it can handle heavy traffic, it is used as reverse proxy also. IIS is only used for windows based applications.
- We have 'winscp' for file transfer, it is a mini windows in linux server.
- Generally frontend servers called as HTTP servers on port 80. Hosts html and java based applications.
- Backend is also HTTP servers but on port 8080. Hosts applications like tomcat, jboss, .net, python etc.
- These frontend and backend servers will connect through API's
- How to know your Public IP address (Your Router like airtel) ? Just type 'What is my ip in google'
- Every router has two sections Public and Private. Modem or router will provide private IPs to the internal systems like phone, laptop, refrigerator etc. using NAT. If you type 'ipconfig' in cmd you will get all details, IPv4 is my PrivateIP. IPv4 are exhausting and we are upgrading to IPv6 till then we can use IPv4. We have 2power32 IPaddresses. If we allocate all these, we get problems. So they brought 'NAT' Network Address Translation. However latency will be slow that is nothing but time to respond will be somewhat slow.
- What is Fibre exchange points ?
- What is Enterprise archive file ? Servlets (DB) ; JSPS (UI) ---> Monolithic
- What is Monolithic vs Microservices ? Monolithic means single unified application (Enterprise archive file, where everything will be in one file only, has DB also which is nothing but 2 tier architecture), easy to start, hard to scale. Microservices will split into independent services, scalable and flexible but more complex.
- Since we have multiple servers and to connect from one server to another server 'telnet <IPaddress> <port_number>'
- If telnet is not installed ---> 'sudo yum install telnet -y' and 'netstat -lntp' shows all TCP ports currently being listened on, along with the process ids using each port. I use it in DevOps to check whether services like Nginx, MySQL or application servers are actually listening on the expected ports or not ?
- Frontend (WEB) and Backend (API) are Stateless ; DB is Statefull.
- WEB and API will work only when DB is in existence. Example of CRUD over facebook.
- We are using web servers as nginx on HTTP protocol only, it can also use HTTPS.
- Installing packages using yum and dnf. But dnf is preferred while configuring project manually because it consumes less memory when compared to yum. Yum is used in automation like shellscripting.
- Location of nginx configuration 'cd /etc/nginx/nginx.conf'
- Location of default content of nginx 'cd usr/share/nginx/html/'
- What is Forward proxy and Reverse proxy ? Nginx is used as reverse proxy.
- Reverse proxy is mainly used for Load balancers and Server anonymous.
- Location of reverse proxy configuration 'vim /etc/nginx/default.d/roboshop.conf'
- What are the famous HTTP status codes ?
- Configure the Roboshop project manually ?
- Whenever you do any changes in configuration makesure 'systemctl restart nginx'
- How to check running logs ? 'tail -f /var/log/messages'
- What is this IP 127.0.0.1 ? It's a local host which accept connections only from that particular server. It will not allow connections from external servers. To allow from external servers, we need to update to '0.0.0.0'
- How to find a particular folder or something ---> find . -name "<star>nginx<star>" Here . means current folder searching with particular name called nginx.
- To check all logs 'less -f /var/log/messages'
- What is Domain Name System (DNS) and how does it work ?
- How do you register and setup your domain ? Best and cheapest domain register is 'Hostinger'
- All components first hit redis because it's a cache server. If data is not available in redis then it will hit DB. It helps to speed up data retrieval process by storing frequently accessed data in memory rather than having to repeatedly fetch it from the root servers which will slower the response. Example of downloaded movie by 1 user.
- Steps to install any application in linux servers ?
- Shift+g ---> Go down ; gg ---> Go up ; q ---> Quit
- What is deployment or release wether it's manual or automation ?
- What is the difference between Synchronous and Asynchronous in networking ?
- How do you get authentication to github to push the developed code from VS ? We use 'Keypair authentication' instead of username and password everytime.
- How to clone any repo ? We have HTTPS and SSH.

### Session-12
- Why we use SSH based authentication to connect to github accounts ?
- What is the Port number of SSH ? 22 its a secure connection.
- We can add multiple github accounts in config file.
- You can keep your private key in any location but make sure to give correct location of your Private key in
  config file.
- Here the location of private key is created in /c/Users/saikiran & i have given ~ / saikiran.pem, how come
  the location is same ? Because when you enter command "pwd" it will show your current directory when you
  are in "~" location.
- Which one should we prefer while cloning the repo HTTPS (or) SSH ?
- HTTPS is for Username & Password, while SSH is used for Private key based authentication. But prefer HTTPS
  while cloning any repository from github.
- Github is nothing but just a folder in internet with tracking capabilities.
- What is Shibang in Shellscript (or) Bashscript ? #!/bin/bash
- If you want git in Visual Studio only, then go to View, Terminal, Select gitbash.
- If you enter wrong URL while pushing to github "git remote set-url origin <url_of_the_repository>"
- If git is not configured in the github account yet, still developers can start writing their code in VS
  until git is ready and later they can push it to the git.
- A normal folder will become git, when you initialize "git init"
- How do you capture the output of any linux command into a variable ? using command substitution like this
  DATE=$(date) ; ID=$(id -u) etc.
- What is the use of arguments in the shellscript ? $1, $2, $3... $N, $@, $#
- While connecting to external systems like DB, how to hide password while entering in terminal ?
- Is really Data-types are important in shellscript ? NO!
- What is arrays in shellscript ? Array index will start from 0,1,2,3.... We have notation for "ALL" that is
  "@" and how many args are passed is "#"
- Write a shellscript of array using FRUITS example ?

### Session-13
- Write a shellscript using condition, if given number is greater than 100, given number is lessthan 100.
- Install mysql, git, postfix, net-tools first using conditions, functions & store logs in tmp.
- Write a loop script to print numbers from 1 to 1000 ?
- Write a shellscript to install multiple packages using loops ?
- What is root user and exit status ? id=0, (id -u), $?
- What is function in shellscript ? We generally keep our functions under variables.
- There will be NO logs in "less /var/log/messages" we need to store that logs, otherwise we cannot
  troubleshoot, but the best practice is to keep a separate log file for applications and only push critical
  events to /var/log/messages. Make sure you should not log in the current folder of server come outside and
  then do.
- What is the purpose of redirection ? Nothing but storing the output in our required folder.
- How to redirect the output ? "yum install nginx -y > output.text" you can keep any name in place of output
  like saikiran.text etc.
- What are special variables in shellscript and they should be in double qotes and how do you use the colour
  coding in shellscript ?
- You should not do any changes (or) adding new files in server terminal, come one step back like after going
  to home folder (cd) like ~ ---> Here you can store the logs for practicing as siva showed in the terminal,
  here in terminal, if you get any errors (or) not working properly you can delete that folder and clone
  again from the github (NO problem).
- Sudo dnf remove <package_name> -y (or) sudo yum remove <package_name> -y 
- How do you handle the errors in shellscript ? Using a special variable called exit-status $?
- What is the disadvantage in shellscript ? Even if shellscript faces any error, it wont stop, it will
  continue to run the script. It is our responsibility to check the errors by writing conditions & exit
  status.
  
### Session-14 
- Write a shellscript to install multiple packages using loop, like giving args outside the script ?
- Configure the Roboshop project using shellscript ?
- What is SED in shellscript ? If i want permanent change (sed -i) & temperory change (sed -e) ?
- Where this SED is used in shellscript ? It is used to search, find, replace, insert or delete text in a
  file without opening the file in a text editor.
- Command to check for remote connections ? netstat -lntp
- Shellscript is like keeping all individual linux commands in one file, instead of running one by one
  commands, which was done while configuring the project manually.
- yum list installed git (or) yum list installed | grep <package_name>
- Can we set $? (Exit status) to automatically exit in shellscript ? "set -e" but it wont work.
- Instead of giving &>> $LOGFILE everywhere, we can give "exec &>$LOGFILE" under logfile name.
- What is the use of logs ? In shell scripting, logs are used to record what the script did, when it did it,
  and whether it succeeded or failed. They act like a black box recorder for your script — if something goes
  wrong, you can look back and see why.
- To see full log file ---> sudo cat /var/log/messages
- To see page by page ---> sudo less /var/log/messages
- To follow logs in real time (or) to see running logs ---> tail -f /var/log/messages

### Session-15
- unzip -o /tmp/web.zip ---> Here "o" is to overwrite, if you run the script multiple times.
- mkdir -p /app ---> Here -p means if folder exists, it will not create.
- Dont forget to restart nginx server after doing any changes in configuration file.
- Make sure to add all private servers in the web cofiguration.
  
### Session-16
- Write a shellscript to delete old logfiles which are morethan 14 days old ?
- Check Disk Usage and Send email for alerts ?
- Generally we have cat /etc/passwd in this, we have all the users information like user_id, group_id,
  user_name etc. So how to read this whole information properly (or) in a structured way ? For that we can
  use IFS (Internal field separator).
- What is the algorithm for deleting old log files ? Decide SOURCE_DIR, Search for files, Delete.
- How do you create files with old date in server ? "touch -d 20231201 <anyname.log>"
- Command to find old logfiles morethan 14 days old with .log extensions only ?
- Instead of direct rm -rf, we used while loop to read command output line by line & then delete.
- Command to check the information about total space & available space on a file system ? df -hT
- How to create a new volume (or) disk in aws console & what is the condition for that ?
- What are the commands to make the disk into usage ? Go through the overview steps of the disk creation.
- Creating disk is the work of Storage team not DevOps. But just know how it works.
- How do we find different types of file systems ? Using reverse search.
- How do you mail the above disk usage from linux server ? We will configure the company mail server details
  to send email alerts.
- So we call mail.sh whenever we want to monitor on disk_usage, not only on disk_usage, we can also call for
  CPU_Utilization, Memory_Utilization etc for monitoring purpose using shellscript, because sometimes mailing
  is not in our control, linux team will give a script like "mail.sh" we can simply call that instead of
  writing this whole command "echo "$message" | mail -s "High Disk Usage" info@joindevops.com"
- Then how to call mail.sh ? "sh mail.sh" "DevOps Team" "High Disk Usage" "$message" "info@joindevops.com"
  "ALERT High Disk Usage" Whatever you write after sh mail.sh is arguments we are passing.
- Basically no need to follow the color coding or formatting, we can just use as it is in mail configuration
  gmail.MD document (or) if your company provide the email configuration document just simply follow that.
- So configuring gmail.MD document for sending mails is morethan enough.
- Monitoring team responsibility is, if websites are down, then monitoring team will send alerts to
  Developers team. If servers are down, then monitoring team will send alerts to DevOps team.

### Session-17
- What is Crontab ? Usage of crontab & giving the script location in "crontab -e"
- How to see the running logs of a Crontab ? tail -f /var/log/cron
- What is Optargs in shellscript ? We can control the script behaviour by giving extra inputs to the script
  using a tool called Optargs.
- How to set any shellscript as Native Linux Command ? echo $PATH
- If you install any softwares in these PATHS then, automatically windows (or) linux will pick up from this
  PATHS only.
- Generally if you keep your script in "/usr/local/bin" location, then you NO need to give ".sh" while
  executing the shellscript.
- So "sudo cp 18-greetings.sh /usr/local/bin/greeting (Copied as a greeting name)
- Give executive access "sudo chmod +x /usr/local/bin/greeting" now if you are in any folder otherthan the
  script folder also, just run by using name "greeting" (or) greeting -n sai -w good evening.
- Till now we have created ec2 instances & route53 records manually by logging into aws console.
- Like if web then PublicIP, if not web then PrivateIP right ? Also if mongodb, mysql, shipping then t3.small
  and remaining t2.micro.
- We can now create using aws CLI "aws command line" to automate. In every server we have aws command line,
  you can check using "aws help" in server.
- So we need to write a script to automate using "aws CLI" for creating instances & records.
- What are Roles to Resources ? Not only for persons, resources should also have access to access another
  resource, for that we have Roles to Resources like for example if you have created one EC2 and this EC2
  instance should go and create another new instances (or) route53 records.
- How to create a role for ec2 in aws console ? IAM/Roles/Create role/Select EC2 as use case/Next/Admin
  access (or) AmazonEc2fullaccess/Route53 full access/Give any name to the role.
- How will you asign above role to the EC2 in aws console ? Select the already created instance & go to
  Actions/Security/Modify IAM role/Select your created role.
- Remove old credentials which was created for aws console (For UI) in .aws/ folder by using rm -rf, if you
  got any errors in cd location using "ls -la" command because that was hidden folder.
- Command to create instances with tags ?
- Command to list instances and find the one with your specific name tag ?
- Command to terminate the instances ?
- How do you create administrator user in aws console ? By going to IAM, Users, Create user, Attach policies
  directly, Administrator access, Click on the created user, Security credentials, Create accesskey, select
  CLI.
- Then "aws configure" after creating administrator user in aws console.
- Why we created roles in IAM ? Here if person, he can keep Access_key & Secret_keys safely, will EC2 keep
  these credentials secretly ? If anybody has access to this EC2, he can able to see these credentials using
  "ls -la" command in cd .aws/ because these keys are saved in .aws/ folder only. Thats why we have created
  roles to resources in IAM.
- Write a shellscript to create all instances & records using aws CLI ? Go through the "roboshop.sh" file in
  Roboshop-Shellscript.
- What is UPSERT in shellscript ? If the record exists, update (or) edit it, if it doesn’t exist, it will
  create the records.
- Important point, So overall create any one instance and give a role to it, so that it will create multiple
  instances from this instance only, you need to clone the "roboshop-shellscript" in the server and run the
  "roboshop.sh" script.
- We used --query is to get the PrivateIP of the instances nothing but query from the existing resource.

### Session-18
- Ansible-server (or) Configuration-server (or) Main-server (or) Controller machine.
- What are the disadvantages in shellscript ? L, S, R, E, E, S
- What are the advantages of ansible over shellscript ? O, C, A, C, O, E, P
- Ansible can create instances on external systems like azure, aws, gitlab but it is not recommended because ansible is only intended for configuration management and application deployment. Because it does not have a state file to create instances as terraform does. So thats why terraform is best for creation of infrastructure only.
- What is configuration management in general and in ansible ? As a DevOps engineer we need to do CRUD over the server effectively.
- What are the application deployment basic steps ?
- What is Idempotence Behaviour in ansible ?
- Create two servers Ansible and Node in AWS ?
- Connect to Node server from Ansible server ? 'sshpass -p DevOps321 ssh centos@NodeIP'
- Create a file in Node from Ansible server ? sshpass -p DevOps321 ssh centos@NodeIP -C "echo Hi how are you > /tmp/sai.txt"
- Install any github session in Node from ansible server ? sshpass -p DevOps321 ssh centos@NodeIP -C "curl <paste_the_RAW_URL> | sudo bash"
- To show the file content directly on terminal just use 'curl <paste_the_RAW_URL>'
- Curl command will not download the file, instead it will show the content on the terminal.
- To download the file in your local, just use 'wget <paste_the_RAW_URL>'
- What is PUSH (Ansible) architecture in ansible ? Agent less
- What is PULL (Chef) architecture in ansible, how do you configure PULL ? Install Agents
- What is the advantage of PULL based when compared to PUSH ?
- Install ansible in ansible-server and connect to Node ? 'ansible -i NodeIP, all -e ansible_user=centos -e ansible_password=DevOps321 -m ping' Hence connection is success between Ansible and Node.
- Install nginx in Node from Ansible ? ansible -i NodeIP, all -e ansible_user=centos -e ansible_password=DevOps321 --become -m yum/service -a "name=nginx state=present/started/stopped"
- What is the difference between Shell commands and Ansible modules ?
- What is the difference between Shellscript and Ansible-playbook ?
- YAML is the markup language used in ansible. Identation is mandatory in yaml format.
- What is Inventory in ansible ? Nothing but a list of hosts (Servers) where Ansible will run its automation tasks on these servers. It’s basically your address book for servers, telling Ansible what machines exist, how to connect to them and how they’re grouped.
- Go through all the files in 'Ansible' folder in VS.
- https://github.com/daws-76s/concepts/blob/master/ansible.MD

### Session-19
- Ansible-Server ---> 'sudo yum install ansible -y'
- ansible-playbook -i inventory.ini -e ansible_user=centos -e ansible_password=DevOps321 <playbook.yaml>
- ansible.builtin.ping ---> Its a ping module.
- ansible.builtin.package ---> Its a package module.
- ansible.builtin.service ---> Its a service module.
- ansible.builtin.debug ---> This module prints whatever you give.
- ansible.builtin.command ---> Used to run command on a remote machine directly without using shell.
- We have variables in ansible play-level, task-level, var_files, vars_prompt, inventory.ini, args.
- Variable preference in ansible ? CMD, Task, File, Prompt, Play, Inventory.ini, Ansible roles.
- What are Data-types in ansible ? We have Skills (List type) and Experience (Map type)
- What are conditions in ansible ? Write a condition for roboshop user exist or not ?
- Similar to $? in shell, we have "rc" in ansible to check the exit status of the previous command.
- Write ansible-playbook to loop Ramesh, Suresh, Saikiran, Mahesh.
- Write ansible-playbook to install nginx, mysql, postfix, net-tools using loop.
- Write ansible-playbook to install nginx, mysql, postfix, net-tools & also loop "name & state"
- What are tags in ansible ? Tags are used in server, if you want a particular task to run.
- ansible-playbook -t devops 16-tags.yaml ; ansible-playbook -t aws 16-tags.yaml
- When we can use tags ? For example take catalogue component, if there is any new version of catalogue, what will you do basically ? We do new deployment (or) new release right ? By using basic deployment steps.
- Command will be ---> ansible-playbook -e component=catalogue -t deployment main.yaml

### Session-20 
- Configure Roboshop Project using ansible ? Go through the 'Roboshop-ansible' in VS.
- Create all the instances & route53 records using shellscript (Roboshop.sh) script.
- Dont forget to give role to the ansible instance, before creating instances and route53 records.
- Delete the old records if exists ---> Hosted zones --> Except NS and SOA.
- In ansible we have used file module, dnf module, user module, get url modules etc.
- How to check remote connections (or) running logs ? sudo tail -f /var/log/messages.
- Black Hole ---> &>> /dev/null (Output stored here will be discarded)
- All the Users informations will be there in 'cat /etc/passwd' in server.

### Session-21
- What is 'UPSERT' in roboshop.sh file in 'Roboshop-shellscript' ? Previously it was 'CREATE' now 'UPSERT'
- What is the difference between Command and Shell ?
- Shell ---> It is like you login inside the server and run the command, Environment variables and redirections (Symbols) will work here.
- Command ---> It is like running the command outside the server, Environment variables and redirections (Symbols) will not work here.
- We used functions in shellscript to avoid the repetition of code right ? So similarly in ansible also we have Ansible Roles.

### Session-22
- We have a special file in linux called a 'Black Hole' located at /dev/null. Any data stored here will immediately discarded (Vanishes) '& >> /dev/null' Here & → runs in background, >> /dev/null → discards output.
- How to run a file (or) playbook in background ? 'nohup ansible-playbook -i inventory.ini -e ansible_user=centos -e ansible_password=DevOps321 mongodb.yaml & >> /dev/null'
- Output will be in 'tail -f nohup.out' it will not come in terminal. We cannot run every script in background because of high memory consumption, you can only run few scripts (or) a small instance in background.
- What are ansible roles ? It is a dry principle, dont repeat yourself like we have used functions in shellscript to avoid the repetition of code. It is a proper directory structure to keep our configuration and we can share this with other users also.
- Ansible roles ---> Common is also a role, we have tasks, handlers, templates, files, vars, defaults, meta, library, lookup_plugins.
- How to debug, if you are facing any error in ansible playbook ? 'ansible-playbook -vvv -i inventory.ini -e ansible_user=centos -e ansible_password=DevOps321 -e component=mongodb main.yaml' We will get the full information on terminal, what is happening in background, so that we can see where is the error.
- What are the supporting files in project ? Like mongodb.repo, catalogue.service, roboshop.conf etc.
- Creating every role is not mandatory, we create what we require.
- How to call common role (Any role) in another role ? 'ansible.builtin.import_role'
- How can we ignore errors in ansible ? Using 'ignore_errors: true'

### Session-23
- What is 'ansible.cfg' file ? It is ansible main configuration file, we can control options from here.
- How to see from where the config file is loading in ansible server ? 'ansible --version'
- What is the default location of config file ? '/etc/ansible/ansible.cfg'
- For example create a test folder in CD location 'mkdir test'
- Then cd test/ and 'cp /etc/ansible/ansible.cfg .' then pwd will be '/home/centos/test'
- Then 'export ANSIBLE_CONFIG=/home/centos/test/ansible.cfg' nothing but i have given first preference.
- When you test 'ansible --version' in any location, then you can see ansible config file is loading from the '/home/centos/test/ansible.cfg' location. Only if you set environment variable for 'ANSIBLE_CONFIG' and incase if you 'UNSET' this environment variable using 'unset ANSIBLE_CONFIG' now it will be loading from the default location that is '/etc/ansible/ansible.cfg'
- There are many options in ansible.cfg file (Ansible configuration settings) we may not use all the options, we only use what is required like inventory_path, ask_vault, timeout, user_name, passwords etc.
- What are the preferences of loading ansible.cfg file ?
- Instead of giving 'ansible-playbook -i inventory -e ansible_user=centos -e ansible_password=DevOps321 -e component=mongodb main.yaml' We can keep -i inventory as a separate file and keep your username and password in ansible.cfg then command usage is 'ansible-playbook -e component=mongodb main.yaml'
- Templates is nothing but a place holders, where we will submit our required values at the run time and it is a Jinja2 format and extension is .j2 go through the code in VS. Like we have used for catalogue.service files.
- What are Handlers in ansible roles and why we use ?
- What is the Usage of tags in ansible ? If you want to run a particular task, then we use Tags.
- How to create a full config file ? 'ansible-config init --disabled > ansible.cfg' Here disabled means by default all options are commented, you can uncomment which ever options you want to use.

### Session-24 
- Till now where we have given Username & Password ? Command line (or) 'ansible.cfg file'
- What is Ansible-Vault ? Storing secrets like keys and passwords etc.
- Difference between encoding and encryption ?
- Ansible uses mathematic algorithm (AES256) to encrypt the vault.
- How to create ansible-vault in ansible-server ?
- Practice folder (Your working directory)
- Create 'vault' folder inside the Practice folder, if we create vault folder in VS (Windows), it will not reflect in the server, so you need to create in linux server only. Same for 'group_vars' folder.
- Next create 'group_vars' folder inside the vault folder then.
- Create 'vault-file' inside the group_vars folder using below command.
- 'ansible-vault create Practice/vault/group_vars/some_name.yaml' keep your Username and Password in this file using 'ansible-vault edit group_vars/saikiran.yaml' ansible_user: centos ; ansible_password: DevOps321 and save it :wq!
- Also create ansible.cfg, inventory.ini and your playbook files (Inside the Practice folder not in vault or group_vars folders)
- Keep 'ask_vault_pass=True' in ansible.cfg (or) 'ansible-playbook saikiran.yaml --ask-vault-pass'
- How to connect to the instance ? 'ansible-playbook saikiran.yaml' since we have inventory in separate file and Username and Password are kept in vault.
- Since our whole infra is in SSM Parameter in AWS systems manager, this is also a vault from AWS, but we integrate ansible-vault with the SSM Parameter and we fetch the values from AWS instead of depending on ansible vault, ansible vault commands and all those things etc.
- What is Dynamic Inventory in ansible ? What is auto-scaling of servers ?
- For example we have 10 servers now because of traffic and i need to run (or) manage these servers using ansible playbooks. Till now we targeted only single server using ansible, but we never targeted multiple servers at a time.
- When auto-scaling is created, ansible will connect to AWS to fetch the IP addresses of the newly created servers (Using auto-scaling). How ansible will fetch IP addresses dynamically ? We have a plugin called 'aws ec2 inventory'
- For example, if you want to run update to the all the web instances then 'ansible-server' should connect to AWS and fetch instances with the Name 'web' which are present in us-east-1 region. We use 'aws ec2 inventory' plugin. Go through the 'web.aws_ec2.yaml' file in the VS.
- You can keep any name like 'saikiran.aws_ec2.yaml' but file must end with '.aws_ec2.yaml'
- Syntax of the above plugin is below, you can search in google.
  
        plugin: amazon.aws.aws_ec2
        regions:
        - us-east-1
        filters:
        tag:Name:         
        - web
  
- Here tag:Name ---> Is same as what we see Instances section in aws, there we have Name, Instance ID, Instance state, Instance type etc. So first is we want Name.
- Paste the above syntax in 'web.aws_ec2.yaml' in server in CD location using 'vim web.aws_ec2.yaml'
- Make sure to install 'botocore and boto3' then only plugin will work.
- To install botocore and boto3 using python, we use 'pip'
- First know which version of python is using in ansible ? 'ansible --version' pip should also be the same version of python.
- So 'sudo yum list | grep pip'
- sudo yum install python3.11-pip.noarch -y (Select from the above list)
- Now install 'pip3.11 install boto3 botocore'
- 'ansible-inventory -i web.aws_ec2.yaml --list' now it will fetch the instances with name 'web'
- Ansible fetched all the web-instances right ? Now if you want to connect to this web instances. 'ansible aws_ec2 -i web.aws_ec2.yaml -e ansible_user=centos -e ansible_password=DevOps321 -m ping' then web instances will give us replay 'pong'
- What is Plug and Play ? If your ansible-server wants to connect to external systems like aws, azure, gcp etc. Then we need to add some plug of aws, azure, gcp thats what we call plug, similarly if ansible have aws plugin to connect to aws ec2, then we can fetch IP addresses. That is nothing but 'AWS Dynamic inventory plugin'
- We use ansible.cfg file to minimize the commands (or) arguments to the script in server.
- Use 'ansible-vault encrypt group_vars/<some_name>.yaml' if already has existing vault.
- If you want to edit the existing vault ---> 'ansible-vault edit web.yaml'
- If you want to know wether it is encrypted or not ? 'cat group_vars/<some_name>.yaml'
- If you want to see your credentials ? then 'ansible-vault view group_vars/<some_name>.yaml'
- You can use ansible-vault anywhere in the roboshop project for any components you want.
- Earlier we used Ansible-vault but recently we migrated to AWS SSM Parameter, since our entire infra is in AWS. We integrated ansible-vault with SSM Parameter to fetch the values directly from the AWS instead of ansible-vault. Which is a seamless integration instead of depending ansible-vault and ansible-vault commands.

### Session-25
- What is terraform and why it is used ? In how many ways we configured our project ? Why we prefer ansible as configuration management while configuring the big project ?
- Why we din't prefer manual configuration over Ansible and Shellscript ?
- What are the advantages of Terraform ? V, C, A, I, C, A, M, H
- What is Inventory management in terraform ? It is about tracking all the infrastructure resources which terraform provisions and manages using terraform state file (Terraform.tfstate). This state file acts like a inventory. When you terraform plan (or) apply. It will compare your desired state with current state.
- What is declarative in terraform and How to setup and install terraform ?
- Install 'hashicorp terraform extension' to get colors.
- How to get authentication to AWS to push the created infra ? aws CLI install
- You can install aws cli in two ways ? One is regular method of downloading aws cli software and run the file in windows laptop. Another one is just run the shown commands in cmd from the internet.
- How to test wether the aws CLI is installed (or) not in cmd and gitbash ? aws --version
- If credentials are not found then do 'aws configure' before that you need to create terraform administrator user in IAM (or) use existing secret and access keys.
- Where this credentials like Secret-key and Access-key will be saved ? .aws folder
- What is the syntax of terrafrom to create any resources and what we call this syntax of terraform ?
- What is the importance of provider in terraform and what is the extension of terraform to save ?
- Where to run the terraform commands in gitbash ? Wherever .tf files exist
- What are the terraform commands and what is their functionality ?
- What is variable syntax ? Is really data-type in variable syntax is important ? NO!
- Go through this https://github.com/daws-76s/terraform
- We can also give Access-key and Secret-keys under region to get the authentication to AWS in provider section, but its not safe to do. Thats why we downloaded 'aws CLI' to authenticate.
- So Dont push the Access-key and Secret-key to the github (or) internet for safety reasons.
- Go through the all files in Terraform folder in VS.

### Session-26
- What is the importance of .gitignore file in terraform ?
- What is the use of terraform.tfvars ?
- How to give terraform.tfvars file from the command prompt for plan and apply ?
- Here terraform.tfvars name is not mandatory, we can use any name like 'saikiran.tfvars'
- If you dont give -var-file then terraform will take default values from variables.tf file
- Write a terraform code using terraform.tfvars example ?
- Variable preferences in terraform are below ?
- Command line ---> terraform plan -var="instance_type=t3.medium"
- Var_file ---> terraform plan -var-file="saikiran.tfvars"
- terraform.tfvars
- Environment variable.
- Write a terraform code, if mongodb then t3.small (or) t2.micro using condition ?
- Create instances and route53 records using Count_based loop and For_each loop ?
- Count_based is to iterate list and For_each is to iterate maps.
- What is function in terraform and what is length function here ? We cannot create our own functions, we have to use terraform inbuilt functions only.
- Why output block is used in terraform and why it is useful ? what is the syntax of output ?
- Go through the output block in count folder VS ?

### Session-27 
- What is locals in terraform and syntax of the locals ? How to call a local ?
- What is Data-sources in terraform and why it is used ? For example if you want AMI then 'terraform query ami' in google search. Here data-source is used to query the data dynamically from the providers aswel as from the existing resources also.
- Types of loops ? Count_based, For_each, Dynamic_loop
- What is Dynamic_loop and where it is useful ?
- What is Terraform State (State and Remote state) ?
- What is Declarative state and Desired state ?
- What is Current state in terraform and where it will be stored ? Terraform.tfstate
- When Desired state == Current state, then terraform will not take any action.
- When Desired state =//= Current state, then terraform will create.
- Why the terraform will create lock file while terraform is working on it ?
- Explain the concept of local state using example of when 2 persons are working on same repo ?
- What errors these persons will face, if they are working on same repo ?
- So terraform will compare my state and devops person state. If both are running terraform apply, here duplicates may come and some may get error as already exist.
- So for this issue we have a central state file to check wether the infra already exist or not ? That is remote state (S3 bucket).
- Terraform.tfstate is a crucial file, should not delete.
- What are the two disadvantages in local state ? Collaboration environment and Security
- So create S3 bucket and lock that bucket using dynamodb table ?
- What are the different remote states we have and why we use only 'terraform s3 remote state'
- Where to keep this remote state in terraform code ? Another name of remote state is Backend.
- If we write more lines of script we say configuration is increasing.
- S3 buckets are chargeable in aws, so delete after practice.
- Use different key names in s3 bucket like in the previous you have used different key 'foreach' you can use as per your wish but not with the same key names because it will merge all.
- Interview question ? We are using S3 bucket with Dynamodb locking, here local state will not work because it will create duplicates and errors, security will not be there inside the local. So we have to keep it safely in the remote storage like S3 bucket, it will provide better collaboration among the team members and also security.

### Session-28
- How to create multiple environments with terraform in 3 ways ? Using same code but with different configuration ?
- How do you control different environments in tfvars method ? Using 'startswith' function ?
- We create different buckets and dynamodb tables for Dev and Prod in tfvars method.
- And also we create different folders for Dev and Prod in VS.
- Can we use 1 bucket for both Dev and Prod in tfvars method ? YES!
- So create 2 Buckets and 2 Dynamodb tables in aws console in tfvars method with unique names ?
- You need to initialize Dev backend while terraform init and same for Prod also.
- When you are switching from one env to another env, you must reinitialize it.
- Then you can terraform plan, apply (or) destroy using -var-file
- What if you forgot to give -var-file ? It will load default values from variables.tf
- What if you commented variables.tf file also ? It will ask the user to prompt inputs. So that you will come to know i forgot to give -var-file.
- Only 1 bucket is created in workspace, inside that it will automatically create a default folder env:/ and inside this env folder, terraform will automatically create Dev and Prod workspaces.
- If you want to know workspace commands just 'terraform workspace'
- How to create workspace ? 'terraform workspace new dev' do it in gitbash.
- When you are using terraform it has default variable that is 'terraform.workspace'
- So we use 'lookup' function in workspace method to control different environments.
- lookup(map, key) ---> Giving input as map and passing the key below is the example.
- lookup(var.instance_type, terraform.workspace) 1st one is map and second one is key.
- So which approach is better ? Tfvars, Workspace, Different repos for different envs ?
- Provisioners are used to execute the commands on a local machine (or) remote server after it's created, typically used for initial configuration like boot strapping. Provisioners are used only for ec2.
- What is local-exec provisioner in terraform and what is the syntax ? It enables a keyword ${self.id}
- What is remote-exec provisioner in terraform & what is the syntax ?
- Local-exec --> Run on your local machine --> Use case is to notify, trigger local scripts --> No remote access is needed.
- Remote-exec --> Runs on your remote server --> Use case is to install softwares, configure ec2 post setup, need SSH connection to access remote host for linux and WinRM access for windows.
- What is the disadvantage of local-exec ? Local-exec provisioner run only one time not every time.
- Provisioners are useful to integrate terraform with configuration management tools like ansible to get end to end automation.
- We can write multiple provisioners also like for example 'on_failure = continue' nothing but same as ignore errors in ansible.
- What is the difference between Terraform and Ansible ?
- We can also create ec2 instances using ansible but it does not have state file as terraform does, that is why terraform is best for creation of infrastructure and ansible is best for configuration management only.
- What is Creation time and Destroy time in terraform ? Why we use them ?

### Session-29
- What is Module Development in terraform and what is the syntax ? Go through the code of EC2 module in Terraform modules in VS. Here provider.tf will not be there in module developing.
- How many types of Modules and How many types of Roles are there ?
- It is DevOps engineer responsibility to write README.md file to let others know how to use module. We keep information like what resources we have created in HA and inputs like what are required, what are optional. What outputs we are provided etc.
- Create a VPC in aws console ? CIDR (10.0.0.0/16)
- Google has given some PrivateIP address ranges those only allocated to PrivateIP not for PublicIP, there you can see 24,20,16 bit-blocks.
- Even ISP people will configure your PrivateIP address in any range among these 3 bit-blocks only.
- We can select any range, but siva selected as 10.0.0.0/16 range.
- Atleast you need to create 16 servers to use VPC '10.0.0.0/28' ---> 16 servers, 10.0.0.0/16 ---> 65k servers, generally we give VPC CIDR as 10.0.0.0/16 only, because it does not cost anything, so we can go for maximum.
- Create Public subnet in aws console ? CIDR 10.0.1.0/24
- Create Private subnet in aws console ? CIDR 10.0.2.0/24
- Create Database subnet in aws console ? CIDR 10.0.3.0/24
- Create Public, Private and Database route tables in aws console ?
- Associate Public, Private and Database route tables with their respective subnets ?
- Give internet access to the Public subnets.
- Enable Auto-asign public IPv4 address only to the Public subnet.
- Create Internet Gateway and attach to your created VPC in aws console.
- What is the difference between Public and Private subnets ?
- CIDR (Classless Inter-Domain Routing) ? We can asign custom IP address range to the subnets.
- Use always terraform best practices for naming convention like using "_" to avoid double naming.
- We used Open source modules sometimes, we have dedicated cloud team who develops modules and use them.
- How do you check internet is working or not ? ping google.com, Ipv4 is 32bit and Ipv6 is 64 bit.
- Router (Internet Gateway) ---> It has PublicIP and PrivateIP. PublicIP is nothing but just type what is my_ip in google, there you can see Ipv4 address that is your PublicIP, not ipv6. What is your PrivateIP just ipconfig in cmd there you can see IPv4 address Under wireless LAN adapter Wifi.
- What is your actual IPaddress ? Just type in google what is my IP, if anybody wants to connect to my laptop you can connect using this IP address only. You cannot connect with PrivateIP address.
- AWS wont charge for VPC, subnets, route tables, it only charges when you are creating server.
- We can create as many private subnets we want, however for functionality purpose, we have only two subnets which is Public and Private subnets.
- Watch from 26:11 to 1:14:21 to understand how VPC works.

### Session-30
- What resources we have created inside the VPC in aws console ?
- First we have created VPC in aws (Your created VPC is Isolated, even aws dont have access to it). It is like your Private Data-Center in aws cloud.
- Created Internet Gateway (IGW) and attached to the VPC.
- Created Public, Private and Database subnets in atleast 2-AZs for High Availability.
- Created Route tables (Public, Private and Database) and associated with their respective subnets in both regions 1a and 1b.
- Added Internet Gateway route in Public Route table, because internet should be enabled in Public not in Private, that is the difference between Public and Private subnets.
- Enabled Auto-asign Public IPv4 address only to the Public subnet not to the Private subnet.
- When you create a VPC, a default route table also known as main route table is automatically created to that VPC. It contains a local route that enables communication with the subnets within the VPC. While this default route table cannot be deleted, its routes can be modified and custom route tables can be created and associated with specific subnets to provide more granular control over network traffic.
- What is NAT Gateway and why it is used ?
- NAT Gateway should be created in Public subnet (1a or 1b) and why only in Public subnet ?
- Creating NAT Gateway is not enough we need to add routes between Private subnets and to the Internet gateway (NAT) which is in Public subnet.
- Which ever Private subnets like Database subnet (or) any other Private subnets wants to connect to the internet, they should add route to the NAT gateway which is in Public subnet. How to add routes is the below line ?
- Select any of the Private subnet/Routes/Edit routes/Add route (Destination = 0.0.0.0/0, Target = NAT gateway, then select default one in dropdown under Target section only)
- When you create a NAT gateway, aws will create instance in the background. We dont have access to that instance, since this instance IP is dynamic, whenever you off and on. So create ElasticIP for this instance first and then create NAT Gateway.
- NAT and ElasticIP is chargeable, so delete after practice.
- Can we get StaticIP for this instance ? YES! we can get but it is very costly thing.
- Even your home PublicIP is Dynamic. If you want StaticIP, you need to pay money to ISP provider.
- What is VPC peering and what is the condition to create VPC peering connection ?
- Create a VPC peering connection between Roboshop_VPC and Default_VPC
- So let us take Requestor VPC = Roboshop VPC ; Acceptor VPC = Default VPC
- Accept request in the same account and then add routes in VPC.
- Try to add routes in main route table, because it is the default route table which is created automatically to communicate between the subnets, if not reflecting, then add explicitly in each route table.
- If you want only one (or) two Private subnets wants to connect to the vpc peering main road then you can add in those two route tables only.
- You need to add from the other side also not just one side. This is nothing but routes in VPC.
- Go through the Terraform-aws-vpc-module, how we developed VPC and resources inside it.
- We have a Tagging strategy because we have more resources, so we use better tagging strategy.
- We have Common_tags and Resource_tags ? What is the difference between them ?
- We used merg function in tagging strategy to merge Common_tags and Resource_tags.
- You can also create s3 bucket in VPC module development.
- We can also write condition in variable syntax using 'validation' keyword

### Session-31
- Go through the code of Terraform-aws-vpc-module in VS.
- While developing VPC module, we come across Peering section, is really Peering connection is required ? Peering may not require for everyone, when this Peering is useful ?
- By default Peering connection between two VPC is not possible.
- If we want to connect with the resources which are in another VPC, then you require peering.
- How to connect to other VPC which is in another company ? Install VPN in Default_VPC and Connect.
- Example consider Requestor is Roboshop and Acceptor is User provided VPC or Default VPC.
- In VPC peering, when you are adding routes in VPC, if acceptor VPC is not in our control what you will do ? We should inform them to add the acceptor route in their terraform code.
- Big companies depends on multiple companies to deal different modules.
- So users can decide if peering is required or not ? If required they have to give VPC peering id, if they are not giving, we should consider default VPC. Go through the peering.tf file
- Overall developing your VPC module is completed and you pushed it to the internet (Github) then how to refer this ? source = "git::<https_URL>ref=main"
- So when you do terraform init, then module will be downloaded in where we are testing the code and it will automatically create a folder called module.
- Till now we used Allow-all method while creating SG, but now we use strict rules.
- How to use Security Groups effectively according to the Roboshop documentation ?
- We install VPN in Default_VPC to connect to Private instances which are Present in Roboshop_VPC.
- We can create a folder (Example) and keep all the testing code in it, so that it will be easy for everyone to use the module.
- We keep all our resources in 1a zone.
- In VPC module developing, we need to publish outputs then only users can get the information.
- We have a Database subnet group because Databases have different behaviour, nothing but just adding database subnet ids.
- We also have Open source modules for VPC, if you search in google you can use that also, instead of developing, but for practice you need to know.

### Session-32
- Till now we used Allow-all method while creating SG, it is just for practice only but now we need to follow strict SG rules according to the Roboshop Documentation only.
- We have developed our own customized module for creating VPC right ? In this session also we are going to develop our own customized module for SG. Refer Roboshop-aws-sg-module in VS.
- We created Security groups and SG rules for all components according to the Roboshop Documentation.
- Why we created separate folders for every resources in Roboshop-terraform ? Refresh time
- Since they are in separate folders, consider they are like different projects.
- Go through 01-vpc, 02-sg, 03-vpn, 04-ec2 code in Roboshop-terraform in VS.
- What is the main input required to create a SG ? VPC_ID
- For example in Big companies, 1 team is taking care for VPC, another team is taking care for SG etc. How do you get the information of resource which is in another team, project, folder ? SSM Parameter store
- What is SSM Parameter store in AWS systems manager ? Configuration storage.
- What does Configuration storage (or) Central storage do ?
- What is the Naming convention while storing Configuration is Key-Value pair in SSM ? Generally Naming format will be in linux structure like /roboshop/dev/vpc_id
- As we know Data-sources is used to query the data dynamically from the providers and also from the existing resources right ? But to query from the existing resource, we need to give some input like vpc_id, this vpc_id we cannot get from the data-source, but we used data source only to query the default vpc_id but to take the created vpc_id, again data-source is not an option, because we need to give vpc_id as input.
- Since VPC is in different folder, how do we get vpc_id in SG ? You need to store vpc_id in SSM Parameter store first and then read that saved Key-Value in SG using data-source option.
- Generally it is not mandatory to create ingress rules while creating SG and why ? But egress is static because this traffic is creating from our server, mostly it will be constant.
- In real time, whenever you want few ports to open, you need to write a mail to firewall team, then they will open the port, if they are using terraform they will do changes in main.tf file
- In Security groups, we have two names 'Name' and 'Security group name' what is the difference ?
- As a module developer, you must output the resources in output.tf file like IDs etc. So that other teams will use it.
- Now creating all Security groups according to the Roboshop Documentation. Mongodb --> Should accept connections from Catalogue and User, what should be the ingress (Security group rule) of mongodb now ? Source should be the CatalogueIP and Port 27017, Similarly for User also.
- Is CatalogueIP is constant everytime ? NO! then what should we do ? We need to take the ElasticIP which is very costly, because we have 12 Private servers, that means we need to create 12 EIPs. If Big project, we may need to create thousands of EIPs, this will generate huge bill to the company.
- So Security group has given 1 option, first create Mongodb and Catalogue Security groups.
- Then go to the Security groups in aws console and select created mongodb SG/Edit inbound rules/Add rule, Type is Custom TCP, Port 27017 and in source just type 'sg' next to the custom, you will get the created SGs, in that select already created Catalogue SG. Same for the User also.
- Now write a terraform code for all the SGs according to the Roboshop Documentation.
- Now creating EC2s for the roboshop 04-ec2 in VS using Open-source module from the internet.
- Here the only disadvantage is you cannot connect to this Private instances using SSH because Private instances dont have PublicIP. We have two options Jump host and Installing VPN in Default VPC to connect to private instances which are in Roboshop VPC but make sure you have Peering connection between Default VPC and Roboshop VPC.

### Session-33
- What are the two ways to connect to Private Instances ? Jump Host and VPN
- How to connect to Private Instances using VPN ?
- In which VPC should we install OpenVpn (or) create server for VPN ? Default_VPC
- We must have a peering connection between Default_VPC and Roboshop_VPC.
- All our private instances are in Roboshop_VPC only.
- How the traffic is routing from Home server to Private instances ?
- What is the SG rule when mongodb is accepting connections from OpenVpn ?
- Make sure to enable VPN in all private instances by giving SG of OpenVpn instance to all private instances with SSH rule.
- How to install OpenVpn in server and connect to it ? Configuring VPN is not our responsibility, we have separate team for this. We use Cisco VPN in our company which is costly but for practice we used OpenVpn Connect.

### Session-34
- We have created VPC, Security groups, VPN, Instances. So now we want all instances to automatically configured, for that we need to create ansible server in default subnet (Default VPC) this server will provision all instances using ansible playbooks and also create SG for ansible on port SSH 22 to connect to all instances securely.
- For this we need to write a small shellscript ec2-provision.sh in VS to provision the instances. NO need to give sudo access in this script because userdata will get sudo access automatically but in provisioners we need to give sudo access.
- There is one disadvantage in user-data. If user-data fails one time, it will not come again, we will address this issue with provisioners. So delete ansible-server and do again terraform init, plan, apply.
- Userdata logs will be in sudo cd /var/log, ls -la, tail -f cloud-init-output.log
- LB (Target groups and Rules) and Launch templates (Auto scaling and Policy)
- First create 2 nginx servers (UI and UX) while creating add userdata #!/bin/bash, yum install nginx -y, mkdir -p /usr/share/nginx/html/ui, echo "<h1GreaterthanSymbolHi we are from UI team<h1GreaterthanSymbol" > /usr/share/nginx/html/ui/index.html, systemctl restart nginx. Create same for Backend team.
- We are using Application LB because it is most intelligent and Classic LB is very old.
- Create LB security group, here from where the tarffic is coming to this LB ? From the internet, therefore ingress rule should be HTTP and CIDR 0.0.0.0/0
- Create SGs for these two nginx servers, these servers will get request from LB, therefore ingress rule should be a SG which is attached to LB.
- Create target groups for example UI, UX in Listeners first then register using include as pending in default subnet.
- Now create Load Balancer with port 80 in Default_VPC subnet with min two AZs.
- Rules in Load balancers, there is default rule, you can add as many rules you want, you can keep path as a condition in this UI/UX example, if path is /ui/* then send to UI target group. Keep Priority as 1.
- Load Balancer will give us a DNS name, generally we configure this name in route53 record, so create a new record, copy the DNS name and paste and you need to keep Alias and select Alias to Application and Classic Load Balancer.
- Mostly in companies, errors are not because of coding, it is because of configuration change, even if we make small changes in configuration, we get errors, so thats why we need to keep config independently in SSM Parameter store (Central storage or Configuration storage)
- SG is very important, since we are connecting to every resources present in aws.
- Individually we can understand every concept but when we configure the project using all concepts, it will create huge confusion, like for example if we give a request from client (or) from our laptop, the request should reach to the end service which is present in aws, request will cross many stages like client-side configuration should be clear, vpc, igw, subnets etc. have many resources to cross and reach the end service. So this visualization should there in us. Thats why SG is important to use in every resources.
- No Problem if you delete '.terraform' folder and lock file.
  
### Session-35
- Understand the concept of 3-Tier architecture diagram.
- Start a project Roboshop-infra-Dev in VS, this is for Dev environment, since this is multi-env, you have three options Tfvars-method, Workspace-method and Different repos for different environments, present siva is now creating different repos for different environments. Every method has pros and cons, you can tell this in interview. We also need to create for SIT, UAT, PROD Environments.
- We keep Web-ALB in https on port 443 because it is facing to the public. App-ALB is private LB, this App-ALB is within our network, we can keep this in http on port 8080 (or) 80.
- There will be NO direct connections from now, only through Load Balancer.
- We use Auto-scaling only for frontend and backend. For Databases we use RDS, DynamoDB etc.
- Creating Databases using PULL strategy. We have one disadvantage in PUSH that is Once we pushed the configuration from the ansible server to the nodes and if the configuration is disturbed or anybody did changes in ansible server, we dont have any idea, so ansible implemented PULL architecture aswel, we can schedule a crontab to PULL the configuration periodically from Git not from the ansible-server and run it, since ansible is idempotence in nature, even if the program runs multiple times, nothing will happen. So go through the code of Roboshop-ansible-roles-Terraform in VS.
- Why we use terraform provisioners (Null resource) instead of user-data ? Because we dont know wether the user-data is succeeded or not until we see the logs in server and moreover it will run only one time. But in provisioner we can see on terminal, wether the bootstrap is happening or not ?
- Every platform like azure, gcp, aws cloud platform will have its own solution to maintain configuration and secrets, in aws cloud we have more resources like ec2, dynamodb, lb etc. So for every service you may use passwords or any other secrets in the configuration at some point of time like in mysql, we have password Roboshop1@, so we have SSM Parameter store, services will refer this.
- For example in aws cloud, EC2 is a service and if this EC2 wants to retrieve the configuration or passwords which are present in SSM Parameter, then this EC2 must have access to that SSM right ? For that only we give roles to the EC2 in IAM. Second thing is here we are using ansible to provision servers, so ansible should pull the configuration or passwords whatever present in aws from SSM Parameter, then ansible should connect to the aws first, that means ansible should download boto3 and botocore python modules. Third thing is ansible-server should also have IAM role (or) IAM policy to PULL the configuration or passwords from the AWS. If these 3 things are there, we can implement vault.
- IAM role we have given in the code is iam_instance_profile = role-name, present this role has full admin access, later we can restrict in IAM concepts.
- We store passwords in SSM Parameter manually not automated.
- So first store the password in SSM Paramater, for example we have root_password in mysql right ? Store that and naming should be roboshop/dev/msql_root_pass and select secure string and value should be the password itself Roboshop@1, so here ansible should retrieve this password, for that we have a syntax called 'lookup' put this syntax in the ansible-roles, where ever this password is there.
- If you go manually like ansible.builtin.command/shell there will be no idempotence behaviour, thats why mostly use module only. If there is no official modules from ansible, we can use community modules.
- Web and App tier (If traffic increases, Auto-scaling will create instances)

### Session-36
- How is the workflow in company like from client to team members ?
- What is Launch template ? It is like hiring template like HR (Auto-scaling)
- So first create Application Load balancer is a latest generation works on TCP layer7, we can redirect to different projects using one single App_ALB.
- What is context path and host path ?
- Now create catalogue target group nothing but like a team creation. Who will take resources in this team ? HR (Auto scaling) for this we need hiring template. How this hiring template will be ready ? Below are the points.
- First create instance.
- Provision instance with ansible or shell.
- Stop the instance.
- Take the AMI from the ec2 instance only.
- Delete the instance.
- Now create launch template with AMI.
- If we give this Launch template to the auto-scaling, it will create the instances depending up on the traffic.
- Create Listener or rules.
- Create Auto-scaling policy.
  
### Session-37
- What is deregistration ? Once the de-registration is started, instance should complete its pending requests and LB should not give any new requests. We have given 300 or 60 seconds time for this.
- What is rolling update ? We have many strategies but rolling update is very famous.
- Now for web component. First create security group and then 'Web_ALB' here listener is 443 (Give access from internet) and rule should be if anybody enter 'web-dev.daws76s.online' our website should open. Before creating listener, you need to create certificate that is HTTPS, there should be a domain for certificate, so create domain on *.daws76s.online and attach this certificate to listener. Go through 07-acm in VS. If you are mentioning listener 443 then you should attach the certificate.
- You need to validate the domain, so aws will give you CNAME name and CNAME value using this you need to create a record in whichever domain you are using like we are using hostinger or in aws or some other websites, you can only create records, if you have those particular domains login credentials only.
- Few applications are in cloud VM based and few applications are in containers.
  
### Session-38
- Creating 07-acm (AWS Certificate Manager) using terraform code.
- Now start creating Web-ALB '08-web-alb'
- Now create web components '09-web'
- Then create CDN cloud front. What is CDN ? Cloud front is useful to cache only static (Like media and images) content, not dynamic content.
- AWS will charges for data transfer also, like how much data you transferred.
- Till now we have created web, catalogue right ? Next go for cart, shipping, payment etc. Nothing but do samething like copy paste, but siva told we can also develop module for this instead of copy paste, this module is only for roboshop project, not for other projects. Because backend components have same behaviour. But you can only focus on copy paste, you just know how to develop this module.

### Session-39
- Terraform-roboshop-app in VS. It is nothing but module developing for roboshop instances, this module is only for roboshop project not for other projects. Just know how siva is creating this module, you can follow the previous process only to avoid confusion. This is completely customised modules only for roboshop project.

### Session-40
- Note that redis and CDN (Cloud front) are different.
- We have Behaviours options in cloud front.
- In behaviours by default, it is sending all path patterns to the origin 'web-dev.daws76s.online'
- We can create behaviours like if '/media/* (or) /images/* ---> Then only apply cache policy and get the remaining content directly from the origin (or) Load balancer 'web-dev.daws76s.online'
- Depends upon the project, we can create cache policies. Like we can disable cache policy to the dynamic content and enable to the static content.
- What is Ordered cache behaviour ? Means you can define a priority order of caching rules (Cache /images/* differently than /api/*)
- What is Invalidation options in cloud front ? It will clear the old cache files from all the edge locations, so users always get the updated content from the origin. It is better to create Invalidation after every deployment. 
- How the traffic will travel from CDN to Web component ?
- We have two types of services. VPC based and Non VPC based what it means ?
- What is Project Infra ? Non frequently changing like VPC, SG, VPN, Databases, Web-ALB, App-ALB
- What is Application Infra ? Frequently changing like catalogue, shipping, cart etc.
- Whenever there is a change in application infra then CICD for catalogue, shipping, cart should run.
- If we give all the paths or secrets of our whole infra which is in SSM Parameter to developers, then they will create application infra on top of project infra.
- We are using shift left strategy in our pipeline like Code quality checks, Tests, Security scanning and performance testing in Dev itself, so that we can catch the issues sooner and also we can reduce the cost aswel as we can improve the software quality.

### Session-41
- What is Git and how it will track ?
- How to generate a commit-id for your content or file ? echo hello | git hash-object --stdin
- Git will calculate based on the content.
- Commit-id is also known as SHA code which has 40 characters (Universal unique id)
- git log --> You will get the commit-ids of the entire content of that repo in github.
- Git is a Key-Value pair (Key=commit-id, Value=content)
- If you want the information about the commit-id then "git cat-file <commit_id> -p"
- If you want all commit-ids in oneline ---> git log --oneline
- Protection rule in Git for main (or) master branch ?
- What is the minimum protection to the main branch ? PR, Require approvals, Require linear history, Dismiss
  stale pull request approvals when new commits are pushed.
- When you create a feature branch and you cloned the main branch. But still commit-ids of main branch &
  feature branch are same and why ? When will the commit-id of feature branch will change ?
- Once developers got approvals, he will get merge options like Merge commit, Squash and merge, Rebase and
  merge. These are nothing but merging strategies.
- Which merging strategies will be preferred among these three ?
- Most in companies go for the Merge commit, not Squash and Rebase why ?
- When to use Merge and when to use Rebase ?
- We are following feature branching strategy, we have main branch as long live branch, anything otherthan
  main branch we call it as feature branch, developers will work in feature branches, they will do CICD in
  feature branch itself, once it is successful they will raise PR, based on the discussions, PR will be
  approved and from the main branch, we do deployment into the higher environments QA, SIT, UAT, PROD.
- Once we got succeeded in merging code into the main branch, we can deploy into higher environments like QA,
  SIT, UAT, and PROD. What if we success in DEV and failed in QA ? what should i do ? again they should create
  another feature branch, they should change the code again in Dev environment and then do CICD.
- You will have ".git" folder in every repo, it stores all the information of git like tracking, metadata,
  objects etc. Everything will be stored in this folder only.

### Session-42
- How to install Jenkins in server ?
- Installing java in Jenkins is mandatory because jenkins is developed on java only, but no need to install jenkins in agent (Java is enough for the agent to work).
- Jenkins-Master may not required to know everything, but agent must know everything because actual work is done by the agent only, however logs will be shown in Jenkins-Master.
- Jenkins port number is 8080, Nexus port number is 8081.
- What is Free-style project in Jenkins ?
- What is the difference between creating aws resources in aws console & through code ?
- Difference between Free-style & Pipeline jobs ?
- Create a job first using Free-style & then Pipeline ?
- What is Pipeline script from SCM or GitOps ? 
- Write a RAW syntax of a Declarative pipeline ?
- What is agent in Jenkins ? How many agents are required ?
- How do you configure Master-Agent architecture in jenkins ? Manage jenkins, nodes, create node, executors, remote root directory, labels, launch methods, host, configure credentials, host key verification strategy. 
- Where does the entire jenkins database will be ? /var/lib/jenkins, similarly we need to create a directory for agent also in /home/centos/jenkins-agent (Any-name) because CentOS dont have sudo access in /var/lib/jenkins, it has only in home folder (or) click on question mark ? symbol, there you can see how to give the path.
- How many agents you are using in your company ? We are supporting multiple programming languages like java, python, nodesjs, .net for each language, we have 2-2 agents.
- Triggers in Jenkins pipeline ?
- Environment in Jenkins pipeline ?
- Options in Jenkins pipeline ?
- Parameters in Jenkins pipeline ?

### Session-43
- Difference between Scripted pipeline & Declarative pipeline ?
- Input option in Jenkins pipeline ?
- Create a Jenkins file for infra to vpc. Use terraform init, plan, apply. Use input option before apply. Since this pipeline is running on agent. We need to install terraform command & aws credentials (Aws configure) in agent server. While aws configure dont take sudo access because Jenkins-master is connecting to agent using centos. Search in google like install terraform linux.
- To get colors we have a plugin called ansiColor('xterm') in options itself. So install this plugin in manage jenkins, plugins. Also write a code in jenkins file in options. If plugins are not working even after installing just do systemctl restart jenkins.
- Jenkins pipeline when with parameters.
- That means overall we can write CICD for infra also.
- Before doing CICD for application infra, project infra should be ready.
- What are CI part & CD part stages in application like catalogue ?
- What is pipeline utility steps plugin ? To read the Json file.
- Next is installing dependencies ? Installing nodejs (From the roboshop documentation) in agent is mandatory in order to install npm dependency.
- Next zip (Build) the above catalogue output code nothing but artifact & store in nexus repository.
- We use Sonatype nexus because it is a widely adopted and reliable artifact repository manager. Create an instance with a minimum of 2GB RAM & 30GB storage (T3.medium). While the actual installation is typically handled by the SRE (Site Reliability Engineering) team, it's important to understand the concept. Dont worry about installation or updates. What is internal YUM repositories ? This is why Nexus acts as a central point not only for storing build artifacts but also for serving as a local repository for all required libraries and dependencies.
- Now create a cataloge repository to hold the catalogue artifacts using "maven2 hosted" format. What is maven2 hosted format ? It is popular format, used for maintaining application artifacts in unique way. Group id ---> com.roboshop, artifact id ---> catalogue, version ---> 1.0.0. Folder structure be like com/roboshop/catalogue/version folder 1.0.0, 1.0.1, 2.0.0 etc.
- We have version policy Release (Prod), Snapshot (Dev), Mixed (Both)
- Allow redeploy in Deployment policy because we are in dev.
- Now we get URL of that repository.
- Remove workspace directory after pipeline success.
- Install "Pipeline Stage View Plugin" in jenkins.
- How to create any file as backup ? Example Jenkinsfile.bkp (or) main.tf.bkp

### Session-44
- We have artifact in jenkins, how to push this to catalogue nexus repository ? We have Nexus artifact uploader plugin, install this in jenkins UI & also keep the code in jenkinsfile.
- What is the Algorithm for Catalogue (CI) ?
- What is the Algorithm for Catalogue (CD) ?
- Go through the code of Catalogue CI & CD in VS.
- What is Upstream (CI) & Downstream (CD) in jenkins pipeline ?
- How to call another pipeline from jenkins pipeline ? Using "Buildjob"
- You need to attach vpn SG to the agent, because catalogue is accepting connections from vpn.

### Session-45
- Types of scannings in jenkins pipeline ? Static source code analysis, Static Application Security Testing (SAST), Dynamic Application Security Testing (DAST), Open Source Library Scanning, Docker Image Scanning.
- We are using "Shift-Left" method, we do all types of scannings in Dev enviroment itself, to make sure everything is ok, then only we can go for the higher environments.
- How the Sonarqube scanner will work ? Installation of sonarqube is taken care by SRE team. Jenkins-Agent will clone the code in his server and it should have "scanner cli" software which need to be installed, it will scan the code and upload to the "Sonarqube" console (or) server. Then developers will see the results in "Sonarqube" console (or) server.
- Port number of sonarqube is 9000.
- Sonar-project.properties ?
- Quality Gates in sonarqube (We keep some standards) ?
- If quality gates failed, should we fail the pipeline and inform developers to fix this code ? YES
- So we should keep a condition in pipeline (Sonar-project.properties) to fail the pipeline "sonar.qualitygate.wait=true" node modules comes from internet, so NO need to scan node_modules directory here, so we put this line of code in properties "sonar.exclusions=node_modules**"
- What is multi branch pipeline ? We are using multi branch pipeline in jenkins.
- What is Jenkins shared library ? What is the process ?
- For example developers are the owner of the catalogue repository, but jenkinsfile will be managed by the DevOps engineer only. So DevOps engineer doing frequent changes in DevOps repo (Catalogue) is not good. For this only we have jenkins shared library (Centralized pipeline). For example if we have 20 repos we need to write same jenkinsfile for every repo, instead we can create and maintain the shared library repo (Groovy code, reusable pipeline steps). We can keep all multiple pipelines in jenkins shared library for different languages and deployment platforms.
- We need to inform this Jenkins shared library repo to the jenkins by going to the manage jenkins, system, global pipeline libraries, add here, default version should be main and name (Any-name), project repo should be git URL. Refer this library in jenkins pipeline using @Library('roboshop-shared-library'). We use groovy syntax in jenkinsfile #!groovy
- How to call these pipelines ? For example nodejsVM, javaVM, pythonVM is a centralized pipeline. We need to send parameters like what type of application and component to "pipelineDecission.groovy"
- "pipelineDecission.groovy" we can decide which pipeline to call.

### Session-46
- What is the pipeline process you are following in your company ? Interview question.
- We are using Multi branch pipeline & Jenkins shared library. Tools we used in this are Jenkins, Terraform, Ansible, Nexus, Sonarqube.
- We have CICD for infrastructure & application deployment.
- Basically we divide the project into 2 types Project Infra & Application infra.
- In project infra most it is one time creation like vpc, sg, vpn, databases etc. Since it is non frequently changing, we don't delete infrastructure once it is created. We are maintaining entire infra in different folders for different resources because of less refresh time and common configuration can be kept in SSM Parameter store. We make sure infra plan is reviewed before apply.
- Application infra is frequently changing as a part of release or deployment. We use launch templates, auto scaling policies, target groups, listeners, rules etc. Using this we are gradually removing the old version and making up the new version of application.
- In Application CICD, we are following shift-left method, everything will be done in Dev environment like clone, scans, unit testing, build, deployment, functional test cases etc. Once DEV deployment is over, we can deploy applications to any higher environments like SIT, UAT, etc. PROD deployments must happen through CR and JIRA process.
- https://github.com/daws-76s/concepts/blob/master/CICD.MD
- First create whole project infra using one jenkinsfile. If there is NO dependency from one folder to another folder like 04-databases & 05-app-alb. For that we have "Parallel stages" in Jenkins pipeline (We need to use a keyword called parallel) so because of this parallel, both resources will create at a time to save the time. Other folders like VPC, SG, VPN have dependencies (Like it is following sequential process). We can also add plan command or 07-acm code also.
- We can keep all static values like nexus URL, file path, credentials etc in "pipelineGlobals.groovy"
- What is change management process ?
- What is Jira to Jenkins Integration ? Jira is a ticket management tool.
  
### Session-47
- Algorithm for CICD pipeline for Roboshop is first make sure project infra (Dev & Prod) is ready. So create  one jenkinsfile for whole project infra.
- For example we are going for catalogue, then create 1 catalogue repo and download the code from roboshop documentation using wget URL or download manually into that catalogue repo & also keep jenkinsfile, point this jenkinsfile to shared library (Dry principle & centralized pipeline) & also make sure you have shared libraries configured in jenkins system configuration in manage jenkins.
- Shared library VM pipeline will be called & stages will be clone, get the version from package.json, install dependencies, unit tests, build, scans. If developer opt for deploy, we can deploy.
- Then catalogue deploy will call terraform-roboshop-app.
- We are passing environment, version, component to the bootstrap script.
- Bootstrap script will clone roboshop-ansible-roles-tf and run catalogue role.
- Now setting up CICD for user module. As a DevOps team, we have nodejs CICD is ready & a new project user module is started by the developers and how can you setup CICD for user module ? User module developers will send a mail to the DevOps team stating that we have started user module and we want DevOps team to help us to setup CICD for user module, then DevOps team will setup meeting with developers and explain our centralized pipeline structure which we used for catalogue. So now setup user module. Create 1 repo for user module and tell them to keep the jenkinsfile. Dont forget to create repo for user in nexus. If new project is started they should have repo existed in nexus, generally this will be done by SRE team.
- Few companies keep single VPN for all environments, we can also keep single VPN, but it is better to keep 1 VPN for every environment.
- Normal pipeline for CD (Deploy), Multi-branch pipeline for CI.

### Session-48
- Physical servers, Virtualization, Containerization.
- Independent Houses, Apartments, Individual rooms.
- Security is more in Physical server since everything will be in our control, while VM there are chances anybody can look into, so implement proper security in VM and Containers.
- What is Containerization ?
- What is Virtualization concept (or) VMware ? Nothing but Resource Utilization.
- Resource Utilization in VM is better when compared to Physical server, Resource Utilization in Containers is much better than VM.
- What is Dedicated Hosts in aws ?
- Resource Utilization is good in VM when compared to Physical servers like creating multiple logical servers and if require we can take extra configuration from the big physical server.
- So we have Containerization concept inside the VM. We need to create individual rooms inside the VM, but system resources (CentOS, 1GB ram, 100GB HDD) are shared, that means containers will take resources based on their demand from this system resources. System resources will dont block. Boot time is very less (With in seconds) compared to VM (EC2 instance).
- When we are moving to Docker & Kubernetes, we dont care what is the underline OS.
- What is configuration ? Example of vacating Individual house, Apartment and Room. Configuration will be less in containers when compared to Physical servers and VMs.
- What is AMI & Container ? Both are same and have FatOS (4GB)
- Docker image ---> BaseOS (5MB-250MB) + application run time + created users + created directory + installed applications.
- Working in DEV, but not working in PROD ? Main issue is configuration changes and OS. If you use different OS in QA, UAT or PROD, but the advantage of docker image is we take same image from Dev to Sit, Uat, Prod. Thats why we call it as immutable image and portable, we even dont know what is the base OS we are using, but our intention is image should work.
- How to install docker in servers ?
- When you install docker, a group called "docker" is created.
- Users who are in this group, they can only access docker commands without root user.
- So add your user (Centos) to this group. "usermod -aG docker centos"
- Then logout & login again in server.
- Now docker commands will work without root user.
- Difference between AMI & EC2 ? EC2 is the running version of AMI.
- Difference between Docker image & Container ? Container is the running version of Docker image.
- Docker commands are docker images, docker pull nginx, docker pull nginx:stable-bullseye
- Now create container from the above created image nginx "docker create nginx:latest"
- Next run "docker start <container_id>"
- To see the running containers "docker ps" ; To see all containers with all status "docker ps -a"
- To remove "docker rm <container_id>" before you need to stop "docker stop <container_id>"
- To remove without stopping ---> docker rm -f <container_id>
- To remove images ---> docker rmi <image_name>/image_id
- To remove all images at a time ---> "docker images -a -q" then "docker rmi docker images -a q"
- Instead of Pull + Create + Run commands ---> docker run nginx
- To run in background ---> docker run -d nginx
- Nginx is running now and how can i access it ? You cannot use VM port to container, so you need to allocate any port to the host first "docker run -d -p 8080:80 nginx" 8080 port is for VM or host, this is mapped with nginx port or container port 80. This is interview question, how can you expose a port of a container ?
- You cannot use same port 8080 because it is already allocated, you can use any other random ports. When you create container, you are getting random names.
- To create with name ---> docker run -d -p 8081:80 --name sai nginx
- How can you login to the existing container ? "docker exec -it <container_name/id> bash"
- How to see the base OS of a container ? cat /etc/*release
- Container will also have IP address ---> docker inspect <container_id>
- How to create our own Docker image ? Using dockerfiles

### Session-49
- What is the difference between Virtualization & Containerization (Interview question) ? Resource utilization is not good in Virtualization when compared to Containerization.
- A declarative way of creating our own docker image using dockerfiles. You can create using dockerfile reference from google. First create a repo for dockerfiles.
- We need to learn instructions for building our Roboshop as Docker images. We have multiple Instructions you can refer in Dockerfile reference from google.
- Dockerfile should be "Dockerfile" with D caps.
- First instruction is FROM. Nothing but we should have a baseOS or image, upon this image only we install everything for application.
- After cloning repo in server. How to build the created docker image ? docker build -t <URL>/<USERNAME>/<IMAGE>:<VERSION> .
- Here t --> tags, URL ---> After building the image, we need to push to somewhere right ? Which is dockerhub and URL is "docker.io" similar to dockerhub, we have ECR in aws for that also we have URL, similarly we have Nexus docker registry URL, you can push to any URL.
- Incase if you dont want to push to the dockerhub, you can create in local "docker build image:version ."
- If you want to push from local to dockerhub then just retag it "docker tag image:version url/username/image:version
- Login to docker then "docker push image:version url/username/image:version"
- Nexus repository is to maintain artifacts, Dockerhub is used to maintain docker images.

### Session-50
- What is Dockerfile & why we use different instructions ? A Dockerfile is a text file that contains a set of instructions to build a Docker image. It defines everything your container needs like OS, software, dependencies, configurations and the default command. Dockerfile is a declarative way of creating docker image. It’s like a recipe for creating a Docker image.
- We have instructions in Dockerfile FROM, RUN, CMD, LABEL, EXPOSE, ENV, COPY, ADD, ENTRYPOINT, USER, WORKDIR, ARG, ONBUILD.
- FROM ---> Defines the base image for the Dockerfile. Every Dockerfile must start with a FROM instruction.
- RUN ---> Executes commands at build time and creates a new image layer, usually for installing packages or dependencies.
- CMD ---> Defines the default command that runs when a container starts. It can be overridden at runtime.
- LABEL ---> Adds metadata to the image, like maintainer info, version, or description.
- EXPOSE ---> Documents the port the container listens on at runtime. It doesn’t publish the port; it just declares it.
- ENV ---> Sets environment variables inside the container, useful for configuration and passing dynamic values.
- COPY ---> Copies files/directories from the host machine into the container filesystem.
- ADD ---> Similar to COPY, but also supports remote URLs and automatically extracts compressed files.
- ENTRYPOINT ---> Defines the main command that always runs when the container starts. Unlike CMD, it’s not easily overridden.
- USER ---> Specifies the user (or UID/GID) under which the container will run, mainly for security to avoid root.
- WORKDIR ---> Sets the working directory for subsequent instructions like RUN, CMD, ENTRYPOINT, COPY, and ADD.
- ARG ---> Defines variables that are passed at build time using --build-arg, useful for dynamic image builds.
- ONBUILD ---> Adds a trigger instruction that executes later, when the image is used as a base for another build.
- Note that in Dockerfile, first instruction should be "FROM" nothing but referring baseOS.
- What is RUN vs CMD instruction ?
- 


### Session-51
- 

### Session-52
- How to build all images at a time ? for i in mongodb mysql catalogue cart user shipping payment web ; do cd $i ; docker build -t $i:v1 . ; cd .. ; done
- How to run all images as containers ? docker compose up -d
- What are the best practices you will follow as a DevOps engineer efficiently & securely in Docker ? Use only official images from the dockerhub, Create custom dockerfiles, Keep images & containers size small, Use multi stage builds, Use docker volumes to persist the data, Use custom networks to isolate containers from other projects, Docker system prune will delete the unused data to create free space.
- Containers are temporary, if you remove docker then data will also be deleted.
- Two types of volumes "unnamed & named volumes"
- Volumes are used only for database applications like mysql, mongodb etc.
- How to create a volume ? "docker volume create nginx" created volume should be mounted.
- You should not run container with root access because there may be a chance that container getting complete file system access of the underline host. So create one system user in hostOS which ever like if you are using alpine then create user in alpine & add it to the group (Roboshop)
- What is Docker architecture ?
- What is Docker layer ? Docker images are build in multiple layers.
- Instead of installing docker & docker compose manually, siva has created one shellscript to install automatically "curl <raw_url> | sudo bash"

### Session-53
- Kubernetes and AWS are PaaS (Platform as a Service) that means whatever the services are required to make your application up and running, everything will be provided by them only. For example to store the configuration and secrets. In AWS we have SSM parameter store. In Kubernetes we have 'ConfigMap'
- Docker is CaaS (Containers as a Service) can be used inside the PaaS also.
- What is DockerHost (or) Workstation ? Nothing but a server which we created for Docker.
- What are the disadvantages in Docker ?
- What is Orchestrator ? Kubernetes is the most popular container Orchestration tool.
- Even though Docker is used for both building the images and running the containers but we use kubernetes to run and manage the containers because of the above disadvantages in Docker.
- In VS we write Dockerfiles and Kubernetes manifest files ---> Push to Github ---> We pull Dockerfiles and Manifest files in DockerHost ---> We build images in DockerHost ---> Save it in Dockerhub ---> We push k8 manifest files to Kubernetes using 'kubectl' command which need to be installed in DockerHost.
- We can also build the images in windows laptop but windows will not directly support docker, in background windows will work around on VMware to build the images then laptop and docker will become very slow. So we have a separate server to build the images that is nothing but DockerHost (or) Workstation server.
- Kubernetes is also same as Master-Node architecture which we know in jenkins, request will first come to Kubernetes Master and this K8-master will asign work to nodes. If small project 1 Kubernetes-Master (Minikube) is enough, if big project we need to create Kubernetes Master-Node architecture.
- So first we are practicing Kubernetes-Master (Same as Jenkins-Master alone) we call it as 'Minikube' is a single node cluster. Master and Node are same here.
- We have a module in internet (Open-source) a git repo just type 'Terraform aws minikube' developed by scholz.
- Go through the code 'Terraform-aws-minikube' in VS. In this we created 'Minikube cluster server' and 'Workstation server' In workstation we setup a bootstrap to install Docker, Kubectl and Docker-compose.
- A 'kubeconfig' file is created in minikube cluster (Login to minikube server in gitbash or in server). This file contains authentication and cluster information like how to connect to minikube cluster etc. So to connect kubernetes cluster we should have 'kubectl' command (This kubectl command is automatically installed in minikube cluster). This command will check kubeconfig file in home folder only automatically because it uses kubeconfig file to determine how to connect to a minikube or kubernetes cluster. So we should create a folder '.kube' in home location and copy the kubeconfig file 'cp kubeconfig .kube/config' renaming should be config not kubeconfig. So now we connect to minikube cluster using kubectl only not using SSH connection. Here 'kubectl' means Kubernetes controller (Brain of K8)
- After creating Workstation and Minikube cluster, how to connect to Minikube from Workstation ? Install kubectl for centos8 and give execution access in Workstation server (DockerHost) Move that kubectl into /usr/local/bin/kubectl
- To connect to kubernetes cluster server (Minikube) you must have authentication file (Kubeconfig) so create one folder '.kube' in home location in DockerHost server also and paste the authentication file inside this folder. You can copy from gitbash also using cat command. Vim config (Name should be config)
- What are Kubernetes resources ? Go through the code of 'K8 resources' in VS.
- Workload resources (Pods, Deployments, StatefulSets)
- Networking resources (Services)
- Storage and config (ConfigMaps, Secrets)
- Cluster-level resources (Namespaces, Nodes)
- Every resource is in yaml format with a simple syntax. Every resource will start with apiVersion. When you push to github and pull in server then how to run that file ? kubectl apply -f <file_name>.yaml (or) kubectl create -f <file_name>.yaml and kubectl delete -f <file_name>.yaml
- What is the difference between create and apply ?
- In Docker we call container but in Kubernetes we call Pod (It is the smallest deployable unit in kubernetes). Pod can contain multiple containers. Each Pod has its own IP address.
- How to create Pod in kubernetes ? We will write a manifest file to create the Pods. Search in kubernetes.io for Pod creation, there you can see simple yaml syntax to create Pods.
- If you dont give namespace, then Pod will be created in default namespace.
- kubectl get pods ---> Will fetch pods from the default namespace, if they are available.
- kubectl get pods -n roboshop ---> Pods will be fetched from the roboshop namespace only.
- Interview question ? Write a simple Pod definition ?
  
      apiVersion: v1
      kind: Pod
      metadata:
        name: Saikiran-Pod
      spec:
        containers:
        - name: saikiran-contianer
          image: nginx
          ports:
          - containerPort: 80
  
- What is logging solution ELK in kubernetes ? Here container should store logs in 'ElasticSearch' is an external volume from AWS.
- What is Sidecar and Proxy in Pod ? Proxy means request will first come to sidecar and then main container will evaluate from where the request has come and then give reply.
- How to login to any container in kubernetes cluster ? kubectl exec -it <file_name_without.yaml> -c <container_name> --bash
- To get full information of any Pod ? kubectl describe pod
- Difference between Labels and Annotations ? Its a key-value pair. Labels are used to select (or) to attach with other kubernetes resources while, Annotations are used to connect with external objects like Load Balancers.
- Lables have limitations on length and characters of a key-value. Annotations has no limits, we can keep heavy information in annotations.

### Session-54
- We write Dockerfiles and Manifest files in VS, Push to github, We create Workstation in AWS and install all required client packages like docker, kubectl, eksctl. We pull Dockerfiles and Manifest files in DockerHost then we save created images in Dockerhub then using 'eksctl' command it will create Amazon EKS Kubernetes cluster and it will have multiple EC2 instances (or) nodes (or) Spot Node group (Is used to reduce the billing)
- We dont have SSH access to EKS kubernetes cluster (Master) it is completely managed by AWS, even Node group is also managed by AWS.
- We need to install 'eksctl' in DockerHost (Workstation) also. Refer module from internet (Open-source) git repo for installing eksctl. You can see simple yaml file to install eksctl. So write a yaml file in VS.
- Overall create 1 workstation and install all client packages like docker, docker-compose, kubectl, eksctl and login in superputty then check 'kubectl version' and 'eksctl version'
- Eksctl means 'eks controller' it is the brain of kubernetes cluster.
- From this server (Workstation) it will now create EKS kubernetes cluster, it will take time about 20min.
- First clone the eksctl repo in Workstation server and then create cluster using 'eksctl create cluster --config-file=<file_name>.yaml' Here workstation is creating ekscluster. We need to give access to AWS console before that 'aws configure' Now it will take time to create ekscluster like atleast 20min.
- What is mean by Spot Instances in kubernetes cluster ? These can be ideal for Dev not Prod.

### Session-55
- What is resource block in containers ? Nothing but we can set the limits on CPU and Memory a container can use. We have two types of limits 'Soft limit' and 'Hard limit' Requests are soft limit given when container starts and limits are hard limit.
- Write a resource definition of a Pod include resource block ?

          apiVersion: v1
          kind: Pod
          metadata:
            name: hello-pod
          spec:
            containers:
            - name: hello-container
              image: nginx
              ports:
              - containerPort: 80
              resources:
                requests:
                  cpu: "100m"
                  memory: "68Mi"
                limits:
                  cpu: "200m"
                  memory: "128Mi"

- In AWS we have SSM parameter to store the configuration and secrets, similarly every platform as a configuration and secrets storage. In kubernetes also we have 'ConfigMap' nothing but a key-value pair. So create 1 ConfigMap.
- How to define above ConfigMap key-value pair in Pod ? Set 'env:' variable, use 'valueFrom' and 'configMapkeyRef' also we have 'envFrom' what is this ? Nothing but referring configMap directly in Pod.
- Secrets in kubernetes is also a key-value pair for storing secrets. We can refer secrets using 'secretRef'
- What are 'Services' in Kubernetes ? In Kubernetes, Services are used to provide a stable way to access Pods. Because Pods are ephemeral they can be created, destroyed or moved between nodes anytime. Each Pod get its own IP address but that IP changes if the Pod restarts. If your app (Say, frontend) needs to talk to another app (Say, backend) it can’t rely on these ever-changing Pod IPs. So we have a solution that is Services, which has a fixed IP address (ClusterIP) and sometimes a DNS name to access a set of Pods. We have three types of services. ClusterIP (Purely internal to kubernetes) NordPort (You can expose to outside world) Load balancers (You can expose to outside world). That means first request will go to service then to Pod. That means Pod should be attached to the service.
- If you want Pod to Pod communication they should send a request to service first. That means we should attach Pod to a Service. How do we attach Pod to service ? Using Labels and Selectors.
- So first write a Pod definition and then Service definition in yaml file.
- What if we want multiple Pods ? We can write another Pod definition also but its not a good practice.
- What is the difference between 'ReplicaSet' and 'DeploymentSet' ?
- ReplicaSet will only creates identical Pods, if Pod crashes it will create new Pods. If you try to scale these Pods, it just create replica of Pods does not support rolling update, rollback in case of any failures.
- DeploymentSet will manage ReplicaSets also support rolling update which gradually upgrade to new version and also supports rollback, we can revert to old version incase of failure. We can also scale up and down Pods.
- Pods and ReplicaSets are the subset of DeploymentSets.
- DeploymentSet ---> Creates ReplicaSets ---> Create Pods

### Session-56
- We build image and save in Dockerhub then we write manifest file and inform Kubernetes how to run this image using this manifest file. These are the only two options we follow while configuring roboshop project.
- Configuring Roboshop project into Kubernetes. Go through the code of 'K8-roboshop' in VS.
- Start configuring mongodb component first in 'K8-roboshop' folder in VS.
- First keep all mongodb code like catalogue.js, user.js files in mongodb folder.
- Second write Dockerfile for this mongodb.
- Third write K8 manifestfile to inform kubernetes how to run this mongodb image using this manifest file.
- Now pull in 'K8-roboshop' server and login to the Docker first then build the image using 'docker build -t joindevops/mongodb:v1 .'
- Then push the mongodb image to Dockerhub using 'docker push joindevops/mongodb:v1'
- Next create manifest file (Kubernetes file) which resource should we use now ? Pod vs ReplicaSet vs DeploymentSet ? We use DeploymentSet resource. We should mention image pull policy as Always, this policy will pull the latest image everytime in Pod from the Dockerhub. If we do not keep this policy, application will not update.
- How do i force Kubernetes to re-pull an image ? Using 'imagePullPolicy: Always'
- Attach this mongodb deployment to the Service (ClusterIP) because mongodb should not be exposed to outside world.
- Now push to Github, Pull in server, Create namespace in K8-roboshop folder. In mongodb 'kubectl apply -f <filename>.yaml'
- Similarly create for catalogue and other components also.
- We have Debug Pod in Kubernetes ? In this file we can keep Pod in running for 100000 seconds, so that we can do some operations on that Pod.
- If catalogue is not connecting to mongodb 'telnet mongodb 27017' that means here catalogue Pod is in another node and mongodb Pod is in another node. So request should go like this catalogue-Pod, catalogue-Node, mongodb-Service, mongodb-Node, mongodb-Pod. Here siva has given allow all ports in SG as of now.
- Next go for the Web component. Note that if config map is changed, you should restart the Pod. In web we used Load balancer as Service because web should expose to the outside world. Similarly write for remaining components.

### Session-57
- What are Stateful and Stateless applications ?
- EBS ---> Hard disk and EFS ---> Google drive etc.
- For example we have EKS cluster and Worker nodes. Where the data will be stored ? In worker nodes only. Here Nodes and Pods are ephemeral that means temporary. Storing data in Nodes are risk because Nodes are temporary. So we should have some external storage or like temporary storage (Like Hard disk, we use which is outside the laptop) That means we take separate storage interface, we mount this storage (This can be EBS/EFS) to EKS cluster, so here data will be stored in storage (Volumes) not in worker nodes.
- Kubernetes volumes are of two types Internal volumes and External volumes.
- What are Internal volumes ? Stores data in worker nodes. Internal volumes are ephemeral (Temporary) but we have use cases like 'emptyDir' and 'Hostpath'
- These temporary volumes or ephemeral volumes will be there until Pods and Worker nodes are there. While External volumes are permanent.
- What does 'emptyDir' do in kubernetes ? A temporary storage inside the Pod.
- What does 'hostpath' and 'DaemonSet' do in kubernetes ?
- External volumes are 2 types Static provisioning and Dynamic provisioning.

### Session-58
- What is the difference between Hard disk and Cloud drives ? HD sits near to the computer. Cloud drives are network drives like google drive, icloud etc.
- EBS (Elastic block store, created outside the system say HD)
- EFS (Elastic file system, say google drive)
- External volumes are permanent. We have Static provisioning and Dynamic provisioning.
- Static provisioning ---> We have to create storage by ourself. First we need to create storage, creating storage is the responsible of storage admin or K8 admin. Create EBS volume in AWS with 10GB in same zone where the server is created. Next make this volume available to k8 cluster and also install drivers like 'aws-ebs-csi' in server because when you installing something external resource, you need to install their drivers also. A proper role (EC2 full access) should be attached to ec2 instances (Node group) to access EBS.
- What are Kubernetes resources (or) Objects ?
- What is Persistent volume in kubernetes ? It represents the external storage because as a K8 admin you dont have access to storage space. We do operations on Persistent volume. We also have PVC (Persistent volume claim) Pods should request volume through PVC. It is like a request to PV (Persistent volume)
- Pods connect to PVC ---> PVC connects to PV.
- We have restrictions on volumes like readwriteonce, readwritemany, EBS volume should have readwriteonce access only once because it is HD.
- If Pods wants some storage they should request to PV through PVC.
- When you apply, where your Pod is getting created ? In any Node. Where should that Pod is created is controlled by using 'Node selectors' we can label the nodes also. We also have 'Affinity and Anti-affinity' that means we can decide like Pod should not go to that particular nodes.
- What is Dynamic provisioning ? Volume should be created automatically by K8. In static we created external volume EBS, PV by ourself right ? But in Dynamic, we have a object called 'StorageClass' that will automatically create external storage EBS, PV aswel based on the request and also install drivers and give role to that EC2 instance.
- If networking is there then it is VPC resource, if networking is not there then it NON VPC resource.
- If Pod is created inside the namespace resource. Since storage class is cluster level resource, admin should create this, so EBS will have storageClass cluster wide.
- Go through the concept https://github.com/sivadevopsdaws74s/k8-resources/tree/master/storage
- What is Reclaim policy ? Nothing but what happens to PV when PVC is deleted, for that only we have 2 policies those are Retain policy, PV and Data will be remain. When you select Delete policy, underline volume also be deleted.
- Next EFS, create file system in AWS console. It will be more in size say 47TB for a single file. There will be No limit on size in EFS. Next create PV, PVC and use PVC in the Pod.
- What are the access points in EFS ? We can use 1 file system for entire organization also using access points. For example we can give 1 access point to roboshop project and another access point to flipkart project using unique path, user ID, group ID and permissions like 'AmazonElasticfileSystemFullAccess' in storage class.

### Session-59
- Helm charts are used for 2 purposes to templatise K8 manifest files and another one is package manager.
- Helm charts purpose is to templatise the kubernetes manifest files and package manager for kubernetes.
- Basically we do only two steps one is Build the image or pull the image if public and another one is configure the image through manifest files to run Pods.
- Once kubernetes manifest files are ready, changes in this manifest files will be very rare, so instead of changing in manifest files, we use helm charts which will keep all constant values separately to templatise manifest files without touching manifest files.
- Install Helm in server using commands from internet (or) from helm website. 
- First file to setup is 'Chart.yaml' and 'templates' folder are mandatory to templatise the manifest files. Whatever kubernetes resources you are using that must be kept in templates folder.
- Go through the code of 'Helm-charts' in VS. Here helm will hit kubectl command in the background itself.
- Understand the helm commands in helm website for example 'helm install nginx .'
- We keep constant values in 'values.yaml' file to templatise the manifest files in Helm root folder.
- How to use that value which we kept in values.yaml ? {{ .Values.deployment(Anyname).replicas }}
- Another purpose is 'Package manager' Helm is the package manager for Kubernetes. It allows you to package, version, install, upgrade and manage Kubernetes applications easily using Helm charts — similar to how apt or yum manage packages on Linux.
- What are Helm repos ? We have 'artifact HUB'
- In static provisioning we have EBS drivers right ? We installed these drivers from the internet using yaml files but here we using helm to install 'aws-ebs-csi' drivers using below steps.
- So first add helm repo in server, in this repo we have kubernetes resource files.
- Next 'helm repo update' similar to yum update
- Then install 'aws-ebs-csi' drivers using shown command in internet.
- What is Statefulset ? Used to create stateful applications in kubernetes. Nodes inside stateful applications should have static host names to communicate with other nodes. Stateful applications should follow orderly provisioning as well as terminate process.
<img width="712" height="415" alt="Screenshot 2025-10-11 214559" src="https://github.com/user-attachments/assets/459f3e93-3c31-42f3-a340-d0bd81b2c003" />
- What is Deployment ? Used to create stateless applications in kubernetes.
- What is the difference between Statefulset and Deployment ? Deployment is used for stateless applications, each pod is identical can be created and destroyed at anytime, Pod IPs will be changing after every restart and it is easy for scaling, mainly used for web, frontend and api. Statefulset are used for stateful applications, each pod has fixed name and also maintain stable storage using PVC and ensures orderly deployment and deleted in reverse sequential order. Mainly used for Databases like mongodb, mysql redis.
- Interview question ? Why Headless service is useful for StatefulSet ? Normally a Service in Kubernetes gives a single cluster IP — it load balances traffic across all Pods behind it. So instead of single IP, it will give all Pod IPs. StatefulSet manages stateful Pods, each Pod has A unique stable hostname, Its own storage PVC, Ordered creation and termination. To make this possible, the StatefulSet must have a way to give each Pod a unique DNS name.
But a Headless Service is created without a cluster IP
- Now configure mongodb in statefulset using helm. We keep Chart.yaml, templates folder, values.yaml are mandatory.
- How to run this mongodb ? 'helm install mongodb .'

### Session-60
- Continuation of configuring other components using helm charts.
- What is RBAC ?
- Creating databases using StatefulSet.
- What are the conditions to use Stateful ? First install EBS drivers using helm commands like helm repo add, update and upgrade. Give role 'AmazonEBSSCIDriverPolicy' access to EC2 instances. Install storageclass, this will create drivers automatically
- If you want better UI in kubernetes, we have a tool called 'K9s' install this tool in server from open source git called 'derailed/k9s' from internet 'viaWebi for linix and macos' after installing just type 'k9s'
- Generally we face errors in Kubernetes are like 'error image pull' because for rabbitmq we dont have customised image, it was pulled from the dockerhub, but we have given our customised path to pull the image. Another one container is not starting (CrashLoopBackOff error) means the Pods container keeps crashing and restarting repeatedly.
It usually happens due to wrong configuration, application errors or missing dependencies. You fix it by checking Pod logs and correcting the root cause.
- RBAC ---> Till now we deployed K8 resources using with admin user like 'kubectl apply' with admin access but in projects, we dont get admin access, there will be separate eks-admin team. We are DevOps engineers for roboshop project. We will only get access to Roboshop Namespace. RBAC will generally administrators will do not DevOps.
- EKS Admin Team → Controls the entire EKS cluster.
- DevOps Team (Roboshop) → Controls only their namespace (Once granted).
- HPA (Horizontal Pod Auto-scaling)
- Generally what Auto-scaling will do ? It will check the avg CPU utilization, if crosses 75% then VMs are getting increased. So similarly in kubernetes also, it should increase or decrease the Pods depending upon the traffic using HPA. So we need to install Metrics server, generally in server to check this utilization we use top command, but in kubernetes dont know how much resources are using a Pod. So for that we need to install metrics server which measures Pod resources dynamically. Install from internet. Then it will measure the Pod. Command is 'kubectl top pods'
- Next one is 'Your deployment should have resources implemented' For example 2 pods are running and i want avg utilization of these two Pods. For example life of a human limit is 100 years, so we compare years with number 100.

### Session-61
- Continuation of configuring remaining components.
- Horizontal scaling (vs) Vertical scaling ? Horizontal scaling is adding more servers. If one server crashes then remaining servers can handle requests. Vertical scaling is increasing (or) decreasing CPU and memory resources of a single Pod. Horizontal scaling is better to choose.
- Conditions to use Horizontal scaling is we should install metrics server and deployment should have resources mentioned then only it will calculate the CPU and Memory then depending up on this it will scaleup or down.
- Now we need to configure web component. Classic LB is very old. Latest one is Application LB but when it comes to kubernetes in cloud by default it is taking Classic LB. So to change this we need to use a 'ingress control' So first request will come to ingress controller then it will decide to go which application. Installing ingress controller is not DevOps work, it is by EKS admin work.
- Go through the code of 'K8-ingress' in VS.

### Session-62
- What is your Kubernetes architecture ? Nothing but incoming request to the system and outgoing request from the system.
- Control plane have few components. One of them is 'kube-apiserver' when you enter a command like 'kubectl get pods' first request goes to kube-apiserver. Kube-apiserver generally validate authentication and authorization.
- Getting information is the responsibility of kube-apiserver and handover request to Scheduler.
- Creating resources is the responsibility of Scheduler. This will decide in which node i should create Pod based on few factors like node labels and selectors, taints and tolerations, affinity and anti-affinity.
- Next component is 'etcd' is the central database of Kubernetes that stores all cluster data — like configuration, state of Pods, Nodes, Secrets and more. It is very crucial if we lose, we dont get the data back. Etcd and Control Plane will be taken care by AWS.
- Another component is 'kube-controller-manager' responsible for noticing and responding when nodes are down and then making nodes up. Job controller controls the jobs like create pods, once pod completes their task, job controller will mark as completed. Replication controller it will make sure requested number of replicas are always running.
- Node components ---> kubelet is a component that make sure nodes are connected to control plane.
- Kube-proxy component is responsible to forward the request from services to pods.
- 'Container runtime' can run any images to containers.
- All the above points are kubernetes architecture you need to explain this in interview.
- Deployment strategies, we have used rolling update.
- In Terraform, a Blue-Green Deployment means creating two identical environments — one (Blue) currently running the live app and another (Green) as a new version — then switching traffic to Green once it's tested and stable, ensuring zero downtime and easy rollback.

### Session-63
- Important point to remember that creating EKS cluster, upgrading, ingress controller are K8 admin work.
- What are taints and tolerations ?
- Taints are like 'Do Not Enter' sign on a Node.
- Tolerations are like 'Special Passes' that allow certain Pods to enter despite the sign.
- For example if i taint a node then by default scheduler cannot schedule the pod on that node. Tolerations is a excuse that allow certain Pods to enter despite having taints to Node.
- Affinity ---> Stay together and Anti-affinity ---> Stay apart
- Pod affinity means Pod 1 is running and Pod 2 likes Pod 1 then Pod 2 wants to run where the Pod 1 is running.
- Pod anti-affinity means opposite.
- How to upgrade the EKS cluster ? Before upgrading we will announce NO releases or changes to the applications. Upgrading the EKS cluster the job of K8 admin team.

### Session-64
- Monitoring concept. Actually there will be a separate team that comes under support team. It is the job of SRE role not DevOps enginner but you can tell that iam learning monitoring tools like Prometheus and Grafana.
- Monitoring are of two types White box and Black box. Black box is closed, we dont know the internal details. White box is open, we know the internal details of app (or) system.
- As a normal user how can you monitor the facebook ? By checking facebook website is running or not ? Login is working or not ? Input validations etc. All these checks are Black box because we dont know the internal details of the FB. White box monitoring can be done by those who know the internal details of the FB like facebook employees can check all FB servers are up and running ? CPU, Memory, Disk utilization, Log errors etc.
- We have 4 golden signals in monitoring ---> Latency (Low latency) Traffic (Always measure traffic like how many users are sending request) Errors (Log errors, application errors) Saturation (Measure CPU, Memory, Disk)
- What is Time series database (TSDB) used in Prometheus ? Prometheus has a built-in small database that stores all the data it collects from your servers, apps or containers — like CPU usage, memory, requests etc. But it doesn’t store data like a normal database (MySQL or MongoDB). It stores data over time — that’s why it’s called a Time Series Database (TSDB). For example 'CPU was 30% at 10:00 AM'
- In every node (Servers) have 'Node exporters' and Prometheus is connected to node exporters and it will send data to the central storage in Prometheus. You need to install nord exporters in servers. We can keep code in ansible file to install node exporter.
- What is Periodic time intervals in TSDB ? We can decide wether we want data for every 1m, 2m, 15s etc. For example if prometheus wants data from node 1 for every 5min say then prometheus will connect to node 1 exporter for every 5min and pull the metrics and save it in TSDB. We need to configure this in prometheus.yaml file
- Prometheus has few components like http-server, alert manager and service discovery (Nothing but ec2 scrapping)
- Create 1 server and install prometheus with t3.medium (30GB) because we are installing grafana also. Install prometheus from the website.
- Prometheus is collecting metrics from the node exporters and it can collects its own metrics also. If you type 'up' or 'up[2m]' in search bar, it will show the results. You can search for graph also.
- In Prometheus, graph option is not that user-friendly (We use Grafana). After installing grafana, admin is the username and password to login.
- Grafana is used for multiple sources, rightnow we are using for Prometheus. So install prometheus in grafana Data sources option. Next create 'Dashboard' you can create multiple dashboards.
- What is dynamic scrapping ? In cloud and dynamic enviroments IPs are ephemeral in auto-scaling to the newly created servers IPs, so we need to keep 'scrap_config' code in prometheus.yaml file then prometheus automatically finds new targets to scrape metrics without adding them manually. Make sure prometheus server should have minimum permission to describeInstances. So create a role for Prometheus server.
- We also have filter options to control only whichever instances we want prometheus to monitor. We should mention 'tags' in nodes.

### Session-65
- Next concept is Alerting. If instance is down or shows 0 value in grafana interface then we need to send alert to the alert manager. So raise the alert in system (You can refer the documentation from the prometheus website, you have to mention in prometheus.yaml file under rule_files)
- What is alert-manager ? It will manage all incoming alerts. Install alert manager in server from the internet and also inform prometheus.yaml file
- To send this alert in email you need to configure 'Amazon simple email service' from AWS. First add identity as email id. From this email id only we send email alerts. Next create SMTP credentials. Keep all this code in alertmanager.yaml file only.
- Prometheus datatypes are two types. Instance vector and Range vector.
- What is Instance vector ? What is the value of instance rightnow like cpu usage ? You get the latest CPU usage for each instance at this moment.
- What is Range vector ? This gives CPU usage values collected during the last 5 minutes not just one moment.
- What is scalar ? Its just a value or a single number.
- What is Counter vs Guage ? Counter will keep increasing for example a CPU. Guage means it can go UP and DOWN anytime.

### Session-66
- ELK (ElasticSearch Logstash Kibana) is a DataBase to store the log files. A popular log monitoring tool. Usually application logs shifted to this ELK for analysis and Kibana is the UI for ElasticSearch.
- So create a server for ELK and install all required components (Refer elk.MD file from siva repo)
- So now you need to push the logs from server to above created ELK. For that you need to install Agent (File beat also called as Sidecar) in sever. For example we want to ship logs from web server of roboshop. So in file beat configuration you need to replace with ELK Internal IP to push the logs (Give enabled true) and also give the path of logs which you want to access.
- We have 'Logstash' component which takes input from the agent and filter it in a proper format and push it to the ELK. So install logstash from the siva repo only.
- So here filebeat should send logs to logstash not ELK. So comment the ELK IP in filebeat.yaml configuration and uncomment the logstash lines and replace with ELK Internal IP.
