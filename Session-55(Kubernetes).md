### Resources in Pod 
We have more containers in VM and if any of the container got traffic increased and that container uses more and more resource from VM, and blocking VM because of this other containers cannot use resource, So for that we need to write a resources: block to allocate to container to restrict the resources consumed by containers. This is useful in scaling the containers. We can allocate or restrict when containers starts. We use soft limit and hard limit for autoscaling.

              apiVersion: v1
              kind: Pod
              metadata:
                name: hello-pod
              spec:
                containers:
                - name: hello-pod
                  image: nginx
                  ports:
                  - containerPort: 80
                  resources:
                    requests:
                      cpu: "100m"
                      memory: "68Mi"
                    limits:
                      cpu: "200m"
                      memory: "128Mi"

### What are Services in kubernetes ?
- If you want to expose Pods to other application or outside world, we use services and also for Load balancing and service mesh.
- 3 types of services ClusterIP (Purely internal to kubernetes) NordPort (You can expose to outside world) Load balancers (You can expose to outside world) Services are like route53 records.
- If you want to connect to Pod, first request should go to service then to Pod. That means if you want to communicate with Pod to Pod communication you must use service. Because Pod is very dynamic, they may be running or terminated we dont know.
