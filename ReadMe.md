Docker Compose:
===============

Docker Compose is used for creating a multicontainer architecture.

Docker Compose files are created using yaml or yml files and they are more re-usable.

Installing Docker Compose:
===========================
1) Open this site:
    https://docs.docker.com/compose/install/
2) click on linux tab and copy & paste the commands from 1 and 2.

3) After installation check whether in your linux/windows terminal is installed properly or not:
    docker-compose --version
  -> this command will display respective version what you have installed on your system it will display.
  
Steps to Write and perform actions over docker compose:
===========================================================
To Start the containers
docker-compose up

To start the containers in detached mode
docker-compose up -d 

To stop the containers
docker-compose stop

To stop and delete the containers 
docker-compose down

To see the list of processes in the containers
docker-compose ps

To start the stopped container
docker-compose start

To pause the excuting 
docker-compose pause

To unpause
docker-compose unpause


1) To run the files which I uploaded here the format is :
   
   Syntax:
      docker-compose -f filename up -d
   
   - filename: you can give in which file you saved the docker-compose activity that file name should give over therr.
   
   - in my case i given like this compose1.yml
      
      eg: docker-compose -f compose1.yml up -d

2) To start the environment in detached mode:
    
    docker-compose -f compose1.yml up -d
    
3) To stop the environment:
    
    docker-compose -f compose1.yml stop -d
    
4) To delete the enviroment:
    
    docker-compose -f compose1.yml down -d


Usecase-1:

create a docker compose file for setting up a wordpress container and link with a mysql container

---
services:
 mydb:
  image: mysql:5
  environment:
   MYSQL_ROOT_PASSWORD: chaithu

 mywordpress:
  image: wordpress
  ports:
   - 9999:80
  links:
   - mydb:mysql
...


Usecase-2:
Create a docker compose file for setting up the CI-CD environment
where a jenkins container is linked with 2 tomcat containers
vim docker-compose.yml or nano docker-compose.yml
---
version: '3'

services:
 jenkinsserver:
  image: jenkins
  ports:
   - 5050:8080

 qaserver:
  image: tomcat
  ports:
   - 6060:8080
  links:
   - jenkinsserver:jenkins

 prodserver:
  image: tomcat
  ports:
   - 7070:8080
  links:
   - jenkinsserver:jenkins
...

usecase-3:
Create a Docker compose file to setup the LAMP Environment:
vim docker-compose.yml
---
version: '3'

services:
 mydb:
  image: mysql:5
  environment:
   MYSQL_ROOT_PASSWORD: chaithaya

 apache:
  image: httpd
  ports:
   - 9090:80
  links:
   - mydb:mysql

 php:
  image: php:7.2-apache
  links:
   - mydb:mysql
   - apache:httpd

...

usecase-4:
create a docker compose file to setup the selenium testing environment where a selenium
hub container should be linked with chrome and firefox node containers.

---
version: '3'

services:
 hub:
  image: selenium/hub
  ports:
   - 4444:4444
 
 chrome:
  image: selenium/node-chrome-debug
  ports:
   - 5901:5900
  links:
   - hub:selenium
   
 firefox:
  image: selenium/node-firefox-debug
  ports:
   - 5902:5900
  links:
   - hub:selenium

...
