
client - application or part of network manager
server - device
## Docker installation
https://linuxhint.com/install_configure_docker_ubuntu/
sudo systemctl enable --now docker
## Netopeer installation
* This is the file link https://github.com/cesnet/netopeer
* Use the latest Dockerfile from below link
https://github.com/sysrepo/sysrepo/blob/master/deploy/docker/sysrepo-netopeer2/latest/supervisord.conf
Run docker server
sudo docker run -it --rm -p 8300:830 --name netopeer netopeer
## ssh configuration
sudo service SSH restart
Patch your SSHd configuration. The netconf server (single-level, for instance) will be called automagically by sshd when a netconf client connects. In Ubuntu the file is /etc/ssh/sshd_config

Port 830
Subsystem netconf /usr/local/bin/netopeer-server-sl

#Docker image http://www.seguesoft.com/index.php/how-to-set-up-netopeer-server-to-use-with-netconfc

setup sshd
/etc/ssh/ - vim sshd

run docker
docker run -it --rm -p 8300:830 --name netopeer netopeer

docker build -t netopeer docker ps -a

## Connect to server
connect 127.0.0.1 --login root
sudo ssh root@127.0.0.1 -p 830

## tips and tricks
make modifications in supervisord.conf
docker build -t netopeer .

docker run -it --rm -p 8300:830 --name netopeer netopeer
docker ps -a    
docker stop containerid
docker rm containerid

https://hub.docker.com/r/sysrepo/sysrepo-netopeer2/
## check ip
docker container ls -a    
docker inspect -f '{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' containerid    
