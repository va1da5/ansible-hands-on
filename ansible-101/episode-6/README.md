# Episode 6

**Ansible Vault and Roles**

## Notes

```bash
# encrypts variables
ansible-vault encrypt vars/api_key.yml

# asks decryption password before running playbook
ansible-playbook vault.yml --ask-vault-pass

# use file to decrypt vault
ansible-playbook vault.yml --vault-password-file=~/.ansible/api-key-pass.txt

ansible-vault decrypt vars/api_key.yml

# Allow editing the values while encrypted
ansible-vault edit vars/api_key.yml
```

**Ansible Roles**

```bash
# Creates a boilerplate for Ansible role
ansible-galaxy role init nodejs


```

## References

- [Github: Ansible Role: Filebeat for ELK Stack](https://github.com/geerlingguy/ansible-role-filebeat)
