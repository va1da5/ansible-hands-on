# Hands-on Ansible

The repository contains notes and playbooks after going over various Ansible tutorials and hands-on practice exercises.


## Ansible 101

### Getting Started

```
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt

cd ansible-101

vagrant up
```

### Notes

```bash
# Ad hoc commands using Ansible

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
```


## References

- [Ansible Documentation](https://docs.ansible.com/)
- [Ansible Configuration Settings (ansible.cfg)](https://docs.ansible.com/ansible/latest/reference_appendices/config.html)
- [Youtube: Ansible 101 by Jeff Geerling](https://www.youtube.com/playlist?list=PL2_OBreMn7FqZkvMYt6ATmgC0KAGGJNAN)
- [geerlingguy Vagrant Boxes](https://app.vagrantup.com/geerlingguy)
