# xargs

### Find files and untar them

```
find . -name "*.tar.gz" | xargs -I {} tar xvf {}
```

### File names with spaces

```
find . -name "*.tar.gz" | xargs -d '\n' -I {} rm -f {}
```
