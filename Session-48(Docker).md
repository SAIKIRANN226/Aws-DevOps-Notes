### Overview of the Previous Sessions
- We learned linux commands for system management.
- First we configured the project Manually.
- Then automated the project using Shellscript and Ansible.
- Then created Infrastructure using Terraform.
- Project Infrastructure + Jenkins CICD for Applications + We installed Applications.
- Finally we deployed into the VMs in AWS cloud (Like EC2 is nothing but a VM)
- That means till now our Applications are deployed into VM based.
- From this sessions, we are going to Deploy applications in Docker & Containerization.

### Containerization
Containerization is a lightweight form of virtualization (VM) that involves packaging an application and all its dependencies (Like libraries, configuration files, & binaries) into a single, self-contained unit called a container. This allows the application to run consistently across different environments from a Developer's laptop to test environments to Production servers. How the world evolved from past is the below example.
Physical severs (Laptop) ---> Virtualization (VM) ---> Containerization. When we compare these 3 we have more security in Physical servers, however we can increase security by taking few steps in later sessions.

- Physical servers booting time is very high from configuring to until application is UP & RUNNING.
- Virtualization VM's booting time is medium from configuring to until application is UP & RUNNING.
- Containers booting time is very fast from configuring to until application is UP & RUNNING.

### Virtualization concept
- Cloud technologies are using VM-Ware concept, a Big Physical server (For example 16GB ram, 1TB HDD & CPU)
  will be there. We will divide this big server into multiple logical servers like below.
- Host OS ---> Windows ; VM-ware ---> We install Hypervisor software in Host OS ---> Guest OS.
- Here Guest OS is nothing but Logical server, we can create multiple logical servers like below.
- For Ubuntu ---> 1GB ram, 100GB HDD (Isolated from the other servers)
- For Centos ---> 1GB ram, 100GB HDD (Isolated from the other servers)
- For Fedora ---> 1GB ram, 100GB HDD (Isolated from the other servers) these are like VMs
- This whole process is called "Resource Utilization" from the Physical server.
- When you create a server in aws, it will create from the Big Physical server only, however these servers
  are isolated from the other servers and big physical server aswel.
- Resource Utilization is good in VM when compared to Physical servers.
- We also have "Dedicated Hosts" in aws, nothing but Physical servers used by big companies.
- When we are moving to Docker and Kubernetes, we dont care what is the underline OS.
- Create an account for "Docker Hub" 

### How the containers will be created from VM ?
For example we have created 1 Guest OS (or) 1 VM for Centos (1GB ram, Centos, 100GB HDD) But application is used only 0.1GB of ram, 10GB of HDD, remaining space is wasted right ? So this is nothing but virtualization VM concept right ? and here Hypervisor is blocking remaining space, that means resource utilization is not that much better when compared to containers. So in this VM only we have containerization concept, nothing but we have containers installed in this VM, containers are isolated from each other (Similar to the individual rooms example) but system resources (CentOS, 1GB ram, 100GB HDD) are shared, that means containers will take resources based on their demand from this system resources. System resources will dont block. Boot time is very less (With in seconds) compared to VM (EC2 instance).

### Configuration
When comparing with the example of vacating the place from Independent house, Apartment, Individual rooms. We can take all the things in a single bag (All your things are nothing but configuration) and we can vacate the Individual room with in hours, but when we try to vacate the Flat in Apartment, your things (Configuration) will be more compared to Individual room and vacating time will be more like 2-3 days. So similarly when you are vacating from the Independent house is also same, (All your things are even more configuration) it will take atleast one week time to vacate.

### Example of AMI (You want to set up 10 laptops for your office team)
- Option 1
- Buy 10 empty laptops.
- Install Windows on each.
- Install Chrome, MS Office, Zoom, and configure settings one by one. This takes a lot of time.
- Option 2 (better)
- Set up one laptop perfectly with Windows + Chrome + MS Office + Zoom + settings.
- Take a clone image (backup) of that laptop.
- Copy that image to 10 laptops. Now all laptops are identical and ready quickly.

### Example of how ami will be ?
- AMI ---> Server + configured the server using ansible + stop the server + take AMI
- Container ---> FatOS + application run time + created users + created directory + installed application.

