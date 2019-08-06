# SSH

### Generate key

```
ssh-keygen -t rsa -b 4096 -o -a 256 -f key.pem -C Comment
```

### Generate host key

```
ssh-keygen -f /etc/ssh/ssh_host_rsa_key -N '' -t rsa
```

### Generate public key from private key

```
ssh-keygen -y -f key.pem > key.pub
```

### ssh-agent

```
eval `ssh-agent`
```
