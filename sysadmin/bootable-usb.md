# Bootable USB

## From macOS

```
diskutil list
diskutil unmountDisk /dev/disk2
sudo dd if=~/Downloads/isos/ubuntu-18.04-desktop-amd64.iso of=/dev/disk2 bs=1m
diskutil eject /dev/disk2
```
