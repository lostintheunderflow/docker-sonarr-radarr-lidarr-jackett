[linuxserverurl]: https://linuxserver.io
# Description
Mix of [LinuxServer.io][linuxserverurl] (Sonarr, Radarr, Lidarr, Jackett) into one container.

## Usage
```
CONFIG="/home/osmc/Docker/configs" #folder for storing configurations
DISK="/mnt/superbig" #target folder for downloads, movies, tv, music
docker create \
 --restart=unless-stopped \
 -d \
 -e PUID=1000 -e PGID=1000 \
 -e TZ=Europe/Paris \
 -p 7878:7878 \
 -p 8686:8686 \
 -p 8989:8989 \
 -p 9117:9117 \
 -v /etc/localtime:/etc/localtime:ro \
 -v ${CONFIG}:/config \
 -v ${DISK}/Torrents:/downloads \
 -v ${DISK}/Séries:/tv \
 -v ${DISK}/Films:/movies \
 -v ${DISK}/Musique:/music \
 --name=mediamanager \
 lsioarmhf/sonarr:latest
```
