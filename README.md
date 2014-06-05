CEGMA in a Docker Container
===========================

Setting up a CEGMA installation can sometimes be a pain. This Dockerfile will build a container for CEGMA and all of its dependencies.

Let's say I have some data at /path/to/data/scaffolds.fasta. If you have docker, it's as easy as:

    cd /path/to/data
    docker run -v `pwd`:/data -w /data robsyme/cegma:latest cegma -g scaffolds.fasta

![docker run command explanation](http://i.imgur.com/rCOyJwN.png)

This will download the [latest cegma-docker image](https://index.docker.io/u/robsyme/cegma-docker/) from index.docker.io, make a new container, mount the host directory inside the container and run cegma on the file 'scaffolds.fasta', just as if you'd installed cegma and all it's dependencies yourself on the host. When cegma is finished, docker closes the container. If you want docker to delete the container when cegma is done, just add '--rm=true'. Note that this won't delete your cegma results, just the container.

If you're on ubuntu 14.04 and don't have docker, you can install it with the incantation

    sudo apt-get install docker.io
    sudo ln -sf /usr/bin/docker.io /usr/local/bin/docker

If you're not on Ubuntu 14.04, the Docker people [have you covered](https://www.docker.io/gettingstarted/#h_installation).

Maybe you don't like the way I've set up the container (no worries, I understand). If so, you can simply take the Dockerfile from this repo, make changes and build it yourself

    git clone https://github.com/robsyme/cegma-docker.git
    cd cegma-docker
    env editor Dockerfile # Make changes to your heart's content
    docker build -t cegma:v2.5 .
    docker run -it cegma:v2.5 bash

