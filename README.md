# Dockerized Education Platform
This is a dockerized version of the education platform for trying out the platform locally.

Further details on the platform can be found on the main [platform wiki page](https://github.com/mdenet/educationplatform/wiki).

Any bugs, feature requests, or suggestions can be added to the [issue tracker](https://github.com/mdenet/educationplatform/issues).

[![MDENet education platform demo](https://img.youtube.com/vi/QHwYlqBQ-W0/hqdefault.jpg)](https://www.youtube.com/watch?v=QHwYlqBQ-W0)


## Prerequisites 
### Core
 1. [GIT](https://git-scm.com/)
 2. [Docker](https://www.docker.com/)
 3. [Docker Compose](https://docs.docker.com/compose/install/)

### System
1. Disk space - 20 GB 
2. Memory - 3 GB

If using a linux based virtual machine, the minimum recommended settings of 3GB system memory and 30GB virtual disk should be used.

### Windows Preconfiguration
If using Windows to run the platform, a few additional steps are required.

- Enable long paths for git.
```
git config --global core.longpaths true
```

- If the mdenet/educationplatfom-docker repository has previously been checked out, you may have to clear submodule indexes so that file line endings re-normalised correctly.

```
git submodule foreach 'git rm --cached -r .'
``` 

- Ensure that the docker daemon is running by starting Docker Desktop from the start menu or by powershell command  
``` 
& "[DOCKER_INSTALL_PATH]\Docker\Docker Desktop.exe" 
```
where `DOCKER_INSTALL_PATH` is the path to install docker which  usually defaults to
`C:\Program Files\Docker`.


- Ensure that the docker is set to use the linux engine by right-clicking the Docker Desktop icon in the system tray menu and selecting use linux engine or by running the command 
```
[DOCKER_INSTALL_PATH]\Docker\DockerCli.exe -SwitchDaemon -SwitchLinuxEngine
```

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

docker compose up --build 
```

> Note it may take approximately 10 minutes the first time the platform is built.


## Access the platform

Once docker has [started](#build-and-run-the-docker-image) the containers, the platform will be available at http://127.0.0.1:8080

**403 Error**

If a 403 forbidden permissions error is encountered, the permission of the files used in the docker volumes must be configured. For linux based system run the following command from the `educationplatform-docker` directory.

``` 
chmod -R 755 {public,educationplatform-examples} 
```

## Stopping the platform

To safely stop the platform use `ctrl-c`  in the terminal running the platform.
