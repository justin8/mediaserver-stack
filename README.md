# Media server stack

This is a basic docker-compose setup that will run nginx, sonarr, couchpotato, jackett and transmission. The conf.d example file is used to specify the domains to respond on, as well as the folders to use for config and to mount for storage of files in the containers. It also sets up samba to have a single share for the storage mount point on the local network.

## Requirements:
* docker
* docker-compose
* portinus (pip package)
* python3
* systemd

## Usage

To install/update the service:

1. Make a copy of `mediaserver.conf.example` as `mediaserver.conf` in this folder and customize it
2. Run `./install`
3. On first install, some things will need to be manually set up prior to opening the service up; i.e. passwords for the services. Keep in mind that transmission overwrites the config on shutdown, so only edit it's config while offline.


## Notes

* This setup also supports redirection via the jwilder/nginx-proxy image. If it is started with `network_mode: bridge` it should just work.
