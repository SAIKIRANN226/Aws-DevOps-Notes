### Roboshop-Infra-Dev (CICD for Project Infra)
In previous sessions, like i said we can also write Jenkinsfile for project infra also right ? and also we wrote Jenkinsfile for VPC. Now create the whole project infra using same method instead of doing manual process like using terraform commands init, plan and apply. So create by writing 1 Jenkinsfile to all the project infra. If there is NO dependency from one folder to another folder like 04-databases and 05-app-alb. For that we have "Parallel stages" in Jenkins pipeline (We need to use keyword called parallel) so because of this parallel, both resources will create at a time to save the time. Other folders like VPC, SG, VPN have dependencies (Like it is following sequential process). We can also add plan command (or) 07-acm code also.

### Roboshop-Infra-Dev (CICD for Catalogue)
Now go for catalogue application, already created in the previous session from "Shared library" using multi branch pipeline, go through the previous session.

### Project management (Ticketing tool)
We have JIRA (or) ServiveNow. Here we raise CR by keeping the project code, application code, approvals, 
date and time, version, deployment process, revert back process, post deployment testing and attaching test results, attach scanning results, we mention Dev, Sit, Uat status, Jenkins build URLs etc. We need to mention the screenshots of results etc. So we mention maximum all possible details in CR. After rasing this we will get ticket id for JIRA, this JIRA id should mention int he below Change management process and also we mention CR number also after rasing CR request below. All these process will raise by either DevOps team or L2 team.

### Change management process (CR)
When we are going for production we have Change management process. We will raise CR (change request) every organization have their own tool to manage CRs. DevOps team will raise CR, in this CR ticket we have project code, application code, approvals, date and time, version, deployment process, revert back process, post deployment testing, JIRA id. Then this ticket will rise (or) it will go as NEW status. First this new status will go to the team lead and he will check the JIRA ticket id and information init thoroughly, he will write some comments and approve. Next this CR will go to the delivery manager, he also writes some comments and approve, then finally it will go to the Client. Finally we get CR id, and this CR id should mention in the JIRA tool (or) ServiceNow tool. Then we have Jira to Jenkins Integration

### Jira to Jenkins Integration
JIRA team will do this, in JIRA we have a button "Trigger prod" this button will trigger based on the time and date we have provided in the CR. Then JIRA will check CR is approved or not ? If prod trigger time is same as in CR. Then it will trigger Jenkins pipeline.

### Points to remember
- Interview question ? Explain the CICD architecture in your project ?
- Go through the CICD in concepts folder https://github.com/daws-76s/concepts/blob/master/CICD.MD
- nodejsVM.groovy is a Dev pipeline using shift left method.
- Multi branch pipeline is only for CI not for CD
- We write separate pipeline for PROD, here we will hardcode the values, not by sending from the CI
