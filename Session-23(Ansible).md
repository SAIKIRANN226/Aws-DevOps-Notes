### Ansible.cfg
- It is ansible main configuration file, we can control options from here, if we enter "ansible --version" in
  the server terminal, we can see from where the configuration file is loading.
- Generally config_file will be in the default location ---> "/etc/ansible/ansible.cfg"
- For example create a folder "mkdir test" in CD location.
- Then cd test/ and "cp /etc/ansible/ansible.cfg .", then pwd will be "/home/centos/test"
- Then "export ANSIBLE_CONFIG=/home/centos/test/ansible.cfg" nothing but i have given first preference.
- When you do "ansible --version" in any location, then you can see ansible_config file is loading from the
  "/home/centos/test/ansible.cfg" location. Only if you set environment variable for "ANSIBLE_CONFIG" and
  incase if you "UNSET" this environment variable, using "unset ANSIBLE_CONFIG", now it will be loading from
  the default location that is "/etc/ansible/ansible.cfg"
- We have many options in "ansible configuration settings" file nothing but "ansible.cfg". We may not use all
  the options, we only use what we required like inventory_path, ask_vault, timeout, user_name, passwords etc.
  
So changes can be made and used in a configuration file which will be searched for in the following order
- ANSIBLE_CONFIG (environment variable if set)
- ansible.cfg (in the current directory)
- ~/.ansible.cfg (in the home directory)
- /etc/ansible/ansible.cfg

So instead of giving -i inventory -e user_name -e password to the command, we can put this is in ansible.cfg and command usage is "ansible-playbook -e component=mongodb main.yaml"

### Templates in roles
Templates is nothing but a place holders, where we will submit our required values at the run time and it is a Jinja2 format and extension is .j2, go through the code in VS. Like we have used for catalogue.service files.

### Handlers in roles
Sometimes you want a task to run only when a change is made on machine. For example you may want to restart a service if a task updates the configuration of that service, but not if the configuration is unchanged. So Ansible uses Handlers to address this usecase, for this we use "notify", why we use this handlers because some servers will take 2-3 mins of time and other servers like nginx it will not take more time to restart, it will take few seconds thats it.

### Usage of Tags in ansible
Tags.yaml is to run a particular tag ---> ansible-playbook -t devops 16.tags.yaml ---> did not given hosts because it will test in the local host, if you dint mention the tags in the command it will run all tasks, so where this tags are useful ? for example a new version is going to release for a catalogue, so for that we need to deploy a new version, that means we need to Stop the service/Remove old code/Download latest code/ and then restart, here do we no need to run all the catalogue script ? No, we just create a deployment.yaml file in common folder inside the tasks folder. Usage: "ansible-playbook -e component=catalogue -t deployment main.yaml"

### Points to remember
- To check logs "sudo less /var/log/messages"
- "cat /etc/systemd/system/catalogue.service"
- To create a full config_file "ansible-config init --disabled > ansible.cfg"
- We should not restart the service unnecessarily in production env, only do when it is required.
- If you want to run a particular task, then we use Tags.
