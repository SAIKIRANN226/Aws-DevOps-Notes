### Project configuration
1. Creating the server
2. Installing programming languages
3. Downloading the code or application
4. Creating directories and users
5. Installing dependencies
6. Start application

### Deployment (or) Release process
1. Developer pushes the code
2. Stop the server
3. Remove/backup the old code
4. Download new code
5. Start the server

### The above is for manual process 
Then what is the difference between manual and automation process ? Manual disadvantages are
1. Downtime
2. Time consuming
3. Human erros 
4. Trouble shooting is tough like finding who did the mistakes, and repeated tasks

Programming ---> java,.net,python etc.
Scripting ---> shell,python,ansible,terraform,kubernetes,docker

### Patterns and methods to learn any scripting
If you take any scripting we have below topics
1. Variables
2. Data types
3. Conditions
4. Functions
5. Loops

### Algorithm thinking must be there in scripting
Example:- Installing git through scripting, we need to make sure below points in general
1. Check wether the user have sudo access or not ?
2. If not sudo throw the error
3. If sudo proceed and then
4. Install package "git"
5. We need to check explicitly wether the git installed or not ?
6. If error in installation then throw the error, otherwise say success

### Authentication to the github account to push the code
Every developer writes code in VS and pushes to the github for that we have two authentications they are
1. Username and Password ---> For every push it is a time taking process to enter username and password
2. Username and Key it is one time process which are below points

- Where to keep scripts ? in github account
- Generate a key-pair in gitbash
- To connect to git we are using keypair authentication. 
  Publickey = Should be in the server (CentralGit), Privatekey with you
- Cat Publickey and paste in github ---> Settings ---> ssh and gpgkeys ---> New ssh-key paste
- Keep your Private key ---> There is .ssh folder in user folder if there is no folder, create one 
  in c/users/saikiran(user) ---> In this create a file with a name of "config" with no extension 
  and then paste the below content (or) you can search in google like "git ssh config syntax"

        Host github.com
          HostName github.com
          User git
          PreferredAuthentication publickey
          IdentityFile ~/.ssh/daws-76s -----------------> Private key location it can be anywhere it 
                                                          is not mandatory to be in the 
                                                          ~homefolder(~ ---> home folder)but need to
                                                          to give the location correctly

### When you create a new repo in github
To clone any repo we have "HTTPS and SSH"
HTTPS --> You should give username and password(used by others to clone)
SSH --> Just Private-key is enough, now we are using this method only(used by owners who created repo)

### Few GIT (Global Information TrackingSystem) commands commonly used
It is a de-centralised(Distributed)version control system, now a days everyone is using distributed 
because we can recover the data if lost, but not with centralised one which are like TFS.
- git init
- git add
- git commit -m "message"
- git remote add origin 
- git push origin master
- Dont forget to configure your username and email by "git config --global"
- We also have staging area in the git nothing but temperory area, send the code what is completed 
  for now (Nothing git add command only)
- Now everything is set, developing in gitbash is not so good so we have IDE (Integrated Development 
  Environment)

### Points to remember
- We have VS (IDE) in laptop and develop code in VS
- Push to GIT
- Pull in the server if any changes
- What ever a small change you want you must do in the VS --> Push to git --> Then pull in server
- Don't do any changes in the servers
