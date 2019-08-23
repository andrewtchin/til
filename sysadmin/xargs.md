# xargs

### Find files and untar them

```
find . -name "*.tar.gz" | xargs -I {} tar xvf {}
```
