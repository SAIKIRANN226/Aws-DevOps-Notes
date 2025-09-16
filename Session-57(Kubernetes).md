### Continuation of configuring roboshop using kubernetes
- How to select your namespace in server and then create ? kubens <namespace>
- kubectl get svc ---> You will get classic LB.

### Stateful and Stateless ?
- Entire software technology 'Storage' is the base
- Mysql, mongodb etc. are Stateful applications.
- Catalogue, cart, shipping, web etc. are Stateless applications.

### Storage (or) Kubernetes volumes
<img width="543" height="538" alt="Screenshot 2025-09-16 150609" src="https://github.com/user-attachments/assets/0d693011-3743-4f0f-b68f-90055132d257" />

- We have two Internal volumes 'emptyDir' and 'hostpath' these will store data in worker nodes (Ephemeral volumes like temporary)
- We have two External volumes 'Static provisioning' and 'Dynamic provisioning' (Persistent volumes like permanent)
- What does emptyDir do ? Is used to mount the volume to the sidecar and also main container using emptyDir, then sidecar get access to storage. In sidecar we have a 'filebeat' a public image from elastic search, so we keep filebear as a sidecar. Sidecar is nothing but 'filebeat' then this filebeat will ship logs, so there is some configuration for filebeat that is Input & Output. Input is what logs to access. Output is where to store that logs. We should inform this to filebeat. You can take filebeat from the internet. For example set up for nginx, like search in google 'filebeat to ship nginx logs in kubernetes'
- Hostpath ---> We need to ship all the worker node logs to external system, not only we need to ship pod logs, we also need to ship underline OS logs also that is nothing but worker node logs. We have 'DeamonSet' it will make sure a Pod runs in each and every Node. Fluentd will be deployed as deamonset that can access underlying hostpath logs /var/log directory and send them to elk.




