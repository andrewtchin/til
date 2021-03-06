# govc

### Get vCenter hostname

```
govc option.ls config.vpxd.hostnameUrl
govc option.ls config.vpxd.instanceName
```

### Dump VM info

```
govc vm.info -json vm_name | jq '.' | cat > outfile
```

### Find VM name by IP

```
govc vm.info -vm.ip <ip_address>
govc vm.info -json -vm.ip <ip_address> | jq -r ".VirtualMachines[].Name"
```

### Shutdown Guest OS

```
govc vm.power -s=true <vm_name>
```

### Get VM Power State

```
govc vm.info -json <vm_name> | jq -r ".VirtualMachines[].Runtime.PowerState"

poweredOn, poweredOff
```

### Delete VM

```
govc vm.destroy <vm_name>
```

### Get VM moid

```
govc vm.info -dump -json vm_name | jq -c '.VirtualMachines[] | .Self.Value'
```

## NTP
```
govc host.date.change -server pool.ntp.org
govc host.service enable ntpd
govc host.service start ntpd
```
