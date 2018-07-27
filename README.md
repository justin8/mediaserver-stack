# Media server stack

This is a basic docker stack setup that will run nginx, sonarr, couchpotato, jackett and transmission.

## Requirements:
* docker

## Usage

To install/update the service:

1. Make a copy of traefik.toml.example in to your traefik config directory and customize it if required
2. Make a copy of `vars.example` as `vars` in this folder and customize it
3. Ensure that all required directories already exist
4. Run `source vars` to read in your settings
5. Run `docker stack deploy -c docker-stack.yml mediaserver`
6. On first install, some things will need to be manually set up prior to opening the service up; i.e. passwords for the services. Keep in mind that transmission overwrites the config on shutdown, so only edit it's config while offline.


## Notes

* This setup also supports redirection via the jwilder/nginx-proxy image. If it is started with `network_mode: bridge` it should just work.
