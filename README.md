![Docker Cloud Automated build](https://img.shields.io/docker/cloud/automated/vladdsm/docker-r-studio.svg)
![Docker Cloud Build Status](https://img.shields.io/docker/cloud/build/vladdsm/docker-r-studio.svg)

# docker-r-studio

## News

2021-06-01: Update R version 4.1.0
2021-03-21: Update R version
2020-12-30: Refresh packages
2020-10-27: Update R version
2020-09-16: Update of the image
2020-04-19: Added `golem`, `cranlogs` packages, more elaborated readme file, 
2020-04-12: Update to R version 3.6.3

## Description

To allow usage of R-Studio in a portable way using Docker Container

## Procedure

### Build the image

* `docker build -t vladdsm/docker-r-studio .` - to build image
* `docker login` - to authenticate
* `docker push vladdsm/docker-r-studio` - to push image to docker hub.

### Run Container

#### !! make sure to use your own [strong] passwords in case it will work in the server
#### !! make sure to replace my computer name [vladdsm] with yours

#### Create dedicated executable file and map specific directory e.g. RunRStudio

`docker run --rm -p 8787:8787 -e USER=myself -e PASSWORD=guest -v /Users/vladdsm/R_Studio_Shared:/home/myself/projects vladdsm/docker-r-studio`

Note: Create all your projects in the mapped local folder: e.g. `/Users/vladdsm/R_Studio_Shared`

### Run R studio in the browser

* Access running container with the browser: `http://localhost:8787`, once prompted add your username and password...
* Create new project inside folder 'projects'. 
* All working projects will be synchronised to the local computer in the folder `/Users/vladdsm/R_Studio_Shared`

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
`docker exec -it [container ID ] bash` to use bash in the running container and perform manipulations with container
`docker commit -m 'comment' [container ID] vladdsm/docker-r-studio` to save changes

Only use this procedure for troubleshooting purposes

### Tag the image to keep versions

`docker tag vladdsm/docker-r-studio vladdsm/docker-r-studio:Version1.0`
`docker push vladdsm/docker-r-studio:Version1.0`

### Pull image from the Docker Hub

`docker pull vladdsm/docker-r-studio`
