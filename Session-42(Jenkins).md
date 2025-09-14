### Merge conflicts in Git
- If git finds different code in the same line number, then git cannot understand. For example below.
- Developer-1 creates 1 branch named as conflict-1 & cloned the main branch and writes his code.
- Developer-2 creates 1 branch named as conflict-2 & cloned the main branch and writes his code.
- Now Developer-1 raised PR and got approved from the reviewers, then he will merge into main.
- But Developer-2 is still writing his code and later when he try to raise PR, he will see "This branch has
  conflicts that must be resolved" so he should understand that main branch has moved forward, so he need to
  pull those changes in his local first and then resolve the conflicts with Developer-1 by discussing. Then
  Developer-2 will push to the github stating that conflicts are resolved in commit message. Now the
  Developer-2 can merge into the main branch without any issue. If you see in conflicts, we can see few lines
  are from Developer-1 and few lines of code are from Developer-2. So Pull before Push is the best strategy
  because, we dont know what other people did.

### Installation of Jenkins (CICD)
- Create 1 instance using t3.small (since it is heavy application) with 30GB & default SG.
- Take Jenkins PublicIP and connect in the superputty (Username: centos ; Password: DevOps321)
- Go to the "Jenkins.io" click on download, then select CentOS and run the shown commands in the server.
  Installing java is mandatory in server (since jenkins is developed on java). NO need to install jenkins
  in agent (java is enough to work for agent). Jenkins-Master may not required to know everything, but
  agent should know everything because, actual work is done by the agent, however logs will be shown in
  Jenkins-Master server only.
- Then sudo su - ; systemctl start jenkins ; systemctl enable jenkins ; systemctl status jenkins
- Take Jenkins instance PublicIP and open in chrome with jenkins port 8080. Usage: 173.34.65:8080 in
  chrome, proceed to click on the "continue to site"
- Password will be in the shown path (just cat with root user).
- Then install suggested plugins.
- Set Username and Password and start using jenkins.

### Commands to install Jenkins in linux server
- You are running Jenkins on Java 17, support for which will end on or after Mar 31, 2026. Refer to the
  documentation for more details. This was the alert seen in jenkins server, since Java 21 is not working.
- sudo yum install java-17-openjdk-devel -y
- sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
- sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
- sudo yum install jenkins -y
- sudo systemctl daemon-reload
- sudo systemctl enable --now jenkins
- sudo systemctl start jenkins
- sudo systemctl status jenkins

Whatever we do in the jenkins we call it as job, nothing but it has some work to do, just create one sample job (or) pipeline in "Freestyle Project" is nothing but everything you do it in UI, this can be done easily. Like for example we can create terraform resources in the aws console also, that is also nothing but a Free style and later we started creating resources through terraform scripting, so now create a sample Freestyle job and take buildsteps as "execute shell" then apply, save and click on "buildnow" and check in the console output. Here build is the main job iam giving to jenkins to work. That means i have given a job to jenkins is to just print "hello world" content.

### Difference between creating aws resources in aws console and scripting ?
Advantanges are, we can control versions like, if something goes wrong we can rollback the changes to the previous version and we have PR process to understand what is happening etc. When you create a job in free style, we dont know who created ? who did the changes ? restoring and maintenance is difficult, because it doesn't have any versions etc. So nobody is using Freestyle, but still jenkins is providing the option to create the jobs using Freestyle. 

### Difference between Freestyle job and Pipeline job ?
Free-style job is no one is preffering, since everything can be done from the console and it is very easy for everyone to do the changes and we dont understand who did what changes and it is very difficult to restore to the normal stage because of this we moved to the pipeline.

### Jenkins pipeline syntax
Now understand the Jenkins pipeline syntax from google. Now create a job with pipeline project and select "hello-world" from the pipeline script just for sample and try to build, you can add any number of stages in the hello-world script. Now this pipeline is in jenkins, here also anybody can come and do the changes, so we have another option called "Pipeline script from SCM" If you put this pipeline in the git then jenkins will automatically pull from the git and build it. We call this as "GitOps" this is the best approch. So create a project in VS "Learn-Jenkins" jenkins script always starts with capital letter "J" 'Jenkinsfile' and select job as Pipeline script from SCM in jenkins UI and select git from "SCM" and then give the created "Learn- jenkins" git URL in repository URL. NO need of credentials because it is public and script path you can keep same name as "Jenkinsfile" then apply, save and build.  

