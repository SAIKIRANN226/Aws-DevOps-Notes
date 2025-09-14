### How to create our own image using Dockerfiles ?
- Create 1 repo in github for this Dockerfile.
- Create 1 folder "FROM" this is nothing but first instruction because we need base OS, you can refer in
  docker references website.
- Then write Dockerfile inside the FROM folder.
- File should be "Dockerfile" D must be capital letter. Go through the code in VS.
- Create 1 instance for docker and login, install docker init.
- Clone the git repo in the docker server, and go to the FROM folder
- Now build docker image here using "docker build -t URL/Username/Image:VERSION ."
- URL is where we push docker image after building, we have multiple URLs like we have "docker.io" we have ECR
  URL in amazon, we also have Nexus docker registry URL, you can push to any URL. Generally companies will
  push ECR and Docker registry, not to Docker hub.
- If you dont give any URL, bydefault it will push to the docker hub
- docker build -t joindevops/from:v1 .
- Before pushing, we need to login
- If you dont give URL,Username. That means you are maintaining image in your local, by using the below
  "docker build -t from:v1 ." it will start building the image
- Then see "docker images"
- To push this image after saving in your local, you need to retag by using below command.
- "docker tag from:v1 joindevops/from:v1"
