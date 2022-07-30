# Dcoker 🐬 
Useful commands to create docker containers and more. Star it for future reference. 

Will be adding more here as I continue learning. 


1. First build an image in the root of your project folder 
2. In this example I use Node, so visit [DockerHub](https://hub.docker.com/) and search for the particular version
3. In your docker file type the following.
 
```
FROM node:lts-gallium //use node version image from docker hub

WORKDIR /usr/src/newProject //The absolute or relative path to use as the working directory. Will be created if it does not exist.
COPY ./ ./  //the first "./" is the root of our project in our local machine, and the second the location we want to copy to our container
RUN npm install // this is one of the run layers to install the project packages

CMD ["/bin/bash"] // what to run in the container which allows access to bash

```
Let's test it out and build the image, in the terminal

| Command   | Description  |
| ------------- | ------------- |
|`docker build -t newProject`| the `-t` means tag and "." builds all |
|`docker run -it newProject` | this runs the docker container we just created. A hash will be generated for the container and will have access to use node now.|
|`docker run -d newProject`| runs the image container in the background |
|`docker ps`|lists all the container that are currently running|
|docker exec -it 'container's hash id' bash| exits and the list goes the hash refernced container bash|
|`docker-compose up --build`| this comands brings the container and runs build, this way we wont have to re-run `docker-compose run "name-of-app"` every time we build or make changes |
|docker stop 'container's hash id'| stops the running container |
|docker run -it -p 3000:3000 | container port to host (our machine) port. this way will be able to run it on locally on port 3000 from the container|


This is `docker-compose.yml` sample to refer to

```yml

version: '3.6'

services:
  app-name:
    container_name: backend
    build: ./
    command: npm start
    working_dir: /usr/api/src/app-name
    ports:
      - "3000:3000"
    volumes:
      - ./:/usr/api/src/app-name 
    
```

`volumes` can watch the changes in the container directory and updates as we make changes locally. 

