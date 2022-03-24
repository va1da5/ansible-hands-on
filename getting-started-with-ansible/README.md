# Getting Started With Ansible


Ansible Control Host - a machine where Ansible resides and performs automation tasks against the rest of servers.

```bash
ansible all -i inventory -m ping

ansible all -m gather_facts --limit 192.168.56.101

ansible all -m dnf  -a update_cache=true --become

ansible-playbook install_webserver.yaml

ansible all -m gather_facts --limit 192.168.56.101 | grep ansible_distribution
        "ansible_distribution": "CentOS",
        "ansible_distribution_file_parsed": true,
        "ansible_distribution_file_path": "/etc/redhat-release",
        "ansible_distribution_file_variety": "RedHat",
        "ansible_distribution_major_version": "8",
        "ansible_distribution_release": "NA",
        "ansible_distribution_version": "8.5",

# list available tags
ansible-playbook --list-tags install_webserver.yaml

playbook: install_web_server.yaml

  play #1 (all): all    TAGS: []
      TASK TAGS: [host-update]

  play #2 (servers): servers    TAGS: []
      TASK TAGS: []

# scope execution to tags
ansible-playbook --tags host-update install_webserver.yaml


```



## References

- [Tutorial Playlist](https://www.youtube.com/watch?v=3RiVKs8GHYQ&list=PLT98CRl2KxKEUHie1m24-wkyHpEsa4Y70&ab_channel=LearnLinuxTV)
