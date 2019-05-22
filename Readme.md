# This file is for basic docker commands 


## Basic docker commands:

`docker container ls `  To list running containers only.


`docker container ls -a` To list runnning + stopped containers. 


`docker run ubuntu`  docker run command is used to start a container.


`docker run -it ubuntu`  -it is to login inside a container 

as soon as you `exit` the container which you started using `-it` it will terminate the container


`docker run nginx` 

`docker run -d nginx`  `-d` is used to run the container in background ... 


` docker exec -it  9a64d5d63bdc /bin/bash` 


How to stop a running container:

`docker container stop <container_id>`

You can always restart a stopped container by using `docker start <container_Id>` command. 
 
How to kill a running container 

`docker kill <container_id>`

You can always restart a stopped container by using `docker start <container_Id>` command. 



How to remove a stopped container:

`docker rm <container_id>`

How to remove a running container :

`docker rm -f <container_id>`

You cannot remove a running container. Stop the container before attempting removal or force remove


### Volumes

docker run -it -v /home/ubuntu/demo:/root  ubuntu

content inside "demo" will be available inside "root"


### How to push images to hub.docker.com

![image](https://user-images.githubusercontent.com/31384241/58144246-4572b100-7c6b-11e9-93a8-8e3f459caf63.png)
