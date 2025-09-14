### Algorithm for CICD pipeline for Roboshop
- Make sure Dev and Prod Infra is ready, create jenkinsfile for this also.
- Get connected to two separate VPN's for Dev and Prod environments.
- For example we are going for catalogue, then create 1 catalogue repo and jenkinsfile, point this
  jenkinsfile to share libraries (dry principle and centralized pipeline) and also make sure you have
  shared libraries configured in jenkins system configuration in manage jenkins.
- Shared library VM pipeline will be called and stages will be clone, get the version from package.json,
  install dependencies, unit tests, build, scans (sonar,sast,open sourcelibraries scan, dast), if developer
  opts for deploy, we can deploy.
- Then catalogue-deploy will call terraform-roboshop-app.
- We are passing environment, version, component to the bootstrap script.
- Bootstrap script will clone roboshop-ansible-roles-tf and run catalogue role.

### Setting up CICD for User module now
As a DevOps team, we have nodejs CICD is ready and a new project user module is started by the developers and how can you setup CICD for user module ? user module developers will send a mail to the DevOps team stating that we are started user module and we want DevOps team to help us to setup CICD for user module, then DevOps team setup meeting with developers and explain our centralized pipeline structure which we used for catalogue. So now setup user module. Create 1 repo for user module and tell them to keep the jenkinsfile. Dont forget to create repo for user in nexus. If new project is started they should have repo existed in nexus, generally this willl do SRE team, but here we should.


### Points to remember
- Few companies keep single VPN for all environments, we can also keep single VPN, but it is better to
  keep VPN for every environment.
- Generally we dont load the data into the mongodb using ec2 instance, we have admin UI to load the data,
  since we dont have any option, so we are loading through ec2 instance.
- Normal pipeline for CD (deploy), multi-branch pipeline for CI
