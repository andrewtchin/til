# gpg

### Symmetric encryption
```
gpg --output encrypted.data --symmetric --cipher-algo AES256 un_encrypted.data

gpg \
--symmetric \
--cipher-algo aes256 \
--digest-algo sha256 \
--cert-digest-algo sha256 \
--compress-algo none -z 0 \
--s2k-mode 3 \
--s2k-digest-algo sha256 \
--s2k-count 65011712 \
--force-mdc \
--quiet --no-greeting \
<input_file>

gpg --output un_encrypted.data --decrypt encrypted.data
```

### Asymmetric encryption
```
echo "blah" | gpg --encrypt --armor --recipient "test@example.com" --no-version
gpg --output data.tar.gz.gpg --encrypt --armor --recipient "test@example.com" data.tar.gz
gpg --output file --decrypt data.tar.gz.gpg
```
