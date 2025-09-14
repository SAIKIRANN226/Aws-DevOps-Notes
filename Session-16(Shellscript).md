### Today we have two tasks to work on
- Delete log files more than 14 days old only with .log extension not any other files.
- Check Disk Usage and Send email for alerts.

### Simple algorithm for deleting old log files
- First decide, what is your Source-Directory (Folder where we are storing log files).
- Search for more than 14 days old, only with .log extension not any other files.
- Then Delete "rm -rf". Below is the simple script to delete old log files.

### 15-delete-old-log.sh
- Create a folder for logs in cd location in linux server 'mkdir /tmp/saikiran-logs'
- Create few files with old date in that folder 'touch -d 20231201 <anyname.log>'
- find . -type f -mtime +14 ---> f(Files), .(Means current directory)
- find . -type f -mtime +14 -name "*.log" ---> We want only with .log extension files.
- Now we can delete using "rm -rf" but we use while loop to read "command_output" line by line.
- You can search in chatgpt like write a shell script to delete old log files in a folder morethan 14 days
  old, you will get the script then copy and adjust according to your requirement and it worked for me.

### 16-ifs.sh
Generally we have "cat /etc/passwd" in this we have all the users information like user_id, group_id, user_name etc. So how to read this whole information properly ? or in a structured way, for that we can use IFS (Internal field separator).

### 17-disk-usage.sh
Command is "df -hT", if the disk usage goes above 70% we need to triggger a mail, so create another disk of 12GB for practice because, in real time there will be more disks, so go to aws console and then navigate to Elastic Block Store ---> Volumes ---> Create volume ---> Action ---> Attach to the instance, so while creating disk there is one condition like for example disk should always near to the laptop. Similarly here also disk should create in the same availability zone where the server is created, when you check in the server "df -hT" still created disk is not showing, so you need to explicitly mount it by using a command "lsblk" and to make into usage, create a file system using "sudo file -s /dev/xvdf" ---> dev (Devices) and we are creating xvdf folder inside the devices folder, then check wether it is created or not ? "sudo lsblk -f" and then run this command "sudo mkfs -t xfs /dev/xvdf" and then create a folder in root folder "cd /" by using this command "sudo mkdir /data" then mount it by "sudo mount /dev/xvdf /data".

### Overview steps of the above disk creation
- Create a disk in Elastic Block Store and attach to the instance.
- lsblk ----> To make available (or) disk is added.
- sudo file -s /dev/xvdf ----> To create a file system.
- sudo lsblk -f ----> To check wether the disk is functional (or) not ?
- sudo mkfs -t xfs /dev/xvdf ----> It is xfs type.
- sudo mkdir /data ----> To create a data folder in "cd /"
- sudo mount /dev/xvdf /data ----> Mounting.

### Finding different types of Files system or Disks using grep command
- df -hT | grep xfs
- df -hT | grep tmp
- df -hT | grep -v tmp ---> -v means i dont want lines with tmp words 
- df -hT | grep -vE 'tmp|File' ---> | ---> or ; & ---> and

### mail.sh
- Mailing the above disk usage to send alerts, sending mails from linux we have to configure email, so install
  the packages from gmail.MD document in concepts folder in linux server in home folder CD, but in real time
  company will give you mail server details to configure and in this, we need to configure gmail. Postfix will
  hit gmail API ; cyrus-sasl-plain will set authentication ; mailx is a command to send mail, so thats why we
  need to install these packages from gmail.MD document.
- We need "From" address and "To" address.
- So open gmail in chrome go to Profile/manage_your_google_account/security/2-step_verification/turn-on/app
  passwords/app_name(any)/copy the generated password, this password is only for linux wont work for gmail. 
- Remove spaces in password and put "from" address in the place of xyz:your gmail without "@gmail" and put
  in the "vim /etc/postfix/sasl_passwd"
- We can also do mail formatting for better looking along with the color coding.
- Just write whatever you want from the compose message in gmail website with your required colors and format
  then copy and paste in the converting text to html format from google websites and put the converted text to
  html lines in a template and replace according to your requirement in template using SED editor.
- Next thing is "mail.sh" we call this whenever we want to monitor on disk_usage, not only on disk_usage, we
  can also call for CPU_Utilization, Memory_Utilization etc. For monitoring purpose using shellscripting,
  because sometimes mailing is not in our control, linux team will give a script like "mail.sh" we can simply
  call that instead of writing this command "echo "$message" | mail -s "High Disk Usage" info@joindevops.com"
- Then how to call mail.sh ? "sh mail.sh" "DevOps Team" "High Disk Usage" "$message" "info@joindevops.com"
  "ALERT High Disk Usage", whatever you write after sh mail.sh is arguments we are passing.

### Improved way of deleting old log files
- Instead of deleting only one particular folder, user has to enter source directory.
- Action ---> We will ask user wether we should archive or delete instead of deleting log files of 14 days
  which is not a good practice.
- If he select archive ---> Where is the destination directory ?
- Time ---> Optional, if he gives take it otherwise, 14 days default.
- Memory ---> Optional, if he dint given then dont consider memory, if he gives then consider it.

### Below is the usage of command
old-logs.sh -s <source_dir> -a <archive/delete> -d <destination_dir> -t <no_of_days> -m <memory_in_mb>

### Algorithm to check for the above command
- Wether the user has given proper command like -s, -a, -t, -m check all these inputs, if he dont give proper
  input, then tell him the correct usage.
- Source directory exists (or) not ?
- Destination directory exists (or) not ?
- If he dont give destination directory throw the error.
- Then archive (or) delete.

### Points to remember
- For any programming languages (or) for any scripting. It is all about variables, datatypes, conditions, loops
  and functions, but with a little different syntax, only we need to make sure wether we are following the
  correct algorithm or not ?
- Shift+G ---> To go down in the config_file.
- gg ---> To go top in the config_file.
- Basically no need to follow the color coding or formatting, we can just use as it is in mail configuration
  gmail.MD document, or if your company provides the email configuration document just simply follow that.
- So configuring gmail.MD document for sending mails is morethan enough.
- Monitoring team responsibility is to monitor servers,websites etc. If websites are down then monitoring team
  will send alerts to Developers team, if servers are down then monitoring team will send alerts to DevOps
  team.
- Creating disk is the work of "Storage team" not DevOps. But just know how it works.
