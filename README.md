# Docker

# list of Docker Commands

 * Check all docker containers
   docker ps -a

 * Check all started docker containers
   docker ps

 * Start a stopped container
   docker start <container-name>

 * Stop a container
   docker stop <container-name>

 * Remove all containers
   docker stop $(docker ps -a -q)
   docker rm $(docker ps -a -q) 

 * Attach to a container
   docker start <container-name>
   docker attach <container-name>

 * Run bash shell in container
   docker container exec -it <container-name> bash
 
 * Delete container forcefully
   docker container rm -f <container-name>

 * Download a new docker image
   docker pull <image-name:version>

 * Docker Stats
   docker stats

 * See all Docker images
   docker images

 * Delete an Image
   docker rmi <image-name>
  
 * Remove all images
   docker image prune -a

 * Remove unused images
   docker image prune

 * Check all the networks created by docker
   docker network ls
 
 * Create Image from base container
   docker commit {base image} {new image name}



 * Launch container from an image
   docker run -itd --name <container-name>  <image-name>

   i: interactive
   t: tty
   d: background process

 * Launch container with specific port
   docker run -it -p <host-port>:<docker-port>  <image-name>
   
 * Lauching an nginx container which runs on port 80
   docker pull nginx
   docker run -itd -p 80:80  --name webserver  nginx

   Check using docker ps container should be present

 * Check a running container
   docker inspect <container-name>



 * Build a docker image using a Dockerfile
   docker build -t <image name you want to give>  <Dockerfile path>

 
 * Push image to docker hub
   docker login  (Login to docker hub only needed once)
   docker tag <localsystem image name>   <username>/<preferred image name>
   docker push <username>/<preferred image name>


 * Create a new network called my-network; it will default to using the bridge driver.
docker create network my-network 

 * Use the -d flag to select an alternative driver, such as host.
docker create network my-network -d host 

 * Connect a container to an existing network.
docker network connect <network> <container> 

 * Remove a container from a network it’s currently connected to.
docker network disconnect <network> <container> 

 * List all the Docker networks available on your host, including built-in networks such as bridge and host.
docker network ls 

 * Delete a network by its ID or name. This is only possible when there are no containers currently connected to the network.
docker network rm <network> 



docker volume create testvol1

docker volume ls

docker volume inspect testvol1

---------------------------------------
Mounting a Volume using -v or --mount
---------------------------------------
docker run -it --name=srv01 --mount source=testvol1,destination=/data centos

docker run -it --name srv04 -v testvol1:/data centos

docker run -it --volumes-from srv01 --name srv02 centos /bin/bash

---------------------------------------
Mounting a Host Directory as a Data volume 
---------------------------------------
mkdir files
cd files

touch file.txt

docker run -it –-name srv05 -v "$(pwd)":/data1 centos


docker volume rm [volume_name]
