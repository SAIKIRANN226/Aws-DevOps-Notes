### Sessions (1-11)
- What is computer and what characterstics does computer hold ? What is the purpose of Server, TV, Phone ?
- What is client-server architecture ? Transferring media from phone to laptop and vice versa.
- How does windows operating system works ? We have 2 types of OS linux and windows.
- What is the difference between linux and windows operating systems ?
- How to connect to linux server (Node) ? Box ---> Server ; Lock ---> Public key ; Key ---> Private key.
- What are the authentication mechanisms to connect to any linux server ? We use SSH (Secure shell) to connect.
- Create a link between LOCK and KEY ? 'ssh-keygen -f <file_name>' you can also directly generate keys in .ssh folder
- How to enable extensions in control panel ? File explorer, view, unhide extenions for known file types.
- What is the syntax of public key ? 'ssh-rsa {code} laptop-name'
- What is the syntax of private key ? 'BEGIN OPENSSH PRIVATE KEY {code} END OPENSSH PRIVATE KEY'
- Now create a server in AWS and connect to that server using public and private keys in gitbash or server.
- Import keypair in AWS Network and security options --> Keypairs --> Actions and Import key pair (Public key) without any gaps.
- Create a SG (Firewall) for inbound. All traffic 0.0.0.0/0 (Representation of internet)
- Launch instance using keypairs and take Amazon Linux 2AMI (HVM). Make sure the key pair name while you are creating in server should match the key pair in network and security options in aws.
- How to connect to server in pwd (User directory) location ? 'ssh -i saikiran.pem ec2-user@IP'
- Amazon Linux / Amazon Linux 2 ---> Default user name is 'ec2-user'
- Ubuntu ---> Default user name is 'ubuntu'
- Centos ---> Default user name is 'centos'
- Debian ---> Default user name is 'admin (or) debian'
- RHEL ---> Default user name is 'ec2-user (or) root'
- Cheapest region is us-east-1 ---> Latency is somewhat slow which is negligible.
- What is absolute path and relative path ? An absolute path is the complete path to a file or directory starting from the root. Relative path is relative to current directory.
- HTTP --> 80 Hypertext Transfer Protocol (Unencrypted web traffic)
- HTTPS --> 443 Hypertext Transfer Protocol Secure (Encrypted web traffic)
- SSH --> 22 Secureshell (For secure remote login and file transfer)
- SMTP --> 25 Simple Mail Transfer Protocol (Sending email)
- DNS --> 53 Domain Name System (Resolving domain names to IP addresses)
- Gitbash ---> Is an SSH client and also a mini linux.
- Protocols ---> We have different types of protocols like HTTP, HTTPS, SSH, SMTP, DNS etc.
- $ ---> Normal user ; # ---> Root user (Sudo su -) to exit from root just type exit.
- Pwd ---> Present working directory you will be directly land in /c/users/saikiran
- How to get help from any particular command ? <command_name> --help
- What are the basic Git commands ? https://dzone.com/articles/top-35-git-commands-with-examples-and-bonus
- Everything is CRUD in software industry (Example of facebook)
- How to update a file with content, save, read ? Just press enter and ctrl+d
- Removing file and folder commands ? rm, rm -rf, rmdir, rm -r <folder_name>
- How to use copy and move commands in linux ? If you use mv command with in the same folder, it works as rename also.
- Grep command in linux is a case sensitive. Linux will treat DevOps and DEVOPS as different. So to make this case insensitive (i) use grep -i ---> 'grep -i DevOps' another example to find any package ---> 'ps -ef | grep -i nginx'
- Piping symbol | ---> One command output will become the input to another command.
- Difference between wget and curl commands ?
- What is cut and awk commands in linux ? We use cut to quickly extract what we require from the text using delimiters. We use awk, when we need more advanced processing like filtering rows or formatting output.
- What are head and tail commands in linux ? Head is used to view the first few lines of a file, while tail is used to view the last few lines. Both are useful for quickly inspecting logs or large files, while 'tail -f' allows real time log monitoring.
- What is VIM in linux ? Is used for creating and editing files. Keys are i, :wq, :q!, :q, :set nu, :set nonu, :noh
- You cannot go directly from 'colon/command' mode to 'insert' mode, you need to go to the 'esc' mode first.
- Different types of search in a file in server ? :/, :?, shift+g, gg, n, q
- How to search a word and replace in a file ? '%s/sbin/SBIN/g' ---> g means all occurances. If you want any particular line then ':2s' s=substitute. Where ever your cursor is just press 'yy' it will copy. Just press 'p' to paste, 'u' undo, '10p' copy 10 times.
- We have Read, Write, Execution permissions in linux ? And file notation is R(4), W(2), X(1). Why execution is used in linux ?
- In linux when you create a user, a group with same name will be created. 'sudo useradd saikiran'
- For example to give execution permission to user then 'chmod u+x' and to remove read, write access to group 'chmod g-rw'
- To give read access to all users and to all groups and others also then 'chmod ugo+r'
- To remove write access to a group and inside folder also then 'chmod g-w -R'
- User management is like creating users and giving access to the servers in 2 methods.
- Password authentication mechanism and SSH access authentication mechanism.
- Create a user and password for saikiran in server ---> 'sudo useradd saikiran' and 'passwd saikiran and all user entries will be in 'cat /etc/passwd' location. 'sudo userdel saikiran' to delete any user.
- To know userid just enter 'id saikiran' ---> 1st (uid) ; 2nd (gid) ; 3rd (other groups id). To get groups 'getent group'
- If this saikiran wants to connect to the server using IP address, we need to change a configuration in 'vim /etc/ssh/sshd_config' in gitbash. Here by default linux is disabled for login through password authentication as no, so make this yes then 'systemctl restart sshd' then saikiran will able to connect server using 'ssh saikiran@IP'
- Now raheem joined and how to give SSH authentication (or) using private key ? 'sudo useradd raheem' No need to create password for raheem because we are giving access to him using private key which is SSH.
- I will ask raheem to give his public key through mail. He should create key-pair of this using 'ssh-keygen -f <file-name>'
- Sudo cd /home/raheem/ enter this command in gitbash after connecting to the server, here we will create a folder 'mkdir .ssh' now create a file inside .ssh folder 'vim authorized_key' paste raheem public key here. Username raheem is similar to saikiran user in your laptop in C drive, here we have .ssh folder right ? Same as in raheem user, we need to create .ssh folder explicitly.
- Now we will tell raheem that your username is configured and we will give him the IP address then raheem will login using this command 'ssh -i raheem raheem@IP' Here 1st raheem is his privatekey and 2nd reheem is username.
- The process of creating users and groups is done by linux admin team but just know how to create users and groups, adding users into groups, giving permissions to users etc.
- What is process management in linux ? Nothing but how the OS creates, monitor and terminate processes. Each process has unique id. We can monitor processes using 'ps' and 'top' commands and control them with 'kill <pid>' or 'kill -9 <pid>' commands.
- When process stuck kill the process ---> 'kill PID' do not kill parent process id 1st is PID, 2nd one is parent id. If even kill cannot kill then forceful terminate 'kill -9 PID'
- What is package management in linux ? How the software is installed, updated or removed on the system. We use yum command ; yum list installed ; yum install <package> -y ; yum remove <package> -y
- Algorithm for connecting to any instance ?
- What is service management in linux ? Is about starting, stopping, monitoring. We use tools like 'systemctl' to control them. Example a courier from delhi to hyderabad.
- Systemctl start nginx ---> This is how to make a package into service.
- Systemctl status nginx ---> To know if it is running or not (or) we can also check with process 'ps -ef | grep -i nginx'
- Systemctl stop nginx ---> To stop the service.
- Systemctl enable nginx ---> Automatically services will run.
- Systemctl disable nginx ---> Will disable nginx.
- Network managment in linux ? How do you check port and process running ? 'netstat -lntp'
- What are the general trouble shooting process you do ?
- How to give admin access (or) any other access to linux users ? Example two types of users. Linux admin team should have full admin access ; DevOps team should have limited sudo access.
- Generally to give sudo access, we have one file 'vim /etc/sudoers' It is not recommended to open this file because it is crucial. So linux has given one command to open that file safely that is 'visudo'
- Ramesh ---> Give admin full access, under wheelgroup and enter %admin ALL=(ALL) ALL
- Suresh limited access ---> %devops ALL=(ALL) /usr/bin/yum,/usr/bin/systemctl
- Why adding in the wheel group only ? Because wheel group only have admin access.
- For ramesh we have given full admin access but for suresh we can only give few limited access like 'yum' command, to know where this command is installed 'which yum' (or) 'which systemctl' (or) 'which <command-name>'
- Everytime opening 'visudo' is also a risky. Linux has given one location 'vim /etc/sudoers.d'
- vim /etc/sudoers.d/DevOps (Created folder) --> %devops ALL=(ALL) /usr/bin/yum,/usr/bin/systemctl
- vim /etc/sudoers.d/Admin (Created folder) --> %admin ALL=(ALL) ALL
- What is 3 tier architecture ? Frontend, Backend and Database servers.
- In previous session how do we connected to servers in gitbash ?
- Then how do we connect to servers using putty and super putty (Extension for putty) ?
- In gitbash we call privatekey as '.pem' but in putty we call it as '.ppk' (Putty privatekey)
- How to create this putty private key ? Load '.pem' file in puttygen and save with .ppk extension
- Open putty --> connection --> ssh --> auth --> credentials --> load your saved .ppk file
- Connection --> data --> username (ec2-user) --> then go to session and save (Important)
- Create a server in AWS and take the public IP and paste it in putty (Hostname) click on load to connect.
- To change the font open putty --> appearence --> change and then save to make effect in superputty also.
- What is the linux file system structure ? cd /, boot, dev, etc, lib, home, media, mnt, tmp, var etc.
- From where the html files will load in nginx ? '/usr/share/nginx/html' we have index.html file, go to this folder 'sudo su -' then cd usr/share/nginx/html, here we can also keep your own short html format which should do in the server only.
- When putty stucks (or) unable to enter any command then open putty first load your session then go to connection and give 30 in seconds then go to session and save it. Generally we have value 0, you need to give any value like 30 that means every 30 seconds connection will be alive, you can give maximum 300 seconds.
- What is inode ? For example we have a hard disk and inside the HD we have some memory locations like numbers. When you create a file in HD, it will be saved in any of the memory locations (A number) in HD, this file will point to that memory location (A number) that is nothing but inode. Inode is the representation of file or folder inside the memory, it is a number. How to get that inode number ? 'ls -li'
- What is symlink and hardlink ? Symlink will point to the actual file location not to the inode, while hardlink will point directly to the inode, not to the actual file location. Symlink has its own inode.
- How to create a symlink for a file ? First create a file hello and add content in it using cat command then create symlink 'ln -s /home/ec2-user/hello /tmp/hello-soft' you can give obsolute path or relative path.
- How to create a hardlink for a file ? 'ln /home/ec2-user/hello /tmp/hello-hard'
- We use nginx as frontend servers because it can handle heavy traffic and it is used as reverse proxy also. IIS is only used for windows based applications. We have 'winscp' for file transfer. It is a mini windows in linux server.
- Generally frontend servers called as HTTP servers on port 80. Hosts html and java based applications. While backend is also on HTTP servers but on port 8080. Hosts applications like tomcat, jboss, .net, python etc.
- These frontend and database servers will connect through API's (Backend)
- How to know your public IP address given by your airtel subscription ? Just type 'What is my ip in google'
- Every router has two sections public and private. Modem (or) router will provide private IPs to internal systems like phone, laptop, refrigerator etc. using NAT. If you type 'ipconfig' in cmd, you will get all details. IPv4 is my private IP. IPv4 are exhausting and we are upgrading to IPv6 till then we can use IPv4. We have 2power32 IP addresses. If we allocate all these, we get problems. So they brought 'NAT' Network Address Translation. However latency will be slow that is nothing but time to respond will be some what slow.
- What is Fibre exchange points ? Nothing but how internet is working around the world.
- What is Enterprise archive file ? Servlets (DB) ; JSPS (UI) ---> Monolithic
- What is Monolithic vs Microservices ? Monolithic means single unified application (Enterprise archive file, where everything will be in one file only, has DB also which is nothing but 2 tier architecture) easy to start and hard to scale. Microservices will split into independent services, scalable and flexible but more complex.
- Since we have multiple servers and to connect from one server to another server 'telnet <IPaddress> <port_number>'
- If telnet is not installed ---> 'sudo yum install telnet -y' and 'netstat -lntp' shows all TCP ports currently being listened on, along with the process ids using each port. I use it in DevOps to check whether services like nginx, mysql or application servers are actually listening on the expected ports or not ?
- Frontend (WEB) and Backend (API) are Stateless ; DB is Statefull.
- WEB and API will work only when DB is in existence. Example of CRUD over facebook.
- We are using web servers as nginx on HTTP protocol only, it can also use HTTPS. We use nginx because it can handle heavy traffic.
- Installing packages using yum and dnf. But dnf is preferred while configuring project manually because it consumes less memory when compared to yum. Yum is used in automation like shellscripting.
- Location of nginx configuration 'cd /etc/nginx/nginx.conf'
- Location of default content of nginx 'cd usr/share/nginx/html/'
- What is forward proxy and reverse proxy ? Nginx is used as reverse proxy. Reverse proxy is mainly used for load balancers and server anonymous. Location of reverse proxy configuration 'vim /etc/nginx/default.d/roboshop.conf'
- What are the famous HTTP status codes ?
- Configure the roboshop project manually according to the documentation.
- Whenever you do any changes in nginx configuration make sure 'systemctl restart nginx'
- How to check running logs ? 'tail -f /var/log/messages' To see all logs ? 'less -f /var/log/messages'
- What is this ip 127.0.0.1 ? It's a local host which accept connections only from that particular server. It will not allow connections from the external servers. To allow from external servers, we need to update to '0.0.0.0'
- How to find a particular folder or something ? find . -name "<star>nginx<star>" Here . means current folder searching with particular name called nginx.
- How DNS will work ? When you hit 'joindevops.online' request will first go to Browser_cache --> OS_cache --> ISP_cache --> Root servers --> TLD (Top level domain) --> Name servers information --> A record.
- How do you register and setup your domain ? Best and cheapest domain register is 'Hostinger'
- All components first hit redis because it's a cache server. If data is not available in redis then it will hit DB. It helps to speed up data retrieval process by storing frequently accessed data in memory like redis rather than having to repeatedly fetch it from the root servers, which will slower the response. Example of a downloaded movie by 1 user.
- Steps to install any application in linux servers ?
- What is deployment or release wether it's manual or automation ?
- What is the difference between Synchronous and Asynchronous in networking ?
- How do you get authentication to github to push the developed code from VS ? We use 'keypair authentication' instead of username and password everytime. Public key in github settings and private key in config file (Git ssh config syntax) in .ssh folder
- How to clone any repo ? https is used with username and password, while ssh is used with private key. Mostly ssh is used by repository owners, while https is used to clone others repository in our machine, its better to clone using https only. HTTPS is used for initial setup while SSH is used for ongoing deployments because of security reasons.

