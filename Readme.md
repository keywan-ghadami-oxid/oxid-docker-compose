oxid-docker-compose
=================

Getting started
===========
Join the team:
* [![Gitter](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/keywan-ghadami/oxid-docker-compose?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)
* Or create bugtickets with any question


* git clone --recursive git@github.com:keywan-ghadami/oxid-docker-compose.git
* in the copy config.inc.php.dist => config.inc.php 
* Install Docker https://docs.docker.com/engine/installation/
* Install Docker Compose https://docs.docker.com/compose/install/
* run docker compose start
* get the name of the php container by running: docker compose ps
* asume the name is oxid-docker-compose_php_1 the run
  * docker exec -i -t oxidvargant_php_1 bash
  * run composer install -o --no-dev
* open your browser http://localhost


