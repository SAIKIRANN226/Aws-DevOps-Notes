### Work flow in the company
- Client ---> Business analyst (Web_ALB) from client side ---> Team manager (App_ALB) ---> Team leads --->
  Team members in the project.
- Team manager ---> Only listen to Business analyst.
- Team manager will redirect work to the respective team leads.
  1. UI Team lead ==> If UI work, he will redirect to UI team lead.
  2. Backend Team lead ==> If backend work, he will redirect to backend team lead.
### UI Team (or) Backend Team is a groups
In this groups, we have 1 Team lead, HR, Jr.engineer, Sr.engineer etc. For example HR responsibility is to check if the resources are overloaded then HR should take other resources to distribute the work, or if the resources have less work, he have to terminate them. If they resign he have to replace.
- In overall architecture who is the Team manager ? "Application_LB(App_ALB)
- Team manager listens to ---> Business analyst only
- Here Web_ALB and App_ALB are our persons only, so communication between them is internal only on port 80
  no encryption required here.
- Rules ---> If UI, redirect to UI team. If Backend, redirect to Backend team.
- Who is HR in this ? "Auto-scaling"
- Teams (or) groups are called Target groups.
- Employees are nothing but instances.
- Hiring template is nothing but if a person resigns or overloaded, HR should hire new employees, similarly in
  this architecture, hiring template is "Launch template"
So first create "Application Load balancer" is a latest generation works on TCP layer7, we can redirect to different project using one single "App_ALB" Go through the code of 05-app-alb in VS.
- Context_path
  1. daws76s.online/roboshop ---> Will go to roboshop project
  2. daws76s.online/amazon ---> Will go to amazon project
- Host_path
  1. roboshop.daws76s.online ---> Will go to roboshop project
  2. amazon.daws76s.online ---> Will go to amazon project

### Create catalogue Target group
Go through the code of 06-catalogue, because according to the architecture, we now need to create catalogue (nothing but team)

### Points to remember
- We have given time stamp, just to know at what time the resource is created or destroyed.
- We put "depends_on" syntax  because without completing the above command, it should not be executed.
- Create different buckets for every folder.
