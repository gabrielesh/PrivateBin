# PrivateBin Docker Container

This repository contains the configuration for setting up a PrivateBin docker container using docker-compose. 

### Configuration details
We are using the official PrivateBin Docker image (see the Dockerfile and other documentation at https://hub.docker.com/r/privatebin/nginx-fpm-alpine/). Our compose file does not specify a build. See the above address to choose a specific build.

Our docker-compose file takes the docker container command suggested in the PrivateBin Docker documentation and translates it into a compose file for easier execution. The original suggested command was:
 docker run -d --restart="always" --read-only -p 8080:80 -v privatebin-data:/srv/data privatebin/nginx-fpm-alpine:1.2.1

To run this container after you have cloned or forked a copy to your hard drive/server, navigate to this repo and enter docker-compose up -d in the command line.
We recommend running with the -d flag to run in detached mode (i.e., to run in background).

Any needed environment variables should be either added to an .env file or, better yet, added to the docker-compose file as secrets. For more on docker secrets, see https://docs.docker.com/engine/swarm/secrets/.

