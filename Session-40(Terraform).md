### We have "Behaviours" options in cloud front
- Cloud front is useful to cache only static content
- Dynamic content should not cache.
- When you inspect in network option, then you can see images are loading from different parts
- Those are media and images, these are static
- In behaviours by default, it is sending all path patterns to the origin "web-dev.daws76s.online"
- So we need to create behaviours, if "/media/* (or) "/images/* ---> Then only apply cache policy and get the
  remaining content from the origin (or) Load balancer "web-dev.daws76s.online"
- Depends upon the project, we can create cache policies.
- We have few policies like we can disable the cache policy to the dynamic content and enable to the static
  content.
- We need to disable "caching policy and origin request policy" in default

### We have other option also "Ordered cache behaviour"
Go through the code in VS.

### We also have "Invalidation" options in cloud front
For example if you are going for new deployment, because you changed some content, then you need to remove cache from all the edge locations, so that cloud front will get latest content again and it will cache again new content, for that only we need to create "Invalidations" on whichever path you want. Invalidation will delete this static content which are present in the given paths from all edge locations. If anybody searches then fresh content will be saved in cache. It is better to create Invalidation after every deployment. Using jenkins only we can create Invalidation.

### How the traffic will travel ?
- CDN URL will Hit first ---> https://web-cdn.daws76s.online
- It will check wether we have given any behaviours or not (Nothing but behaviours will be evaluated)
- Then CDN will call catalouge-api, since it is dynamic content, this URL will go "web-alb"
- web-dev.daws76s.online ---> will go to /api/catalogue/catagories
- Then we have listeners and rules in "web-alb"
- Listener is 443 and if we get "web-dev" then the request will go the web component.

### We have two types of services 
- VPC based service, where resources are created inside the VPC (If we apply SG in VPC)
- Non-VPC service, where resources are created outside the VPC (If we dont apply SG in VPC)
- Thats why NO security group will be there for CDN

### How the security groups will work here ?
- NO security group will be there for CDN
- Web-ALB should accept connections from CDN (Internet) on 443
- From Web-ALB to web component
- Web component should accept traffic from port 80 from web-ALB
- From Web-ALB to App-ALB
- App-ALB should accept traffic on port 80 from web and vpn
- App-ALB to catalogue
- Catalogue should accept traffic on port 8080 from App-ALB etc.
- App-ALB to cart
- Cart should accpet traffic on port 8080 from App-ALB etc.
- Here again cart will call catalogue to check the product, cart will not call catalogue directly, cart will
  call App-ALB first, so App-ALB should accept traffic on port 80 from cart, since cart is running on nginx
  and same of the remaining components also.
- Now mondogb should accept traffic on 27017 from catalogue

### How the overall deployement procces will happen ?
For example, if we got a new deployment, say few developers are ready for cart deployment, and few are ready for shipping deployment due to new changes. For example we have vpc, sg, vpn, databases, web-alb, app-alb these are nothing but project infra to create applications, and these are non frequently changing. Project infra should be created by DevOps engineers not developers. Once this whole base is ready, for example take the catalogue, this catalogue is frequently changing and this comes under CICD, what does this mean ? Whenever there is a change in application, CICD should clone, build, scan & create artifact. Generally zip file, store zip files then unit testing ---> This is CI process, then CD process ---> create instance, deploy the latest version, stop the instance, take ami, refresh auto-scaling group. Same for the other components also. This CI and CD process is called "Application infra" which will be changing frequently, Project infra will be changing very rarely. Who will create Application infra ? DevOps or Developers ? Depends on your company but devops should also know this, if we give all the paths or secrets of our whole infra which is in SSM Parameter to the developers, then they will create application infra on top of project infra.

### Shift-left method
Shift-Left in DevOps means performing testing, security, and quality checks in the development cycle itself to catch the issues sooner and we can reduce costs and improve software quality.

### GIT
- Main/master ---> Depicts the code running currently in the production, if there is a change we cannot
  directly change in the prod
- Create a copy of file and do changes, if everything is ok then merge it in main file
- So in git also create another branch from main/master, do the changes here and run the whole process of
  CICD, if everything is good then merge into master and deploy into production.
- We can add branch protection rule in the github account. Keep "pull" request and any other requirement you
  have, we call it has branching policies.

### Points to remember
- Cloud front is useful to cache static content, generally not for dynamic content. Like images from our
  roboshop project.
- We can disable the cache policy in the default also, so that it will fetech from the origins everytime,
  enable only if you need this.
- We are using cloud-front for our front end website, where the images and static content will cached from the
  cloud-front and remaining content we are getting from the load balancer
- Invalidation is nothing but whenever we go for the new deployment, we delete the old cache content from all
  over the edge locations and again cloud-front will get dynamically and save it.
- We are using Shift-left strategy in our pipeline. You must say this in interview.
