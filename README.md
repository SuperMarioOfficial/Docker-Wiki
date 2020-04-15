# Docker tutorials

## Deploying Your First Docker Container
- search for an image ``` docker search <name>```
- run the image ```docker run <options> <image-name>```
  - flag for detached ```-d```  
  - map ports ```-p <host-port>:<container-port> ```
  - attach persistent drive ``` -v <host-dir>:<container-dir>```
- check if container is running ``` docker ps```
- check the logs ```docker logs```
-
