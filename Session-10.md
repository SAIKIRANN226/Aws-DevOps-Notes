### Configuring all components in this session at a time
- Create instances
- Create records and update Private IPaddress of the created instances in hosted zones along with 
  sub domain name and ttl 1
- Dont forget to update in roboshop config_file (Reverse proxy configuration)

### What is deployment wether it is manual or automation
1. Developer will update the code in git and he will push as zip file
2. Download the code
3. Stop the server
4. Remove old code or backup old code
5. Unzip new code
6. Restart the server
7. Testing

### Synchronous vs Asynchronous
http and https websites are ---> synchronous communication server should be always up and running, where the sender waits for the receiver to respond before continuing. It is blocking – the connection is held open until the response comes. If servers not running. We get error code like 400/500. that is called synchronous

### Asynchronous
Servers should 100% up and always running. Communication where the sender does not wait for an immediate response. So they use Messaging broker between client and servers.
Between, Client ---> Messaging broker (Messaging queue) ---> Servers
Example:- Whatsapp messaging when other person is offline

### Points to remember
- T3.medium for mongodb,shipping,mysql. Remaining all t2.small(free tier)
- Rabitmq is for payment it is used for messaging queue database
- Always update records, because when you create new instances it will change the IPaddress
