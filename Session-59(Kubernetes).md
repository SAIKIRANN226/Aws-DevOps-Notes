### Purpose of Helm charts in kubernetes
- Templatise the kubernetes manifest files.
- Package manager for kubernetes.

### Templatising the kubernetes manifest files
- Install Helm in server using commands from helm website.
- Chart.yaml file and templates folder are mandatory to templatise the manifest files.
- Understand the helm commands. 'helm install nginx .' helm list,
- Here heml will hit kubectl command in the background itself.
- You can keep the values in values.yaml file.
- How to mention this values ? {{ .Values.saideployment.replicas}}
- In values.yam file, keep deployment: replicas: 3
- The use of helmcharts is when you are going for the new deployment, we can change the values in templates folder without touching manifest files. Using this command 'helm upgrade nginx .'
- Helm is used to parameterise the kubernetes manifest files is one of the use.
- Next is Package manager ? 
- In VM, we used yum install nginx -y , here yum is getting the package from the internet and install in VM right ? Then what about kubernetes ? Real advantage of helm is Image is already in public (So no need to build the image) and Helm have some public repos to configure the image through manifest files.
- In static provisioning we have EBS drivers right ? We installed these drivers from the internet using yaml files right ? But here we use helm using below steps.
- So first add helm repo in server, in this we have kubernetes resource files.
- Next 'helm repo update' similar to yum update
- Next install aws-ebs-csi drivers.
- Next helm install nginx.
