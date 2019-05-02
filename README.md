# docker-r-studio

## Description

To allow usage of R-Studio in a portable way using Docker Container

## Procedure

### Build the image

`docker login` - to authenticate
`docker build -t vladdsm/docker-r-studio .`

### Run Container

`docker run --rm -p 8787:8787 -e USER=myself -e PASSWORD=guest -v /Users/vladdsm/R_Studio_Shared:/home/myself/r-studio vladdsm/docker-r-studio`

### Stop Container

`CTRL + C`

### Push to Docker Hub

`docker push vladdsm/docker-r-studio`

### Save image locally into the archive

`docker save vladdsm/docker-r-studio > docker-r-studio.tar`

### Delete images from the Docker Image

`docker images` - get image id
`docker rmi <image id>

### Load the container from the archive

`docker load --input docker-r-studio.tar`

### Change state of the image

From another terminal while container is running

`docker ps` - to find container ID
`docker commit -m 'comment' [container ID] vladdsm/docker-r-studio