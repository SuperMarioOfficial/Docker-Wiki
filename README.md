# Docker

- [Wiki/documentation](https://github.com/SuperMarioOfficial/Docker_tutorials/wiki/Documentation)


**Run container from docker repositories**
1. `docker pull <username>/<container-name>`
2. `docker run -d --name <friendly-name> -p <host-port>:<container-port> <name>:<version>` 

**Run container from Dockerfile**
1. `touch Dockerfile`
2. `docker build -t <name><version> .`
3. `docker run -d --name <friendly-name> -p <host-port>:<container-port> <name>:<version>` 

**List all containers**
1.  `docker images`

**Run commands inside the container by name**
1. `docker container ls -a`
2. `docker exec -it <friendly-name> <bash command>`

**Stop a running container by id**
1. `docker ps -a`
2. `docker stop <id>`

**Remove image by id**
1. `docker images`
2. ` docker rm <id>`

**Remove all unused containers (Warning: it keeps only the active ones)**
1. `docker system prune -a`


## convert a container in an image
1. `docker commit <id container> < name>`

## inspect the json of the container
1. `docker inspect <id>`

## tag image
1. `docker tag <container name>:<tag name> <container name>:<new tag name>`

## bind docker container port to any available port on the host in detach mode**
1. `docker run -d -P <tag>`

## bind docker container port to a specific port on the host in detach mode**
1. `docker run -d -p <host port>:<container port> <tag>`

## check networks
1. `docker network ls`

## search for an image by topic
1. `docker search "Microsoft .NET Core"`

## This command to attach local standard input, output, and error streams to a running container.
1. `docker attach container_id/container_name`

## This command allows us to exec another process in a running container.
1. `docker exec option container_id/container_name`

## Deploying Your First Docker Container
1. search for an image ``` docker search <name>```
2. show images ```docker images```
3. run the image ```docker run <options> <image-name>```
    - flag for detached ```-d```  
    - map ports ```-p <host-port>:<container-port> ```
    - attach persistent drive ``` -v <host-dir>:<container-dir>```
5. check if container is running ``` docker ps```
6. check the logs ```docker logs```
7. login into the image bash ```docker run -it <image> bash```

## Deploy Static HTML Website as Container
- Dockerfile for ***Nginx*** (pronounced "engine-x") is an open source reverse proxy server for HTTP, HTTPS, SMTP, POP3, and IMAP protocols, as well as a load balancer, HTTP cache, and a web server
```
<h1>Hello, from the other side</h1>
```
```
FROM nginx:alpine
COPY . /usr/share/nginx/html
```
- Build image from docker file ```docker build -t webserver-image:v1 .```
  - The ```-t``` parameter allows you to specify a friendly name for the image and a tag
- Run the server ```docker run -d -p 80:80 webserver-image:v1```

## How to redirect/map Docker container to a specific port on the host? 
```
FROM scratch
COPY webapp /
EXPOSE 8080
CMD ["/webapp"]
```

## Building single C executable with scratch 
```c
#include <stdio.h>
void main(){
printf("Hello world\n");
}
```
```
FROM scratch   #an explicitly empty image, especially for building images "FROM scratch". It contains only a single binary.
COPY hello /   #copy hello bynary in the root directory in the docker container
CMD ["/hello"] #execute the bynary 
```
- Then, ```docker container runv --rm -v ${PWD}:/src -w /src gcc:7.2 gcc -static -o hello hello.c```


