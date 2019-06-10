# SSH

### Generate key

```
ssh-keygen -t rsa -b 4096 -o -a 256 -f my.key -C Comment
```

### Generate host key

```
ssh-keygen -f /etc/ssh/ssh_host_rsa_key -N '' -t rsa
```
