# Self Signed Certificate Using OpenSSL

This doc contains instructions to set up TLS locally with OpenSSL.

### Step 1: Generate RootCA

```
openssl genrsa -out rootCA.key 4096
```
Generate the root RSA private key

```
openssl req -x509 -new -nodes -key rootCA.key -sha256 -days 1024 -out rootCA.crt
```
Generate the root certificate with root private key

### Step 2: Create Certificate

```
openssl genrsa -out mydomain.com.key 2048
```
Generate the server RSA private key

```
openssl req -new -key mydomain.com.key -out mydomain.com.csr
```
Generate the certificate signing request

```
openssl x509 -req -in mydomain.com.csr -CA rootCA.crt -CAkey rootCA.key -CAcreateserial -out mydomain.com.crt -days 36500 -sha256
```
Sign with RootCA certificate and private key and generate the server .crt

### Step 3:

Move root certificate to Keychain Access

### Miscellaneous

##### Convert .key to .pem
```
openssl rsa -in mydomain.com.key -text > key.pem
```

##### Convert a DER file (.crt .cer .der) to PEM
```
openssl x509 -inform der -in mydomain.com.crt -out cert.pem
```

##### Convert a PEM file to DER
```
openssl x509 -outform der -in cert.pem -out certificate.der
```

##### Generate a new private key and Certificate Signing Request
```
openssl req -out CSR.csr -new -newkey rsa:2048 -nodes -keyout privateKey.key
```

##### Generate self signed pem
```
openssl req -newkey rsa:2048 -new -nodes -x509 -days 3650 -keyout key.pem -out cert.pem
```

##### Check a certificate
```
openssl x509 -in certificate.crt -text
```

##### Check a certificate signing request
```
openssl req -verify -in CSR.csr -text
```