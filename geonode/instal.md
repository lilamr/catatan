INSTALL GIT:  
`sudo apt update  
`sudo apt install git  
`git --version  
  
INSTALL DOCKER:  
`sudo apt update  
`sudo apt install apt-transport-https ca-certificates curl software-properties-common  
`curl -fsSL [https://download.docker.com/linux/debian/gpg](https://download.docker.com/linux/debian/gpg) | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg  
`echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] [https://download.docker.com/linux/debian](https://download.docker.com/linux/debian) $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null  
`sudo apt update  
`sudo apt install docker-ce docker-ce-cli [containerd.io](http://containerd.io)  
`sudo docker --version  
`sudo curl -L "[https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname](https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname) -s)-$(uname -m)" -o /usr/local/bin/docker-compose  
`sudo chmod +x /usr/local/bin/docker-compose  
`docker-compose --version  
`sudo apt autoremove --purge  
`sudo usermod -aG docker $USER  
`su - $USER  
  
CLONE GEONODE:  
`sudo mkdir -p /opt/geonode/  
`sudo usermod -a -G www-data $USER  
`sudo chown -Rf $USER:www-data /opt/geonode/  
`sudo chmod -Rf 775 /opt/geonode/  
`cd /opt  
`sudo git clone [https://github.com/GeoNode/geonode.git](https://github.com/GeoNode/geonode.git) -b 4.1.x geonode  
  
BUILD GEONODE:  
`cd /opt/geonode  
`docker-compose build --no-cache  
  
RUN GEONODE:  
`cd /opt/geonode
`docker-compose up -d  
`buka browser: localhost  
`docker-compose stop