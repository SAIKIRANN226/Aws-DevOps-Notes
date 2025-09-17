### What are the disadvantages in Docker ?
- We have Docker host (Docker server) where all containers are running, what if Docker crash ? We lose all containers.
- Even we use docker volumes, data is still in the docker host, so we lose data.
- What if traffic increases or decreases ? are our containers scalable ?
- Even we have multiple containers to balance the load, who is the load balancers ?
- What if some containers are crashed ? Will docker host able to make it available ?
- What about configuration and secrets ? Where to store them ?
- What if we have multiple hosts running with containers ?

### What is a Kubernetes Cluster?
A Kubernetes Cluster is just a group of computers (servers) that work together to run your applications (containers). These computers can be real servers or virtual machines (VMs) in the cloud. Kubernetes makes sure your applications are always running, healthy, and can handle more users when needed.

### Structure of a Kubernetes Cluster ?
- A cluster has two main parts
- Control Plane (The brain/manager) Decides what should run where. Watches the system and makes sure everything is running as expected. Example think of it as a school principal who assigns teachers (Apps) to classrooms (Servers).
- Worker Nodes (The workers) These are the machines that actually run your applications inside Pods. Example Classrooms where teaching happens.

### What is a Pod?
- A Pod is the smallest unit in Kubernetes.
- A Pod is like a box that contains one or more containers (Your app + dependencies).
- Example If your app is a website, one Pod might have:
- A container for the frontend (React/Angular)
- A container for the backend (Node.js/Java)

### Example to Understand Better, Imagine you are running an online food delivery app (Like Swiggy/Zomato).
- You need A frontend (users place orders) ; A backend (handles orders, payments) ; A database (stores user data, orders)
- Without Kubernetes: You would manually run these apps on servers, restart them if they fail, and scale them when more users join. Hard work!
- With Kubernetes, You tell Kubernetes that
- "I want 3 copies of frontend, 2 copies of backend, and 1 database."
- Kubernetes decides where to run them (on worker nodes).
- If one server goes down, Kubernetes automatically moves those apps to another server.
- If more users join, Kubernetes can automatically add more Pods (scaling).

### Real-World Analogy
Think of Kubernetes as
- Control Plane = The Manager in a restaurant (knows what needs to be cooked, assigns chefs).
- Worker Nodes = The Chefs (do the actual cooking).
- Pods = Kitchen stations (where cooking actually happens).
- Containers = The dishes (food items).
So, the manager doesn’t cook. He just tells chefs what to cook and makes sure everything is running smoothly.

### In short
- A Kubernetes Cluster = a team of servers (nodes)
- Control Plane = boss who manages things
- Worker Nodes = staff that do the work (run apps)
- Pods = little boxes where your apps live
  
### What is Orchestrator ?
- Kubernetes is the popular container orchestrator tool.
- Docker is used for building the images, it can also run containers but not scalable also have above disadvantages.
- In Docker we have rich features to build the image like storing, retrive images etc. But running the containers are not in docker because of above disadvantages, so we use kubernetes to run and manage the containers.
<img width="981" height="413" alt="Screenshot 2025-09-14 114534" src="https://github.com/user-attachments/assets/ffa542cf-852e-438e-b9a5-c2eb174a5137" />
- What is minikube ? It is a single node cluster, master and node is same, it is just to practice few k8 resources, it is not scalable.
- Go through the code of Terraform-aws-minikube in VS. Created from the open source repo from the internet. Nothing but creating one instance in default subnet and installing all k8 components in it automatically.
- What is Workstation and Cluster ? To connect to cluster we need client component that is nothing but workstation (Docker host or Docker server)
- After creating minikube server, login into superputty or in gitbash, aftersome time, a "kubeconfig" file is created and it contains authentication information to connect to kubernetes cluster, so we should have "kubectl" command to connect to k8 cluster, this command is automatically installed in minikube.
- kubectl command will check automatically a file in home folder ~/.kube/config
- Create .kube dicrectory and move that config file into .kube folder --> "cp kubeconfig .kube/config" renaming should be config not kubeconfig
- After creating workstation and minikube cluster, how to connect to minikube from workstation, so install "kubectl install centos" search in google and also give execution access to kubectl. Move that kubectl into /usr/local/bin/kubectl
- To connect to server, you must have authentication file (kubeconfig), so create one folder ".kube" and paste the authentication file inside this folder. You can copy form gitbash also using cat command. vim config (name should be config)

### Kubernetes (K8) Everything here we call resources
- Similar to VPC, we have "Namespace" resource in K8, it is like a project in your kubernetes cluster to provision the resources, it is isolated.
- Every resource is in yaml format with a basic syntax.
- Every resource will be created with apiVersion
- Go through the K8-resources in VS.
- kubectl create -f namespace.yaml ; kubectl get namespaces ; kubectl delete -f namespace.yaml ; kubectl apply -f namespace.yaml
- If you use create onceagain you will get error already exist.
- If you use apply, if not created it will create, if you use again any changes it will update or it will say unchanged.
- Next we have "Pods" is a simple container, it is the smallest deployable unit in kubernetes.
- Difference between Pod & Container ? A Pod can contain multiple containers
- How we created docker container ? docker run -d -p 80:80 -v nginx:/usr/share/nginx/html --name roboshop-nginx nginx (or) using compose right ?
- How to create pod in kubenetes ? We will create a manifest file to create the Pods. Search in kubernetes.io for Pods creation there you can see yaml syntax to create Pods.
- If you dont give namespace, then Pod will be created in default namespace.
- kubectl get pods ---> Will fetch pods from the default namespace, if they are available.
- kubectl get pods -n roboshop ---> Pods will be fetched from the roboshop namespace.
- From the kubernetes will pull the image ? dockerhub
- In Pod (It has IP address) we have multiple containers and also a Network and storage, for example in Pod we have multiple containers and they produce logs everyday. To view that logs easily, we have a logging solution (ELK). For example in a Pod we have 1 container in Pod that is catalogue and catalogue should send the logs to ELK aswel as it should serve the requests also because of this catalogue will not get time to serve request, if it is continously pushing logs to ELK. So we have to create "Sidecar" we keep another container attached to catalogue, so this new container will access to network and storage and it will send logs to ELK.
- We have a proxy also in Pod, like request will come to sidecar first and the request will go to container.
- How to login to any container in kubernetes cluster ? kubectl exec -it <file-name> -c <container-name> --bash
- To get full information of that pod ? kubectl describe pod <pod-name>
- Difference between labels and annotations ? Lables have limitations on length and characters of key-value and used to select other kubernetes resources. Annotations has no limits on length and characters of key-value and used to select external resources to kubernetes like aws load balancers. We can keep heavy information in annotations.
