### Go through the below scripts in VS
- 08-conditions.sh
- 09-install-mysql.sh
- 10-functions.sh
- 11-logs.sh
- 12-loops.sh

### Algorithm for installing any package
- Check if user is root (or) not ?
- If root proceed, If not root, stop and say run with root user.
- Now install package.
- Check wether the package is installed properly (or) not ?
- If success then good, if not success then show what is the error.

### Root user and exit status $?
How to know if it is root user (or) not ? You just enter "id" in the server terminal with root access sudo -, There you can see root user has "id=0" (or) "id -u" then you get root ID, other than zero it is not root user. Shellscript won't stop even if it faces any error, it is our responsibility to stop and solve the error and then proceed, for that we have "exit status" that means we need to check the wether the previous command is success (or) not ? for that we have special variable "$?" ---> If success it has "0", if failure "not 0" (otherthan 0 any number will be there)

### 10-functions.sh
We can put the repeated code in the function, generally we keep functions under VARIABLES, we give args to the shellscript, similarly we need to give inputs to the functions also. You have run the script right ? then where is that log ? There will be NO logs in "less /var/log/messages" we need to store that logs, otherwise we cannot troubleshoot, make sure you should not log in the current folder of server come outside and then do, this is just to show how it works rightnow, for example just type "ls -ltr" in the terminal you can see all the files including hidden and when you "clear" it is gone, so we need to store that by following below steps, not only ls -ltr we can do for any command.

### Redirections (> symbol is for output redirection)
ls -ltr > temp.log ---> Storing ls -ltr log in a temp.log file, Here output is not in terminal, it is in temp.log, to view this "cat temp.log", Usage in the server terminal will be below example go to cd location then "ls -la > /tmp/temp.log (created new file called temp.log inside the tmp folder)". If you give a successful (or) correct command (or) spelling mistake in commands like below.
- "ls -ltrrrrsd temp.log"
- "any-command > temp.log"  ---> Bydefault success output only stores here.
-  1 ---> Success = usage (ls -ltr 1> temp.log)
-  2 ---> Failure = usage (ls -ltr 2> temp.log) ---> It is a success command because there is no spelling
   mistake, So it wont be in the temp.log, If (ls -ljtsssfs 2> temp.log) now it will store because it is 
   wrong (failure) command.
- &> ---> Both wether it is success (or) not it will store in the temp.log
- &>> ----> It will append the new log.
- To open the log file "less <logfile-name>"
   
### Special Variables will work only in double qotes
- $? ---> Checks wether exit status of the previous command is success or not ?
- $0 ---> You will get script name.
- $1 ---> First argument.
- $2 ---> Second argument and so on ...
- $N ---> Nth argument
- $@ ---> All arguments
- $# ---> To know how many arguments are passed to the script.

### Colour coding in shellscript
To enable colors option, you need to give "-e"
- RED ---> R="\e[31m"
- GREEN ---> G="\e[32m"
- YELLOW ---> Y="\e[33m"
- NORMAL ---> N="\e[0m" 

### Points to remember
- Make sure Repository name you create in github and windows folder should be same.
- You should not do any changes (or) adding new files in server terminal, come one step back like after going
  to home folder (cd) like ~ ---> Here you can store the logs for practicing as siva showed in the terminal,
  here in terminal, if you get any errors (or) not working properly you can delete that folder and clone again
  from the github (no problem)
- To remove any package "sudo dnf remove <package_name>"
- You can also redirect the output like this ? "yum install nginx -y > output.text"
- You can keep any name for output "yum install nginx -y > saikiran.text"
