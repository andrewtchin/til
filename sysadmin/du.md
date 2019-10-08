# du

### Size of directory

```
du -hs dir
```

Options:
* h - human readable
* s - Display an entry for each specified file.  (Equivalent to -d 0)

### Find biggest directories

```
du -a /home | sort -n -r | head -n 5
or
du -a / | sort -n -r | head -n 5
or
du -Sh / | sort -rh | head -50
```
