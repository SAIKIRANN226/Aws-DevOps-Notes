### DNS (Domain name system)
For example when you hit "joindevops.online" where will first request will go ?
Browser ---> cache ---> OS ---> cache ---> ISP ---> cache ---> Root servers ---> TLD ---> NS ---> A record

### Domain registars
We can also buy domain in aws also but it is very costly, so we are buying in hostinger, next
register your hostinger domain in aws by going to Route53/Dashboard/Hosted zone/Created hosted zone
and enter you created hostinger domain name here/After created this hosted zone will give us 4 
name servers, update these 4 nameservers in hostinger website by click change name servers, Now
hostinger responsibility is to update Name servers with TLD what ever you have given in the domain
like .online or .in or .com etc. these we call as TLD(Top Level Domain), Next create a record in aws
give your public IPaddress in record, keep TTL has "1" it is like cache, To check whether the record is created or not "nslookup mongodb.joindevops.online" check this in server

### Redis component
It is a cache. It helps speed up data retrieval processes by storing frequently accessed data in memory, rather than having to repeatedly fetch it from slower, persistent storage like a database

### Points to remember
- shift+g = go down
- gg = go up
- q = quit
- Hostinger login with mothukurusaikiran4@gmail.com and domain is "megacitysai.fun"
