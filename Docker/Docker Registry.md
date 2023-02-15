## Hosting a Local Registry

Ad-hoc command:
```shell
# Start
docker run -d -p 5000:5000 --restart=always --name registry -v /path/data:/var/lib/registry registry:2

# Stop
docker container stop registry

# Remove
docker container rm -v registry
```

Compose Example:
```yaml
registry:
  restart: always
  image: registry:2
  ports:
    - 5000:5000
  volumes:
    - /path/data:/var/lib/registry
```
`docker-compose up -d`

### Encryption

#### Using Unencrypted repositories
Instructions above are for unencrypted HTTP repos.
To use this with docker clients you need to set the following in `daemon.json`:
```json
{ 
  // NOTE: outermost curly braces are part of file already if it exists.
  "insecure-registries" : ["myregistrydomain.com:5000"]
}
```

#### Self-Signed Certificate
Generate a self-signed certificate

**Linux**
Copy `domain.crt` to `/etc/docker/certs.d/myregistry.domain.com:5000/ca.crt` on docker host. No need to restart

**Windows**
Right click `domain.crt` in explorer and choose "Install Certificate".
Store in the local machine, and select the "Trusted Root Certificate Authorities" store.
Restart Docker.

**Docker Desktop**
Mac: [Frequently asked questions for Mac | Docker Documentation](https://docs.docker.com/desktop/faqs/macfaqs/#add-custom-ca-certificates-server-side)
Windows: [Frequently asked questions for Windows | Docker Documentation](https://docs.docker.com/desktop/faqs/windowsfaqs/#how-do-i-add-custom-ca-certificates)

**Additional Troubleshooting**
See [Test an insecure registry | Docker Documentation](https://docs.docker.com/registry/insecure/)

#### CA-Signed Certificate
Instructions at [Deploy a registry server | Docker Documentation](https://docs.docker.com/registry/deploying/)

## Managing Images

Tag and push image to repository
```shell
docker tag ubuntu:16.04 regserver:5000/my-ubuntu
docker push regserver:5000/my-ubuntu
```

Remove image locally to save space
```shell
docker image remove ubuntu:16.04
docker image remove localhost:5000/my-ubuntu
```

Pull the image from the repository
```shell
docker pull regserver:5000/my-ubuntu
```


----
# Sources
[Deploy a registry server | Docker Documentation](https://docs.docker.com/registry/deploying/)
[Test an insecure registry | Docker Documentation](https://docs.docker.com/registry/insecure/)

# Further Reading
[Deploy a registry server | Docker Documentation](https://docs.docker.com/registry/deploying/)
- Authentication
- More on certificates and encryption
- Air-gapped Registries
