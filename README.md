[![Build Status](https://travis-ci.org/gabrielesh/PrivateBin.svg?branch=master)](https://travis-ci.org/gabrielesh/PrivateBin)

# PrivateBin Docker Container

This repository contains the configuration for setting up a PrivateBin docker container using docker-compose easyly.

### Configuration : 
We are using the official PrivateBin Docker image (see the [Dockerfile and other documentation](https://hub.docker.com/r/privatebin/nginx-fpm-alpine/)). Our compose file specifies the latest build : latest

We have taken the docker container command suggested in the PrivateBin Docker documentation and translated it into a compose file for easier execution. The original suggested command was
 ```
 docker run -d --restart="always" --read-only -p 8080:8080 -v $PWD/conf.php:/srv/cfg/conf.php:ro -v $PWD/privatebin-data:/srv/data privatebin/nginx-fpm-alpine
 ```
### Config Files : 
Config files are located in .cnf/ directory.

.env.ewample : contains tunables variables


conf.php : contains full configuration


# To Run
PrivateBin suggests running the Docker container in the backround using `docker-compose up -d` (-d for detached mode).



