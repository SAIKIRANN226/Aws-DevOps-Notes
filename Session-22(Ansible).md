### To run the file (or) script in the background
We have a special file in Linux called a "Black Hole" located at /dev/null. Any data written to it is immediately discarded (vanishes). The usage is "saikiran.txt & >> /dev/null" Here & → runs in background, >> /dev/null → discards output. "nohup ansible-playbook -i inventory.ini -e ansible_user=centos -e ansible_password=DevOps321 mongodb.yaml & >> /dev/null" ---> Output will be in nohup.out, it will not come in the terminal. If small instance (or) 1 instance, you can run the script in background, we can't run every script in the background, because memory consumption will be high, so better to run only few scripts in the background if you want.

### Ansible roles
It's a dry principle, dont repeat yourself. It is similar to the functions in shellscript to avoid the repetition of the code. It is a proper directory structure to keep our configuration and we can share this with other users also. Refer "Roboshop-ansible-roles" in VS. Command to run playbook for ansible role is "ansible-playbook -i inventory.ini -e ansible_user=centos -e ansible_password=DevOps321 -e component=mongodb main.yaml"

- We know playbook contains multiple plays and multiple tasks (or) modules, we have written multiple tasks
  while configuring the roboshop project right ? apart from the tasks, we have other things also like handlers,
  templates, vars, files, defaults etc. These are called roles to maintain a proper directory structure.
- Common is also a role, where you can keep common things like creation of apps, users etc. will be there
  right in every module ? so we keep them in common roles between all the roles and call it whenever required.
  You can give any name like "app-setup" name for app creation etc.
- So How to call a role in another role ? We have "ansible.builtin.import_role"
- What are files in ansible roles ? These are nothing but supporting files like we have catalogue.service,
  roboshop.conf, mongodb.repo etc. Without these files we cannot complete our configuration.
- Next we have "vars" in ansible roles ? We have come across variable preferences in ansible variables right ?
  So here vars comes last (or) least in preference.
- We have meta in ansible roles ? Meta information like who wrote the script, when it was updated etc.
- We library in ansible roles ? Like if no module is found in ansible website, you can develop your custom
  modules using pythong script.
- We also have lookup_plugins in ansible roles ? to connect to external systems like aws, azure etc.
- So directory structure should be like Roles/mongodb/tasks/main.yaml
- In every directory main.yaml should be there, ofcourse we have one main.yaml in Roles directory that is is
  to call component thats it.

### How to debug, if you are facing any error
"ansible-playbook -vvv -i inventory.ini -e ansible_user=centos -e ansible_password=DevOps321 -e component=mongodb main.yaml" we will get the full information in the terminal, which is happening in the background, so that we can see where is the error.

### Points to remember
- To see the running logs in the background use "tail -f nohup.out"
- To set the indentation in VS use "shift+tab and tab"
- mongodb.repo, catalogue.service, user.service etc. These files are called supporting files, this we can keep
  in the files roles.
- Creating every role is not mandatory, we can create only what we required.
- If you want to call a common role in any roles like catalogue,mongodb etc. Use "ansible.builtin.import_role"
- We can use "ignore_errors: true" in ansible also.
