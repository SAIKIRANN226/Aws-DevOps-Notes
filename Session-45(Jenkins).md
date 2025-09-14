### Types of scannings in Jenkins pipeline
- Static Source Code Analysis ---> It will test the source code without executing the program and also it
  will find the potential bugs, security vulnerabilities, code quality issues, and ensure we are meeting the
  project (or) company standards or not ? "Sonarqube" is most widely used tool for this type of testing.
- Static Application Security Testing (SAST) ---> Mainly focus on the security without executing the program to
  identify security vulnerabilities early in Dev Environment. "Fortify" is the tool.
- Dynamic Application Security Testing (DAST) ---> Like if anybody hacks how they test the application, same
  intense testing will be done by DAST while application is running in Dev itself & tool is "Web inspect"
- Open Source Library Scanning ---> We get all the libraries from the internet right ? to scan these we use a
  tool called "Nexus IQ"
- Docker Image Scanning ---> We have "TwistLock" (or) "ECR Scanning"
- We are using "Shift-Left" method, we do all types of scannings in Dev enviroment itself, to make sure
  everything is ok, then only we can go for the higher environments.
- All the scanning tools are costly but siva tried to implement only Sonarqube and Docker.

### How the Sonarqube scanner will work ?
- Note that same process for any scanning tools.
- Jenkins-Agent will clone the code in his server, and jenkins agents have scanner cli software which need
  to be installed, it will scan the code and upload to the "Sonarqube" console (or) server.
- Then developers will see the results in "Sonarqube" console (or) server.

### Sonarqube installation and setup
- First create 1 instance for Sonarqube (t3.medium) with 30GB, actually this should be taken care by the
  SRE team only not DevOps team, but we should have idea about how the installation is done.
- Take sudo access "sudo su -" ; then "labauto" command ; Select the number 60 which is "sonarqube"
- Then "netstat -lntp" port for sonarqube is 9000
- Now take the IP address of sonarqube with port 9000 and enter in the URL tab.
- Username: admin ; Password: admin ; Then change the password
- Install "scanner cli" in agent-server ---> sudo su - ; labauto ; select 61 (sonar-scanner)
- In which location this sonar-scanner will install ? /opt/sonar/conf/sonar-scanner.properties
- Then vim sonar-scanner.properties and give the below two credentials without any gaps.
- sonar.host.url=http://44.333.22.206:9000, give privateIP, since publicIP is dynamic and remove #
- sonar.login=<token> by generating token sonarqube console My_account/Security.
- Now sonar-scanner cli will able to publish the results into the sonarqube console.

### Sonar-project.properties
If you want to configure in CI pipeline, you need to create this file, "sonar-scanner" is the command to read sonar-project.properties to scan the code and uploading the results. Go through the code in VS. Push to the git and run the CI pipeline in jenkins UI.

### Quality Gates in sonarqube (We keep some standards)
As a devops engineer, we need clean code like 0 Bugs, 0 Code snells, Security rating should be A, Code coverage should be 80 etc to deploy into production. So create a Quality Gate (Any-name) & add condition On Overall Code, here we need developer to choose among different options, but rightnow we are going for one option "Condition coverage" and value 80 and also add another condition like Code snells should be 0, Vulnerability should be 0, Bugs should be 0, Maintainability rating should be A, Security rating should be A. So in this way you can add any number of conditions by sitting with developer. You can also keep same conditions for New code also & click on the "Set as Default". If quality gates failed, should we fail the pipeline and inform developers to fix this code ? yes fail the pipeline and inform developers. So we should keep a condition in pipeline (sonar-project.properties) to fail the pipeline "sonar.qualitygate.wait=true" node modules comes from internet, so NO need to scan node_modules directory here, so we put this line of code in properties "sonar.exclusions=node_modules**

### Actual scenario in the company
Till now we directly pushed into the main branch right ? so now we need to create feature branch and do the changes and then push it to the main branch, because as we know in Git we have multiple branches, so single pipeline will not work, we need to create multi-branch pipeline. We have Language (Catalogue is NodeJS) and Deployment platform (We can deploy in aws VM, Docker, Kubernetes, or On-premise). Depends up on these two, we need to create pipeline because different Languages and Deployment platforms have different commands. For example HDFC bank have 200 projects and many microservices, here if you write a pipeline for NodeJS and VM, it should applicable to all NodeJS and VM projects instead of duplicating the pipeline, nothing but if you want to add one small stage in the pipeline, you cannot add in all the multiple pipelines right ? so instead we can change at one place and it will applicable to all NodeJS and VM projects, this is same as Terraform modules for reuse. So for this only jenkins has given an option called "Jenkins shared library" treat your pipeline as library and use it where ever you want.

### Process for the above concept
- Create a feature branch in catalogue
- Configure multi-branch pipeline
- Configure Jenkins shared libraries

### Jenkins shared library (Centralized pipeline)
Go through the code of "Roboshop-shared-library" in VS, here we can write our pipelines with minimum code. Inside the vars folder, we created a centralized pipeline for nodejs and named as "nodejsVM.groovy" this pipeline will work for all nodejs and VM projects, we need to inform this Jenkins shared library repo to the jenkins by going to the manage jenkins/system/global pipeline libraries/add here, default version should be main and name (Any-name)/project repo should be git URL. Refer this library jenkins pipeline using @Library('roboshop-shared-library') and send parameters like what type of application and component. Similarly we can also create for javaVM/pythonVM/goVM etc. Whatever files there in "Roboshop-shared-library" are called as Shared libraries (or) Centralized Pipelines. Below is the overall process.
- I created a repo "Roboshop-shared-library" and added pipelines here
- I added Jenkins system configuration, location and name of the library
- How to refer this in Jenkinsfile in catalogue ? go through VS.

### Points to remember
- For Jenkins, database will be stored inside the server in /var/lib/jenkins, but for Sonarqube especially
  in production env, the storage will be in dedicated databases like postssql, mysql.
- We have developer version also for sonarqube, install that in server without database for practice.
- You can create multiple quality gates in sonarqube.
- How to backup the jenkinsfile ? "Jenkinsfile.bkp" (or) main.tf.bkp for terraform
- You should say we are using multi-branch pipeline in jenkins.
- Who is the owner of the catalogue repo ? Developer
