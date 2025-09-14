### Configuring roboshop project
1. Web/frontend tier        ---->  Stateless(If crashes, we can recover)
2. App/Api/backend tier     ---->  Stateless(If crashes, we can recover)
3. DB tier                  ---->  Statefull(If crashes, tough to recover)
Web and API will only work when DB is in existence, So that CRUD over DB will happen

### "CRUD" over Database (Example when you create a new user in facebook)
1. Create a user if iam new to FB
2. Read user if i login 
3. Update user if i update anything in the FB
4. Delete user if i delete anything in the FB

Nginx (80) is used as "reverse proxy" in this project, we have RHEL=Fedora=centos=awslinux all are same flavoured but in this project siva has created his own AMI based on "centos8" browse more AMI's in 
Nvirgnia ----> search "devops-practice" ---> community AMI's ---> select "Centos-8-DevOps-Practice" this 
is not key based because we cannot create keys for every servers it is very tough so we are using username 
and password authentication. Username is = centos; Password is = DevOps321

- Create a security group, allow all traffic and 0.0.0.0/0 just for practice only
- Create a web instance with devops-practice with no keypair to start configuring roboshop project
- Now create putty session ---> give session name ---> connection data ---> username = centos
  appearence ---> change the font to 14 and save the session ---> click on centos, but here you have 
  already created saikiran session so click on saikiran and load and then paste the IPaddress above
  and then click on open
- Open super putty and connect to the web instance with PublicIP
- Now open documentation and follow the steps of web server configuration
- Superputty we can create multiple tabs and we can also rename the instance
- We are using nginx (80) as webserver it is http server, make sure nginx should take http not https
  where you are testing the URL of nginx server, other webservers may use https like facebook.com or 
  google.com and many others also but nginx also supports to https but mostly used as http server only.
- yum, dnf ---> Used to install packages but dnf is preffered in manual configuration because dnf
  consume very less memory
- In the server where does the nginx configuration is saved ? "cd /etc/nginx/" vim nginx.conf
- Where does the default content will be saved in the nginx server ? "cd usr/share/nginx/html/" in 
  this folder we have index.html file, Here we need to delete this default content and we can keep
  our own content which must be in html format you can search in google.

### Forward proxy
Forward proxy is servers are not aware of clients behind VPN, like anonymous access to hide our identity,
forward proxies cant understand real clients. Security ---> Companies can impose restrictions not to use particular sites and to monitor internet behaviour. Here clients (we) are aware of proxy, servers are not aware (Example:- Commonly used vpn's by the people)

### Reverse proxy
Clients (We) are not aware of server side (Example:- nginx ---> Loadbalancer) for example when we login
to facebook.com we are not aware that from where the information is comming from, because facebook will
not give access to their DB or API to know, So in protect their applications they use reverse proxy
to secure their code, similarly in roboshop project also nginx is used as reverse proxy.

### Famous HTTP status codes
- 100 To 199 ---> Informational responses
- 200 To 299 ---> Success 
- 300 To 399 ---> Redirect 
- 400 To 499 ---> Client (We) side errors (Purely client side error) like if we dont give proper input.
- 500 To 599 ---> Server side errors (Purely project side error) 

### Roboshop configuration
Better to follow below sequences (or) you can follow according to the document
1. Mongodb ---> t3.small
2. Catalogue ---> t2.micro
3. Redis ---> t2.micro 
4. User ---> t2.micro
5. Cart ---> t2.micro
6. Web ---> t2.micro
7. Mysql ---> t3.small
8. Shipping ---> t3.small
9. RabbitMq ---> t2.micro
10. Payment ---> t2.micro
11. Dispatch ---> t2.micro

### Caching
Watch from (50:01) just to understand what is cache?

### Points to remember
- Whenever you update the configuration you must restart the nginx
- How to check the running logs ? "tail -f /var/log/messages"
- Where is the reverse proxy configuration ? "vim /etc/nginx/default.d/roboshop.conf"
- Whenever you do any changes makesure "systemctl restart nginx"
- 127.0.0.1 this IP belongs to localhost nothing but mongodb server this will come while configuring
  the mongodb
- How to find a particular folder or something ---> find . -name "*nginx*" Here . is current folder searching
  with particular name called nginx
- To check all logs "less -f /var/log/messages"
- A web server is software and hardware that uses HTTP and other protocols to respond to client requests made
  over the World Wide Web, displaying website content like text, images, and applications.
