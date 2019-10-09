# ansible

### Syntax check

```
ansible-playbook playbook.yml  --syntax-check
```

### Ad hoc commands

```
ansible gitlab-runners -m shell --user ubuntu -a 'docker rm $(docker ps -aq)' -i ansible_hosts
ansible gitlab-runners -m shell --user ubuntu -a 'docker rmi $(docker images -aq)' -i ansible_hosts
ansible gitlab-runners -m shell --user ubuntu -a 'docker volume prune -f' -i ansible_hosts
```