### Session-12
- Why we use ssh based authentication to connect github accounts ? Port number of ssh is 22 and it's a secure connection.
- We can add multiple github accounts in config file. You can keep your private key in any location but make sure to give correct location of your private key in config file. Here the location of private key is created in '/c/Users/saikiran' and i have given ~ /saikiran.pem, how come the location is same ? Because when you enter command 'pwd' it will show your current directory when you are in '~' path. Github is nothing but just a folder in internet with tracking capabilities.
- What is shibang in shellscript (or) bashscript ? #!/bin/bash
- If you want gitbash in visual studio only then go to view, terminal, select gitbash.
- If you enter wrong URL while pushing to github 'git remote set-url origin <url_of_the_repository>'
- If git is not configured in the github account yet, still developers can start writing their code in VS until git is ready and later they can push it to git. A normal folder will become git when you initialize 'git init'
- Variables in shellscript is a dry concept like dont repeat yourself. We can call these using $ symbol.
- How do you capture the output of any linux command into a variable ? Using a command substitution like DATE=$(date), ID=$(id -u), Result=$(ls -la) etc.
- What is the use of arguments in shellscript ? It is used to pass input values to a script at run time instead of hardcoding, so this makes the script dynamic and resuable. They are accessed using variables like $1, $2, $3... $n, $@, $# inside the script.
- How to hide password while connecting to external systems like DB in terminal ? 'read -s'
- Is really data types are important in shellscript ? NO! it will automatically consider which data type is.
- What is arrays in shellscript ? Array index will start from 0,1,2,3.... we have notation for 'ALL' that is '@' and how many args are passed is '#' write a shellscript of array using FRUITS example ?
- How to switch from main-master (or) master-main branch ? git branch -M main/master
- If you want to create a folder in github with .md extension just use '/' after naming your folder and after '/' just create a file with .md extension. Example 'AWS_DevOps_Notes(Repo)/Shellscript/Session-01.md'

### Session-13
- Write a shellscript using condition. If given number is greater than 100 or less than 100.
- Install mysql, git, postfix, net-tools first using conditions, functions and also store logs in tmp folder.
- Write a script using loops to print numbers from 1 to 1000 and also install multiple packages using loops ?
- What are these ? Root user ---> id=0, (id -u) and Exit status ---> $?
- What is function in shellscript ? We generally keep functions under variables.
- There will be NO logs in 'less /var/log/messages' we need to store that logs explicitly otherwise we cannot troubleshoot but the best practice is to keep a separate log file for applications and only push critical events to '/var/log/messages' make sure when you practice logs, dont log in the working folder of server come outside and then do.
- What is the purpose of redirection ? Nothing but storing the output in our required folder or file.
- How to redirect the output ? 'yum install nginx -y > output.text' you can keep any name in place of output like saikiran.text
- What are special variables in shellscript and they should be in double qotes and how do you get colour coding in shellscript ?
- You should not do any changes (or) adding new files in server terminal, come one step back like after going to home folder (cd) like ~ ---> Here you can store the logs for practicing as siva showed in the terminal. Here in terminal, if you get any errors (or) not working properly you can delete that folder and clone again from the github (No problem)
- Sudo dnf remove <package_name> -y (or) sudo yum remove <package_name> -y 
- What is the disadvantage in shellscript ? Handling errors is the main disadvantage in shellscript because by default shellscript does not stop when error occurs, it will continue to run the script with other commands. It is our responsibility to check the errors by writing conditions and also using a special variable called exit status '$?'
  
### Session-14 
- Write a shellscript to install multiple packages using loop, like giving args outside the script ?
- Configure the roboshop project using shellscript ?
- What is SED in shellscript and where it is used ? It is used to search, find, replace, insert or delete text in a file without opening the file in a text editor. Generally vim is used for humans but for scripts, we need to use SED editor. If i want permanent change (sed -i) and temperory change (sed -e)
- Command to check for remote connections and ports opened or not ? 'netstat -lntp'
- Shellscript is like keeping all individual linux commands in one file instead of running one by one commands which was done while configuring the project manually.
- Yum list installed git (or) yum list installed | grep <package_name>
- Can we set $? (Exit status) to automatically exit in shellscript ? 'set -e' but it does not work because when you are configuring the project for the first time and you may need to create a folder and there is no folder then shellscript will automatically exit.
- Instead of giving '&>> $LOGFILE' everywhere, we can give 'exec &>$LOGFILE' under logfile name.
- What is the use of logs ? In shell scripting, logs are used to record what the script did, when it did it and whether it succeeded or failed. They act like a black box recorder for your script — if something goes wrong, you can look back and see why.
- To see full log file ---> sudo cat /var/log/messages
- To see page by page logs ---> sudo less /var/log/messages
- To follow logs in real time (or) to see running logs ---> tail -f /var/log/messages

### Session-15
- unzip -o /tmp/web.zip ---> Here 'o' is to overwrite even if you run the script multiple times.
- mkdir -p /app ---> Here 'p' means if folder exists it will not create.
- Similarly you can also write a condition like if user exist then dont add, if not add.
- Dont forget to restart nginx server after doing any changes in nginx configuration file.
- Make sure to add all private servers in web configuration.
  
### Session-16
- Write a shellscript to delete old logfiles which are morethan 14 days old ?
- Generally we have cat /etc/passwd in this, we have all the users information like user_id, group_id, user_name etc. So how to read this whole information properly (or) in a structured way ? For that we can use IFS (Internal field separator).
- Check Disk Usage and Send email for alerts ?
- What is the algorithm for deleting old log files ? Decide SOURCE_DIR, Search for files, Delete.
- How do you create files with old date in server ? touch -d 20231201 <anyname.log>
- Command to find old logfiles morethan 14 days old with .log extensions only ?
- Instead of direct rm -rf, we used while loop to read command output line by line & then delete.
- Command to check the information about total space & available space on a file system ? df -hT
- How to create a new volume (or) disk in aws console & what is the condition for that ?
- What are the commands to make the disk into usage ? Go through the overview steps of the disk creation.
- Creating disk is the work of Storage team not DevOps. But just know how it works.
- How do we find different types of file systems ? Using reverse search.
- How do you mail the above disk usage from linux server ? We will configure the company mail server details to send email alerts.
- So we call mail.sh whenever we want to monitor on disk_usage, not only on disk_usage, we can also call for CPU_Utilization, Memory_Utilization etc for monitoring purpose using shellscript, because sometimes mailing is not in our control, linux team will give a script like "mail.sh" we can simply call that instead of writing this whole command "echo "$message" | mail -s "High Disk Usage" info@joindevops.com"
- Sometimes in our company we dont have access, linux team will configure mail.sh, so we can call them by using below command.
- sh mail.sh" "DevOps Team" "High Disk Usage" "$message" "info@joindevops.com" "ALERT High Disk Usage" Whatever you write after sh mail.sh is arguments we are passing.
- Basically no need to follow the color coding or formatting, we can just use as it is in mail configuration gmail.MD document (or) if your company provide the mail configuration document just simply follow that. So configuring gmail.MD document for sending mails is morethan enough.
- Monitoring team responsibility is, if websites are down, then monitoring team will send alerts to Developers team. If servers are down, then monitoring team will send alerts to DevOps team.

