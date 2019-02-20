# ovf

### Get OVF environment

```
vmtoolsd --cmd "info-get guestinfo.ovfenv"

ovfenv dump
```

### Deploy OVA

```
ovftool --acceptAllEulas --name=new-vm --datastore=datastore1  /path/to/the.ova 'vi://administrator@vsphere.local:password@vcenter.example.com/ha-datacenter/host/cluster1'
```
