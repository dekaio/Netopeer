# Netopeer

#Docker image
http://www.seguesoft.com/index.php/how-to-set-up-netopeer-server-to-use-with-netconfc    
 
# setup sshd    
/etc/ssh/ - vim sshd    
# run docker
docker run -it --rm -p 8300:830 --name netopeer netopeer

docker build -t netopeer
docker ps -a
