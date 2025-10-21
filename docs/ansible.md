# Ansible

## Basic actions

Install collections from galaxy:

```bash
ansible-galaxy install -r requirements.yml
```

Run a playbook:

```bash
ansible-playbook -i inventory/ playbook.yml
```

Shutdown all servers in an inventory:

```bash
ansible all -i inventory/ -m shell -a "shutdown -h now" --become
```
