### Ansible-Vault
Till now we have given Passwords and Usernames in the terminal (or) in the command line (or) in the ansible.cfg file right ? but it is not secure, so we now use ansible-vault, nothing but storage of secrets like keys, passwords etc. 
- Encoding ---> A proper pattern to encode the text, in this format everybody can guess the secret.
- Encryption ---> Generating a random text using mathematic algorithm (AES256) tough to guess.
- So we encrypt ansible-vault, those who know the password, they can only decrypt the code.
1. asaiaavaa ----> sai (Encoding)
2. hsdh234sk456jdksd ----> sai (Encryption)

### How to create ansible vault in ansible-server ?
- Practice folder (Your working directory)
- vault folder (Create inside the Practice folder), if we create vault folder in VS (Windows), it will not
  reflect in the server, so you need to create using linux server only, same for the group_vars folder.
- group_vars folder (Create inside the vault folder) then
- Create vault-file inside the group_vars folder using below command.
- "ansible-vault create Practice/vault/group_vars/some_name.yaml" and also
- Create ansible.cfg, inventory.ini and your playbook files (Inside the Practice folder not in vault or
  group_vars folders)
- Put "ask_vault_pass=True" in ansible.cfg (or) "ansible-playbook 01-playbook.yaml --ask-vault-pass"
- How to connect to the instance ? "ansible-playbook 01-playbook.yaml" since we have inventory in
  separate file and Username/Passwords are kept in vault.
- Since our whole infra is in SSM Parameter in AWS systems manager, this is also a vault from AWS, but we
  integrate ansible-vault with the SSM Parameter and we fetch the values from AWS instead of depending on
  ansible-vault and ansible-vault commands.

### Dynamic Inventory
- Till now we dint used aws cloud services completely, its like a on-premise for us, like we have only servers
  and domains thats it.
- For example our situation is like we had on-premise servers and applications are deployed manually and
  lateron we used shellscript to configure the project and because of ansible advantages we used ansible to
  configure the project, but when this ansible is useful ? If we have more servers to configure then we can
  use ansible, if you have less servers we can configure the project using shellscript only.
- After digital revolution from 2016, "Auto-scaling of servers is highly required" If traffic increases,
  servers should automatically create, if traffic decreases then servers should automatically delete.
- For example we have 10 servers now because of traffic and i need to run (or) manage these servers using
  ansible-playbook. Tillnow we targeted single server only using ansible, but we never targeted multiple
  servers at a time.
- When auto-scaling is created, ansible will connect to AWS to fetch the IP_addresses of the newly created
  servers (using auto-scaling). How ansible will fetch IP_addresses dynamically ? 
- If you want to run update to the all the web instances then "ansible-instance" should connect to AWS and
  fetch instances with name "web" which are present in us-east-1 region. We use "aws ec2 inventory" This is a
  plugin, Go through the "web.aws_ec2.yaml" file in the VS. Paste the content of "web.aws_ec2.yaml" in the
  server in CD location using "vim web.aws_ec2.yaml"
- Make sure to install "botocore and boto3" then only plugins will work.
- To install botocore and boto3 using python, we use "pip"
- First know which version of python is using in ansible ? "ansible --version" pip should also be the same
  version of python.
- So "sudo yum list | grep pip"
- "sudo yum install python3.11-pip.noarch -y" (select from the above list)
- Now install "pip3.11 install boto3 botocore"
- "ansible-inventory -i web.aws_ec2.yaml --list" now it will fetch the instances with name of "web"
- Ansible fetched the web-instance right ? now if you want to connect to this web instance use this command
  "ansible aws_ec2 -i web.aws_ec2.yaml -e ansible_user=centos -e ansible_password=DevOps321 -m ping" then web
  instance will give us replay "pong"

### What is Plug and Play
- If your ansible-server wants to connect to the external systems like aws,azure,gcp or alibaba etc. Then we
  need to add some plug (of aws,azure,gcp or alibaba), thats what we call plug, similarly if ansible have
  aws plugin to connect aws ec2, then we can fetch IP_addresses. That is nothing but "AWS Dynamic inventory
  plugin"

### Points to remember
- We use ansible.cfg to minimize the commands (or) arguments to the script in server.
- If esc button is not working while saving the file you can use "ctrl+c"
- Use "ansible-vault encrypt group_vars/<some_name>.yaml" if already has existing vault.
- If you want to edit the existing vault ---> "ansible-vault edit web.yaml"
- If you want to know wether it is encrypted or not ? then "cat group_vars/<some_name>.yaml"
- If you want to see then "ansible-vault view group_vars/<some_name>.yaml"
- You can use ansible-vault anywhere in the roboshop project for any components you want.
- Earlier we used Ansible-vault and recently we migrated to AWS SSM Parameter store, since our entire infra is
  in AWS. We integrated ansible-vault with SSM Parameter to fetch the values from the AWS. Which is a seamless
  integration instead of using ansible-vault and ansible-vault commands.
