
# PrivateBin Docker Container

This repository contains the configuration for setting up a PrivateBin docker container using docker-compose easyly.

### Configuration : 
We are using the official PrivateBin Docker image (see the [Dockerfile and other documentation](https://hub.docker.com/r/privatebin/nginx-fpm-alpine/)). Our compose file specifies the latest build : latest

We have taken the docker container command suggested in the PrivateBin Docker documentation and translated it into a compose file for easier execution. The original suggested command was
 ```
 docker run -d --restart="always" --read-only -p 8080:8080 -v $PWD/conf.php:/srv/cfg/conf.php:ro -v $PWD/privatebin-data:/srv/data privatebin/nginx-fpm-alpine
 ```
### Config Files : 

docker-compose.yml : Should be edited to fit your needs.
``` 
user: 1001
#used to force the user used to run PrivateBin (refer to docker documentation)
#Docker uses user 1000 by default
#to find your user uid run : id -u <username>
#replace 1001 by YOUR USER id, if different.
``` 

Config file is located in .cnf/ directory.


conf.php : contains full configuration for Privatebin v1.7.5


# To Run

Run foollowing commands assuming Docker and Docker-Compose are installed and configured for your user : 

First, clone this repository, it will create a directory containing all needed files.

```
git clone https://github.com/gigadjo/PrivateBin.git
```
Then move into the PrivateBin directory that just has been created.
```
$ cd PrivateBin
```

Edit files according to your needs, they are located in cfg/ directory.

When done, run Private Bin using Docker Compose : 

```
$ docker compose pull
$ docker compose up -d
```
# To Update 

Run the following commands : 
```
$ docker compose down
$ docker compose pull
$ docker compose up -d
```
