### Configure roboshop using Dockerfiles
Nothing but creating dockerfiles for components and deploy as containers. Create a folder in VS "Roboshop-Docker" We now create Dockerfiles, create or build image, run as containers. First create for mongodb
No need of baseOS, we can directly take official mongodb images from the dockerhub instead of take baseOS (Centos) and installing programming languages or nginx. You can directly use official mongodb image.

### Dockerfile for mongodb component
- Refer dockerfiles from internet of roboshop repo. Use according to our roboshop documentation, dont use all options from here, because few options are not related to roboshop documentation.
- Keep *.js files, we have js files of catalogue, user
- These js files will load into mongodb automatically.
- Next build the image "docker build -t mongodb:v1 ." Use names here not ip addresses because it will be changing, names will work as a dns.
- See wether the image is created or not ? "docker images"
- Next "docker run -d --name mongodb mongodb(image-name):v1"
- Now check logs ? "docker logs mongodb"

### Dockerfile for catalogue component
- Refer Dockerfile in roboshop github from internet. Use nodejs:18 as per our documentation not 14. So take nodejs18 image from the dockerhub.
- Keep server.js and package.json files.

### Networking in Docker
- As we know our modem is having publicIP and that publicIP is giving internal IPs to our laptops, phones, etc. which are used internal nothing but NAT right ?
- ifconfig, if you enter this command in server, you will see a few lines of code of "eth0:" similar to the NAT in docker also we have one publicIP(provided by aws through ethernet) and that publicIP will give IP addresses to the containers
- So similarly a modem (docker0) is created by default, so this docker0 has IP for example 172.17.0.1 and this IP will give to the containers like 172.17.0.1/2/3/4....
- We have one disadvantage if containers are in default network, container cannot communicate with each other through names if they are using docker default network.
- So create our own network in docker ? docker network create roboshop
- "docker run -d --name mongodb --network=roboshop mongodb:v1" nothing but we are telling our containers to use roboshop network to communicate.

### Dockerfile for web component
- Follow same process but make changes according to your roboshop project.
- Same for other components also.

### What is Docker compose ?
Instead of starting containers one by one or stopping, we can use "Docker compose" you need to install this docker compose in docker server from the internet using commands. And write a "docker-compose.yaml" for whole containers. Just use "docker compose up -d" "docker compose down"

### Points to remember
- Take t3.medium for Docker instance, because we run more containers.
- You can see roboshop project in internet, there you have docker files for reference.
