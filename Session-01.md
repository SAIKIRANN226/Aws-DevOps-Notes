### What is computer ?
Laptop, Mobile, Refrigerator, Washing machine etc. We can call these also a computer because a computer has some characterstics like CPU, RAM, STORAGE etc. When we connect these devices to Internet (WiFi) an IPaddress will be created to operate the computer (or) to compute with in the local and worldwide from anywhere in the world.

### Below is the example of Usecases
- www.facebook.com ---> Is a Server, Based on the purpose like below.
- TV ---> Is used for Broadcasting.
- Mobile ---> Is used for calls.
- Server ---> Is used for Hosting web applications to serve users (or) clients.

### Client-Server Architecture
- Client ---> Who is requesting information.
- Server ---> Who is giving information.
- For example, Phone and laptop is "viceversa" when transferring media.
- Therefore whole IT is communication between clients and servers.

### Operating systems
Windows OS ---> A bridge between User and Hardware 
User instructions will turn into ---> Commands turn into ---> 0/1 ---> Hardware. OS will takcare of converting 0's and 1's

### Windows vs Linux
- Windows ---> Graphics (Load increases on CPU, memory & everything)
- Linux ---> Servers world (No graphics, Faster, reliable, lesscost, stability, security comes from unix
  principles only)

### How to connect to Linux servers ?
BOX = Linux server (or) Node
LOCK = Public key (should be in aws-server)
KEY = Private key (should be with you)

### Authentication mechanisms to connect linux server
- What you know ---> Username and Password
- What you have ---> RSA tokens
- What you are  ---> Palms, retina, fingerprints etc. As of now we use second method, so we use SSH (Secure
  shell)

So here we need to generate (or) create a link between "LOCK and KEY" by using a command in gitbash 
"ssh-keygen -f <filename>" and press enter two times, so there will be two files generated with ".pub" and one more file with the same name but "without extension" to unable extension go to Controlpanel, File explorer options, View, Unhide extensions for known files and then rename your private key with ".pem" and the syntax for the keys are below.
- Syntax for Publickey is ---> ssh-rsa {code} Laptop-name
- Syntax for Privatekey is ---> BEGIN OPENSSH PRIVATE KEY {code} END OPENSSH PRIVATE KEY
So you have created a link, now create a server in aws and connect to that server with these keys.

### Steps to connect to SSH-server with keys in the gitbash 
- Import keypair in aws by going to --> Network and security options --> Keypairs --> Actions and Import key
  pair (Publickey) without any gaps.
- Create a Security group (Firewall) for inbound ---> All traffic ---> 0.0.0.0/0 (Representation of internet)
- Launch instance with keypairs and take Amazon Linux 2AMI (HVM)
- Take PublicIP of the instance and username is "ec2-user" (or) Centos and "Privatekey"
- ssh -i <path-to-privatekey> username@IP ===> Usage {ssh -i saikiran.pem ec2-user@123.23.234.5} and this
  command should be enter in the gitbash in the pwd "c/Users/saikiran"
- Note:- Use Centos as username not ec2-user ---> ssh -i saikiran.pem centos@123.23.234.5

Cheapest region is "us-east-1" ---> Latency is somewhat slow which is negligible. Every region has min 2 availability zones, everything here we call as resources, like EC2 (Server). Where ever you are if you type 
CD and enter you will go to User directory. "clear" command will clear all the lines, when you open gitbash by default you will be landed in the "/c/Users/saikiran" lcoation and when ever you stuck in the gitbash 
just enter "ctrl+c"

### Absolute path and Relative path
- Absolute path ---> ssh -i /c/users/user/saikiran.pem ec2-user@IP (If you dont know where you are then you
  can give from the starting)
- Relative path ---> Just know where you are by PWD and then give the path from there like
  "ssh -i saikiran.pem ec2-user@IP" when you are in user directory.

### Points to remember
- HTTP --> 80 Hypertext Transfer Protocol (unencrypted web traffic)
- HTTPS --> 443 Hypertext Transfer Protocol Secure (encrypted web traffic)
- SSH --> 22 Secure Shell (secure remote login and file transfer)
- SMTP --> 25 Simple Mail Transfer Protocol (sending email)
- DNS --> 53 Domain Name System (resolving domain names to IP addresses)
- Gitbash ---> Is an ssh client and also a mini linux
- Protocol ---> We have different protocols like https,http etc.
- Port number for SSH ---> 22
- Ec2 server ---> SSH server
- "$" ---> Normal user
- "#" ---> Root user(sudo su -) to exit from root just "exit"
- "pwd" ---> Present working directory you will be launched in /home/ec2-user
- "uname" ---> Will tell the kernel name
- {command-name} --help ---> Get help from that particular command (or) you can get help from man command also
  "man <command-name>"
