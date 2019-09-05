[![Build Status](https://travis-ci.org/gabrielesh/PrivateBin.svg?branch=master)](https://travis-ci.org/gabrielesh/PrivateBin)

# PrivateBin Docker Container

This repository contains the configuration for setting up a PrivateBin docker container using docker-compose. 

### Configuration
We are using the official PrivateBin Docker image (see the [Dockerfile and other documentation](https://hub.docker.com/r/privatebin/nginx-fpm-alpine/)). Our compose file specifies the latest build, 1.2.1.

We have taken the docker container command suggested in the PrivateBin Docker documentation and translated it into a compose file for easier execution. The original suggested command was
 ```
 docker run -d --restart="always" --read-only -p 8080:80 -v conf.php:/srv/cfg/conf.php:ro -v privatebin-data:/srv/data privatebin/nginx-fpm-alpine:1.2.1
 ```
For better security, our compose file references a host port variable specified in an .env file. Git has been set to ignore .env files; see .env.example file for how to specify your host port and any other sensitive information needed for your installation.

This repo includes a custom configuration file `conf.php` as a second volume in our `docker-compose.yml`. In that file we have modified our PrivateBin [configuration](https://github.com/PrivateBin/PrivateBin/wiki/Configuration) as follows:
- Set burn after read as default
- Set default expiration to 1 day
- Set the HTTP header containing the visitors IP address, i.e. X_FORWARDED_FOR (because our website runs behind a reverse proxy)
- Allow file uploads, with a 4 Mebibyte limit

# To Run
PrivateBin suggests running the Docker container in the backround using `docker-compose up -d` (-d for detached mode).



