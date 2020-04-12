![Docker Cloud Automated build](https://img.shields.io/docker/cloud/automated/vladdsm/docker-r-studio.svg)
![Docker Cloud Build Status](https://img.shields.io/docker/cloud/build/vladdsm/docker-r-studio.svg)

# docker-r-studio

## News

Update to R version 3.6.3, 2020-04-12

## Description

To allow usage of R-Studio in a portable way using Docker Container

## Procedure

### Build the image

`docker login` - to authenticate
`docker build -t vladdsm/docker-r-studio .`

### Run Container

#### !! make sure to use your own [strong] passwords
#### Create dedicated executable file and map specific directory e.g. RunRStudio
`docker run --rm -p 8787:8787 -e USER=myself -e PASSWORD=guest -v /Users/vladdsm/R_Studio_Shared:/home/myself/r-studio vladdsm/docker-r-studio`

### Run R studio in the browser

Type in the browser:

`http://localhost:8787`, once prompted add your username and password...

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
`docker exec -it [container ID ] bash` to use bash in the running container

### Tag the image to keep versions

e.g.: `docker tag vladdsm/docker-r-studio vladdsm/docker-r-studio:Version1.0`
