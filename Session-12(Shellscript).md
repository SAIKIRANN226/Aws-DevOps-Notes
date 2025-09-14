### Why we use SSH based authentication to connect to Github account ?
To push our developed code from VS to Github account using gitbash client, we use SSH based authentication. Because we work with multiple github accounts, so for every account logging with username and password is not a good practice and SSH (22) is more secure.

### Algorithm for connecting to Github account using SSH ?
- Generate new Key-Pair (or) use existing Key-Pair "ssh-keygen -f <file_name>" press enter two times.
- Public-Key will be with .pub extension, you need to give .pem extension manually for Private-Key.
- To enable extension File Explorer Options in Control_panel/View/Unhide_extensions for known file types.
- Cat Public-Key and paste in Github_settings/SSH_and_GPG_Keys/New_SSH_key/Give_any_name without gaps.
- Keep Private-Key in ".ssh" folder, if it is not there you have to manually create the .ssh folder in your
  user directory "C:/Users/saikiran/.ssh"
- Create a config_file with NO extension in .ssh folder, in this config file keep the config_syntax and give
  the correct location of your Private-Key, we can add multiple github accounts here in config file.
- Note that config file must be created in .ssh folder only, you can keep private-key in any location.
  
                    Host github.com
                      HostName github.com
                      User git
                      PreferredAuthentications publickey
                      IdentityFile ~/saikiran.pem
  
- Here the location of private-key is created in /c/Users/saikiran and i have given ~ / saikiran.pem,
  how come the location is same ? because when you enter command pwd it will show your current directory
  when you are in "~" location.
- We have HTTPS and SSH to the repository.
- HTTPS is Username and Password, clone HTTPS_URL when you have read only access.
- SSH is Just Private-Key, you can clone if you are the owner of the respository. But prefer HTTPS while
  cloning the repository.
- Github is nothing but a folder in internet with tracking capabilities.
- Learn Dzone git commands from the below URL's
- https://dzone.com/articles/top-20-git-commands-with-examples
- https://dzone.com/articles/top-35-git-commands-with-examples-and-bonus
- git add . ; git commit -m "proper message" ; git push -u origin master

### Shellscript (or) Bashscript
- #!/bin/bash ---> This we call it as "Shibang" it is the first line to check the syntax of the shellscript,
  we need to give the location of bash, which is in "/bin/bash" but we write first line as "#!/bin/bash" apart
  from the first line, if you see "#" anywhere, it is commentout.
- If you want git in Visual Studio only, then go to view ---> Terminal ---> Select gitbash.
- If you enter wrong URL while pushing to github then we can set using the below command.
  "git remote set-url origin <url_of_the_repository>"
- If git is not configured in the github account yet, still developers can start writing their code in the VS
  until git is ready and later they can push it to the git.
- A normal folder will become git, when you initialize by using command "git init"
- We develop code (or) script in VisualStudio.
- Using gitbash client, we push the code (or) script to the github repository.
- Create a t2.micro server in AWS.
- Git clone <URL> in the server. Because we are cloning for the first time and go to your script location
  then "sh <script_name>" , git pull ---> If you want only changes.
- Echo command is only used for printing purpose.

### Go through the below scripts in VS
- 01-hello-world.sh
- 02-variables.sh
- 03-variables.sh
- 04-variables.sh
- 05-variables.sh
- 06-data-types.sh
- 07-arrays.sh

### Points to remember
- If you make any changes in the code in VS and if you save that changes by pressing ctrl+S, then colour will
  change to yellow. So to make normal then you must push the code to the github account.
- In linux when you open gitbash we are automatically landing in the home directory to know that just type
  "pwd" then you can see your landed location "/c/users/user(saikiran), Here definitely you will have ".ssh"
  folder, if it is not there you need to create .ssh folder, It will be hidden, use "ls -la" command.
- How to switch from main-master (or) master-main branch ? "git branch -M main"
- If you want to create a folder in github with .md extension, just use '/' after naming your folder and after
  '/' just create a file with .md extension. Example 'AWS_DevOps_Notes(Repo)/Shellscript/Session-01.md'
