# jenkins-with-docker

Here are two alternatives to bring up a jenkins server with slaves using Docker containers.

## Rafaelnexus-tutorial

This directory contains a docker-compose file that will run two images.

* jenkins master

* jenkins slave

The jenkins slave will be built based on the dockerfile that is on the internal directory called _jenkins-slave_

To make sure the containers start off clean, run:

> docker-compose build

and then,

> docker-compose up

Verify what is running with

> docker-compose ps -a

If the slave is no longer up, don't worry. Follow along.

### Enter to Jenkins master service

Go to your browser, type localhost:8080, it should open up Jenkins, and you will have to configure it as the initial run.

After having set up the admin user, (same as the user and password that is written in _docker-compose.yml_), in another tab, run again

> docker-compose up

> docker-compose ps -a

Now, the slave should be up, because it is able to login with the configured credentials.

The jobs you configure on Jenkins, will run on the slave now, which is the preferred architecture.

## activity1-dind-jenkins

This directory contains a docker-compose that will start two containers.

* Jenkins master image

* Docker in docker image

It also creates volumes for both containers, and a network between them.

### Usage

When starting Jenkins this way, it will __not__ have a slave attached. 

But it can be added via a pipeline through another repo that has a Jenkinsfile that commands to build a jenkins-slave image.

This is why we need the Docker-in-Docker image in a network with jenkins, so that Jenkins can run docker commands in the pipelines.

The example project that does this is [here](https://github.com/danibyay/cicd-pipeline-train-schedule-pipelines)

Take as reference the __Dockerfile__ inside build/ and the __Jenkinsfile__.
