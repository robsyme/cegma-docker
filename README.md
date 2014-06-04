CEGMA in a Docker Container
===========================

Setting up a CEGMA installation can sometimes be a pain. This Dockerfile will build a container for CEGMA and all of its dependencies.

The easiest way to use CEGMA is to pull the trusted docker build image from index.docker.io

    
Alternatively, you can simply take the Dockerfile from this repo and build it yourself

    wget https://github.com/robsyme/cegma-docker/archive/v2.5.tar.gz
    tar -xzvf v2.5.tar.gz
    cd cegma-docker-2.5
    docker build -t cegma:v2.5 .
    docker run -it cegma:v2.5 bash

