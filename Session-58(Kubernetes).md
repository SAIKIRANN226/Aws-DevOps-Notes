### External volumes
- Static provisioning ---> 2 types of volumes EBS (Elastic block store) like Hard disk, EFS (Elastic file system) like NFS type.
- In Static provisioning, first we will create storage, either by storage admin or k8 admin. Next make this volume available to k8 cluster. And also install drivers
- A proper roles should be attached to ec2 instance to access EBS.

### Kubernetes volume object/resources
- We have resources like namespace, pods, secrets, configmap etc. Similarly we also have resources in Kubernetes volumes those are persistent volume it represent the external storage like EBS.
- We also have persistent volume claim that means Pods should request volume through pvc.
- Pods should connect to PVC, PVC connect to persistent volume.
