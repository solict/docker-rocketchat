# Rocket.Chat.Docker
Rocket.Chat recipes based on [Debian](https://www.debian.org/) and [CentOS](https://www.centos.org/) for [Docker](https://www.docker.com/).  
Continues on [Nodejs.Stack.Docker](https://github.com/solict/nodejs.stack.docker) recipes.

Requires [Docker Compose](https://docs.docker.com/compose/) 1.6.x or higher due to the [version 2](https://docs.docker.com/compose/compose-file/#versioning) format of the docker-compose.yml files.

There are docker-compose.yml files per distribution, as well as docker-compose.override.yml and .env files, which may be used to override configuration.
An optional [Makefile](../../tree/master/Makefile) is provided to help with loading these with ease and perform commands in batch.

Scripts are also provided for each distribution to help test and deploy the installation procedures in non-Docker environments.

The images are automatically built at a [repository](https://hub.docker.com/r/solict/rocket.chat.docker) in the Docker Hub registry.

## Distributions
The services use custom images as a starting point:
- __Debian__, from the [Nodejs.Stack.Docker](https://github.com/solict/nodejs.stack.docker)
  - [Debian 8 (jessie)](../../tree/master/debian8)
  - [Debian 7 (wheezy)](../../tree/master/debian7)
- __CentOS__, from the [Nodejs.Stack.Docker](https://github.com/solict/nodejs.stack.docker)
  - [CentOS 7 (centos7)](../../tree/master/centos7)
  - [CentOS 6 (centos6)](../../tree/master/centos6)

## Services
These are the services described by the dockerfile and dockercompose files:
- Main, adds the main application on top of upstream Nodejs service

## Images
These are the [resulting images](https://hub.docker.com/r/solict/rocket.chat.docker/tags/) upon building:
- Main service:
  - solict/rocket.chat.docker:debian8_main
  - solict/rocket.chat.docker:debian7_main
  - solict/rocket.chat.docker:centos7_main
  - solict/rocket.chat.docker:centos6_main

## Containers
These containers can be created from the images:
- Main service:
  - debian8_main_xxx
  - debian7_main_xxx
  - centos7_main_xxx
  - centos6_main_xxx

## Usage

### From Docker Hub repository (manual)

Note: this method will not allow you to use the docker-compose files nor the Makefile.

1. To pull the images, try typing:  
`docker pull <image_url>`
2. You can start a new container interactively by typing:  
`docker run -ti <image_url> /bin/bash`

Where <image_url> is the full image url (lookup the image list above).

Example:
```
docker pull solict/rocket.chat.docker:debian8_main

docker run -ti solict/rocket.chat.docker:debian8_main /bin/bash
```

### From GitHub repository (automated)

Note: this method allows using docker-compose and the Makefile.

1. Download the repository [zip file](https://github.com/solict/rocket.chat.docker/archive/master.zip) and unpack it or clone the repository using:  
`git clone https://github.com/solict/rocket.chat.docker.git`
2. Navigate to the project directory through the terminal:  
`cd rocket.chat.docker`
3. Type in the desired operation through the terminal:  
`make <operation> DISTRO=<distro>`

Where <distro> is the distribution/directory and <operation> is the desired docker-compose operation.

Example:
```
git clone https://github.com/solict/rocket.chat.docker.git;
cd rocket.chat.docker;

# Example #1: quick start, with build
make up DISTRO=debian8;

# Example #2: quick start, with pull
make img-pull DISTRO=debian8;
make up DISTRO=debian8;

# Example #3: manual steps, with build
make img-build DISTRO=debian8;
make net-create DISTRO=debian8;
make vol-create DISTRO=debian8;
make con-create DISTRO=debian8;
make con-start DISTRO=debian8;
make con-ls DISTRO=debian8;
```

Type `make` in the terminal to discover all the possible commands.

## Credits
Rocket.Chat.Docker  
Copyright (C) 2017 SOL-ICT  
Luís Pedro Algarvio

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.
