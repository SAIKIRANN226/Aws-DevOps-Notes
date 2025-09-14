### How to build all images at a time ?
for i in mongodb mysql catalogue cart user shipping payment web ; do cd $i ; docker build -t $i:v1 . ; cd .. ; done

### How to run all images as containers now ?
Before running images, make sure all images are ready. Then run all images as containers using "docker compose up -d" command.

### Best practices in Docker as a DevOps engineer do ?
- Search in google or chatgpt like docker best practices are like working with docker efficiently and securely.
- Use only official images
- Create custom dockerfiles
- Keep images and containers small like below 1GB, so in order to reduce the size of the image, you have to use base image also very small size (or) bare minimum OS from the dockerhub like alpine, disto, coreOS etc.
- Use multi stage builds. Mainly used for java applications, after building the source code, we get the jarfile, we will use 1 stage to build the jarfile and copy the jarfile into another stage, where we have only JDK and JRE environment that can reduce the image size because we dont need maven in run time environment.
- Use docker volumes to persist the data.
- Use custom networks to isolate containers from other projects.
- Docker system prune will delete the unused data and we reclaim the storage.

### Multi stage builds
- Multi stage builds are mostly used for java project, because in java we compile source code, we will get byte code (jar file) then we run byte code.
- JDK (Java development kit)
- JRE (Java runtime environment)
- If you want to run java application JRE is enough
- While developing we use JDK, but to run we use JRE, because JDK memory > JRE memory

### Docker volumes
- When you remove docker ? What happens to data ? Will data be removed ? Yes data also be deleted because containers are temperory
- Two types of volumes unnamed volumes & named volumes
- How you created network, similarly you can create docker volume also "docker volume create nginx" "docker volume inspect nginx"
- unnamed volumes will not be there in docker management you need to manage yourself, while named volumes you have docker commands to manage the volumes like removing, creating, inspect etc.
- When to use volumes ? When you using database applications then you have to use it. So create volumes and also mount it.
- You should not run container with root access because there may be chance that container getting complete file system access of the underline host. So create one system user in hostOS which ever like if you are using alpine then create user in alpine and add it to the group (Roboshop)

### Docker architecture
When you hit "docker run nginx" 
- Docker command will send a request to docker daemon (engine)
- Docker engine receives the request
- It will check wether the image is available in local or not ?
- If available it will create container and show the response to client
- If not available then it will pull from central dockerhub and keep it in local.
- Create container and respond to client

### Docker layers
- What ever instructions you write that are nothing but layers
- For example first instruction is baseOS
- Then create container out of base instruction
- Next runs second instruction inside the container
- Then it will create image out of these
- Then it will create container out of those 2 instructions
- It will run next instruction

### Points to remember
- Instead of installing docker and docker compose manually, siva has created one shellscript to install automatically so use that "curl <RAW_URL> | sudo bash"
- How to check logs of a container ? docker logs shipping
