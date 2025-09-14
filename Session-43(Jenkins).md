### Types of Pipeline syntax
- Old pipeline is "Scripted pipeline" in this groovy will not work.
- Latest pipeline is "Declarative pipeline" & syntax starts with pipeline {}
- Everything will work here in Declarative pipeline.
- Syntax of both the pipelines is same.
- Interview question (write a raw syntax of a declarative pipeline)

### Input option in Directives
Taking approval before going to the next stage. For example we have terraform init, plan and apply. Before terraform apply, reviewers should approve. We can keep terraform init, plan and apply stages in pipeline. Not only terraform commands, we can also keep inputs to the environments like Dev, Sit, Uat, Prod.

### Jenkinsfile
- If small project, every resources (sg.tf, vpc.tf, ec2.tf files etc) will be in one folder. If big project
  then we can keep resources in separate repos (folders) same like "Roboshop-Infra-Dev" so that we can reduce
  the Refresh time, if we put all resources in one folder then "Refreshing Time" will be longer. Incase if we
  do any small changes also, it will take some time to reflect the resources. If we keep all the resources in
  separate repos (folders) we need to write separate jenkinsfiles for every resources.
- Go through the example of Jenkinsfile in 01-vpc in "Roboshop-Infra-Dev" folder, that means we can write
  Jenkinsfile (or) we can create pipeline for Infrastructure also. But in this project we did not created
  Jenkinsfiles for Infra because we rarely touch the infra, so infrastructure is created in normal way using
  terraform, this is just to show that we can also create jenkinsfile for infra also, so first create whole
  project infra and then do CICD in Jenkinsfile for every applications like catalogue, cart, shipping etc.
- So create ROBOSHOP-INFRA (anyname) folder in jenkins UI and add VPC in this folder as pipeline project,
  script path should be "01-vpc/jenkinsfile" similarly do for other infra like SG also just for practice.
- Instead of writing separate jenkinsfiles for all resources, we can keep one jenkinsfile and parameterize
  everything to work for all resources.
- You may get ERROR, Terraform command not found because it is running in the agent and agent dont have 
  terraform, so we need to install few tools in node server like "terraform command" and "aws configure"
  if you are using ony master then install in master only. While "aws configure" do not configure through
  root user because, master is connecting using centos, it is not taking sudo access.
- We have "when" with parameters condition in Jenkins pipeline (search in google)
- So overall we can write CICD for infra also for resources like vpc, sg, vpn etc.

Should we keep infra ready to create CICD for applications ? Project infra should be ready what is the project infra ? like vpc, sg, vpn, databases, app-alb, acm, web-alb etc. Whichever are long term that are project infra, whichever are short term those are application infra, so before you do CICD for applications we need to keep project infra ready, so now we should do CICD for catalogue app, for that we should have catalogue application should be in git and write a Jenkinsfile for catalogue application.

### CI (Continous Integration)
Continous Integration is nothing but whenever developers pushes the code to the git continously, we should have the below stages for catalogue application. If CI success then only we should go for CD.
- Get the catalogue version first if required
- Clone the catalogue code
- Install Dependencies
- Unit tests
- Multiple types of scans like Sonar-scan, SAST, DAST, Open-source, Docker-image etc.
- Build the code, to build the code we need to install npm
- Publish artifacts to nexus (nexus is a repo to hold artifacts)
- Deploy the code
- Post Build

### CD (Continous Deployment)
- Deploy to Dev, Sit, Uat, Prod environments.
- Functional test cases.
- Publish the results.

Create one separate repo in git and folder in VS for catalogue and keep the catalogue code in this folder, code can be downloaded from "daws" repository. Refer Catalogue folder in VS, package.json and server.json is the main code of catalogue and write a Jenkinsfile for this catalogue and refer "Jenkinsfile.bkp" for full script. We can see few dependencies are there in package.json and server.json, so we should write a code in pipeline syntax to download those dependencies.

