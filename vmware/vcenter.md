# vCenter

### Adding Trusted Root CA

Show available cert stores

```
/usr/lib/vmware-vmafd/bin/vecs-cli store list
```

Show trusted roots

```
/usr/lib/vmware-vmafd/bin/vecs-cli entry list --store TRUSTED_ROOTS
```

Add cert

```
/usr/lib/vmware-vmafd/bin/dir-cli trustedcert publish --chain --cert ca.pem
```

### Support Bundle
```
ssh root@<vcsa_ip>
shell
vc-support -l
```

### NTP
```
ntp.test --server pool.ntp.org
ntp.set --servers pool.ntp.org
ntp.get
timesync.set --mode NTP
timesyc.get
```

### Status
```
service-control --list
service-control --status
```
