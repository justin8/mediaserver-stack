# Media server

This is a basic docker-compose setup that will run nginx, sonarr, couchpotato, jackett and transmission. The conf.d example file is used to specify the domains to respond on, as well as the folders to use for config and to mount for storage of files in the containers. It also sets up samba to have a single share for the storage mount point on the local network.

## Requirements:
* docker
* docker-compose
* rsync
* samba
* systemd

## Usage

To install/update the service:

1. Copy `mediaserver.conf.d.example` to `/etc/conf.d/mediaserver` and fill in the values
2. Run `sudo ./install` to install the service and enable it for next reboot
3. Run `sudo systemctl start mediaserver` to start the service.
4. On first install, some things will need to be manually set up prior to opening the service up; i.e. passwords for the services. Keep in mind that transmission overwrites the config on shutdown, so only edit it's config while offline.

## Known issues

* It runs as root; obviously not the best.
* Only tested on Ubuntu 16.04 LTS
* Samba is required on the host machine; but this avoids all issues with nmbd/smbd/etc. This can at least be solved using `network_mode: host`
