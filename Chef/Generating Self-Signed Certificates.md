## Self-Signed Certificate

```shell
openssl req -newkey rsa:4096 -nodes -sha256 -keyout domain.key \
  -addext "subjectAltName = DNS:myhost.domain.com" \
  -x509 -days 365 -out domain.crt
```
Use `myhost.domain.com` as a CN
The `domain.crt` file is the public version of the cert, and `domain.key` is the private key.




----
# Sources
[Test an insecure registry | Docker Documentation](https://docs.docker.com/registry/insecure/)