### Overview of the Previous Session
- Created VPC.
- Created Internet gateway and attached to the VPC.
- Created Public, Private & Database subnets in atleast 2-AZ for High Availability.
- Created Route tables (Public, Private & Database) and associated it with their respective subnets in two 
  regions 1a and 1b.
- Added Internet Gateway route in the Public Route table, because internet should be enabled in Public not
  in Private, that is the difference between Public & Private subnets.
- Enabled auto-asign Public IPv4 address only to the Public subnet not to the Private subnet.
- Note that when you create a VPC, aws will automatically create a default route table (10.0.0.0/16) this
  route table is used for communication between the subnets.

### High Availability on Public subnets
- az-1 = one Public_subnet     = 10.0.1.0/24 ---> us-east-1a
- az-2 = another Public_subnet = 10.0.2.0/24 ---> us-east-1b

### High Availability on Private subnets
- az-1 = one Private_subnet     = 10.0.11.0/24 ---> us-east-1a
- az-2 = another Private_subnet = 10.0.12.0/24 ---> us-east-1b

### High Availability on Database subnets
- az-1 = one Database_subnet     = 10.0.21.0/24 ---> us-east-1a
- az-2 = another Database_subnet = 10.0.22.0/24 ---> us-east-1b

### NAT Gateway is used to enable outgoing internet in Private subnets
- If we need to update any package or download something in the private subnets, for this we need to connect
  to internet. But what traffic is this ? is it OUTGOING ? or INCOMING ?
- If server wants to download something then it is OUTGOING traffic, INCOMING traffic is already disabled
  in private subnets. So if we want to go outside and download safely we have "NAT Gateway"
- This NAT Gateway should be created in the public subnet (1a or 1b) because we have given internet access
  to the public subnets.
- Creating NAT Gateway is not enough, we need to add routes between private subnets & to the Internet gateway
  (NAT) which is in public subnet. Then only private subnets can access internet and download anything. Like
  for example if only one of the private subnets wants to connect to internet then that private subnet should
  have a road (Route) to Internet Gateway (NAT) which is in public subnet. So like that which ever private
  subnets like data base subnet or any other private subnets wants to connect to internet, they should add
  route to the NAT gateway which is in public subnet.
- So you need to add in the route tables (Private and Database) then only you will get access to the Internet.
  Select any of the private subnet/routes/edit routes/add route (Destination= 0.0.0.0/0, Target= NAT gateway,
  select default one in dropdown under Target section only).
- When you create NAT gateway, aws will create instance in the background (We dont have access to that)
  that means NAT and ElasticIP is chargeable. Before creating NAT gateway we have one rule because created
  instance in the background has IPaddress which is dynamic whenever you off and on, it will change the
  IPaddress, for that we need to create ElasticIP.
- So create ElasticIP first --> Then create NAT Gateway.
- Note that if you want static IP, we need to pay money, like for example even your home PublicIP is dynamic
  it is changing everytime, so if you want static home Public IPaddress you need to pay to the ISP provider
  in your area.

### VPC peering in aws cloud
Example of the two villages, for every village we have pincode, so similarly in the VPC what is pincode ? 
That is CIDR. Bydefault we cannot connect two VPCs, it is possible through VPC peering, only when both 
VPC's should have different CIDR. Then only VPC peering is possible. Below is the example we created.
Requestor VPC = I want to connect with you please accept my request.
Acceptor VPC  = Ok i will accept your request.

### Below is the example of VPC peering
- So let us take "Requestor VPC = Roboshop VPC ; Acceptor VPC = Default VPC"
- Now try to create VPC peering connection, after creating in the same account you need to accept request in
  the "Actions" option. Take example of villages now you have created a main road (Peering Connection)
  between two villages, but if you want streets (Every subnets or only which ever subnet you want) to connect
  to main road, so connect all street roads to the VPC peering main road, nothing but routes right ?
- So try to add routes in the main route table, go to the VPC main route table there edit routes in
  destination give the other VPC_CIDR to connect and target should be peering connection and under the
  peering connection select the dropdown option and save it.
- If it is not reflecting then you need to add routes in all route tables explicitly.
- If you want only one or two private subnets wants to connect to the vpc peering main road then you can add
  in those two route tables only. You need to add from the other side also not just one side. This is nothing
  but routes in VPC.

### Terraform-aws-vpc Module development in VS
- Terraform-aws-vpc-module ---> Is a module we are developing.
- Testing code is in created "Example" folder in "Terraform-aws-vpc-module"

### Now create below all these using terraform code
- Create VPC
- Create Internet gateway and attach
- Create all subnets
- Create route tables
- Create routes
- Associate with subnets
- Create elasticIP
- Create NAT
- Add NAT gateway route in public and database subnets
- Peering connection
- Routes

### "Common tags" this is a map type
We have tagging strategy, like we have more resources in roboshop project like vpc subnet, route tables, NAT gateway and many more. So for all these resources we also have common tags to use like below. Common tags are applicable to all resources. We can overwrite this common tags any time.

     Project = "Roboshop"
     Terraform = "true"
     Environment = "dev" 
     Name = "Saikiran"

### "Resource tags" this is also a map type
Resource tags are specific tags. We have different tags like vpc tags, subnet tags, nat tags etc. But we want both tags, for example we have Name = "Mothkur" in resource tags compared to Name = "Saikiran" in common tags, what will happen if we merge common tags and resource tags ? Then resource tags only applicable, that means Name = "Mothkur" in resource tags will be considered. So for this we have function in terraform that is "terraform merge" and "tags = merge(var.common_tags, var.vpc_tags)" we can merge as many maps we want. So now we are developing VPC module thats why we use vpc_tags in code.

### Points to remember
- To go directly in to your working folder in gitbash "cd /d/repos/Practice"
- When you create a NAT Gateway an instance will be created automatically in the background, we cannot access
  this instance, this instance IP address will be changing dynamically whenever you off and on, so we need to
  create ElasticIP first and then create NAT gateway.
- Tagging strategy is important in terraform.
- You can also create s3 bucket for vpc_module.
