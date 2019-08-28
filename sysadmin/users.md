# users

### Add user
```
useradd <username>
```

### Add user to group

```
sudo adduser <username> <groupname>
```

### Get group ID from group name
```
getent group <groupname>
```

### Show all groups
```
cut -d: -f1 /etc/group
```

### Show all users
```
cut -d: -f1 /etc/passwd
```

### Show current user's group
```
groups
```

### Show a user's groups
```
groups <username>
```

### Show user info
```
id <username>
```

### Set password for user
```
passwd <username>
```
