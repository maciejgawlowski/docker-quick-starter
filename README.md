# Docker quick installation instructions

### Docker installation
```
yum remove docker docker-common docker-selinux docker-engine
yum install -y yum-utils device-mapper-persistent-data lvm2
yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
yum install docker-ce docker-ce-cli containerd.io
```

### Docker daemon configuration

Create file `/etc/docker/daemon.json`:
```
{
    "data-root": "/home/docker-data", //store Docker data (volumes, images etc.) in specified path
    "storage-driver": "overlay", //storage driver configuration for Docker data
    "insecure-registries" : ["my.private.registry.com:5000"], //private Docker images repository url
    "log-driver": "json-file", 
    "log-opts": {"max-size": "10m", "max-file": "3"} //truncate Docker logs to 10mb and max 3 files
}
```

### Add Docker to autostart
```
systemctl enable docker
```

### Verify Docker
```
systemctl start docker
docker ps
reboot
docker ps
```

### Docker-compose installation
```
yum install epel-release
yum install -y python-pip python-devel gcc
pip install --upgrade pip
yum upgrade python*
pip install docker-compose
```

### Verify Docker-compose 
```
docker-compose --version
```

### CTOP installation (Container monitoring tool)
```
sudo wget https://github.com/bcicen/ctop/releases/download/v0.7.1/ctop-0.7.1-linux-amd64 -O /usr/local/bin/ctop
sudo chmod +x /usr/local/bin/ctop
```

### Verify CTOP
```
ctop
```