### Session-17
- What is Crontab ? Usage of crontab & giving the script location in 'crontab -e'
- How to see the running logs of a Crontab ? tail -f /var/log/cron
- What is Optargs in shellscript ? We can control the script behaviour by giving extra inputs to the script using a tool called Optargs.
- How to set any shellscript as Native Linux Command ? echo $PATH
- If you install any softwares in these PATHS then, automatically windows (or) linux will pick up from this PATHS only.
- Generally if you keep your script in '/usr/local/bin' location, then you NO need to give '.sh' while executing the shellscript.
- So 'sudo cp 18-greetings.sh /usr/local/bin/greeting (Copied as a greeting name)
- Give executive access 'sudo chmod +x /usr/local/bin/greeting' now if you are in any folder other than the script folder also, just run by using name 'greeting' (or) greeting -n sai -w good evening.
- Till now we have created ec2 instances & route53 records manually by logging into aws console.
- Like if web then PublicIP, if not web then PrivateIP right ? Also if mongodb, mysql, shipping then t3.small and remaining t2.micro.
- We can now create using aws CLI 'aws command line' to automate. In every server we have aws command line, you can check using 'aws help' in server.
- So we need to write a script to automate using 'aws CLI' for creating instances & records.
- What are Roles to Resources ? Not only for persons, resources should also have access to access another resource, for that we have Roles to Resources like for example if you have created one EC2 and this EC2 instance should go and create another new instances (or) route53 records.
- How to create a role for ec2 in aws console ? IAM/Roles/Create role/Select EC2 as use case/Next/Admin access (or) AmazonEc2fullaccess/Route53 full access/Give any name to the role.
- How will you asign above role to the EC2 in aws console ? Select the already created instance & go to Actions/Security/Modify IAM role/Select your created role.
- Remove old credentials which was created for aws console (For UI) in .aws/ folder by using rm -rf, if you got any errors in cd location using 'ls -la' command because that was hidden folder.
- Command to create instances with tags ? aws ec2 run-instances --image-id ami-xxxxxxxx --count 1 --instance-type t2.micro --security-group-ids sg- 903004f8 --tag-specifications 'ResourceType=instance,Tags=[{Key=Name,Value=Saikiran_instance}]'
- Command to list instances and find the one with your specific name tag ? aws ec2 describe-instances --filters "Name=tag:Name,Values=MyInstanceName" --query "Reservations[].Instances[].InstanceId" --output text
- Command to terminate the instances ? aws ec2 terminate-instances --instance-ids i-0abc123456def7890
- How do you create administrator user in aws console ? By going to IAM, Users, Create user, Attach policies directly, Administrator access, Click on the created user, Security credentials, Create accesskey, select CLI.
- Then 'aws configure' after creating administrator user in aws console.
- Why we created roles in IAM ? Here if person, he can keep Access_key & Secret_keys safely, will EC2 keep these credentials secretly ? If anybody has access to this EC2, he can able to see these credentials using 'ls -la' command in cd .aws/ because these keys are saved in .aws/ folder only. Thats why we have created roles to resources in IAM.
- Write a shellscript to create all instances & records using aws CLI ? Go through the 'roboshop.sh' file in Roboshop-Shellscript.
- What is UPSERT in shellscript ? If the record exists, update (or) edit it, if it doesn’t exist, it will create the records.
- Important point, So overall create any one instance and give a role to it, so that it will create multiple instances from this instance only, you need to clone the 'roboshop-shellscript' in the server and run the 'roboshop.sh' script.
- We used --query is to get the PrivateIP of the instances nothing but query from the existing resource.

### Session-18
- Ansible-server (or) Configuration-server (or) Main-server (or) Controller machine.
- What are the disadvantages in shellscript ? L, S, R, E, E, S
- What are the advantages of ansible over shellscript ? O, C, A, C, O, E, P, R
- Ansible can also create instances on external systems like azure, aws, gitlab but it is not recommended because ansible is only intended for configuration management and application deployment. Because it does not have a state file to create instances as terraform does. So thats why terraform is best for creation of infrastructure only.
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
- What is PULL (Chef) architecture in ansible, how do you configure PULL ? By installing agents in nodes.
- What is the advantage of PULL based when compared to PUSH ?
- Install ansible in ansible-server and connect to Node ? sudo yum install ansible -y and then 'ansible -i NodeIP, all -e ansible_user=centos -e ansible_password=DevOps321 -m ping' Hence connection is success between Ansible and Node.
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
- Not only external hosts like web, it can also connect to the local hosts. Ansible can manage its own server also.
- We have variables in ansible play-level, task-level, var_files, vars_prompt, inventory.ini, args.
- Variable preference in ansible ? CMD, Task, File, Prompt, Play, Inventory.ini, Ansible roles.
- What are Data-types in ansible ? We have Skills (List type) and Experience (Map type)
- What are conditions in ansible ? Write a condition for roboshop user exist or not ?
- Similar to $? in shell, we have 'rc' in ansible to check the exit status of the previous command.
- Write ansible-playbook to loop Ramesh, Suresh, Saikiran, Mahesh.
- Write ansible-playbook to install nginx, mysql, postfix, net-tools using loop.
- Write ansible-playbook to install nginx, mysql, postfix, net-tools & also loop 'name & state'
- What are tags in ansible ? Tags are used in server, if you want a particular task to run.
- ansible-playbook -t devops 16-tags.yaml ; ansible-playbook -t aws 16-tags.yaml
- When we can use tags ? For example take catalogue component, if there is any new version of catalogue, what will you do basically ? We do new deployment (or) new release right ? By using basic deployment steps.
- Command will be ---> ansible-playbook -e component=catalogue -t deployment main.yaml

### Session-20 
- Configure Roboshop Project using ansible ? Go through the 'Roboshop-ansible' in VS.
- Create all instances & route53 records using shellscript (Roboshop.sh) script.
- Don't forget to give role to the ansible instance before creating instances and route53 records.
- Delete old records if exist ---> Hosted zones --> Except NS and SOA.
- In ansible we have used file module, dnf module, user module, get url module, package module, ping module, service module, debug module, command module etc.
- Black Hole ---> &>> /dev/null (Output stored here will be discarded)

### Session-21
- What is 'UPSERT' in roboshop.sh file in 'Roboshop-shellscript' ? Previously it was 'CREATE' now 'UPSERT' why ?
- What is the difference between Command and Shell ?
- Shell -> You login inside the server and run the command. Environment variables and redirections (Symbols) will work here.
- Command -> You run the command outside the server. Environment variables and redirections (Symbols) will not work here.
- We used functions in shellscript to avoid repetition of code right ? Similarly in ansible also we have ansible roles.

### Session-22
- We have a special file in linux called a 'Black Hole' located at /dev/null. Any data stored here will immediately discarded (Vanishes) '& >> /dev/null' Here & → runs in background, >> /dev/null → discards output.
- How to run a file (or) playbook in background ? 'nohup ansible-playbook -i inventory.ini -e ansible_user=centos -e ansible_password=DevOps321 mongodb.yaml & >> /dev/null'
- Output will be in 'tail -f nohup.out' it will not come in terminal. We cannot run every script in background because of high memory consumption, you can only run few scripts (or) a small instance in background.
- What are ansible roles ? It's a dry principle, dont repeat yourself like we have used functions in shellscript to avoid the repetition of code. It is a proper directory structure to keep our configuration and we can share this with other users also.
- Ansible roles ---> Common is also a role, we have tasks, handlers, templates, files, vars, defaults, meta, library, lookup_plugins.
- Lookup plugins are used for connecting to external systems using dynamic inventory.
- How to debug if you are facing any error in ansible playbook ? 'ansible-playbook -vvv -i inventory.ini -e ansible_user=centos -e ansible_password=DevOps321 -e component=mongodb main.yaml' We will get the full information on terminal like what is happening in the background, so that we can see where is the error.
- What are the supporting files in project ? Like mongodb.repo, catalogue.service, roboshop.conf etc. without these, configuration will not be complete.
- Creating every role is not mandatory, we create what we require.
- How to call common role (Any role) in another role ? 'ansible.builtin.import_role'
- How can we ignore errors in ansible ? 'ignore_errors: true'
- To set indentation in VS use 'shift+tab and tab' 

### Session-23
- What is 'ansible.cfg' file ? It is ansible main configuration file, we can control options from here.
- How to see from where the config file is loading in ansible server ? 'ansible --version'
- What is the default location of config file ? '/etc/ansible/ansible.cfg'
- For example create a test folder in CD location 'mkdir test'
- Then cd test/ and 'cp /etc/ansible/ansible.cfg .' then pwd will be '/home/centos/test'
- Then 'export ANSIBLE_CONFIG=/home/centos/test/ansible.cfg' nothing but i have given first preference.
- When you test 'ansible --version' in any location then you can see ansible config file is loading from the '/home/centos/test/ansible.cfg' location. Only if you set environment variable for 'ANSIBLE_CONFIG' and incase if you 'UNSET' this environment variable using 'unset ANSIBLE_CONFIG' now it will be loading from the default location that is '/etc/ansible/ansible.cfg'
- There are many options in ansible.cfg file (Ansible configuration settings) we may not use all the options, we only use what is required like inventory_path, ask_vault, timeout, user_name, passwords etc.
- What are the preferences of loading ansible.cfg file ?
- ANSIBLE_CONFIG (Environment variable if set)
- ansible.cfg (In the current directory)
- ~/.ansible.cfg (In the home directory)
- /etc/ansible/ansible.cfg
- So instead of giving 'ansible-playbook -i inventory -e ansible_user=centos -e ansible_password=DevOps321 -e component=mongodb main.yaml' We can keep -i inventory as a separate file and keep your username and password in ansible.cfg then command usage is 'ansible-playbook -e component=mongodb main.yaml'
- Templates is nothing but a place holders, where we will submit our required values at the run time and it is a Jinja2 format and extension is .j2 go through the code in VS. Like we have used for catalogue.service files.
- What are Handlers in ansible roles and why we use ?
- What is the Usage of tags in ansible ? If you want to run a particular task, then we use Tags.
- How to create a full config file ? 'ansible-config init --disabled > ansible.cfg' Here disabled means by default all options are commented, you can uncomment which ever options you want to use.

