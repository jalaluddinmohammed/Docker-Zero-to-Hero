# Docker Commands Cheatsheet with Examples

##  docker images

Lists Docker images on the host machine.

docker images

### docker build

Builds image from Dockerfile.

docker build -t my_image:latest .

### docker run

Runs a Docker container. 

There are many arguments which you can pass to this command for example,

`docker run -d` -> Run container in background and print container ID
`docker run -p` -> Port mapping

docker run -d --name my_container -p 8080:80 my_image:latest

use `docker run --help` to look into more arguments.

### docker ps

Lists running containers on the host machine.

### docker stop

Stops running container.

### docker start

Starts a stopped container.

### docker rm

Removes a stopped container.

docker rmi my_image:latest

### docker rmi

Removes an image from the host machine.

docker rmi my_image:latest

### docker pull

Downloads an image from the configured registry.

### docker push

Uploads an image to the configured registry.

### docker exec

Run a command in a running container.

docker exec -it my_container /bin/bash

### docker network

docker network ls

Manage Docker networks such as creating and removing networks, and connecting containers to networks.
