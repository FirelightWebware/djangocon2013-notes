# Django and Docker a Marriage Made in Heaven

_Speaker: Ken Cochrane_


This covers the entire talk and is way better than my notes: 
https://www.docker.io/the_whole_story/


## Intro

Docker was originally code that powered dotCloud, a PaaS. Original version
written in Python, but the new version is written Go.

Still a very young project (6 mos), but mature for it's age. Released to the
world on March 27, 2013. June 2013 openstack compatibility.

5300+ Github stars, 100's of projects build on Docker, and 1000's of 
"docerized" apps.

And open-source negine that automates the deployment of any application...


Uses LinuX Containers (LXC), control groups and namespaces, and AUFS.

LinuX containers are like mini vms, let you run a linux system in another
linux system. Like a very light-weight vm. Containers boot fast, in seconds.

You can put 100's to 1000's of containers on one server.

In VMs the guest OS is duplicated, but in containers they share the base OS.

There is a base image, and the files are just diffs from the base image.


### Installation

You can use vagrant, or there is an apt repo. For vagrant there is a repo 
you can just clone and do `vagrant up`, yadda yadda.


There is a slide on how to get docker up on Digital Ocean in 5 easy steps. It
takes about 2 minutes to get it up and running.

Digital Ocean actually has an official Docker image you can deploy from.

Digital Ocean is giving a $10 credit with tinyurl.com/docker10, promo code
DJANGOCON2013.

#### Requirements

- Ubuntu 13.04
- AUFS
... [more]


## Common Use Cases

- local dev env
- deployment
- unit testing

### Unit Testing

sometimes one test can corrupt another test. use containers to isolate tests into
their own environment. no more worrying about tests not cleaning up after each other.
parallelize the tests across multiple machines.

### System Testing

Easily create all the different system configuration to test against. no need to worry
about breaking or rebuilding a test server.

[test fabric scripts](http://agiliq.com/blog/2013/06/self-testing-fabfile-using-docker/)

### Continuous Integration

Run unit tests afetr each source commit. StriderCD.com is based on docker and runs
your CI tests before deployment. 


### Deployment

dokku, Flynn.io, deis.io, chef, puppet, salt, ansible, etc.

dokku is an open source PaaS -- a mini Heroku, less than 100 lines of bash. Uses
heroku buildpacks. Git push deployment.

flynn, open source PaaS written in Go, but still very young.

deis is in beta, open source git push deployenet, written in Python, you can use
docker images for deployment, supports scaling and application formation.

ipmd/salt-minion


### Local Development

VM's are heavy, run 100's of containers on laptop vs a handful of VMs. easier
to duplicate production environment if you have a complex setup.

http://blog.coutapp.com/articles/2013/08/28/docker-git-for-deployment


## Projects Using Docker

- npmt.abru.pt: node.js module testing
    - one container per module is created then destroyed when test is finished
- jiffylab, by preston holmes, provides an entirely web based env for instruction
    - python and unix shell env running in it's own docker container
    - gh: ptone/jiffylab
- memcached SaaS
    - built as a class project
    - memcached saas build with RoR on top of Docker
- Try RethinkDB
    - Saas that let you try out RethinkDB
    - one DB per container
    - containers killed in 24 hours
- openstack-docker
    - deploy to linux containers instead of VMs


## How do I use Docker?

- **container**: linux container
- **imag**: snapshot of a container
- **dockerfile**:jlo

[..more]

### commands

ps list the containers on the system
run runs commands againsta an image to create a containers
[more]

### process

first start off with a build, then create an image out of a good base container,
then publish to docker index. an image is a summation of all the diffs that get
from your base image to your container.

    # run command and exit
    $ docker run ubuntu echo "hello world"
    # run bash
    $ docker run -i -t ubuntu bash

A dockerfile is a simple scripting language that allows you to automate the createion
of docker images. built in caching. add them to any project repo to "dockerize" the project
online tutorial: docker.io/learn/dockerfile/

### examples

start ubuntu container and update
    $ docker run -i-t ubuntu:12.10 bash
    $ [a2bc13] apt-get update

save image
    $ docker commit -m "comment" a2bc13 username/image

see Dockerfile examples in slides

### the docker index

written in django. similar to PyPI but for docker images. only public stuff.
docker image metadata. account required to publish images (free).

index.docker.io

### docker registry

open source python flask app, manages the storage of the images, install private
registry for private images

## The API

docker has a REST based api used to control the docker daemon. the docker cli
uses the same api. clients available for most languages.

docker-py is the python client. there's a javascript client too.

[there is a slide with an example using docker-py]

interesting projets with docker UIs, shipyard, angular, dockland (ruby)

## Docker 1.0

coming out soon.


## Reference

### Speaker

@kencochrane
works for dotCloud (corporate sponser of Docker)
