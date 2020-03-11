# awk

### Replace literal \n with newline

```
awk '{gsub(/\\n/,RS)}1' file.txt
```
