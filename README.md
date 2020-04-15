# Docker tutorials

## Deploying Your First Docker Container
- search for an image ``` docker search <name>```
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
FROM nginx:alpine
COPY . /usr/share/nginx/html
```
- Build image from docker file ```docker build -t <build-directory>.```
  - The ```-t``` parameter allows you to specify a friendly name for the image and a tag
