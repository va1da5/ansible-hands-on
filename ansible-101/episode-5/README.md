# Episode 5

**Playbook handlers, environment variables, and variables**

## Notes

```bash

# magic variables, such as ansible_os_family could
# be found using the setup module
ansible -i inventory centos -m setup | grep ansible_os_family -A2 -B2

```
