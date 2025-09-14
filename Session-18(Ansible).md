### Disadvantages in Shellscript
- We have hundreds of linux distributions like debian, centos, ubuntu, rhel etc.
- Shellscript will not work for all linux distributions even though 99% commands may be same.
- You need to write separate scripts for separate distributions.
- Scalability issues, shellscript cannot configure more number of servers incase of big billion days.
- Error handling, to handle errors we need to write functions, validations explicitly.
- Readability issues, shellscript syntax is not easy to understand for everyone without learning linux.
- Shell will only work for linux, not for external systems like aws,azure etc.
- We need to work manually on external systems by using their particular modules, commands, syntax.
- Shellscript will not manage sensitive information like passwords, keys etc.
- Ansible is rich in modules to interact with almost all popular platforms.
- Ansible playbooks are easy to understand through YAML format.

### Advantages of Ansible over Shellscript
- Ansible is an open-source automation tool.
- Configuration management tool.
- Application deployment.
- Cloud Provisioning and Orchestration (But not recommended).
- It can also connect to external systems like aws, azure, gcp, gitlab etc to create instances. But it is
  not recommended, ansible is only intended for configuration management & application deployment.

### What is configuration management ?
For example if you buy a new laptop, you need to install softwares and setup like username and passwords then connect to wifi etc. This is nothing but configuring your new laptop what you required. So similarly in linux also, before deploying application, we need to make the server ready. For example below.
- Installing Packages.
- Installing Programming languages.
- Installing Build tools.
- Installing Application Runtime.
- Creation of Users, Folders, etc.
- Setting Permissions.
- Creation of Systemctl services.
- As a DevOps engineer we need to do this effectively (Basically CRUD over the server)
- Creation of configuration --> Should be fast and accurate.
- Read the configuration --> It is easy to read the configuration of server through ansible playbooks.
- Update the configuration --> Any changes in configuration should be rolled out asap.
- Delete the configuration --> Delete the configuration if not required.

### Application Deployment basic steps
- Stop the server.
- Remove old code (or) Backup old code.
- Download the new code.
- Restart the server.

### Ansible has Idempotence Behaviour
If you run program multiple times, that can create samething multiple times, where as in ansible, if the user does not exist then it will create, if exist it will ignore, that means even if you run the program infinite times also, it will not create any damage. Providing same results irrespective of the number of executions is called idempotence.

### Just create 2 servers in aws Server & Node
Now take the NodeIP and go to the Server instance "sshpass -p DevOps321 ssh centos@nodeIP", so now you are logged in to node from the server instance successfully, you can do anything here (or) exit from the node server then "sshpass -p DevOps321 ssh centos@nodeIP -C "echo hello > /tmp/hello.txt" here no need to login into the node to create file in node server from the server. You can also install packages, for example take any github repository like installing MySQL file, copy the URL from the URL tab then enter the following command "sshpass -p DevOps321 ssh centos@nodeIP -C "curl <paste_the_URL> | sudo bash" Note that curl appears to point to the webpage of a GitHub repository rather than a raw script file. To fix this, you should use the raw URL for the script file on GitHub. You can get the raw link by clicking the "Raw" button when viewing the file on GitHub or you can test any of your session by taking raw URL and apply the command, all the content of the session will appear in the terminal.

### Overview of the above
- sshpass -p DevOps321 ssh centos@NodeIP
- sshpass -p DevOps321 ssh centos@NodeIP -C "echo hi saikiran > /tmp/sai.txt"
- sshpass -p DevOps321 ssh centos@NodeIP -C "curl <paste_the_RAW_URL> | sudo bash"

### PUSH Architecture (Ansible is a PUSH)
Configuration server (or) Ansible-server (or) Main server (or) Controller machine is agentless. It can connect to any number of remote servers. Main configuration server pushes the configuration to the nodes without logging into the nodes in the background itself and ofcourse it is using SSH connection in the background, we only just make sure wether the connection is established successfully between nodes and ansible server. Here the Node-1, Node-2, Node-3 etc. are nothing but Remote servers.

### PULL Architecture (Chef is a PULL)
How do we configure pull based in chef ? we will configure agents in the nodes to check periodically say for every 1 hour (or) it will check 24*7 that means bandwidth will be wasted, resource consumption like CPU, Memory etc. will be high and also there is one advantage in pull based architecture in some scenarios, this point shiva will discuss in the later sessions.

### Installing Ansible and connecting to Node 
- sudo yum install ansible -y, where ever the ansible is installed, we call it has a ansible server.
- To connect to node from the ansible server "ansible -i nodeIP, all -e ansible_user=centos -e
  ansible_password=DevOps321 -m ping". Here "i" is inventory, we can give multiple servers, so as of now we
  have given "all". It is just checking wether the connection is established between ansible and node,
  ansible is sending "ping" and node is sending back "pong" that means connection is success.
- Best example for Pull vs Push is a courier from Delhi to Hyd.

### Example of installing nginx in Node from Ansible
- ansible -i nodeIP, all -e ansible_user=centos -e ansible_password=DevOps321 --become -m yum -a "name=nginx
  state=present". Here (present = install ; --become = root user ; m = module ; a = arguments).
- To start the server = ansible -i nodeIP, all -e ansible_user=centos -e ansible_password=DevOps321 --become
  -m service -a "name=nginx state=started/stopped/restarted"

### Shellscript (vs) Ansible
- In linux everything we call as ---> Commands
- In ansible everything we call as ---> Modules
- Here we run one by one commands to install whatever, so instead we put these commands all together in one
  file and run the script, similarly ansible have modules (commands) to put together and run as a playbook
  and the syntax for the playbook is in YAML format, yet another markup language, example banking withdrawal
  form nothing but a predefined format.

### DTO (Data Transfer Object)
Transferring data from one system to another. Some of the markup languages are XML,HTML,JSON,YAML etc. Example if you give your Facebook credentials in your laptop browser then how the credentials is transferred to the Facebook ? Through XML format (Extensive markup language) is the most used, and popular markup language is html (Hyper text markup language), JSON (Java script object notation) and YAML also.

### Markup languages
Refer this in your VS (Concepts), just to know how the markup languages look like no need to practice this.
But practice yaml in this concepts. Indentation is mandatory in this languages.
- person.xml
- person.json
- person.yaml
Note:- Inventory is a list of hosts that ansible server will connect to the different components, do this in the server after going to the ansible location.
- ansible -i inventory web --list-hosts
- ansible -i inventory cart --list-hosts
- ansible -i inventory ungrouped --list-hosts
- ansible -i inventory all --list-hosts

### 01-playbook.yaml
- Open the server ---> Git clone ---> CD ansible then enter the below command.
- ansible-playbook -i inventory.ini -e ansible_user=centos -e ansible_password=DevOps321 <file_name>

### 02-nginx.yaml
- Open the server ---> Git clone ---> CD ansible then enter the below command
- ansible-playbook -i inventory.ini -e ansible_user=centos -e ansible_password=DevOps321 <file_name>

### Points to remember
- https://github.com/daws-76s/concepts/blob/master/ansible.MD ---> Paste this URL in chrome you will be
  redirected to the page of content to know how ansible works.
- If you stuck anywhere in the gitbash and unable to enter any command then use "ctrl+C"
- sudo yum install ansible -y, this will make server as Ansible server.
- To run a playbook ---> ansible-playbook -i inventory.ini -e ansible_user=centos -e
  ansible_password=DevOps321 <file_name>