### Session-24 
- Till now where we have given Username and Password ? Command line (or) 'ansible.cfg' file right ?
- What is Ansible-Vault ? Storing secrets like keys and passwords etc.
- Difference between encoding and encryption ?
- Ansible uses mathematic algorithm (AES256) to encrypt the vault. Those who know the password they can only decrypt the code.
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
- What is Inventory management in terraform ? It is about tracking all the infrastructure resources which terraform has created and manage the infra using terraform state file (Terraform.tfstate). This state file acts like an inventory. When you terraform plan (or) apply. It will compare your desired state with current state.
- What is declarative in terraform and How to setup and install terraform ?
- Install 'hashicorp terraform extension' to get colors.
- How to get authentication to AWS to push the created infra ? aws CLI install
- You can install aws cli in two ways ? One is regular method of downloading aws cli software and run the file in windows laptop. Another one is just run shown commands in cmd from the internet. Before installing aws cli make sure you have created terraform user or administrator user and then configure 'aws configure'
- How to test wether the aws CLI is installed (or) not in cmd and gitbash ? 'aws --version'
- If credentials are not found then do 'aws configure' before that you need to create terraform administrator user in IAM (or) use existing secret and access keys.
- Where this credentials like Secret-key and Access-key will be saved ? '.aws' folder
- What is the syntax of terrafrom to create any resources and what we call this syntax of terraform ?
- What is the importance of provider in terraform and what is the extension of terraform to save ?
- Where to run the terraform commands in gitbash ? Wherever .tf files exist
- What are the terraform commands and what is their functionality ?
- What is variable syntax ? Is really data-type in variable syntax is important ? NO!
- Go through this https://github.com/daws-76s/terraform
- We can also give Access-key and Secret-keys under region to get the authentication to AWS in provider section but its not safe to do. Thats why we downloaded 'aws CLI' to authenticate. So Dont push the Access-key and Secret-key to the github (or) internet for security reasons.
- Go through the all files in Terraform folder in VS.

### Session-26
- What is the importance of .gitignore file in terraform ?
- What is the use of terraform.tfvars ? It will overwrite the value in variables.tf file
- How to give terraform.tfvars file from the command prompt for plan and apply ?
- Here terraform.tfvars name is not mandatory, we can use any name like 'saikiran.tfvars'
- If you dont give -var-file then terraform will take default values from variables.tf file
- Write a terraform code using terraform.tfvars example ?
- Variable preferences in terraform are below ?
- Command line ---> terraform plan -var="instance_type=t3.medium"
- Var_file ---> terraform plan -var-file="saikiran.tfvars"
- terraform.tfvars
- Environment variable.
- Write a terraform code like if mongodb then t3.small (or) t2.micro using condition ?
- Create instances and route53 records using Count_based loop and For_each loop ?
- Count_based is to iterate list and For_each is to iterate maps.
- What is function in terraform and what is length function here ? We cannot create our own functions, we have to use terraform inbuilt functions only.
- Why output block is used in terraform and why it is useful ? what is the syntax of output ?
- Go through the output block in count folder VS ?

### Session-27 
- What is locals in terraform and its syntax ? How to call a local ?
- What is Data-source in terraform and why it is used ? For example if you want AMI then 'terraform query ami' in google search. Here data-source is used to query the data dynamically from the providers aswel as from the existing resources.
- Types of loops ? Count_based, For_each, Dynamic_loop
- What is Dynamic_loop and where it is useful ?
- What is Terraform State (State and Remote state) ?
- What is Declarative state and Desired state ?
- What is Current state in terraform and where the created resources will be stored ? In terraform.tfstate file that is nothing but current state.
- When Desired state == Current state then terraform will not take any action.
- When Desired state =//= Current state then terraform will create.
- Why the terraform will create lock file while terraform is working on it ?
- Explain the concept of local state using example of when 2 persons are working on same repo ?
- What errors these persons will face, if they are working on same repo ? So terraform will compare my state and devops person state. If both are running terraform apply, here duplicates may come and some may get error as already exist.
- So for this issue we have a central state file to check wether the infra already exist or not ? That is remote state (S3 bucket).
- Terraform.tfstate is a crucial file should not be deleted.
- What are the two disadvantages in local state ? Collaboration environment and Security.
- So create S3 bucket and lock that bucket using dynamodb table ?
- What are the different remote states we have and why we use only 'terraform s3 remote state'
- Where to keep this remote state in terraform code ? Inside the provider and another name of remote state is Backend.
- If we write more lines of script we say configuration is increasing.
- S3 buckets are chargeable in aws, so delete after practice.
- Use different key names in s3 bucket like in the previous you have used different key 'foreach' you can use as per your wish but not with the same key names because it will merge all.
- Interview question ? We are using S3 bucket with Dynamodb locking. Here local state will not work because it will create duplicates and errors, security will not be there inside the local. So we have to keep it safely in the remote storage like S3 bucket, it will provide better collaboration among the team members and also security.

### Session-28
- How to create multiple environments with terraform in 3 ways ? Using same code but with different configuration ?
- How do you control different environments in tfvars method ? Using 'startswith' function ?
- We create different buckets and dynamodb tables for Dev and Prod in tfvars method.
- And also we create different folders for Dev and Prod in VS.
- Can we use 1 bucket for both Dev and Prod in tfvars method ? YES!
- So create 2 Buckets and 2 Dynamodb tables in aws console in tfvars method with unique names ?
- You need to initialize Dev backend while terraform init and same for Prod also. 'terraform init -backend-config=dev/backend.tf'
- When you are switching from one env to another env, you must reinitialize it using 'terraform init -reconfigure -backend-config=prod/backend.tf'
- How to terraform plan, apply (or) destroy using -var-file ? 'terraform plan -var-file=dev/dev.tfvars'
- What if you forgot to give -var-file ? It will load default values from variables.tf
- What if you commented variables.tf file also ? It will ask the user to prompt inputs. So that you will come to know you forgot to give -var-file.
- Only 1 bucket is created in workspace, inside that it will automatically create a default folder env:/ and inside this env folder, terraform will automatically create Dev and Prod workspaces.
- If you want to know workspace commands just 'terraform workspace'
- How to create workspace ? 'terraform workspace new dev' do it in gitbash.
- When you are using terraform it has default variable that is 'terraform.workspace' what is it ? If you are in dev then the value of terraform.workspace will becomes 'dev' if you are in prod then the value of terraform.workspace will becomes 'prod'
- So we use 'lookup' function in workspace method to control different environments.
- lookup(map, key) ---> Giving input as map and passing the key below is the example.
- lookup(var.instance_type, terraform.workspace) 1st one is map and second one is key.
- So which approach is better ? Tfvars, Workspace, Different repos for different envs ?
- Provisioners are used to execute the commands on a local machine (or) remote server after it's created, typically used for initial configuration like boot strapping. Provisioners are used only for ec2.
- What is local-exec provisioner in terraform and what is the syntax ? It enables a keyword ${self.id}
- What is remote-exec provisioner in terraform and what is the syntax ?
- Local-exec --> Run on your local machine --> Use case is to notify, trigger local scripts --> No remote access is needed.
- Remote-exec --> Runs on your remote server --> Use case is to install softwares, configure ec2 post setup, need SSH connection to access remote host for linux and WinRM access for windows.
- What is the disadvantage of local-exec ? Local-exec provisioner run only one time not every time.
- Provisioners are useful to integrate terraform with configuration management tools like ansible to get end to end automation.
- We can write multiple provisioners also like for example 'on_failure = continue' nothing but same as ignore errors in ansible.
- What is the difference between Terraform and Ansible ?
- We can also create ec2 instances using ansible but it does not have state file as terraform does, that is why terraform is best for creation of infrastructure and ansible is best for configuration management only.
- What is Creation time and Destroy time in terraform ? Why we use them ?

### Session-29
- What is module development in terraform and what is the syntax ? Go through the code of EC2 module in Terraform modules in VS. Here provider.tf will not be there in module developing.
- How many types of modules and how many types of roles are there ?
- It is DevOps engineer responsibility to write 'README.MD' file to let others know how to use module. We keep information like what resources we have created and inputs like what are required, what are optional, what outputs we have published etc.
- Create a VPC in aws console ? CIDR (10.0.0.0/16)
- Google has given some private_ip address ranges those only allocated to private_ip not for public_ip, there you can see 24,20,16 bit-blocks. Even ISP people will configure your private_ip address in any range among these 3 bit-blocks only.
- We can select any range but siva selected as 10.0.0.0/16 range.
- You need to create atleast 16 servers to use VPC '10.0.0.0/28' ---> 16 servers, 10.0.0.0/16 ---> 65k servers. Generally go for maximum VPC CIDR as 10.0.0.0/16 because it does not cost anything.
- Create Public subnet in aws console ? CIDR 10.0.1.0/24
- Create Private subnet in aws console ? CIDR 10.0.2.0/24
- Create Database subnet in aws console ? CIDR 10.0.3.0/24
- Create Public, Private and Database route tables in aws console ?
- Associate Public, Private and Database route tables with their respective subnets ?
- Give internet access to the public subnets.
- Enable auto-asign public IPv4 address only to the public subnet.
- Create internet gateway and attach to your created VPC in aws console.
- What is the difference between Public and Private subnets ?
- CIDR (Classless Inter-Domain Routing) ? We can asign custom IP address range to the subnets.
- Use always terraform best practices for naming convention like using '_' to avoid double naming.
- We used open source modules sometimes and also we have dedicated cloud team who develops modules to use them.
- How do you check internet is working or not ? 'ping google.com' Ipv4 is 32 bit and Ipv6 is 64 bit.
- Router (Internet Gateway) ---> It has public_ip and private_ip. What is your actual IP address or public_ip ? Nothing but just type 'what is my ip in google' there you can see Ipv4 address that is your public_ip, not Ipv6. If anybody wants to connect to my laptop they can connect using this IP address only. You cannot connect with private_ip address. What is your private_ip just 'ipconfig' in cmd there you can see IPv4 address Under wireless LAN adapter Wifi.
- AWS wont charge for VPC, subnets, route tables, it only charges when you are creating server.
- We can create as many private subnets we want however, for functionality purpose, we have only two subnets which is public and private subnets.

### Session-30
- What resources we have created inside the VPC through aws console ?
- First we have created VPC in aws. Your created VPC is isolated even aws dont have access to it. It is like your private data center in aws cloud.
- Next created internet gateway (IGW) and attached to the VPC.
- Created Public, Private and Database subnets in atleast 2-AZs for high availability.
- Created Route tables (Public, Private and Database) and associated with their respective subnets in both regions 1a and 1b.
- Added internet gateway route in public route table because internet should be enabled in public not in private, that is the difference between public and private subnets.
- Enabled auto-asign public IPv4 address only to the public subnet not to the private subnet.
- When you create a VPC, a default route table also known as main route table is automatically created to that VPC. It contains a local route that enables communication with the subnets within the VPC. While this default route table cannot be deleted, its routes can be modified and custom route tables can be created and associated with specific subnets to get more control over network traffic.
- What is NAT gateway and why it is used ? It should be created in public subnet (1a or 1b) and why only in public subnet ?
- Creating NAT gateway is not enough we need to add routes between private subnets and to the internet gateway (NAT) which is in public subnet.
- Which ever private subnets like database subnet (or) any other private subnet wants to connect to the internet, they should add route to the NAT gateway which is in public subnet. So select any of the private subnet/routes/edit_routes/add_route (Destination = 0.0.0.0/0, Target = NAT gateway, then select default one in dropdown under target section only)
- When you create NAT gateway, aws will create instance in the background. We dont have access to that instance, since this instance_ip is dynamic. So create elastic_ip before creating NAT and then attach this elastic_ip while creating NAT gateway. NAT and ElasticIP are chargeable, so delete after practice.
- Can we get static_ip for this instance ? YES! we can get but it is very costly thing.
- Even your home public_ip is dynamic. If you want static_ip, you need to pay money to ISP provider.
- What is VPC peering and what is the condition to create VPC peering connection ?
- Create a VPC peering connection between Roboshop_VPC and Default_VPC
- So let us take Requestor VPC = Roboshop VPC ; Acceptor VPC = Default VPC
- Accept request in the same account and then add routes in VPC. Try to add routes in main route table because it is the default route table which is created automatically to communicate between the subnets, if not reflecting then add explicitly in each route table.
- If you want only one (or) two private subnets wants to connect to the vpc peering main road then you can add in those two route tables only. Make sure you need to add from the other side also not just one side. This is nothing but routes in VPC.
- Go through the 'Terraform-aws-vpc-module' how we developed VPC and resources inside it.
- We use better 'tagging strategy' since we have more resources. So we used common_tags and resource_tags. What is the difference between them ? We used merg function in tagging strategy to merge common_tags and resource_tags.
- You can also create s3 bucket for VPC while developing vpc module (Optional)
- We can also write condition in variable syntax using 'validation' keyword

