# systemd

### List all failed units 

```
systemctl list-units --state=failed
```

### List units in progress

```
systemctl list-jobs
```

### List enabled units

```
systemctl list-unit-files --state=enabled
```

### List dependencies

Show dependencies (units required or wanted) to start the named unit. 

```
systemctl list-dependencies sshd.service
```
### Verify/lint unit

```
systemd-analyze verify my.service
```

### Debug

Set `/etc/systemd/system/systemd-networkd.service.d/10-debug.conf`

```
[Service]
Environment=SYSTEMD_LOG_LEVEL=debug
```
### Analyze

```
systemd-analyze
systemd-analyze critical-chain
systemd-analyze blame
```

### Generate systemd graph
```
# generate graph with dot (sudo apt install -y graphviz):
systemd-analyze dot > myfile
cat myfile | dot -Tsvg > system.svg

# graph one service
systemd-analyze dot admiral_startup.service
```


### Show hostname info
```
hostnamectl
```
