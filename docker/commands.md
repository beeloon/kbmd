# Docker basics

### Check Docker version
```bash
docker --version
```

### Docker startup (fedora)
```bash
sudo systemctl start docker 
```

### Build new docker image
```bash
# Build new test image with docker file 
# that located in . directory
docker build -t test .
```

### Docker images
```bash
# show all images
docker images

# Run hello_world image
docker run hello_world

# Run hello_world image in background and made 
# ports on which it listens are made available.
docker run -dP hello_world

# delete image by id
docker rmi <image_id>
```

### Docker containers
```bash
# show running containers 
docker ps

# show all available containers
docker ps -a

# stop container by container_name
docker stop <container_name>

# remove container from container list
docker rm <container_name>
```

### Manage Docker as a non-root user (without sudo)
```bash
# 1. Create the docker group.
sudo groupadd docker

# 2. Add your user to the docker group.
sudo usermod -aG docker $USER

# 3. Restart system (or Log out and Log back)
```

### DOCKERFILE