### Session-31
- Go through the code of 'Terraform-aws-vpc-module' in VS.
- While developing VPC module, we come across peering section and is really peering connection required ? Peering may not require for everyone and when this peering is useful ? By default peering connection between two VPC is not possible.
- If we want to connect with the resources which are in another VPC then you require peering connection.
- How to connect to other VPC which is in another company ? Install VPN in Default_VPC and Connect.
- Example consider requestor is Roboshop and acceptor is user provided VPC or Default VPC.
- In VPC peering, when you are adding routes in VPC, if acceptor VPC is not in our control what you will do ? We should inform them to add the acceptor route in their terraform code. Big companies depends on multiple companies to deal different modules.
- So users can decide if peering is required or not ? If required they have to give VPC peering id, if they are not giving, we should consider default VPC. Go through the peering.tf file
- Once the VPC module is completed, it was pushed to github, so that other environments can reuse it. In Terraform, we can refer the module like this ---> source = "git::<https_URL>ref=main" when we run terraform init, terraform downloads the module and stores it inside a automatically created folder called module. We need to write a README.MD file to let others know, how to use the modules and also we need to publish outputs then only users can get the information. We keep all our resources in 1a zone. We can create a folder (Example) and keep all the testing code in it, so that it will be easy for everyone to use the module.
- Till now we used 'allow-all' method while creating SG but now we use strict SG rules.
- How to use security groups effectively according to the roboshop documentation ?
- We install VPN in Default_VPC to connect to private instances which are present in Roboshop_VPC.
- We have a Database subnet group because databases have different behaviour nothing but just adding database subnet ids.
- We also use open source modules for VPC in google instead of developing it but just know how to develop the vpc module also.

### Session-32
- Till now we used 'allow-all' method while creating SG. It is just for practice only but now we need to follow strict SG rules according to the roboshop documentation only.
- We have developed our own customized VPC module right ? In this session also we are going to develop our own customized SG module. Refer 'Roboshop-aws-sg-module' in VS.
- We created security groups and SG rules for all components according to the roboshop documentation.
- Why we created separate folders for every resources in Roboshop-terraform ? Refresh time
- Since they are in separate folders, so consider they are like different projects.
- Go through 01-vpc, 02-sg, 03-vpn, 04-ec2 code in Roboshop-terraform in VS.
- What is the main input required to create a security group ? VPC_ID
- For example in big companies, 1 team is taking care for vpc, another team is taking care for security groups etc. How do you get the information of resource which are in another team, project, folder, company ? We have a service called 'SSM Parameter store' in aws systems manager. This is nothing but a configuration storage (or) central storage where different applications can store the configuration and different applications can refer the configuration.
- What is the naming convention while storing configuration is 'key-value' pair in SSM ? Generally naming format will be in linux structure like '/roboshop/dev/vpc_id'
- As we know data-sources is used to query the data dynamically from the providers and also from the existing resources right ? But to query from the existing resource, we need to give some input like vpc_id, this vpc_id we cannot get from the data-source but we used data source only to query the default vpc_id but to take the created vpc_id again data-source is not an option because we need to give vpc_id as input.
- Since VPC is in different folder, how do we get vpc_id in SG folder ? You need to store vpc_id in SSM Parameter store first and then read that saved vpc_id (or) key-value pair in SG folder using data-source option.
- Generally it is not mandatory to create ingress rules while creating SG because ingress rules (Ports) may change later like adding new rules or deleting rules, this can be modified later according our requirement but egress is static because this traffic is creating from our server, mostly it will be constant. In real time, whenever you want few ports to open, you need to write a mail to firewall team then they will open the ports. If they are using terraform they will do changes in main.tf file
- In security groups, we have two names 'Name' and 'Security group name' what is the difference ?
- As a module developer, you must output the resources in output.tf file like IDs etc. So that other teams will use it.
- Now creating all security groups according to the roboshop documentation. Mongodb --> Should accept connections from 'catalogue' and 'user' what should be the ingress (Security group rule) of mongodb now ? Source should be the catalogue_ip and port 27017, similarly for user also.
- Is catalogue_ip is constant everytime ? NO! then what should we do ? We need to take the elastic_ip which is very costly because we have 12 private servers that means we need to create 12 EIPs. If big project, we may need to create thousands of EIPs this will generate huge bill to the company.
- So security group has given 1 option, first create mongodb and catalogue security groups.
- Then go to the security groups in aws console and select created mongodb SG/Edit_inbound_rules/Add_rule, type is custom tcp, port 27017 and in source just type 'sg' next to the custom, you will get the created SGs, in that select already created catalogue SG. Do same for the user also.
- Now write a terraform code for all the SGs according to the roboshop documentation.
- Now creating EC2s for the roboshop 04-ec2 in VS using 'open-source module' from the internet.
- Here the only disadvantage is you cannot connect to this private instances using SSH because private instances dont have public_ip. We have two options 'Jump host' and 'Installing VPN in Default VPC' to connect to private instances which are in 'Roboshop_VPC' but make sure you have peering connection between 'Default VPC and Roboshop VPC'

### Session-33
- What are the two ways to connect private instances which are in Roboshop_VPC ? 'Jump Host' and 'VPN'
- What is jump host ? Create one EC2 in public subnet and login to this ec2 first and from there connect to mongodb.
- How to connect private instances using VPN ?
- In which VPC should we install OpenVpn (or) create server for VPN ? Default_VPC
- We must have a peering connection between Default_VPC and Roboshop_VPC.
- How the traffic is routing from home server to private instances ?
- What is the SG rule when mongodb is accepting connections from OpenVpn ?
- Make sure to enable VPN in all private instances by giving SG of OpenVpn instance to all private instances with SSH rule.
- How to install OpenVpn in server and connect to it ?
- Configuring VPN is not our responsibility, we have a separate team for this.
- We use cisco VPN in our company which is costly but for practice we used OpenVpn connect.
- If you feel slow while terraform commands like init, plan, apply in gitbash. It is because of vpn (Disconnect vpn and try)

