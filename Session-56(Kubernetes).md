### We have only two Process
- For example if you want to install windows11 in your laptop, you must have a physical pendrive and in that it should have windows11 software to install in laptop, then we will give lot of configuration options while installing, So similarly We build image and push to the dockerhub, and we write manifest files and inform kubernetes how to run the image.

### Configuring roboshop project into kubernetes
- First we are going for Mongodb and in mongodb, we are following above two steps only.
- Keep Dockerfile, catalogue.js, user.js files
- Next login "docker login" 
- Next build the image in mongodb location in server ---> docker build -t joindevops/mongodb:v1 .
- Now push it ---> docker push joindevops/mongodb:v1
- Next create kubernetes manifest file, which resource should be use ? Pod vs ReplicaSet vs Deployment ? We use only Deployment.
- Create namespace.yaml file.
- Next create catalogue same above steps.
