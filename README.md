# RaspberryPiHomelab
A simple guide to setting up a homelab environment on a Raspberry Pi.  

## Installing Raspberry Pi Os 
To set up the Raspberry Pi, you’ll first need to install the OS using `Raspberry Pi Imager`

* Visit `https://www.raspberrypi.com/software/` to install Raspberry Pi Imager 
* Click on the application and select your Raspberry pi model 
* Select operating system **->** other **->** Raspberry Pi Os Lite (64 bit) no desktop environment
* Select storage device (select an sd card which the rapsberry pi will use)
* Configure settings: hostname, Wifi SSID/pass, enable ssh, username and pass
* Insert your sd card into your Raspberry Pi
* Wait till the setup is done and insert your username and pass

## Installing Git 
Git allows you to clone, manage, and version control projects on your `Raspberry Pi`

* `sudo apt update && sudo apt upgrade -y` to update packages 
* `sudo apt install git -y` 
* `git --version` to verify git was installed

## Installing Docker 
Docker allows you to manage containers, images for a homelab environment 

* `curl -sSL https://get.docker.com | sh`
* `sudo usermod -aG docker <username>` add user to docker group
* `docker --version` to verify docker was installed

## Installing Portainer 
Portainer is a web interface for your `Raspberry Pi` for managing your docker containers 

* `git clone github.com/AJamell/RaspberryPiHomelab.git`
* `cd RaspberryPiHomelab/portainer` change directory to git folder
* Change configurations of **Docker Compose** file to edit ports, data folders, env variables, etc 
* `docker compose up -d` docker compose file will run 
* `docker ps` to check running containers
* Run `http://<hostname>.local:<port>` to check if portainer is running 

## Installing Navidrome
Navidrome hosts your very own music library

* `cd RaspberryPiHomelab/navidrome` change directory to navidrome folder
* Change configurations of **Docker Compose** file to edit ports, music folders, env variables, etc
* Move music mp3 file to your music folder for testing
* `docker compose up -d` run navidrome through docker compose 
* Run `http://<hostname>.local:<port>` to check navidrome is running

## Sources

* [Docker And Portainer Install](https://youtu.be/O7G3oatg5DA?si=BBOGb8YrGyLZ_qUL) <br>
* [Image Raspberry Pi](https://www.youtube.com/watch?v=sq5S1MM2Pmo&t=43s)
* [Music Copyright](https://youtu.be/80xoyPca3zI?si=HOxbp_jP-HgiZFi7)




