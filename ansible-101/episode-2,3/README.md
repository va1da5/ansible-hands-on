# Episodes 2 and 3

## Notes

**Ad-hoc tasks and Inventory**

```bash
# get started
cd ansible-101/web-app
vagrant up

ansible multi -i inventory -a "hostname"
# is same as 
ansible multi -i inventory -m command -a "hostname"
# "command" module gets run by default when module is not specified

# Useful commands for monitoring
ansible multi -i inventory -a "free -h"
# df -h - ensure there is local storage available
# date - ensure all servers has the same time

# Returns JSON object with detailed information about a server.
# Could be useful when building multi-step playbook and some
# information might be used from the output of this module.
ansible -i inventory db -m setup

# install chrony
ansible -i inventory multi --become -m yum -a "name=chrony state=present"

# enable chronyd service
ansible -i inventory multi --become -m service -a "name=chronyd state=started enabled=yes"

# Ansible module docs from CLI
ansible-doc "service"

# Limit command execution for a particular node in a group
ansible app -i inventory -a "free -h" --limit "192.168.49.101"
# Wild card works too
ansible app -i inventory -a "free -h" --limit "*.101"


# Ansible command module does not support pipes
# shell module needs to be used for such case
# best practice is not to use shell module, unless absolutely necessary
ansible -i inventory multi -b -m shell -a "tail /var/log/messages | grep python"
```

---

**Introduction to Playbooks**

```bash
ansible-playbook -i inventory playbook.yml

# limit scope to a single host
ansible-playbook -i inventory --limit=192.168.49.101 playbook.yml
```
