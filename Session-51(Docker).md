### Configure roboshop using Dockerfiles
Nothing but creating dockerfiles for components and deploy as containers. Create a folder in VS "Roboshop-Docker" We now create Dockerfiles, create or build image, run as containers. First create for mongodb
No need of baseOS, we can directly take official mongodb images from the dockerhub instead of take baseOS (Centos) and installing programming languages or nginx. You can directly use official mongodb image.

### Concept of eth 0 (ethernet)
When you enter 'ifconfig' in server, you see 'docker 0' this is the docker created its own ethernet network ip that is nothing but gateway ip, this docker 0 will give ip addresses to containers. How to see the containers ip address ? 'docker inspect container_id' you see gateway ip and container ip. The only disadvantage here is containers cannot communicate with each other through names, if they use docker default network. In docker we have 2 types of networking 'host and bridge' so we use bridge networking instead of host (Docker 0 ethernet). So create our own roboshop network and this network is used by containers. If you want to know the commands to create network just 'docker network' Now create 'docker create network roboshop' to see all networks 'docker network ls' bydefault it is bridge network, when you check 'ifconfig' you can see your created network, you can see the gateway ip of roboshop network. So now run the catalogue using 'docker run -d --name mongodb --network=roboshop mongodb:v1'

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

### Concept of docker compose ?
We have dependencies like one component is depending on another components, if we want to run whole project you want to start one by one component, if you want to stop the project, you will stop one by one component. We can use "Docker compose" to make it easy, so you need to install this docker compose for linux for centos 8 in docker server from the internet using commands. And write a "docker-compose.yaml" for whole containers. What does docker compose will do ? It will create a network, create volumes, attach network and volumes to the containers. Same as shellscript instead of running one by one commands. Just use 'docker compose up -d' "docker compose down" this command will create all containers of mongodb, catalogue, web, cart etc. at a time but while creating it will check the dependencies in docker compose. To remove all containers at a time, then 'docker compose down'

### Points to remember
- Take t3.medium for Docker instance, because we run more containers.
- You can see roboshop project in internet, there you have docker files for reference.
