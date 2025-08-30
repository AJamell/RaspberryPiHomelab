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
* `cd RaspberryPiHomelab/portainer` change destaintion to git folder
* `docker compose up -d` docker will run portainer on port 9000
* `docker ps` to check running containers
* run `http://<hostname>.local:9000` to check portainer running on port 9000

## Sources

* [Docker And Portainer Install](https://youtu.be/O7G3oatg5DA?si=BBOGb8YrGyLZ_qUL) <br>
* [Image Raspberry Pi](https://www.youtube.com/watch?v=sq5S1MM2Pmo&t=43s)





