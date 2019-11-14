# vim general

### Wrap text for whole file

```
:set textwidth=80
gg
gqG
```
### Remove trailing whitespace

```
:%s/\s\+$//e
```

### Set file format

```
:set ff=unix
```

### Replace ^M

```
:%s/\r//g
```

### Replace literal \n with actual newline

```
:%s/\\n/\r/g
```

### Expand tabs and retab
```
:set et|retab
```

### Delete every other line
```
:g/^/+d
```
