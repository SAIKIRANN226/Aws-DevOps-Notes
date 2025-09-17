### Continuation of configuring roboshop using kubernetes
- How to select your namespace in server and then create ? kubens <namespace>
- kubectl get svc ---> You will get classic LB.

### Stateful and Stateless ?
- Entire software technology 'Storage' is the base.
- Mysql, mongodb etc. are Stateful applications.
- Catalogue, cart, shipping, web etc. are Stateless applications.

### Storage (or) Kubernetes volumes
<img width="543" height="538" alt="Screenshot 2025-09-16 150609" src="https://github.com/user-attachments/assets/0d693011-3743-4f0f-b68f-90055132d257" />

- We have two Internal volumes 'emptyDir' and 'hostpath' these will store data in worker nodes (Ephemeral volumes like temporary)  
- We have two External volumes 'Static provisioning' and 'Dynamic provisioning' (Persistent volumes like permanent)
- What does emptyDir do ? Is used to mount the volume to the sidecar and also main container using emptyDir, then sidecar get access to storage. In sidecar we have a 'filebeat' a public image from elastic search, so we keep filebear as a sidecar. Sidecar is nothing but 'filebeat' then this filebeat will ship logs, so there is some configuration for filebeat that is Input & Output. Input is what logs to access. Output is where to store that logs. We should inform this to filebeat. You can take filebeat from the internet. For example set up for nginx, like search in google 'filebeat to ship nginx logs in kubernetes'
- Hostpath ---> We need to ship all the worker node logs to external system, not only we need to ship pod logs, we also need to ship underline OS logs also that is nothing but worker node logs. We have 'DeamonSet' it will make sure a Pod runs in each and every Node. Fluentd will be deployed as deamonset that can access underlying hostpath logs /var/log directory and send them to elk.

### What does 'emptyDir' do in kubernetes ?
 We know in a Pod we have main Pod and sidecar. Pod feature is store the multiple containers inside the Pod and share the common Network & Storage. Here containers or Pods are continously store the logs in commong network and storage space (This also temporary), If Pod is terminated or crashed, then how the developers will the logs, he can see the logs only a few lines, what if he wants to see full logs ? Do we have logs available in kubernets ? may be a few lines not entire logs of a Pod. So thats why we have 'Elastic search' is a external volume. We shift this logs to Elastic search, who will shift this logs ? main pod or sidecar ? so side will access to storage and network and continuosly ship logs to elastic search. So to do that side should have access to the storage and network right ? For that we use 'Sidecar' so we mount the volume to sidecar and main container using 'emptyDir' then side car get access to storage. Here inplace of sidecar we have 'filebeat' it is a public image form elastic search. We keep filebeat as a sidecar to the main container. Now filebeat will get access to storage and network space and ship logs to elastic search. SO there will be some configuration to this filebeat like Input and Output. Input is nothing what logs should i access, output is where should i store that logs ? we need to inform this to filebeat. You can take filebeat from the internet but you need to give the input and output configuration to that filebeat. Here siva is taking example of 'filebeat to ship nginx logs in kubernetes'. If the Pod deleted then our applications are also deleted. we dont find any logs, that means till the pods are available, we need logs, for that only we use 'emptyDir'

 ### What does 'hostpath' do in kubernetes ?
 Not only Pod logs, we also need worker node logs (EC2 logs) or underlying logs, we also need to ship these logs also. We need to ship all worker nodes logs /var/log directory to external systems. So we have something called 'DeamonSet' it make sure a Pod runs in each and every node. We have 'fluentd' will be deployed as daemonset that can access underlying host logs and send them to ELK. For example we have Pod and this Pod should access host path say /var/log, bydefault hostpath is very dangerous, we can restrict to only a particular path. we give only readonly, if we give write access pod can do anything.