### Build step in pipeline
To build and run the code, you need to have npm (Node Package Manager) installed. If you encounter an 
error saying "npm not found", it means npm is not installed on the agent server. To fix this, install Nodejs, which includes npm. Once npm is available, you can install the required Nodejs modules by following the documentation. These modules will be saved automatically in a folder called node_modules. The server.js file relies on these libraries from the node_modules folder to function properly. So, when you run npm install, this folder is created and populated with all the necessary libraries. After setup you can zip all project files, including the node_modules folder. Upload the zip file to the Nexus repository. When deploying to another server, you can simply unzip the file — there's no need to reinstall npm or run npm install again, since all dependencies are already included.

### Nexus repository
- When storing artifacts in the Nexus repository, we do not store source code. Instead, we store the output
  of code in the form of a ZIP file containing the build artifacts (including node_modules, etc.)
- We use Sonatype Nexus because it is a widely adopted and reliable artifact repository manager. Create an
  instance with a minimum of 2GB RAM and 30GB storage (t3.medium)
- While the actual installation is typically handled by the SRE (Site Reliability Engineering) team, it's
  important to understand the concept
- In most companies, internet access is restricted on production servers. Instead of downloading libraries
  directly from the internet, they maintain internal YUM repositories containing all necessary packages and
  dependencies.
- This is why Nexus acts as a central point — not only for storing build artifacts but also for serving as a
  local repository for all required libraries and dependencies.

### Commands to run in the nexus server
- sudo su - (Taking sudo access first)
- labauto
- Then select "nexus" (or) type "nexus"
- Select option 2
- netstat -lntp (It will take sometime to open port number of nexus 8081)
- sudo systemctl status nexus.
- Now take the IPaddress of the nexus server and paste in the chrome with 8081 port.
- Sign in process will be same as Jenkins and enable anonymous access.
- Now create a repository in the nexus for the catalogue to hold the catalogue artifacts in admin option,
  then settings options, repositories (Here you have lot of options, we can see yum respositories also), so
  create repo with "maven2 (Hosted)" is popular format.
- Name: Catalogue (Any-name), Version policy: Release/Snapshot/Mixed, Snapshot: Dev, Release: Prod and we
  selected Mixed, Layout policy: Permissive, Deployment policy: Allow redeploy because in Dev we can deploy
  multiple times.
- Now you will get the URL, where we can store the artifacts of catalogue.
- Remove workspace folder in pipeline in post section "deleteDir()" this is must.
- What is maven2 format ?
  1. For example 1000 students in a class, is there any chance of
  2. First name is same ? (It is possible) or
  3. First name + Last name is same ? (May be possible) or
  4. First name + Last name + DOB ? (May be possible) or
  5. So that means at some of time, if you add different combinations, it will become unique.
- Similarly we have project in company and inside it, we have modules like cart module, catalogue etc. and
  they have versions also. So terraform will follow a proper folder structure to store.
  1. Project  ---> Roboshop
  2. Modules ---> catalogue, cart etc.
  3. Versions ---> 1.0.0, 1.1.0, 2.0.0 etc. will increase versions in future. Using these 3 we can create
     an artifact ID, for example below
  4. Group_ID ---> Nothing but roboshop group, we give "com.roboshop" in reverse order
  5. Artifact_ID ---> Catalogue_artifact_ID
  6. Version ---> 10.0.0
  7. Folder structure be like com/roboshop/version/version_files.

### Points to remember
- Install "Pipeline Stage View Plugin" in jenkins.
- Declarative pipeline is more simplified than scripted pipeline.
- To create accesskey and secretkey, go to the SecurityCredentials from the profile.
- Then users/user(saikiranuser)/make sure to delete old keys and create new keys and download the csv
  file for future reference, because secret keys will be only view once.
- How to download any application code in gitbash ? "wget <URL>"
- Nexus port number is 8081
- Basically we dont touch the Infra (Very rare)
- To enable colours we have "ansiColor" plugin & keep "ansiColor('exterm')" in the options aswel & install
  plugin in the jenkins console also, manage_jenkins/plugins/available_plugins, make sure to restart jenkins
  in jenkins-master "sudo systemctl restart jenkins"
- How to create any file as backup ? using .bkp
- Example Jenkinsfile.bkp (or) main.tf.bkp etc.
