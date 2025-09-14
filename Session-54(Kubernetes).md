### Concept of EKS Kubernetes cluster (Elastic Kubernetes Service)
<img width="1007" height="569" alt="Screenshot 2025-09-14 184431" src="https://github.com/user-attachments/assets/d56dd9b5-c203-46fe-9638-1c2f34ea77c0" />
- Go through the code of "K8-Kubernetes-Cluster" in VS. In this we are creating workstation first. We are creating kubernetes cluster using Eksctl is one way.
- How to create cluster ? eksctl create cluster --config-file=name.yaml
- Here ekscluster is creating workstation (Dockerhost) we need to give access to aws console, so use "aws configure"
- Ekssctl cluster will take time like 20min, till then we are learning minikube other features.

### Spot instances
- We create on demand instances
- AWS giving offers on instances, from their spare capacity but they can be interrupted and terminated by AWS with a two-minute warning. These type of instances are ideal for dev environment not for prod.
