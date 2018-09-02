Laravel docker 

step 1:git clone git@github.com:santoshstha/laraveldocker.git

step 2:docker-compose build(this will build image in docker)

step 3:docker-compose up(Start containers on the foreground)

step 4 :docker ps (to view running container docker)

for example 

CONTAINER ID        IMAGE                   COMMAND                  CREATED             STATUS              PORTS                    NAMES
cefcc179a2bb        mysql:5.7               "docker-entrypoint.s…"   2 minutes ago       Up 25 seconds       0.0.0.0:3335->3306/tcp   laraveldocker-mysql
898675dde855        laraveldocker_php-fpm   "/bin/sh -c /usr/bin…"   2 minutes ago       Up 24 seconds       9000/tcp                 laraveldocker-php-fpm
f9feb704a29d        nginx:alpine            "nginx -g 'daemon of…"   2 minutes ago       Up 25 seconds       0.0.0.0:3333->80/tcp     laraveldocker-webserver


step 6:docker exec -it container_id bin/bash

for example to go in php server
       docker exec -it 898675dde855 /bin/bash




Service|Address outside containers
------|---------|-----------
Webserver|[localhost:3333](http://localhost:3333)
MySQL|**host:** `localhost`; **port:** `3335`

## Hosts within your environment ##

You'll need to configure your application to use any services you enabled:

Service|Hostname|Port number
------|---------|-----------
php-fpm|php-fpm|9000
MySQL|mysql|3306 (default)

# Docker compose cheatsheet #

**Note:** you need to cd first to where your docker-compose.yml file lives.

  * Start containers in the background: `docker-compose up -d`
  * Start containers on the foreground: `docker-compose up`. You will see a stream of logs for every container running.
  * Stop containers: `docker-compose stop`
  * Kill containers: `docker-compose kill`
  * View container logs: `docker-compose logs`
  * Execute command inside of container: `docker-compose exec SERVICE_NAME COMMAND` where `COMMAND` is whatever you want to run. Examples:
        * Shell into the PHP container, `docker-compose exec php-fpm bash`
        * Run symfony console, `docker-compose exec php-fpm bin/console`
        * Open a mysql shell, `docker-compose exec mysql mysql -uroot -pCHOSEN_ROOT_PASSWORD`
