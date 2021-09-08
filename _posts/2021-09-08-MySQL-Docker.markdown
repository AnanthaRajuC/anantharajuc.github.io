---
title: "MySQL Docker Image"
author: anantharajuc
categories: [ Docker, MySQL ]
tags: [ Docker, MySQL ]
layout: post
date: 2021-09-08 15:20
image: /assets/images/docker-mysql.jpg
---

This post briefly documents the process of pulling a [MySQL](https://hub.docker.com/_/mysql) [Docker](https://www.docker.com/) image from [docker hub](https://hub.docker.com/) and running few basic commands to interact with it.

---

#### Minimum Requirements

- [Docker](https://www.docker.com/)

---

#### Setup

Start your local Docker Instance if necessary.

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/docker-mysql/1.PNG" /></div>    

Check if you already have any existing MySQL images locally.  

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/docker-mysql/2.PNG" /></div>    

---

#### DockerHub

Check all of the available tags that can be downloaded from this link. https://hub.docker.com/_/mysql?tab=tags  

For demonstration, i'll be using the **8.0.26** version of MySQL.   

**`docker pull mysql:8.0.26`**  
Pull a MySQL Docker Image  

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/docker-mysql/3.PNG" /></div>    

**`docker images`**  
Check if the MySQL Docker image has been successfully pulled.  

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/docker-mysql/4.PNG" /></div>    

---

#### Run the MySQL Docker Image

**`docker run --name mysql-docker -p 3306:3306 -e MYSQL_ROOT_PASSWORD=password -e MYSQL_DATABASE=sbat -e MYSQL_USER=sbat -e MYSQL_PASSWORD=sbat -d mysql:8.0.26`**  
Run the MySQL docker image.  

In the above command, the following parameters can be configured as per your need.

|  Parameter           |   Example Value            |
|----------------------|----------------------------|
|`--name`              | *mysql-docker*             |
|`-p`                  | *3306:3306* (Ports expose) |
|`MYSQL_ROOT_PASSWORD` | *password*                 |
|`MYSQL_DATABASE`      | *sbat*                     |
|`MYSQL_USER`          | *sbat*                     |
|`MYSQL_PASSWORD`      | *sbat*                     |

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/docker-mysql/5.PNG" /></div>    

**`docker ps`**  
List all the running containers to check if your image is running.

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/docker-mysql/6.PNG" /></div>    

---

#### Connect to the Database via CLI

**`docker exec -it mysql-docker mysql -u sbat -p sbat`**  
Connect to MySQL image via interactive CLI.  

In the above command, the following parameters are set as configured in the previous step.

|  Parameter |   Example Value  |
|------------|------------------|
|`-u`        | *sbat*           |
|`-p`        | *sbat*           |

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/docker-mysql/7.PNG" /></div>    

Other ways to connect to the Database docker image.

|                   Command                                             |         Description                            |
|-----------------------------------------------------------------------|------------------------------------------------| 
|`docker exec mysql-docker mysql -usbat -psbat -e 'show databases;'`	| connect to MySQL image without interactive CLI.|
|`docker exec -it mysql-docker mysql -usbat -psbat -e 'show databases;'`| connect to MySQL image without interactive CLI.|

---

#### Interacting with the MySQL Database via CLI

**`show databases;`**  
Lists the databases on the MySQL server host.  

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/docker-mysql/8.PNG" /></div>    

**`show schemas;`**  
A synonym for `show databases;`  

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/docker-mysql/9.PNG" /></div>    

**`use [database_name];`**  
Select any existing database in the SQL schema.  

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/docker-mysql/10.PNG" /></div>    

**`show tables;`**  
List tables in a Database.  

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/docker-mysql/11.PNG" /></div>    

**`exit`**  
Quit MySQL shell.

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/docker-mysql/12.PNG" /></div>    

---

#### Interacting with the MySQL Database via CLI

Connect to the DB by entering the following details in MySQL Workbench.  

|  Key             |   Value                                                                                                      |
|------------------|--------------------------------------------------------------------------------------------------------------|
|*Connection Name* | *Any name of your choice*                                                                                    |
|*Hostname*        | *192.168.99.102* (use `docker-machine ip` to find your Docker Toolbox IP address. usually **192.168.99.102**)|
|*Username*        | *sbat*                                                                                                       | 
|*Password*        | *sbat*                                                                                                       | 

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/docker-mysql/17.PNG" /></div>    

---

#### Cleanup

**`docker stop [container_id]`**  
Stop the container.

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/docker-mysql/13.PNG" /></div>    

**`docker ps -a`**  
List all the containers, including the ones that have finished executing to check if your container has been stopped.

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/docker-mysql/16.PNG" /></div>  

**`docker rm [container_name]`**  
Remove the container.

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/docker-mysql/14.PNG" /></div>    

**`docker ps -a`**  
List all the containers, including the ones that have finished executing to check if your container has been stopped and removed. There wont be any containers listed now.

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/docker-mysql/15.PNG" /></div>    

---


