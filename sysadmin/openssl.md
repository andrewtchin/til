# openssl

### Decode x509 cert

```
openssl x509 -in cert.pem -text -noout
```

### Show certificate chain

```
openssl s_client -showcerts -connect <IP>:<port>
```

### Get fingerprint of remote server

```
openssl s_client -connect <IP>:<port> < /dev/null 2>/dev/null | openssl x509 -fingerprint -noout -in /dev/stdin
```

### Get fingerprint of certificate

```
openssl x509 -in server.crt -noout -sha256 -fingerprint
```

### PEM to CRT
```
openssl x509 -outform der -in starkenterprises.io.cert.pem -out starkenterprises.io.crt
```

### PEM to PKCS8
```
openssl pkcs8 -topk8 -inform PEM -outform PEM -nocrypt -in starkenterprises.io.key.pem -out starkenterprises.io.key.pkcs8
```

### Generate private key
```
# (private key is not encrypted - use -aes256 to specify a password)
openssl genrsa -out server.key.pem 4096
chmod 400 private/${SERVER_CERT_CN}.key.pem
```

### Generate server CSR
```
openssl req \
    -new -sha256 \
    -key server.key.pem \
    -out server.csr.pem \
    -subj "/C=US/ST=California/L=Los Angeles/O=Stark Enterprises/OU=Stark Enterprises Web Services/CN=example.com"
```

### Decode CSR
```
openssl req -in server.csr.pem -noout -text
```

### Generate CSR with SAN

```
cat > csr_details.txt <<-EOF
[req]
default_bits = 2048
prompt = no
default_md = sha256
req_extensions = req_ext
distinguished_name = dn

[ dn ]
C=US
ST=New York
L=Rochester
O=End Point
OU=Testing Domain
emailAddress=your-administrative-address@your-awesome-existing-domain.com
CN = www.your-new-domain.com

[ req_ext ]
subjectAltName = @alt_names

[ alt_names ]
DNS.1 = your-new-domain.com
DNS.2 = www.your-new-domain.com
EOF

openssl req -new -sha256 -nodes -out \*.your-new-domain.com.csr -newkey rsa:2048 -keyout \*.your-new-domain.com.key -config <( cat csr_details.txt )
```

### Symmetric Encryption
```
echo "blah" | openssl enc -aes-256-cbc -e -a

openssl aes-256-cbc -e -in data.tar.gz -out data.tar.gz.enc
openssl aes-256-cbc -d -in data.tar.gz.enc -out data.tar.gz
```

### Generate DH param

http://nginx.org/en/docs/http/ngx_http_ssl_module.html#ssl_dhparam

```
openssl dhparam -out dhparam.pem 2048
```

### Show CAs in root store
```
awk -v cmd='openssl x509 -noout -subject' '
    /BEGIN/{close(cmd)};{print | cmd}' < /etc/ssl/certs/ca-certificates.crt
```

Photon
```
awk -v cmd='openssl x509 -noout -subject' '
    /BEGIN/{close(cmd)};{print | cmd}' < /etc/pki/tls/certs/ca-bundle.crt
```
