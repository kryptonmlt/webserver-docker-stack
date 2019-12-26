# webserver-docker-stack

* 2 docker images
* db - based on mariadb
* web - apache is the main entrypoint which runs php (7.3) through a php-fpm socket
* src/html - contains the website which is added as a docker volume

## Note
* currently src/html contains wordpres 5.3.2 as an example of a working site