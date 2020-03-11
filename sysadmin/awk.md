# awk

### Replace literal \n with newline (update in place)

```
awk -i inplace '{gsub(/\\n/,RS)}1' file.txt
```

### Print column

```
awk '{print $1}'
```
