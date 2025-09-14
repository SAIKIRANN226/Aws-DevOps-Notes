### What are the disadvantages in Docker ?
- We have Docker host (Docker server) where all containers are running, what if Docker crash ? We lose all containers.
- Even we use docker volumes, data is still in the docker host, so we lose data.
- What if traffic increases or decreases ? are our containers scalable ?
- Even we have multiple containers to balance the load, who is the load balancers ?
- What if some containers are crashed ? Will docker host able to make it available ?
- What about configuration and secrets ? Where to store them ?
- What if we have multiple hosts running with containers ?

### What is Orchestrator ?
- Kubernetes is the popular container orchestrator tool.
- Docker is used for building the images, it can also run containers but not scalable also have above disadvantages.
- In Docker we have rich features to build the image like storing, retrive images etc. But running the containers are not in docker because of above disadvantages, so we use kubernetes to run and manage the containers.
<img width="981" height="413" alt="Screenshot 2025-09-14 114534" src="https://github.com/user-attachments/assets/ffa542cf-852e-438e-b9a5-c2eb174a5137" />
- What is minikube ? It is a single node cluster, master and node is same, it is just to practice few k8 resources, it is not scalable.
