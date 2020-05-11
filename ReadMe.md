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

