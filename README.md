# RaspberryPiHomelab
A simple guide to setting up a homelab environment on a Raspberry Pi.  

## Installing Raspberry Pi Os 
To set up the Raspberry Pi, you’ll first need to install the OS using `Raspberry Pi Imager`

* Visit [Raspberry Pi Software](https://www.raspberrypi.com/software/) to install Raspberry Pi Imager 
* Click on the application and select your Raspberry pi model 
* Select operating system **->** other **->** Raspberry Pi Os Lite (64 bit) no desktop environment
* Select storage device (select an sd card which the rapsberry pi will use)
* Configure settings: hostname, Wifi SSID/pass, enable ssh, username and pass
* Insert your sd card into your Raspberry Pi
* Wait till the setup is done and insert your username and pass

## Installing Git 
Git allows you to clone, manage, and version control projects on your `Raspberry Pi`

* `sudo apt update` to update
* `sudo apt install git -y` 
* `git --version` to verify git was installed

## Installing Docker 
Docker allows you to manage containers, images for a homelab environment 

* `curl -sSL https://get.docker.com | sh`
* `docker --version` to verify docker was installed
* `sudo usermod -aG docker <username>` add user to docker group
* `sudo reboot` to reboot the system to apply changes


## Installing Portainer 
[Portainer Dev Page](https://www.portainer.io/) <br>
[Portainer Docker Page](https://docs.portainer.io/start/install-ce/server/docker/linux) <br>
Portainer is a web interface for your `Raspberry Pi` for managing your docker containers 

* `git clone https://github.com/AJamell/RaspberryPiHomelab.git`
* `cd RaspberryPiHomelab/portainer` change directory to git folder
* Change configurations of **Docker Compose** file to edit ports, data folders, env variables, etc 
* `docker compose up -d` docker compose file will run 
* `docker ps` to check running containers
* Run `http://<hostname>.local:<port>` to check if portainer is running 

## Installing Filebrowser
[Filebrowser Dev Page](https://filebrowser.org/index.html) <br>
[Filebrowser Docker Page](https://filebrowser.org/installation.html) <br>
Filebrowser uploads music to your Navidrome folder && JellyFin folder

* First create folders for media 
* Jellyfin and Navidrome will use these folders for content

```bash 
# Create the main directory and subfolders for media and databases
mkdir -p ~/RaspberryPiHomelab/filebrowser/{filebrowser_db,media/movies,media/tvshows,media/music}
# Set permissions so Docker can write to these folders
sudo chown -R $USER:$USER ~/RaspberryPiHomelab
sudo chmod -R 775 ~/RaspberryPiHomelab
```
* `cd RaspberryPiHomelab/filebrowser` change directory to filebrowser folder
* Change configurations of **Docker Compose** file to edit ports, media folders, env variables, etc
* Move music mp3 file to your music folder for testing
```bash 
 mv ~/RaspberryPiHomelab/navidrome/RINZO, MAHIRU - デイドリーム (Daydream) _ J Pop _ NCS - Copyright Free Music.mp3 ~/RaspberryPiHomelab/filebrowser/media/music/
```
* `docker compose up -d` run filebrowser through docker compose 
* Run `http://<hostname>.local:<port>` to check filebrowser is running
* Run `docker ps` or `docker logs <container_id>` to check debug containers
* Run `docker logs <container_id>` to check your randomized admin password to login to filebrowser


## Installing Navidrome
[Navidrome Dev Page](https://www.navidrome.org/) <br>
[Navidrome Docker Page](https://www.navidrome.org/docs/installation/docker/) <br>
Navidrome is a music streaming server that provides a web interface to browse your music collection.

* `cd RaspberryPiHomelab/navidrome` change directory to git folder
* Change configurations of **Docker Compose** file to edit ports, data folders, env variables, etc 
* `docker compose up -d` docker compose file will run 
* Run `http://<hostname>.local:<port>` to check if navidrome is running
* Run `docker ps` or `docker logs <container_id>` to check debug containers

### To upload music to your media folders 
* Open filebrowser and upload your music to the music folder inside the media folder

## Installing Jellyfin 
[JellyFin Dev Page](https://jellyfin.org/) <br>
[JellyFin Docker Page](https://jellyfin.org/docs/general/installation/container/) <br>
Jellyfin is a free software media system that puts you in control of managing and streaming your media.

* `cd RaspberryPiHomelab/jellyfin` change directory to git folder
* Change configurations of **Docker Compose** file to edit ports, data folders, env variables, etc 
* `docker compose up -d` docker compose file will run 
* Run `http://<hostname>.local:<port>` to check if jellyfin is running
* Run `docker ps` or `docker logs <container_id>` to check debug containers

### To upload media to your media folders 
* Open filebrowser and upload your movies to the movie folder inside the media folder
* Open jellyfin and upload your tv shows to the tv shows folder inside the media folder
* Open Jellyfin, Go to settings, Dashboard -> Scan all libraries (This will scan your media and upload any changes to jellyfin)

## Install Hommarr 
[Homarr Dev Page](https://homarr.dev/) <br>
[Homarr Docker Page](https://homarr.dev/docs/getting-started/installation/docker/) <br>
Homarr is a sleek, modern dashboard that puts all of your apps and services at your fingertips. 

* `cd RaspberryPiHomelab/homarr` change directory to git folder
* Run `openssl rand -hex 32` to generate a random password for homarr
* Copy the password and paste it in the `docker compose` file
* Change configurations of **Docker Compose** file to edit ports, data folders, env variables, etc 
* `docker compose up -d` docker compose file will run 
* Run `http://<hostname>.local:<port>` to check if homarr is running
* Run `docker ps` or `docker logs <container_id>` to check debug containers


## Sources
* [Docker And Portainer Install](https://youtu.be/O7G3oatg5DA?si=BBOGb8YrGyLZ_qUL) <br>
* [Homarr Setup Example](https://youtu.be/_QmsBOatmXg?si=euA1CRnWAeXkOS0O)
* [Image Raspberry Pi](https://www.youtube.com/watch?v=sq5S1MM2Pmo&t=43s)
* [Music Copyright](https://youtu.be/80xoyPca3zI?si=HOxbp_jP-HgiZFi7)




