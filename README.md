<div id="top"></div>
<!--
*** Thanks for checking out the Best-README-Template. If you have a suggestion
*** that would make this better, please fork the repo and create a pull request
*** or simply open an issue with the tag "enhancement".
*** Don't forget to give the project a star!
*** Thanks again! Now go create something AMAZING! :D
-->



<!-- PROJECT SHIELDS -->
<!--
*** I'm using markdown "reference style" links for readability.
*** Reference links are enclosed in brackets [ ] instead of parentheses ( ).
*** See the bottom of this document for the declaration of the reference variables
*** for contributors-url, forks-url, etc. This is an optional, concise syntax you may use.
*** https://www.markdownguide.org/basic-syntax/#reference-style-links
[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![MIT License][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]
-->


<!-- PROJECT LOGO -->
<br />
<div align="center">
  <img src="https://i.imgur.com/COkTt73.png" alt="Logo" width="180" height="180">

  <h3 align="center">Jerdle's Homelab</h3>
  <p align="center">Useful Info & Future Planning</p>
</div>



<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#roadmap">Roadmap</a></li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#acknowledgments">Acknowledgments</a></li>
  </ol>
</details>



<!-- ABOUT THE PROJECT
## About The Project

![Product Name Screen Shot][screenshot]

Here's a blank template to get started: To avoid retyping too much info. Do a search and replace with your text editor for the following: `github_username`, `repo_name`, `twitter_handle`, `linkedin_username`, `email_client`, `email`, `project_title`, `project_description`

<p align="right">(<a href="#top">back to top</a>)</p> -->



## Built With
* [Synology DS220+](https://www.synology.com/en-us/products/DS220+)
* [Docker](https://www.docker.com/)
* [Raspberry Pi 4](https://www.raspberrypi.com/products/raspberry-pi-4-model-b/?variant=raspberry-pi-4-model-b-4gb)


<!-- SYNOLOGY -->
# Synology DS220+
### Native
- [Plex](https://forums.plex.tv/t/synology-faq-questions-answers-and-a-few-how-tos/490215)
- Docker

### Backups
- [Movies](data/movies.rtf)
- [TV Shows](data/tvshows.rtf)
- macOS Time Machine
- iOS Photos (Synology Photos)
- iCloud Drive

### Scheduled Tasks
[Plex Auto Updater](https://github.com/YuriyGuts/syno-plex-update)
```
bash /volume1/Scripts/syno-plex-update.sh
```
[Pullio](https://hotio.dev/pullio/) - Updates arr apps from hotio
```
/usr/local/bin/pullio > /volume1/docker/pullio/pullio.log 2>&1
```

<!-- DOCKER -->
# Docker
#### Docker Admin
- [Portainer](http://192.168.1.23:9000/#!/home)
- [Docker Hub](https://hub.docker.com/)
- [hotio.dev](https://hotio.dev/)

### Docker Containers
- [qBittorrent](https://hub.docker.com/r/markusmcnugen/qbittorrentvpn)
- [qBitManage](https://hotio.dev/containers/qbitmanage/)
- [SABnzbd](https://hotio.dev/containers/sabnzbd/)
- [Tautulli](https://hub.docker.com/r/linuxserver/tautulli)
- [Calibre](https://hub.docker.com/r/linuxserver/calibre-web)
- [Jackett](https://hub.docker.com/r/linuxserver/jackett)
- [Radarr](https://hotio.dev/containers/radarr/)
- [Sonarr](https://hotio.dev/containers/sonarr/)
- [Lidarr](https://hotio.dev/containers/lidarr/)
- [Readarr](https://hotio.dev/containers/readarr/)
- [Prowlarr](https://hotio.dev/containers/prowlarr/)
- [Flaresolverr](https://hub.docker.com/r/flaresolverr/flaresolverr)
- [Overseerr](https://hotio.dev/containers/overseerr/)
- [Nginx Reverse Proxy](https://nginxproxymanager.com/)
- [Organizr](https://hub.docker.com/r/organizr/organizr)
- [Homarr](https://hub.docker.com/r/homarr/homarr)

### Installation
docker-compose
<br>
`sudo docker-compose up -d`

system prune
<br>
`sudo docker system prune --all --volumes`

#### Update Containers
2 commands:
<br>
`sudo docker-compose pull`
<br>
`sudo docker-compose up -d`

### qBittorrent + VPN
Using Mullvad VPN port 57001, following command to check IP in docker container
<br>
`curl ifconfig.me`

### Myanonymouse
When qBittorrent is restarted and given a new IP address, Myanonymouse must run a script to set the dynamic seedbox ip
<br>
1. On Myanonymouse, submit new qBit IP address
2. Change the 'Allow session to set dynamic seedbox IP' to true
3. Get the cookie
4. Inside the qBittorrent terminal, open a bash session and run the below script with the cookie

```
curl -c /path/docker/persists/mam.cookies -b 'mam_id=long________session_______string' https://t.myanonamouse.net/json/dynamicSeedbox.php
```
<br>
Expected result
<br>
`{"Success":true,"msg":"Completed"}`


<!-- RASPBERRY PI -->
# Raspberry Pi
### PiVPN
Wireguard with Mullvad VPN
<br>
Add
<br>
`pivpn -a`

QR Code
<br>
`pivpn -qr`

### Homebridge
Compatible w/Apple Homekit
- [homebridge-vesync](https://github.com/mickgiles/homebridge-vesync#readme)
- [Homebridge to Google Smart Home](https://github.com/oznu/homebridge-gsh#readme)

### PiHole
Network-wide ad blocker
<br>
#### Lists
- [Whitelist file](pi/pihole/Pihole-Whitelist.rtf)
- [Blacklist file](pi/pihole/Pihole-Block.rtf)
- [Firebog Blocklists](https://firebog.net/)
- [anudeepND Whitelist](https://github.com/anudeepND/whitelist)

Update
<br>
`pihole -up`

### [Airconnect](https://github.com/philippe44/AirConnect)
Turns Google Home Minis into Airplay targets
- Service autostarts on reboot

### Unattended-Upgrades
Scheduled updates and upgrades

### Other Commands
Update & Upgrade
<br>
`sudo apt update && sudo apt upgrade`

Config
<br>
`sudo raspi-config`
<p align="right">(<a href="#top">back to top</a>)</p>

<!-- ROADMAP -->
## Roadmap
- [ ] Configure Grafana + Prometheus + SNMP for dashboards
    - [ ] [Raspberry Pi Internet Speed Monitor](https://pimylifeup.com/raspberry-pi-internet-speed-monitor/)
- [ ] Nginx Reverse Proxy

<p align="right">(<a href="#top">back to top</a>)</p>

<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/github_username/repo_name.svg?style=for-the-badge
[contributors-url]: https://github.com/github_username/repo_name/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/github_username/repo_name.svg?style=for-the-badge
[forks-url]: https://github.com/github_username/repo_name/network/members
[stars-shield]: https://img.shields.io/github/stars/github_username/repo_name.svg?style=for-the-badge
[stars-url]: https://github.com/github_username/repo_name/stargazers
[issues-shield]: https://img.shields.io/github/issues/github_username/repo_name.svg?style=for-the-badge
[issues-url]: https://github.com/github_username/repo_name/issues
[license-shield]: https://img.shields.io/github/license/github_username/repo_name.svg?style=for-the-badge
[license-url]: https://github.com/github_username/repo_name/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://linkedin.com/in/linkedin_username
[screenshot]: images/screenshot.png
[logo]: images/logo.png
[whitelist]:pi/pihole/Pihole-Whitelist.rtf
[blacklist]:pi/pihole/Pihole-Block.rtf