### Session-34
- We have created 01-vpc, 02-sg, 03-vpn, 04-ec2. So now we want all instances to automatically configured for that we need to create ansible server in default subnet in default vpc. This server will provision all instances using ansible playbooks and also create security group for ansible on port SSH 22 to connect to all instances securely.
- For this we need to write a small shellscript 'ec2-provision.sh' in VS to provision the instances. NO need to give sudo access in this script because userdata will get sudo access automatically but in provisioners we need to give sudo access.
- There is one disadvantage in userdata. If userdata fails one time it will not come again. We will address this issue with provisioners. So delete ansible server and do again terraform init, plan, apply.
- Userdata logs will be in sudo cd /var/log, ls -la, tail -f cloud-init-output.log
- LB (Target groups and Rules) and Launch templates (Auto scaling and Policy)
- First create 2 nginx servers (UI and UX) while creating add userdata #!/bin/bash, yum install nginx -y, mkdir -p /usr/share/nginx/html/ui, echo "<h1GreaterthanSymbolHi we are from UI team<h1GreaterthanSymbol" > /usr/share/nginx/html/ui/index.html, systemctl restart nginx. Create same for UX backend team.
- We are using 'Application_LB' because it is most intelligent and 'Classic_LB' is very old.
- Create LB security group here from where the tarffic is coming to this LB ? From the internet therefore ingress rule of LB should be HTTP and CIDR 0.0.0.0/0
- Create SGs for these two nginx servers, these servers will get request from LB therefore ingress rule of these servers should be a SG which is attached to LB.
- Create target groups for example ui, ux in listeners first then register using include as pending in default subnet.
- Now create LB with port 80 in default vpc subnet with min two AZs.
- Rules in load balancers, there is default rule, you can add as many rules you want, you can keep path as a condition in this ui/ux example, if path is /ui/* then send to ui target group. Keep priority as 1.
- LB will give us a DNS name, generally we configure this name in route53 record, so create a new record, copy the DNS name and paste and you need to keep alias and select alias to application and classic load balancer.
- Mostly in companies, errors are not because of coding, it is because of configuration change, even if we make small changes in configuration, we get errors, so thats why we need to keep configuration independently in SSM Parameter store.
- SG is very important, since we are connecting to every resources present in aws.
- Individually we can understand every concept but when we configure the project using all concepts, it will create huge confusion, like for example if we give a request from client (or) from our laptop, the request should reach to the end service which is present in aws, request will cross many stages like client-side configuration should be clear, vpc, igw, subnets etc. have many resources to cross and reach the end service. So this visualization should there in us. Thats why SG is important to use in every resources.
- No Problem if you delete '.terraform' folder and lock file.
- Creating ec2 instances 04-ec2 in normal way using module but standard way is 'auto-scaling and launch templates'
- Yaml file was mentioned in the 02-sg folder, it is just to refer how the sg connections are given.
- Keeping provider is good in your actual code not in module developing.
  
### Session-35
- Understand the concept of 3-Tier architecture diagram.
- Start a project 'Roboshop-infra-Dev' in VS this is for 'Dev' environment since this is multi-env you have 3 options Tfvars method, Workspace method and Different repos for different environments. Present siva is creating different repos for different environments. Every method has pros and cons you can tell this in interview. We also need to create for SIT, UAT, PROD environments.
- Create separate buckets and dynamodb tables for different folders inside the 'Roboshop-infra-Dev' project.
- We keep 'web-alb' in https on port 443 because it is facing to the public. App-alb is private LB and it is within our network so we can keep this in http on port 8080 (or) 80.
- There will be NO direct connections from now. Only through LB even inside the internal servers also because internal servers ip addresses are dynamic. Lets say if user wants to connect to catalogue then user must connect through app-alb only.
- We use auto scaling only for frontend and backend. For databases we use RDS, DynamoDB etc.
- Creating databases using PULL strategy. We have one disadvantage in PUSH that is once we pushed the configuration from the ansible server to the nodes and if the configuration is disturbed or anybody did changes in ansible server we dont have any idea so ansible implemented PULL architecture aswel we can schedule a crontab to PULL the configuration periodically from git not from the ansible server and run it since ansible is idempotence in nature even if the program runs multiple times nothing will happen. So go through the code of 'Roboshop-ansible-roles-Terraform' in VS.
- Why we use terraform provisioners (Null resource) instead of userdata ? Because we dont know wether the userdata is succeeded or not until we see the logs in server and moreover it will run only one time. But in provisioner we can see on terminal wether the bootstrap is happening or not ?
- Every platform like azure, gcp, aws cloud will have its own solution to maintain configuration and secrets. In aws cloud we have more resources like ec2, dynamodb, lb etc. So for every service you may use passwords or any other secrets in the configuration at some point of time like in mysql we have password Roboshop1@ to store this we have SSM Parameter store.
- For example in aws cloud, EC2 is a service and if this EC2 wants to retrieve the configuration or passwords which are present in SSM Parameter then this EC2 must have access to that SSM right ? For that only we give roles to the EC2 in IAM. Second thing is here we are using ansible to provision servers so ansible should pull the configuration or passwords whatever present in aws from SSM Parameter then ansible should connect to the aws first that means ansible should download boto3 and botocore python modules. Third thing is ansible server should also have IAM role (or) IAM policy to PULL the configuration or passwords from the AWS. If these 3 things are there we can implement vault.
- IAM role we have given in the code is 'iam_instance_profile = role-name' present this role has full admin access later we can restrict in IAM concepts.
- Only thing we cannot automate is storing passwords in SSM that should be done manually.
- So first store the password in SSM Paramater. For example we have root_password in mysql right ? Store that and naming should be 'roboshop/dev/msql_root_pass' and select secure string and value should be the password itself 'Roboshop@1' so here ansible should retrieve this password for that we have a syntax called 'lookup' put this syntax in the ansible roles where ever this password is there.
- If you go manually like 'ansible.builtin.command' (or) 'ansible.builtin.shell' there will be no idempotence behaviour thats why mostly use module only. If there is no official modules from ansible we can use community modules.
- Web and App tier (If traffic increases, auto-scaling will create instances)
- We created databases and provisioned using provisioners instead of userdata.

### Session-36
- Workflow in company from client to team members ? Client --> Business analyst --> Team manager --> Team leads --> Team members.
- What is launch template ? It is like hiring template similar to HR (Auto scaling)
- First create 'app_alb' (Latest generation works on tcp layer 7) this can redirect to different projects using 1 single app_alb. App_alb is nothing but a team manager. Since the app_alb DNS is dynamic so we need to create a record for DNS.
- What is context path and host path ?
- Now create catalogue target group nothing but a team creation. Who will take resources in this team ? HR (Auto scaling) for this we need hiring template. How this hiring template will be ready ? Below are the points.
- First create catalogue target group.
- Create one instance.
- Provision instance with ansible or shell.
- Stop the instance.
- Take the AMI from the above ec2 instance only.
- Delete the instance.
- Now create launch template with the AMI.
- If we give this launch template to the auto scaling then it will create instances depending up on the traffic.
- If you are not aware of what options to give in the code just try to create a sample resource in the aws console and see what options are required and keep the same options in code by taking from the google do for every resource if you are not aware of.
- Create auto scaling group.
- Create listeners and rules.
- Create auto scaling policy.
  
### Session-37
- What is deregistration ? Once the deregistration is started instance should complete its pending requests and LB should not give any new requests to the servers. We have given 300 or 60 seconds time for this.
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
- What is Git and how it will track ? It is just a folder in internet with tracking capabilities.
- How to generate a commit-id for your content or file ? echo hello | git hash-object --stdin  
- Git will calculate the commit-id based on the content. Commit-id is also known as SHA code which has 40 characters (Universal unique id). Git is a key-value pair (Key=commit-id, Value=content)
- Git log --> You will get all the commit-ids of the entire content of that repo in gitbash.
- If you want the information about the commit-id then ---> git cat-file <commit_id> -p
- If you want all commit-ids of a repo in oneline ---> git log --oneline
- What are the minimum protection rules in git for main (or) master branch ? PR, Require approvals, Require linear history, Dismiss stale pull request approvals when new commits are pushed.
- What is dismiss stale pull request approvals when new commits are pushed ? When this setting is enabled, if someone approves a pull request (PR) and then new commits are pushed to that PR then the existing approvals are removed (Dismissed). This ensures that the code which was approved is still valid after the latest changes.
- When you create a feature branch and you cloned the main branch into the feature branch. But still commit-ids of main branch and feature branch are same and why ? When will the commit-id of feature branch will change ?
- Once developer got approvals, he will get merge options (Merging strategies) Merge commit, Squash and merge, Rebase and merge.
- Merge commit ---> A normal commit changes within a branch, while a merge commit combines two branches and preserves both histories. This merge commit will create one extra commit to the main branch when you merge from feature to main branch, that means main branch is moved 1 step forward. This extra commit-id has 2 parents, one is from the feature branch and another is from main branch, so thats why merge commit will preserve both histories, it is like chain structure.
- Squash and merge ---> It combines lot of commits by 1 developer into a single commit for cleaner history. Mostly this is useful for individual developers, who works on microservices and who do lot of commits to main branch which doesnt look good.
- Rebase and merge ---> It rewrites the commit history and creating a linear history without new extra merge commits. It will not preserve the history and commit-ids will be changing.
- Which merging strategies will be preferred among these three ? Mostly companies go for merge commit not squash or rebase why ?
- When to use merge commit and when to use rebase and merge ?
- We are following feature branching strategy, we have main branch as long live branch anything other than main branch we call it as feature branch, developers will work in feature branches and before raising PR we will do CICD in feature branch itself in dev environment, once it is successful they will raise PR based on the discussions. PR will be approved and from the main branch, we do deployment into the higher environments like QA, SIT, UAT, PROD. Since code is same across all environments but configuration is different. Configuration should be dettached from code, for that we are using ssm parameter store.
- What if we success in DEV and failed in QA ? What should they do ? Again they should create another feature branch, they should change the code again in DEV environment and then do CICD.
- We have '.git' folder in every repo nothing but it stores all the information of git like tracking, metadata, objects etc.
- The above all branching strategies will be done by developers only not devops team. We only discuss how the branching strategies should be by sitting with developers and we dont have any rights to raise PR, Approve requests etc.
- If we got emergency, we can just test in DEV and then directly go for the PROD deployment.
- Explain merge conflicts in git ? So pull before push is the best strategy need to follow to avoid merge conflicts.

### Session-42
- Jenkins is a CICD tool, how to install jenkins in server ? Create 1 instance with t3.small with 30GB and default SG. Then install jenkins and java on this jenkins server using jenkins.io website for centos.
- Installing java in jenkins is mandatory because jenkins is developed on java only but no need to install jenkins in agent (Java is enough for the agent to work).
- Jenkins-master may not required to know everything but agent must know everything because actual work is done by the agent only. However logs of agent will also be shown in jenkins-master only. Jenkins port number is 8080 and Nexus port number is 8081.
- What is free-style project in jenkins ? Nothing but creating pipeline through user interface in jenkins server.
- What is the difference between creating aws resources in aws console and through code ? That is the difference between free-style and pipeline jobs ? Advantage in code and pipeline is, we can control versions and rollback changes, if something goes wrong.
- Create a job first using free-style and then pipeline ?
- Anybody can do the changes in free-style aswel as in pipeline jobs from jenkins ui. For that we have best approach that is 'pipeline script from SCM' and jenkins file notation is 'Jenkinsfile'
- Write a RAW syntax of a declarative pipeline ? Script path should be the exact name of jenkinsfile.
- What is agent in jenkins ? How many agents are required ? Since we are supporting multiple programming languages like java, python, nodesjs, .net for each language, we have 2-2 agents.
- How do you configure 'master-agent' architecture in jenkins ? We have multiple agents, we configure in manage jenkins, nodes, create node, executors, remote root directory, labels, launch methods, host, configure credentials, host key verification strategy.
- Where does the entire jenkins database will be ? /var/lib/jenkins, similarly we need to create a directory for agent also in /home/centos/jenkins-agent (Any-name) because CentOS dont have sudo access in /var/lib/jenkins, it has only in home folder (or) click on question mark ? symbol, there you can see how to give the path.
- Triggers in jenkins pipeline ? We have a webhook (Event based communication) in github to setup triggers.
- Environment in jenkins pipeline ? The environment block in jenkins pipeline is used to define environment variables that can be accessed across stages and inside shell commands. It helps in centralizing configuration, avoiding hardcoding and making pipelines reusable. It is also commonly used to give credentials securely and to handle different deployment environments like DEV, QA, PROD.
- Options in jenkins pipeline ? The options block in jenkins pipeline is used to control pipeline execution behavior such as timeout, disable concurrent builds etc.
- Parameters in jenkins pipeline ? Used to accept user inputs at runtime when triggering a build. We can give the inputs like environments and branches.

### Session-43
- Difference between scripted pipeline and declarative pipeline ? Groovy syntax will not work in scripted pipeline.
- Input option in jenkins pipeline ? Taking approval before going to the next stage, we can also keep colours code here.
- Create a jenkins file for infra to vpc. Use terraform init, plan, apply. Use input option before apply. Since this pipeline is running on agent. We need to install terraform command and aws credentials (Aws configure) in agent server. While aws configure dont take sudo access because jenkins-master is connecting to agent using centos, so configure with normal user not with sudo access. Search in google like install terraform linux for centos.
- To get colors we have a plugin called ansiColor ('xterm') in options itself. So install this plugin in manage jenkins plugins. Also write a code in jenkins file under the options. If plugins are not working even after installing just do systemctl restart jenkins.
- Jenkins pipeline when with parameters. In jenkins pipline, when condition is used to control whether a stage should continue or not. When used with parameters it will allow the stages to execute based on user input provided at run time.
- That means overall we can write CICD pipeline for infra also. But we dont create project infra using pipeline, we create only using terraform because this infra is very rarely touched, this is just to show that we can also create jenkinsfile for project infra also. So first create whole project infra using terraform and then create CICD jenkinsfile for application infra like catalogue, cart, shipping etc. Make sure before doing CICD for application infra, project infra should be ready.
- What are CI and CD stages in application like catalogue ?
- CI ---> Pulls the code from git + Build the application + Runs the test
- CD ---> Take the build code + Deploy it to environment.
- Difference between Continuous Delivery and Continuous Deployment ? In continuous delivery, after building the code, we need to wait for the approval, its like manual process, while in continuous deployement, no need to wait for the approval, it will automatically deploy into environments.
- Once the project infra is ready, we write jenkinsfile for catalogue, so keep catalogue code in catalogue folder.
- What is pipeline utility steps plugin ? Install in manage jenkins to read the json file to get the catalogue version.
- Next stage is installing dependencies ? Installing nodejs (From the roboshop documentation) in agent is mandatory in order to install npm dependencies.
- Next stage is build the above catalogue code and zip it (Nothing but artifact) and store in nexus repository.
- We use sonatype nexus because it is a widely adopted and reliable artifact repository manager. Create an instance with a minimum of 2GB RAM and 30GB storage (T3.medium). While the actual installation is typically handled by the SRE (Site Reliability Engineering) team, but it's important to understand the concept. Dont worry about installations or updates.
- What is internal YUM repositories ? Nothing but instead of getting libraries and dependencies from the internet, companies will keep those inside the YUM repositories, so that we can use from here. That is why nexus acts as a central point not only for storing build artifacts but also for serving as a local repository for all required libraries and dependencies.
- Now create a cataloge repository in nexus to hold the catalogue artifacts using 'maven2 hosted' format. What is maven2 hosted format ? It is popular format used for maintaining application artifacts in a unique way like below.
- Group id --> com.roboshop, artifact id --> catalogue, version --> 1.0.0. Folder structure be like com/roboshop/catalogue/version folder 1.0.0, 1.0.1, 2.0.0 etc.
- We have version policy release (Prod), snapshot (Dev), mixed (Both)
- Allow re-deploy option in deployment policy because we are in dev.
- Now we get URL of that repository. In this url only, we store the catalogue artifact. So we zip catalogue artifact in jenkins and send it to this url. Give the nexusURL and authentication, make sure to add nexus credentials in manage jenkins and give that credentials id name in pipeline code also.
- Remove workspace folder in pipeline in post section 'deleteDir()' this is must.
- Install 'Pipeline Stage View Plugin' in jenkins to see in stages.
- How to create any file as backup ? Jenkinsfile.bkp (or) main.tf.bkp

### Session-44
- In previous session, we completed till building the code nothing but as zip file in catalogue CI process but before going for deploy, we need to send this build artifact to catalogue nexus repo which we have created in nexus server. We have catalogue artifact in jenkins CI then how to push this artifact to nexus repository url ? For this we have nexus artifact uploader plugin, install this in jenkins UI and also keep the code in jenkinsfile. Till this we call it jenkins CI process.
- What is the process for catalogue (CI) ? Until the creation and pushing the artifacts to nexus url.
- What is the process for catalogue (CD) ? Create server, provision it using ansible, stop server, take ami, create launch template version, refresh auto-scaling. We already did this in terraform, so copy this whole catalogue code from 'Roboshop-infra-dev'
- Until CI part, no need to create project infra but now we are going for CD, so create project infra and databases first. Catalogue component and other components will be done through CICD. Go through the code of catalogue CI and CD in VS. Previously ansible was downloading the package from s3 bucket, now it should download the artifact from the nexus location and also download specific version (You need to make few changes in roboshop-ansible-roles in appsetup in common files). So what should we give to ansible ? We need to give nexus location and artifact version, so make changes in playbook according to this. So in jenkinsfile you have to pass a variable of version dynamically using -var-file in plan stage (Terraform) and then pass it to ansible in provisioner remote-exec inline. So version is travelling from developers code in vs ---> jenkins ---> terraform ---> ansible
- Keep parameters also for version and environment for catalogue.
- What is upstream (CI) and downstream (CD) in jenkins pipeline ? When CI success then only call CD.
- Catalogue CI will send values of version and environment to CD, how to call another pipeline from jenkins pipeline ? 'buildjob'
- You need to attach vpn SG to the agent because catalogue is accepting connections from vpn.
- We can also install a plugin called 'rebuilder' it will run with the old values.
- We are following semantic versions like major version, minor version, patch version.

### Session-45
- Types of scannings in jenkins pipeline ? Static source code analysis, Static application security testing (SAST), Dynamic application security testing (DAST), Open source library scanning, Docker image scanning.
- We are using shift-left method, we do all types of scannings in DEV enviroment itself to make sure everything is ok then only we can go for the higher environments.
- How the sonarqube scanner will work ? Installation of sonarqube is taken care by SRE team. Jenkins agent will clone the code in his server and it should have 'scanner cli' software which need to be installed same way how you installed sonarqube, it will scan the code and upload to the 'Sonarqube' console (or) server. Then developers will see the results in 'sonarqube' console (or) server. Port number of sonarqube is 9000. But scanner cli should have sonarqube url and login information like username and password, for that we need to give in 'Sonar-project.properties' which is in opt/sonar/conf location, so that scanner cli will understand where to upload the results. Now configure this in pipeline
- Quality gates in sonarqube (We keep some standards) like code should be clean ? If quality gates failed, we should fail the pipeline and inform developers to fix this code. So we should keep a condition in pipeline (Sonar-project.properties) to fail the pipeline 'sonar.qualitygate.wait=true' node modules comes from internet, so NO need to scan node_modules directory here, so we put this line of code in properties 'sonar.exclusions=node_modules**'
- What is multi branch pipeline ? We are using multi branch pipeline in jenkins.
- What is jenkins shared library ? It is a library of pipelines and use it whenever you want and what is the process ?
- For example developers are the owner of the catalogue repository but jenkinsfile will be managed by the DevOps engineer only. So DevOps engineer doing frequent changes in Developers repo (Catalogue) is not good. For this only we have jenkins shared library (Centralized pipeline). For example if we have 20 repos we need to write same jenkinsfile for every repo, instead we can create and maintain the shared library repo (Groovy code, reusable pipeline steps). We can keep all multiple pipelines in jenkins shared library for different languages and deployment platforms.
- We need to inform this jenkins shared library repo to the jenkins by going to the manage jenkins, system, global pipeline libraries, add here, default version should be main and name (Any-name), project repo should be git URL. Refer this library in jenkins pipeline using @Library('roboshop-shared-library'). We use groovy syntax in jenkinsfile #!groovy
- How to call these pipelines ? For example nodejsVM, javaVM, pythonVM is a centralized pipeline. We need to send parameters like what type of application and component to 'pipelineDecission.groovy' we can decide which pipeline to call using this decission.

### Session-46
- What is the pipeline process or cicd architecture you are following in your project ? Interview question prepare well from this https://github.com/daws-76s/concepts/blob/master/CICD.MD This process is for DEV environment but when we go for PROD, we should understand change management process.
- First create whole project infra for 'Roboshop-infra-dev' using one jenkinsfile instead of doing manually. If there is NO dependency from one folder to another folder like 04-databases and 05-app-alb. For that we have 'parallel stages' in jenkins pipeline (We need to use a keyword called parallel) so because of this parallel both resources will create at a time, it will save the time. Other folders like vpc, sg, vpn have dependencies (Like it is following sequential process).
- We can keep all static values like nexus url, file path, credentials etc in 'pipelineGlobals.groovy' in jenkins shared library.
- What is change management process ? Only used for PROD deployment.
- What is JIRA to Jenkins integration ? Jira is a ticket management tool. We will write a separate pipeline for PROD and handover to JIRA team.
  
### Session-47
- Algorithm for CICD pipeline for roboshop project is first make sure project infra (Dev and Prod) is ready and get the vpns connected here we can also keep one vpn for both or different vpn for both. Few companies keep single VPN for all environments, we can also keep single VPN, but it is better to keep 1 VPN for every environment. Next create 1 jenkinsfile for whole project infra for both dev and prod.
- Next go for the application infra which starts with catalogue. So create 1 catalogue repo and download the code from roboshop documentation using wget URL or download manually into that catalogue repo and also keep jenkinsfile for this catalogue and point this jenkinsfile to shared library (Dry principle and centralized pipeline) and also make sure you have shared libraries configured in jenkins system configuration in manage jenkins aswel as keep the code in catalogue jenkinsfile.
- Then jenkinsfile will call shared library and here it will go pipelineDecission based on the case like if nodejsVM then it will call nodejsVM pipeline and stages will be cloned, get the version from package.json, install dependencies, unit tests, build, scans. If developer opt for deploy we can deploy.
- Then we are passing it to the catalogue deploy will call terraform-roboshop-app.
- Bootstrap script will clone roboshop-ansible-roles-tf and run catalogue role.
- Now setting up CICD for user module. As a DevOps team, we have nodejs CICD is ready and a new project user module is started by the developers and how can you setup CICD for user module ? User module developers will send a mail to the DevOps team stating that we have started user module and we want DevOps team to help us to setup CICD for user module then DevOps team will setup meeting with developers and explain our centralized pipeline structure which we used for catalogue. So now setup user module. Create 1 repo for user module and tell them to keep the jenkinsfile. Dont forget to create repo for user in nexus. If new project is started they should have repo existed in nexus, generally this will be done by SRE team.
- Normal pipeline for CD (Deploy) but Multi-branch pipeline for CI.
- This whole process of cicd is VM based, nobody is used vm based everybody is doing in docker and kubernetes. Earlier we were deploying applications into VM later we migrated into the docker and kubernetes if you are 4-5 years of experience. You can tell them like few applications are still in VM, we need to migrate those also. We have different kinds of pipelines, we have nodejsVM pipeline, nodejsEKS pipeline, javaVM pipeline, javaEKS pipeline, we have the setup ready, any deployment platform and any language we support.

### Session-48
- Physical servers (Independent house), Virtualization (Apartment), Containerization (Single room).
- Security will be more in physical server because everything will be in our control, while in virtualization there are chances anybody can look into. So we need to implement proper security in VM and containers using security groups.
- What is containerization ? Containerization is a light weight form of VM.
- How is the booting time of configuring any application until up and running in physical server, VM and containers ?
- What is virtualization concept (or) VM ware ? Cloud technologies are using VM ware concept nothing but resource utilization.
- Resource utilization in VM is better when compared to physical server, resource utilization in containers is much better than VM.
- What is dedicated hosts in aws ? Nothing but physical servers used by big companies.
- Resource utilization is good in VM when compared to physical servers like creating multiple logical servers and if require we can take extra configuration from the big physical server from aws or laptop.
- So we have containerization concept inside the VM. We need to create individual rooms inside the VM. Here system resources (CentOS, 1GB ram, 100GB HDD) are shared that means containers will take resources based on their demand from this system resources. Containers are isolated from each other. System resources will wont block. Boot time is very less (With in seconds) compared to VM ec2 instance. When we are moving to docker and kubernetes, we dont care what is the underline base OS.
- What is configuration ? Example of vacating individual house, apartment and room. Configuration will be less in containers when compared to physical servers and VM.
- What is ami and container ? Ami has Fat OS (4GB) and Container has Base OS (5MB)
- Docker image --> Base OS (5MB-250MB) + application run time + created users + created directory + installed applications.
- Working in dev but not working in prod in VMs ? Main issue is configuration changes and OS this may be because of you are using different OS in QA, SIT, PROD. But where as in docker image the advantage is we take same image from DEV to SIT, UAT, PROD. Thats why we call it as immutable image and portable we even dont know what is the base OS we are using but our intention is image should work.
- How to install docker in servers ? Search in google 'Docker install centos' run the shown commands in server.
- When you install docker a group called 'docker' is created. Users who are in this group they can only access docker commands without root user. So add your user (Centos) to this group. Using 'usermod -aG docker centos' Then logout and login again in server. Now docker commands will work without root user 'docker images' command show you the images exist in the server.
- Difference between AMI and EC2 ? EC2 is the running version of AMI. AMI is recipe and EC2 is dish. An AMI is a pre-configured template that contains the operating system and required software while an EC2 instance is the actual virtual machine created using that AMI. AMIs are used to launch EC2 instances. Similarly the difference between docker image and container ? Container is the running version of docker image.
- If you want to pull image then use 'docker pull nginx' in server, nothing but base OS + nginx installed then try 'docker images' command. Where does this image is pulling ? From the dockerhub. You can signup for dockerhub.
- Docker commands are docker images, docker pull nginx (You will get the latest image)
- Now create container from the above created nginx image 'docker create <image-name/id>:latest' 'docker create nginx:latest'
- Next run the above created container using 'docker start <container_id>' to get the container id use 'docker ps -a'
- To see only running containers use 'docker ps' and to see all containers with all status 'docker ps -a'
- To remove 'docker rm <container_id>' before you need to stop 'docker stop <container_id>'
- To remove without stopping ---> docker rm -f <container_id>
- To remove images ---> docker rmi <image_name>/image_id
- To remove all images at a time ---> 'docker images -a -q' then 'docker rmi docker images -a q'
- Instead of pull + create + run commands ---> docker run nginx. To run in background ---> docker run -d nginx
- Nginx is running now and how can i access it ? You cannot use VM port to container, so you need to allocate any port to the host first 'docker run -d -p 8080:80 nginx' 8080 port is for VM or host, this is mapped with nginx port or container port 80. Interview question is, how can you expose port of a container ? Using 'docker run -d -p 8080:80 nginx' You cannot use same port 8080 because it is already allocated to one container, you can use any other random ports like 8081, 8082, 8083 etc. When you create containers, you will see random silly names of containers. To change name of your own then use 'docker run -d -p 8081:80 --name sai nginx'
- How can you login to the existing container ? 'docker exec -it <container_name/id> bash'
- How to see the base OS of a container ? 'cat /etc/*release' check with sudo access.
- Container will also have IP address, to check this ---> 'docker inspect <container_id>'
- Till now we used others images from the dockerHub right ? Then how to create our own docker images ? 'Dockerfile'

### Session-49
- What is the difference between virtualization and containerization (Interview question) ? Resource utilization is not good in virtualization when compared to containerization. In vm resource utilization is completely blocked.
- A declarative way of creating our own docker images using dockerfiles. First create a repo for dockerfiles in github. First we need to learn instructions to create our own docker images then later we can build our roboshop as docker images. We have multiple instructions, you can refer in dockerfile reference from google. Dockerfile should be 'Dockerfile' with D caps.
- First instruction is FROM. Nothing but we should have a base OS or image, upon this image only we install everything required for application. Push to github, clone in server then build the image using 'docker build -t <URL>/<USERNAME>/<IMAGE_NAME>:<VERSION> .' Here . means we are saying our dockerfile is in current directory.
- Here t --> tags, URL --> After building the image, we need to push to somewhere right ? Which is dockerhub and URL is 'docker.io' similar to dockerhub, we have ECR in aws for that also we have URL, similarly we have nexus docker registry URL, you can push to any URL. Incase if you dont want to push to the dockerhub or any other docker repository hubs then you can push in local also 'docker build -t image:version .' --> Usage is 'docker build -t from:v1 .' If you are not giving url, username, image then you are not pushing to the dockerhub.
- Later if you want to push from local to dockerhub then just retag it 'docker tag image_name:version url/image_name:version'
- Login to docker then 'docker push image:version url/username/image:version'
- Nexus repository is to maintain artifacts and dockerhub is used to maintain docker images.

### Session-50
- What is dockerfile ? A dockerfile is a declarative way of creating our own docker images. It’s like a recipe for creating a docker image and docker container is the dish. Dockerfile starts with capital D. A dockerfile contains a set of instructions to build docker image. These instructions defines everything your container needs like base OS, software, dependencies, configuration etc.
- We have multiple instructions in dockerfile FROM, RUN, CMD, LABEL, EXPOSE, ENV, COPY, ADD, ENTRYPOINT, USER, WORKDIR, ARG, ONBUILD.
- FROM --> Defines the base OS of image. Every dockerfile must starts with FROM instruction only.
- RUN --> Executes commands while building the image not when container starts and creates a new image layer on top of base OS. Usually this instruction is for installing packages or dependencies.
- CMD --> This command runs at the time of container creation. Systemctl command will not work in container to run any services like nginx etc. In order to work, it should be the main OS but the container is on base OS. So we have given the command manually. Search in google like 'nginx running command inside the container' there will be a daemon command put that in CMD. Run it in background and this should be foreground and attach to the screen then send it to the background. We are using -d detach mode in the command. Now push to github then pull in server, go to CMD location then 'docker build -t cmd:v1 .' Now create container 'docker run -d -p 8080:80 cmd:v1' Then check using 'docker ps' take the ip and test in browser if nginx is working or not ?
- LABEL --> Nothing but tags, for example we have 100 white covers and all are white, you know only when you open them, so we give labels to identify easily. That means labels are used for filtering images. How to filter these labels ? 'docker images --filter label=Trainer=Sivakumar'
- EXPOSE --> This instruction is to find image is using which ports ? 'docker inspect'
- ENV --> Sets environment variables inside the container, useful for configuration and passing dynamic values.
- COPY --> Copies files/directories from the host machine into the container filesystem.
- ADD --> Similar to COPY but also supports remote URLs and automatically extracts compressed files.
- ENTRYPOINT --> Defines the main command that always runs when the container starts. Unlike CMD, it’s not easily over written.
- USER --> Specifies the user (or UID/GID) under which the container will run, mainly for security to avoid root.
- WORKDIR --> Sets the working directory for subsequent instructions like RUN, CMD, ENTRYPOINT, COPY, and ADD.
- ARG --> Defines variables that are passed at build time using --build-arg, useful for dynamic image builds.
- ONBUILD --> Adds a trigger instruction that executes later, when the image is used as a base for another build.
- Note that in Dockerfile, first instruction should be "FROM" nothing but referring baseOS.
- Popular interview question, what is RUN vs CMD instruction ? For example when you do 'systemctl start catalogue' then it will create 1 nodejs process and this process will run infinite times, until this process is running you can say your application is running, if this process is not running then your application is not running, if there is no change in catalogue application say for 3 months, then this process will continuously run. Similarly CMD is to make your container running. RUN at the time of image building and CMD runs at the time of container creation.
- What is the difference between COPY vs ADD ? Both are used to copy the files from local to image but ADD have 2 extra capabilities one is it can directly download files from internet, another one is it can directly untar the tar files.
- CMD vs ENTRYPOINT ? Both runs at the container creation time only but CMD command can be over written by another command at run time. ENTRYPOINT command cannot be over written at run time. If you try to do so, the command you are entering at run time will go and append to entrypoint, example of ping google.com and yahoo.com, We can use CMD and ENTRYPOINT for best results like CMD is supplying the default arguments to ENTRYPOINT, user can always over write CMD arguments at the run time, like we are not giving access to over write the main command to users, if user forgot to give arguments, we have CMD to supply the default arguments.
- USER instruction is when you give a root access to user, he can access the underline OS of that container. One docker container should not access to another docker container. We can restrict root access with user instruction to have security. We can disable this option to a user.
- WORKDIR instruction is sets the default directory inside the container where commands will run, similar to setting a current working directory with cd .
- ARG vs ENV instruction ? ARG will provide values to the dockerfile only at build time, while ENV will access values at build time, run time and also in the container.
- ONBUILD instruction is rarely used today but it’s handy for creating reusable base images (It runs later not now).
- Why we are using almalinux:8 as base OS ? Because it's a bare minimum OS or very light OS.

### Session-51
- Configure roboshop project using dockerfiles ? Nothing but creating dockerfiles for all components and deploy as containers. So create a directory in vs as 'Roboshop-docker' and also create a repo for same in github and also create a server using t3.medium in aws and install docker init, add centos user into docker folder then logout and login. What we do ? Create dockerfiles, create image and run as containers. Roboshop project is in internet, siva is taking dockerfiles from internet only. Overall we are migrating VM based applications to Docker containers, you may be get a task like this in company.
- First mongodb component, here we can directly take official mongodb images from the dockerhub instead of creating base OS (CentOS) and installing mongodb on it. Keep catalogue and user js files from roboshop documentation. Automatically these js files will be loaded into mongodb. Then push, pull and then 'docker build -t mongodb:v1 .' Next run 'docker run -d --name mongodb mongodb:v1' How to check logs ? 'docker logs mongodb'
- Next component is catalogue, keep server.js and package.js in dockerfile. Take the nodejs 18 image from the dockerhub. Then build and run, you will get connection error that mongodb is not connected to catalogue. Go through the concept of eth0 in Session-51 then run the catalogue using 'docker run -d --name mongodb --network=roboshop mongodb:v1' and use same command for catalogue also here.
- Next component is web, keep all static content in a static folder from roboshop documentation. Then build and run, while running we should expose the ip address to outside world for web, so 'docker run -d -p 8080:80 --name web --network=roboshop web:v1' Now check wether you able to access website or not ?
- What is docker compose ? Go through the concept of docker compose in Session-51.
- Next component is user, keep server.js and package.json files in dockerfile.
- Next components are cart, redis, mysql will load data like cities into shipping.
- Next shipping component, here we have multi stage builds mainly for java projects, which is very important for interview, while developing java code, we need 'maven jdk' after building this we get jar file but for running no need of maven and jdk, we just need jre (Java runtime environment) jdk is heavy memory. So docker container will restrict this type of building the java code because it will take heavy memory, so thats why we use multi stage builds. This is the best practice we need to use in docker containers. Next go for rabbitmq, payment components.

### Session-52
- How to build all images at a time ? Do this in server command line 'for i in mongodb mysql catalogue cart user shipping payment web ; do cd $i ; docker build -t $i:v1 . ; cd .. ; done'
- How to run all images as containers at a time ? 'docker compose up -d'
- What are the best practices you will follow as a DevOps engineer efficiently and securely in docker ? Below are the points.
- Use only official images from the dockerhub.
- Create custom dockerfiles like we have created for all components.
- Keep images and containers in small size like below 1GB.
- Use multi stage builds, use docker volumes to persist the data. Go through the docker volumes concept in Session-52.
- Use custom networks to isolate containers from other projects.
- Docker system prune will delete the unused data to create free space.
- You should not run container with root access because there may be a chance that container getting complete file system access of the underline host. So create one system user in host OS which ever like if you are using alpine then create user in alpine and add it to the group (Roboshop) using user instruction.
- Go through the concept of docker architecture in session-52 ?
- Go through the concept of docker layer in session-52 ?
- Instead of installing docker setup and docker compose manually, siva has created a shellscript to install automatically. Just use that url here 'curl <raw_url> | sudo bash'

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
