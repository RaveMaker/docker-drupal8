# Docker: Drupal-8
Dockerfile for Drupal-8 with sSMTP client.

docker-compose file includes:
 - Traefik support
 - MariaDB
 - Adminer
 - Backup

## Setup
1. clone the repo
2. edit .env file
3. create ssmtp/ssmtp.conf from provided ssmtp.conf.example

## Network settings:
The stack is divided into two networks, backend and frontend.

the idea behind splitting the stack into two networks
is to block the access of the reverse proxy to the backend containers.

both networks are unique and will be named with stackname_networname such as:

- docker-drupal8_backend
- docker-drupal8_frontend

after running docker-compose up you need to connect your reverse proxy to your new frontend network:
 you can do that manually using:
 - docker network connect docker-drupal8_frontend PROXY_CONTAINER_NAME

if you are using my Traefik setup there is a 'connect.sh' script included
that will connect all your frontend networks to your Traefik container.

Author: [RaveMaker][RaveMaker].

[RaveMaker]: http://ravemaker.net
 