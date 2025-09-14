### Continuation of the previous session
In last session we completed till "Launch-template" now it is the continuation from "Auto-scaling" We have created auto-scaling for catalogue in this session, so same can be done on other components also, before creating those components siva creating for web component, and for remaining components, siva developed customised modules especially for roboshop project to create auto-scaling for remaining components.

### Rolling update
- For example we have 4 instances rightnow
- And 4 new instances should be created and replace with the old instances.
- How the strategy will be followed here ?
- 1 new instance will create, once it is up, then 1 old instance will be deleted (no down time here)
- Similarly like for 2nd, 3rd and 4th instances also.
- We have many strategies, but rolling update is the famous.

### Target deregistration
If 1 instance is handling some requests, and later got terminated due to traffic decrease, then deregistration process will start, for example in a company if a employee got terminated, they cannot relieve him on the spot, they need to complete few formalities like did he completed his pending work or not ? did we settled him or not ? did he served notice period or not ? etc. Same for the instances also.

### Web component
- First create security group and then "Web_ALB" here listener is 443 (give access from internet) and rule
  should be if anybody enter "web-dev.daws76s.online" our website should open. Before creating listener, you
  need to create certificate that is HTTS, there should be a domain for certificate, so create domain on
  "*.daws76s.online" and attach this certificate to listener. Go through 07-acm in VS. If you are mentioning
  listener 443 then you should attach the certificate.
- You need to validate the domain, so aws will give you "CNAME name & CNAME value" using this you need to
  create a record in whichever domain you are using like we are using "hostinger" or in "aws" or some other,
  you can only create records if you have those particular domains login credentials only.
- Give access from internet, since it is 443. Go through 07-acm in VS.

### Points to remember
- In launch-template we have versions, if we want to release a new version of the catalogue, then new version
  of launch template should also be released, we should not delete the Launch-template and create again.
- After updating new version of launch template, we immediately refresh the "Auto-scaling" so we put this
  "update_default_version" = true in code.
- Auto-scaling will not just create instances, it will directly place in the target group and attach the
  instances with the Load balancer.
- If you are not aware of what options to give in the code, just try to create a sample resource in the aws
  console, and see what options are required, and same options put in the code by taking from the google, do
  for every resource if you are not aware of.
- Few applications are in cloud VM based, and few applications are in containers.
- Everytime you do "terraform apply" that means everytime you are releasing a new update, it is no problem if
  you are in Dev environment.
- Whatever we created for this catalogue, same approach for user,cart,shipping and payment also.
