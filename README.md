# InstallDocker-Swarm-on-PI
### Video : 


Links for Os:
* Ubuntu : https://ubuntu.com/raspberry-pi
* Raspberry Pi OS Lite : https://www.raspberrypi.org/software/operating-systems/
* Sd card formatter : https://www.sdcard.org/downloads/formatter/
* Etcher : https://www.balena.io/etcher/
* Refus : https://rufus.ie/
* How to Install OS on PI : https://www.youtube.com/watch?v=y45hsd2AOpw


```bash
echo upgrading .......................
sudo apt-get upgrade

echo updating .......................
sudo apt-get update

echo Installing Docker  .......................
sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common


curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

sudo apt-get install docker-ce docker-ce-cli containerd.io

apt-cache madison docker-ce

sudo apt-get install docker-ce docker-ce-cli containerd.io

sudo apt install docker.io

sudo apt install docker-compose

echo docker  Install Complete ......................

echo docker --version

# ------------------------------------------
# Make sure to start the swarm on manager
# docker swarm init
# -----------------------------------------

docker service create \
  --name=viz \
  --publish=8080:8080/tcp \
  --constraint=node.role==manager \
  --mount=type=bind,src=/var/run/docker.sock,dst=/var/run/docker.sock \
  alexellis2/visualizer-arm:latest


```
