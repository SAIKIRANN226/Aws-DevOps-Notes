### "Putty" to connect to servers
In previous sessions, we learned how authentication is happened while connecting to the linux servers in gitbash, ofcousre it is using ssh in the background. Here in putty also obviously should go 
- Username
- Privatekey/Password
- IPaddress
If we give above three what will putty do in background ? So putty will take above three and it will issue a command "ssh -i <path-to-privatekey> username@IP". In gitbash we call Privatekey as ".pem" format but in putty ".ppk" format (Putty Privatekey)

### First open puttygen
- Load .pem file which you have already created (or) you can create a new one also.
- Click on save Privatekey with .ppk extension.
- Open putty --> connection ---> ssh ---> auth ---> credentials ---> load your saved .ppk file
- Connection ---> data ---> username (ec2-user) ---> then go to session and save (Important)
- Create a server in aws and take the IP and paste it in putty (Hostname) click on load to connect.
- To change the font open putty ---> appearence ---> change & then save to make effect in superputty.

We have extension for putty that is super putty. Just create one server in aws and connect in the superputty try to install nginx, enable, start and check the IP in chrome if it is showing nginx (or) not, so from where the html files will load in nginx ?  "/usr/share/nginx/html" we have index.html file, so go to this folder "sudo su -" then cd usr/share/nginx/html, Here we can also put your own short html format which should do in the server only.

### How to keep sample html website from the internet
- Remove default index.html file in the server "rm index.html" and download sample html website from
  the internet.
- Open winscp double click on the path location on top rightside, which is in grey colour and paste this
  location "/usr/share/nginx/html"
- Drag and drop the html files and folder to the right side mini windows in linux server.
- You will get error "permission is denied" while copy paste.
- ls -l and check html folder has write access to others ? 
- chmod o+w -R html/ (-R means recursive go inside folder and change (or) delete everything)
- Make sure to restart nginx when you add any files to the folder.

### Steps to install nginx (or) any other packages
- sudo su -
- yum install nginx -y
- systemctl enable nginx
- systemctl start nginx
- systemctl status nginx
- systemctl restart nginx

### Linux file system structure
- This PC in windows and in linux we have "cd /"
- boot ---> When server is getting started, server refers this directory and config from grub.config
- dev ---> External devices are mounted here except motherboard
- etc ---> Extra configuration 
- lib ---> Libraries which consists of ".dll" extension (or) other extensions
- home ---> All user directories are created here
- media ---> C-drive , D-drive
- mnt ---> Extra disk mounted here
- opt ---> Optional manual installation of servers (or) applications will be downloaded here
- proc ---> Running processes will be stored here with PID
- root ---> Home folder
- run ---> When server starts uses this directory
- bin ---> Stores commands like cat,vim,touch,cd etc.
- sbin ---> System commands like root access
- tmp ---> Temporory files not important files stored here
- usr ---> All users will be here
- var ---> Variables,log files etc.
When putty stucks (or) unable to enter any command then open putty first load your session then go to connection ---> give 30 in seconds then go to session and save, generally we have value 0 you need 
to give any value like 30, that means every 30 seconds connection will be alive, you can give maximum 300

### Symlink and hardlink (1:01:31)
Inode is the representation of file and folder inside the memory (It is a number), So if you create a file and try ls -li then there is pointer with some number that is nothing file location, We dont have idea where that location is ? That is handled by kernel.

Symlink ---> Is nothing but a shortcut which targets the actual location, In the same way we 
can also create a shortcut for a file by "ln -s <source_where_is_your_file> <destination_path>"  
Usage ===> "ln -s /home/ec2-user/hello /tmp/hello-soft" ---> l ==> linked file, s ==> symbolic, Here 
symlink point to different inode but location is always pointing to actual file memory location, If we 
delete this file we lose link, But not with hardlink it is directly dealing with memory what ever the hardlinks (or) files to inode it will check for the reference until unless all the linked files are 
deleted. Symlink and actual file have their own inodes (or) different inodes to check this "ls -li". 
But in hardlink actual file and hardlink both are pointing to same inode, How to give hardlink ? 
Usage ===> "ln /home/ec2-user/hello hello-hard" if you dont give "s" it will become hardlink

### Points to remember
- We use nginx as front-end servers because it can handle high traffic, it is often used as a reverse proxy,
  we used nginx only in all sessions.
- IIS is only used for windows based infrastructure.
- We have "winscp" for file transfer, it is a mini windows for linux server 
- Generally frontend servers called as http servers open port No:80,hosts html, java based applications.
- Backend is also http servers but port No:8080, hosts like tomcat,jboss,.net,python etc.
- These frontend and back will connect through API's
