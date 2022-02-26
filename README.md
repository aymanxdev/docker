# Dcoker 🐬 
Useful commands to create docker containers and more. Star it for future refernce. 

Will be adding more here as I continue learning. 


1. First build an image in the root of your project folder 
2. In this example I use Node, so visit [DockerHub](https://hub.docker.com/) and search for the particular version
3. In your docker file type the following.
 
```
FROM node:lts-gallium //use node version image from docker hub

CMD ["/bin/bash"] // what to run in the container which allows access to bash

```
Let's test it out and build the image, in the terminal

```
docker build -t newProject . // the "-t" means tag and "." builds all
docker run -it newProject //this runs the docker container we just created. A hash will be generated for the container and will have access to use node now. 
docker run -d newProject // runs the image container in the background
docker ps // lists all the container that are currently running
docker exec -it 'container's hash id' bash // exits and the list goes the hash refernced container bash
docker stop 'container's hash id' // stops the running container
```
