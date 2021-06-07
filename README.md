
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


## Netconf launch   
1. docker run -it --name sysrepo -p 830:830 --rm sysrepo/sysrepo-netopeer2:latest
2. netopeer-cli
3. connect localhost --port 830 --login netconf
4. password is netconf
5. get-config candidate = Returns configuration data of the candidate   
6. get-config --source startup  --filter-xpath /ietf-interfaces:interfaces  =Filtering something   
7. 
## Netopeer gui installation
https://github.com/CESNET/Netopeer-GUI/tree/master/install
