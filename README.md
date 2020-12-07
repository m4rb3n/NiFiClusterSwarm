# Apache Nifi Cluster in Docker Swarm

## Installing Docker (As root)
### RPM
* Enable docker repository
```bash
dnf config-manager --add-repo=https://download.docker.com/linux/centos/docker-ce.repo
```

* Install the lastest compatible version not limiting to the best option because of centos latest version compatibility issues
```bash
dnf install docker-ce --nobest -y
``` 

* Start and enable docker
```bash
systemctl start docker
systemctl enable docker
```

### Debian
TODO

## Cluster Setup
[INSTALLATION.md](install.md)
