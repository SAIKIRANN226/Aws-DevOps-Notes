### Algorithm for Catalogue (CI)
- Create EC2 for Jenkins-Master and connect to it in "super putty"
- Create EC2 for Agent and install nodejs from the catalogue documentation.
- Configure the Jenkins-Agent in manage jenkins.
- Install plugins like AnsiColor, Stage View, Pipeline Utility steps, Nexus artifact uploader.
- Create EC2 for Nexus and connect to it and download nexus by using "labauto" and other commands.
- Create repo in nexus for catalogue to store "catalogue.zip" artifact.
- To push artifacts from jenkins to the nexus, we need to download plugin called Nexus artifact uploader.
- Give the nexusURL and authentication, make sure to add nexus credentials in manage jenkins.
- This is only CI part of catalogue (Until the creation and pushing the artifacts to Nexus)
- "Nexus artifact uploader plugin" So the created CI pipeline and artifact is in jenkins, how to upload that
  artifact into the nexus repo ? for that we have nexus artifact uploader, install this plugin in jenkins
  aswel as write a code in pipeline also.

### Algorithm for Catalogue (CD)
- General Deployment of any application is below.
- Create the server
- Provision the created server using ansible (or) any other scripting language
- Stop the server
- Take AMI
- Create Launch template version
- Refresh auto-scaling

### Process for Continuous Deployment
- First we need to create infrastructure. Create atleast vpc, sg, vpn, databases, app-alb in order to work
  catalogue using normal way terraform commands like init, plan and apply
- You should create catalogue CD by writing jenkinsfile
- Create separate folder for "Catalogue-CD" in VS and also create terraform folder inside the catalogue folder
  and copy the code of catalogue from the "Terraform-Infra-Dev" into this catalogue terraform folder.
- Since the catalogue is private instance, first connect to VPN.
- Dont forget to put ".gitignore" in terraform folder.
- Terraform folder, Jenkinsfile are nothing but deployment scripts.

Previously ansible was downloading the package from the s3 bucket and version was hardcoded, now ansible should download artifact and version from the nexus, so what should we give to the ansible as input ? "Nexus location and Artifact version" that means first it will call main playbook from the roles, so we need to send artifact version to the ansible playbook from the terraform. So create "Catalogue-CD" in VS and we keep all the deployment scripts here and write Jenkinsfile for this. When you build with parameter, then this "Catalogue-CI" should send the value of "verison and environment", so how to call another pipeline from the jenkins pipeline using parameters ? For that we have a small syntax, should be used in the CI part in deploy stage "build job: "catalogue-deploy", wait: true, parameters: params"

### How the artifact version is travelling ?
- Get the version in CI pipeline
- Build ZIP + Upload to Nexus
- Pass Version to CD Pipeline from CI Pipeline
- CD Pipeline Receives the Version
- Terraform Gets version using command line arguments from jenkins CD pipeline
- Terraform Passes to Ansible playbook
- Ansible Uses It to Download Artifact
- Make sure to do changes in ansible playbook that instead of downloading package from s3 we it should
  download from the nexus, you can change in roles/common/app-setup.yaml

### We have a "Upstream job" and "Downstream job"
That means when CI part is success then only it will call CD. Jenkins have application version, it should send that version to terraform, how does it send to terraform ? so we should create a variable of "app_version" in terraform variables. So first write terraform init stage. Here upstream is catalogue-CI and downstream is catalogue-CD

### Points to remember
- Industries will follow Semantic version like major version, minor version, patch version.
- For example 1.0.0 we call semantic version, 1.1.0 is minor version, 2.0.0 is major version like that.
- Until creating artifacts is nothing but CI-part.
- Everytime refreshing and again clicking on build, instead we can download plugin called "Rebuilder"
- Since catalogue is accepting connections from VPN, so we need to attach VPN SG to the agent instance.
- How to call another pipeline from jenkins pipeline ? using "build job"
