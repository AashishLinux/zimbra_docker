# How to Install Zimbra on Docker Container

## Install Docker and docker-compose
# Docker

$ curl -fsSL https://get.docker.com -o get-docker.sh

$ sh get-docker.sh

# Docker Compose

$ LATEST=$(curl -Ls -w %{url_effective} -o /dev/null https://github.com/docker/compose/releases/latest) && LATEST=${LATEST##*/} && curl -L https://github.com/docker/compose/releases/download/$LATEST/docker-compose-$(uname -s)-$(uname -m) > /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose

**Then Create the directory for bind mount**

mkdir /opt/zimbra

**Then clone this repository**

git clone https://github.com/AashishLinux/zimbra_docker.git

cd zimbra_docker

# FOR DOCKER COMPOSE RUN

docker-compose up -d

# FOR SINGLE CONTAINER DOCKER RUN

**clone this repository**

git clone https://github.com/AashishLinux/zimbra_docker.git

cd zimbra_docker

*Build the image

$ docker build -t zimbra_aashish:v01 .    ## You can build the entire image or download the prebuild image from my docker hub by using "docker pull aashish9899/zimbra:latest"

*Run the docker container

docker run -dit --name zimbra.mail.aashishlinux.tk -h mail.aashishlinux.tk -v /opt/zimbra:/opt/zimbra -p 25:25 -p 80:80 -p 443:443 -p 110:110 -p 143:143 -p 465:465 -p 587:587 -p 993:993 -p 995:995 -p 7071:7071 -p 8443:8443 -p 9071:9071 zimbra_aashish:v01

# Now you can exec into the container with

$ docker exec -it zimbra.mail.aashishlinux.tk

# After that run the dns script placed in "/root"

./dns_setup.sh       # it will setup your dns records accordingly

**then start installing zimbra **
cd zcs-8.8.15_GA_4179.UBUNTU20_64.20211118033954
./install.sh
