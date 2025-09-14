### Algorithm for connecting to instance
1. Keygenerate
2. Import publickey
3. Firewall
4. Instance created
5. Connected. If we follow algorithm, troubleshooting will be easy nothing but writing yourself in a 
   notes in general language

### Service management
Watch from (05:40 to 17:50)
1. Install nginx "sudo amazon-linux-extras install nginx1 -y" ---> Package installing
2. "systemctl start nginx" ---> This how to make a package into a service
3. "systemctl status nginx"---> To know if it is running or not (or) we can also check with
   process "ps -ef | grep nginx"
4. "systemctl stop nginx"---> To stop the service
5. "systemctl enable nginx"---> Automatically services will run
6. "systemctl disable nginx" ---> Will disable nginx

### Network managment
Network statistics "netstat -lntp" this command is used to check if ports are running (or) not.
- l ---> Listing means ports waiting for connections,
- n ---> Shows IPaddresses instead of hostnames (or) services, 
- t ---> Shows only TCP connections ignore UDP,
- p ---> Shows the process ID (PID) and the name of the program that is using the socket.
If netstat is not installed then install it, "sudo yum install net-tools". To check their process also 
then use "sudo netstat -lntp". To check wether the netstat is installed (or) not ? Just type "netstat"

### Trouble shooting process
1. Check system resources like CPU memory high consumption ---> Generally we check this in task manager, But
   in terminal Just "top" command ; Hardisk full ---> "df -hT" ; RAM full ---> "free --help" If ram is using 
   more and more we need to kill it and restart
3. Check if the process is running or not ? ---> "ps -ef | grep nginx"
4. Wether the port is opened or not ? ---> "netstat -lntp"
5. Check wether the service is running or not ? ---> "systemctl status <service-name>"
6. Check wether the firewall is opened or not ?
7. Check if internet is working or not by "ping google.com (or) ping IPaddress"

### How to give admin access (or) any other access to linux users ?
Example two types of users.
Linux admin team ---> Full access
DevOps team ---> Limited sudo access

1. Create two groups :- Admin,DevOps ---> groupadd Admin, groupadd DevOps
2. Create two users :- ramesh,suresh ---> useradd ramesh, useradd suresh
3. Create two passwords :- ramesh,suresh ---> passwd ramesh, passwd suresh
4. Make password authentication to yes ---> "vim /etc/ssh/sshd_config" and "systemctl restart sshd"
5. Add ramesh in Admin team :- usermod -g Admin ramesh
6. Add suresh in DevOps team :- usermod -g DevOps suresh
7. To check their details :- id suresh, id ramesh

### Now how to give access ? 
All the below process is done in git after connecting to instance using keypair
Generally to give sudo access we have one file "/etc/sudoers" So "vim /etc/sudoers", It is not 
recommended to open this file because it is crucial so linux has given one command to open then 
file safely that is "visudo"
1. Ramesh ---> Add him to wheel group (or) give Admin full access, under wheelgroup and enter
   %admin ALL=(ALL)   ALL
2. Suresh ---> Add him to wheel group give required limited access, enter the below command
   %devops  ALL=(ALL)  /usr/bin/yum,/usr/bin/systemctl

For ramesh we have given full admin access but for suresh we can give only few limited access 
like "yum" command(To know where this command is installed "which yum" (or) "which systemctl" 
command then open "visudo" under the %wheel group add this line for suresh
"%devops  ALL=(ALL)  /usr/bin/yum,/usr/bin/systemctl" So this way we can give limited access

Everytime opening "visudo" is also a risky, So linux has given one location ---> vim /etc/sudoers.d
- vim /etc/sudoers.d/DevOps(created folder) ---> %devops  ALL=(ALL)  /usr/bin/yum,/usr/bin/systemctl
- vim /etc/sudoers.d/Admin(created folder) ---> %admin ALL=(ALL)   ALL

### 3Tier architecture (52:33)
      Load balancer
           |   
           *
      Frontend servers :- Apache,nginx,IIS etc. Applications we deploy in frontend is 
                          HTML,JS,reactJS,AngularJS etc.
      Backend servers  :- Jboss,tomcat,weblogic etc. Applications we deploy in backend is 
                          Java,.net,python etc.
      Database servers :- sql,mysql,nosql,redis etc.

### Points to remember
- Why adding in the wheel group only ? Because wheel group has admin access
- To change password authentication to yes "vim /etc/ssh/sshd_config" make sure to restart
  "systemctl restart sshd"
- https://github.com/daws-76s/roboshop-documentation ---> 3-Tier architecture diagram
