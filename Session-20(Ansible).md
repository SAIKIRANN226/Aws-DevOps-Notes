### In this session we are configuring roboshop project with ansible
Create a server and install ansible in it by "sudo yum install ansible -y", from ansible we connect to the nodes and here siva is creating the instances and also records using already created shellscript (roboshop.sh) as creating through ansible is somewhat difficult he will show in the upcoming sessions. So just copy the https URL from the github of roboshop.sh and clone in the ansible server and go to the roboshop location and run this command "sh roboshop.sh" before this you need to give role to the ansible server to create the instances ---> Actions/Security/Modify_IAM/Select your role which you have already created or create a new one and then run the roboshop.sh script "sh roboshop.sh" to create instances, before this delete the old records. If exists ---> Hosted zones --> Except NS and SOA.

### Points to remember
- In ansible i have used file module, dnf module, user module, get url modules etc.
- How to connect to mongodb from catalouge ? "mongo --host mongodb.daws76s.online" and use "exit"
- To check wether the data is there or not in catalogue ? 
   "mongo --host mongodb.daws76s.online --quiet --eval 'db = db.getSiblingDB'("catalogue");
   db.products.count()'
- Should check the above command in /app/schema folder.
- To check wether the catalogue is connected to mongodb or not ? is the below command.
- sudo su - and then "tail -f /var/log/messages"
