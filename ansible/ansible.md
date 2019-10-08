# ansible

### Syntax check

```
ansible-playbook playbook.yml  --syntax-check
```

### Ad hoc commands

```
ansible servers -m shell --user ubuntu -a "docker volume prune -f" -i ansible_hosts
```
