### 13-install-packages.sh
Installing any number of packages using "loops" instead of going to the script and again writing few commands, we can install packages from the command line itself same like giving arguments outside the script. And we keep these arguments in the "for loop" as shown in the script. Usage:- "sh 13-install-packages.sh git mysql postfix etc."

### Algorithm to install packages
- Check root user (or) not ?
- If root user then check package is installed or not, To know if package is installed or not in the server
  just "yum list installed", to know anything particular then "yum list installed git", to check exit status
  of the previous command just "echo $?" if "0" it is installed, if installed skip it and tell user, it is
  already installed, if not, install it and validate.
- If not root user then throw the error.

### Configuring Roboshop using Shellscript
- Mongodb ---> t3.small
- Catalogue ---> t2.micro
- Redis ---> t2.micro 
- User ---> t2.micro
- Cart ---> t2.micro
- Web ---> t2.micro
- Mysql ---> t3.small
- Shipping ---> t3.small
- RabbitMq ---> t2.micro
- Payment ---> t2.micro
- Dispatch ---> t2.micro

### SED editor (Stream Line Editor)
To change the configuration for humans, we have VIM editor, but for scripts we have SED editor. It is a temperory editor, so use "-e" and If you want permanent change then use "i" in place of "e". Below is the Example:- sed -e '1 a I am  learning DevOps'<file-name> ---> e=enable, a=append (after). If you want before first line then "i", 1=line1. If want after 2nd line then "2 a".

### How to update lines using SED
- sed -e 's/<word-to-find>/word-to-replace/' ---> First occurrence in the line.
- sed -e 's/<word-to-find>/word-to-replace/g' ----> Global for everything.

### Points to remember
- How to check logs? ---> sudo less /var/log/messages
- To check the remote connections (or) ports ? "netstat -lntp" command.
- Shellscript is nothing but keeping all the individual Linux commands in one file, which was used
  while doing manuall configuration.
- To remove any installed package in the server "sudo yum remove <package_name> -y"
- To check any particular package is installed or not "yum list installed | grep <package_name>"
- To remove file "rm -rf <file_name>"
