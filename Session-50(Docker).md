### RUN instruction in Dockerfiles
The RUN instruction in a Dockerfile executes commands during the image build process. Each RUN instruction creates a new layer in the Docker image, capturing the changes made by the executed command. Go to the RUN folder in server and "docker build -t run:v1 ." (or) RUN instruction is used for software installations or configuration while building the image.


### RUN vs CMD instruction ?
When you do "systemctl start catalogue" it will create 1 nodejs process and this process will run for infinite times, until this process is running, then only we can say catalogue application is running, if this process is stopped, then your application is not running. Here CMD instruction is to make your container running ; RUN instruction will run at the time of image building ; CMD instruction will run at the time of container creation. As we know container is the running version of image, if container is running that means there is something that keeps it running, that is nothing but CMD instruction, so to make container to run infinite times, we use CMD instruction. What should we keep in CMD to run container continuously ? Then use the command
"docker build -t cmd:v1"
- docker build -t run:v1 ---> Run these commands inside the dockerfiles only. Use small letters while executing the commands like from, run, copy, add etc.
- RUN vs CMD ? Popular interview question ? RUN at the time image building, CMD at the time of container creation.
- RUN instruction is used to execute the commands during the image build process, its not for running when the container starts, but for preparing the image.
- CMD does not run during build time, it runs only when you start a container from the image.
- Note that systemctl commands will not work in container because containers are not in main OS, it is in baseOS, systemctl commands will only work in FatOS. So we need to give command manually in order to run the nginx in docker "CMD ["nginx","-g","daemon off;"] you can search in google to get this command. To run your image as a container infinite times, you need to keep this command ["nginx","-g","daemon off;"] run it in background and this should be foreground and attach to the screen, then send it to the background, we are using -d detach mode in the command. Now Push to github, pull in server, go to CMD location, docker build -t cmd:v1 .
- How to run the CMD container ? docker run -d -p 80:80 cmd:v1
- LABEL instruction, nothing but tags, for example we have 100 white covers and all are white, you know only when you open them, so we give labels to identify easily. That means labels are used for filtering images.
- How to filter these labels ? docker images --filter label=Trainer=Sivakumar
- EXPOSE instruction is to find image is using which ports ? docker inspect <image-id>
- ENV instruction is a key-value pair and can be used inside the container.
- COPY instruction is to copy your file from local to your image.
- ADD instruction is also same as COPY, both are used to copy the files from local to image, but ADD have 2 extra capabilities one is it can directly download files from internet and it can directly untar the tar files.
- ENTRYPOINT instruction is very important in inteview questions. CMD vs ENTRYPOINT
- Both will run at the time of container creation only. CDM command can be overridden by another command at run time, while ENTRYPOINT command cannot be overridden, if you try to do so, the command you are entering at the run time will go and append to ENTRYPOINT.
- We can use CMD and ENTRYPOINT for best results, like CMD is supplying the default arguments to ENTRYPOINT, user can always override CMD arguments at the run time. Nothing but like we are not giving access to override the main command to users, if user forgot to give arguments, we have CMD to supply the default arguments.
- USER instruction defines which Linux user the container should run as (instead of default root), mainly for security. We can restrict root access with USER instruction.
- WORKDIR instruction is sets the default directory inside the container where commands will run, similar to setting a current working directory with cd .
- ARG vs ENV instruction ? ARG will provide values to the dockerfile only at build time, while ENV will access values at build time and also run time and in the container also.
- ONBUILD instruction is rarely used today, but it’s handy for creating reusable base images.

### Points to remember
- Systemctl commands will not work in containers, to work it should be main OS, but container is not using
  main OS right ? it is only using base OS. We need to give command manually.
