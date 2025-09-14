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
- Go through the code of Terraform-aws-minikube in VS. Created from the open source repo from the internet. Nothing but creating one instance in default subnet and installing all k8 components in it automatically.
- What is Workstation and Cluster ? To connect to cluster we need client component that is nothing but workstation (Docker host or Docker server)
- When you create minikube server and login into superputty or in gitbash, aftersome time, a "kubeconfig" file is created and it contains authentication information to connect to kubernetes cluster, so we should have "kubectl" command to connect to k8 cluster, this command is automatically installed in minikube.
- kubectl command will check automatically a file in home folder ~/.kube/config
- Create .kube dicrectory and move that config file into .kube folder --> "cp kubeconfig .kube/config" renaming should be config not kubeconfig
- After creating workstation and minikube cluster, how to connect to minikube from workstation, so install "kubectl install centos" search in google and also give execution access to kubectl. Move that kubectl into /usr/local/bin/kubectl
- To connect to server, you must have authentication file (kubeconfig), so create one folder ".kube" and paste the authentication file inside this folder. You can copy form gitbash also using cat command. vim config (name should be config)

### Kubernetes (K8) Everything here we call resources
- Similar to VPC, we have "Namespace" resource in K8, it is like a project in your kubernetes cluster to provision the resources, it is isolated.
- Every resource is in yaml format with a basic syntax.
- Every resource will be created with apiVersion
- Go through the K8-resources in VS.
- kubectl create -f namespace.yaml ; kubectl get namspaces ; kubectl delete -f namespace.yaml
- If you use create onceagain you will get error already exist
- If you use apply, if not created it will create, if you use again any changes it will update or it will say unchanged.
- Next we have "Pods" is a simple container, it is the smallest deployable unit in kubernetes
- Difference between Pod & Container ? A Pod can contain multiple containers















