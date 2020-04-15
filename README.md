# Docker tutorials

## Deploying Your First Docker Container
- search for an image ``` docker search <name>```
- show images ```docker images```
- run the image ```docker run <options> <image-name>```
  - flag for detached ```-d```  
  - map ports ```-p <host-port>:<container-port> ```
  - attach persistent drive ``` -v <host-dir>:<container-dir>```
- check if container is running ``` docker ps```
- check the logs ```docker logs```
- login into the image bash ```docker run -it <image> bash```

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

## How to redirect/map Docker cotainer to a specific port on the host? 
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