### Raw syntax of a pipeline (interview-question)
    pipeline {
          agent {
             node {
                 label 'saikiran-agent'
             }
          }
          stages {
              stage('Build') {
                   steps {
                      echo 'Building...'
                   }
              }
              stage('Test') {
                   steps {
                      echo 'Testing...'
                   }
              }
              stage('Deploy') {
                   steps {
                      echo 'Deploying...'
                   }
              }
          }
          post {
              always {
                   echo 'I will always say hello'
              }
              failure {
                   echo 'This will run if failure'
              }
              success {
                   echo 'This will run if pipeline is success'
              }
          }
    }

### What is agent in Jenkins ?
- For example 1 person can do ---> 1 acre land of agriculture.
- If 100 acres ? ---> Then he will recruit employees and distribute the work.
- Similarly if you are using only one project then 1 "Jenkins-Master" is enough, if you have multiple
  projects, 1 Jenkins server cannot handle the load all alone, for that we have agents to work. Here agent
  is nothing but another server, so create another server in aws for the agent.

### How do you configure Master-Agent architecture in jenkins ?
- We have multiple agents, we configure them in Manage jenkins ---> Nodes ---> Create node
- Executors ---> Nothing but how many jobs can run at a time, this depends on instance configuration
  as of now we put 3
- Remote root directory ---> Generally jenkins has created a folder in which jenkins entire database is in
  /var/lib/jenkins/ similarly while creating agent also we need to create a folder for agent and path should
  be in /home/centos/jenkins-agent (any-name) because CentOS dont have sudo access in /var/lib/jenkins, it
  has only in home folder (or) click on question mark ? symbol, there you can see how to give the path.
- Labels ---> We can set multiple labels, as of now agent-1
- Launch methods ---> One is "Master asking agent to work" another one is "Agent coming to master and asking
  for work" we can use any of them, as of now we are going for "Master asking agent to work" that is nothing
  but "Launch agents via ssh" that means master is connecting to agent through SSH protocol.
- Host ---> We can give any of them PublicIP (or) PrivateIP but siva has given PrivateIP of agent.
- Configure credentials ---> centos (Treat username as secret) & DevOps321, ID=ssh-auth
- Host key verification strategy ---> Non-verifying verification startegy, that means when you are creating,
  it will not ask for the prompt.
- We can add any number of agents like 1 agent is for java, 1 agent is for roboshop, 1 agent is for
  flipkart project etc.

### Triggers in Jenkins pipeline
We have a "WebHook" nothing but when there is an event occurs in one system, then it should inform to the other systems, it is called "Event based communication" what is event in this scenario, whenever developer pushes the code to git, then we want pipeline to run automatically, so we have two systems one is "Git" and another one is "Jenkins" event will come in git, so Git should have information about jenkins (URL), so go the webhook option in Github in your working repository only, click on add "WebHook" add the jenkins URL must be in format like "http://12.233.34.53:8080/github-webhook/" in Payload URL, Content type is Application json, we have multiple events to select according to our requirements, as of now sivakumar selected "Pushes" Similarly in jenkins also we need to check the box "GitHub hook trigger for GITScm polling" and now try to do changes in VS and push to the github and see wether it is working or not.

### Environment in Jenkins pipeline
In a Jenkins Pipeline, the environment block is used to define environment variables that are accessible throughout the pipeline or within specific stages. These variables can hold values such as configuration settings, credentials, file paths, API tokens, URLs and more. Instead of repeating these, we can define them once in the environment block and reuse. You can see in the Jenkinsfile code i have mentioned example. If you run shell command like "env" in the stage, you will get all env variables, you can use as per your requirement. If you want to write a shellscript in the stages use sh """ enter """

### Parameters in Jenkins pipeline 
In Jenkins Pipeline, parameters are used to accept user inputs before the pipeline starts. These inputs can be values like strings, choices, booleans, etc. which you can use throughout your pipeline. Typical use cases for parameters are like choosing build environments (dev, test, prod). When you are using parameters for the first time jenkins is not aware of this parameters, when you build 2nd time then you will get "Build with parameters" option

### Points to remember
- You can directly generate keys in .ssh folder using "ssh-keygen -f <file_name>"
- NO need to install "jenkins" in agents but install "java"
- Post is nothing but after build stage.
- Important note is java18 or 21 version is not working in jenkins, so use java 17 version to install.
- How many agents you are using in your company ? We are supporting multiple programming languages like java,
  python, nodesjs, .net for each language, we have 2-2 agents.
