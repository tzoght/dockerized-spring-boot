#docker-spring-boot

[![Build Status](https://travis-ci.org/tzoght/dockerized-spring-boot.svg?branch=master)](https://travis-ci.org/tzoght/dockerized-spring-boot)


### Note:
Make sure that docker is installed and running on your host

### To build a docker image
```
$ ./gradlew buildImage

```

If successful you will see, for example:
```$xslt
> Task :buildImage 
Created image with ID 'a39610ac70f5'.

```

This docker image is now viewed by :

```
$ docker images

```


Now you can run the docker container locally:

```
$ docker run -t -p5000:5000 a39610ac70f5

```
then go to [http://localhost:5000/health](http://localhost:5000/health)

To stop all docker containers:

```$xslt
$ docker stop $(docker ps -a -q)
```

To remove all images from local cache:

```
$ docker rmi $(docker images -q -a)

```


### To push a docker image to docker hub [https://hub.docker.com](Docker Hub)

Assuming that you have a repository named containerRepo (see build.gradle)

You must set `DOCKER_HUB_USERNAME` and `DOCKER_HUB_PASSWORD` environment variables before running the publish task

```
$ export DOCKER_HUB_USERNAME=<username>
$ expoert DOCKER_HUB_PASSWORD=<username>
$ ./gradlew pushImage

```