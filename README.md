# Dockerized Education Platform
This is a dockerized version of the education platform for trying out the platform locally.

Further details on the platform can be found on the main [platform wiki page](https://github.com/mdenet/educationplatform/wiki).

Any bugs, feature requests, or suggestions can be added to the [issue tracker](https://github.com/mdenet/educationplatform/issues).

## Prerequisites 
### Core
 1. [GIT](https://git-scm.com/)
 2. [Docker](https://www.docker.com/)
 3. [Docker Compose](https://docs.docker.com/compose/install/)
 

### Additional
For eclipse based tool services that aren't yet fully dockerized:

1. Java - OpenJDK version 19 tested
2. [Maven](https://maven.apache.org/) - version 3.9 tested

## Checkout the repository
Use either command to clone the repository and all of its submodules.

**Via https -**
```
git clone --recurse-submodules https://github.com/mdenet/educationplatform-docker.git
```

**Via ssh -** 
```
git clone --recurse-submodules git@github.com:mdenet/educationplatform-docker.git
```

> Note that for ssh access you must [configure](https://docs.github.com/en/authentication/connecting-to-github-with-ssh) your account with a key.

## Build and run the docker image
This builds the docker images and starts the platform servers.
```
cd ./educationplatform-docker
docker compose up
```


## Build and run eclipse-based tool services

This builds the eclipse-based tool services e.g. OCL using maven and starts the services.
```
cd ./educationplatform-docker/platformtools/services
mvn clean 
mvn install
./launch.sh
```
> Note that this can take some time to complete the first time the services are built.

Further details of launching a tool service manually can be found in the platformtools [readme](https://github.com/mdenet/platformtools). 

## Access the platform

Once docker is [running](#build-and-run-the-docker-image) the platform will be available at http://127.0.0.1:8080