### Understanding Amazon Machine Image (AMI) and Docker Image
How do we launch an EC2 instance ? by using AMI right ? Amazon will provide multiple AMI's to launch EC2, 
and we can also create our own AMI and use it, like siva created Centos-8 AMI for us. So similarly to launch 
a container, we need Docker Image, we can also create our own Docker image. That means container is the running version of Docker Image and EC2 is the running version of Amazon Machine Image (AMI). What we have done previously in AMI ---> We have FAT OS (4GB) + Application run time (Java, nodejs etc) + Created users + Created a directory + Installed the application right ? that means while deploying catalogue, We took 1 server + Configured the server using ansible like above all + Stop the server + Take AMI. This is nothing but Amazon Machine Image, we can use AMI image as many times we want, instead of taking one server and doing from the scratch, if image is ready, it is easy for us to deploy applications. Similarly Docker image is also same, but the only difference when compared to Docker Image. Docker image (Like individual room) We have Base OS (250MB) + Application run time (Java, nodejs etc) + Created users + Created a directory + Installed the application. Total space used here around 500MB. AMI (Like apartment) We have FAT OS (4GB) + Application run time (Java, nodejs etc) + Created users + Created a directory + Installed the application.

### Working in DEV, but not working in PROD 
Main issue is configuration changes and OS, is if you use different OS in QA, UAT or PROD, but the advantage of docker image is we take same image from Dev to Sit, Uat, Prod. Thats why we call it as immutable image and portable, we even dont know what is the base OS we are using, but our intention is image should work.

### How to install docker in servers ?
- Create 1 server with (t2.micro) with 30GB
- Search in google "docker install for centos"
- Run the shown commands in the server with sudo su -
- When you install docker, a group called "docker" is created
- Users who are in this group, they can only access docker commands without root user.
- So add your user centos to this group. "usermod -aG docker centos"
- Then logout & login again in server.
- Now docker commands will work without root user.

### Docker commands
- docker images ---> Show you the images exist in the server.
- docker pull nginx ---> Image will be pulled from "Docker Hub" here nginx image is Base OS + nginx 
- Bydefault it will pull the latest nginx (or) if you want you can give specific tags.
  "docker pull nginx:stable-bullseye" etc.
- Now create container from the above created image nginx "docker create nginx:latest"
- To make the container run "docker start <container_id>"
- To see the running containers "docker ps" ; To see all containers with all status "docker ps -a"
- To remove "docker rm <container_id>" before you need to stop "docker stop <container_id>"
- To remove without stopping ---> "docker rm -f <container_id>"
- To remove images ---> "docker rmi <image_name>/image_id"
- To remove all images at a time ---> "docker images -a -q" then "docker rmi `docker images -a q`"
- Instead of Pull + Create + Run commands ---> "docker run nginx"
- To run in background "docker run -d nginx" here -d is detach.
- How to access nginx then ? you cannot use VM port to container, so you need to allocate any port to the
  server first "docker run -d -p 8080:80 nginx" 8080 port is for VM, this is mapped with nginx port 80. This
  is interview question, how can you expose a port of a container ?
- You cannot use same port 8080 because it is already allocated, you can use any other random ports.
- When you create container, you are getting random names.
- To create with name use "docker run -d -p 8081:80 --name sai nginx"
- How can you login to the existing container ? container is also a light weight VM.
- "docker exec -it <container_name/container_id> bash" to see OS, just cat /etc/*release
- Container will also have IP address ---> docker inspect <container_id>

### How to create our own Docker image ?
We have "dockerfiles" is a declarative way of creating our own images, same as shellscript, we put all linux commands in shellscript instead of using one by one commands. Search in google like dockerfiles reference. So create a repo for this also.

### Points to remember
- Monolithic (or) legacy ---> Frontend + Backend (War file and Ear file) say almost 100MB.
- Then later Frontend and Backend got divided. So we started using VMs for Monolithic apps
- That means we have 1 VM for Frontend (UI) ---> 50MB
- Another VM for Backend (Catalogue+user+shipping all in 1 VM) ---> 50MB
- Later we got microservices, they are completely independent applications.
- Since these are very low in space like 5MB like that, so you dont need a VM to run a Microservices,
  so containers are the best approach. We need just Base OS for containers.
