---
title: "Docker and Docker Hub Commands"
layout: post
date: 2020-10-17 09:40
image: 
headerImage: false
tag:
- Docker
- Docker Hub
- Containers
- CLI
star: true
category: blog
author: Anantha Raju C
description: Docker and Docker Hub Commands
---

## Summary:

Docker and Docker Hub Commands

---

#### Docker Meta

|--------------------------------------------|-----------------------------------------------------------| 
|`docker-machine ip default`				 | Check your docker IP default, usually **192.168.99.102**	 |
|	 										 |		 													 |
|`docker-machine ip`                         | Find Docker Toolbox IP address, usually **192.168.99.102**|
|											 |															 |
|`docker version`                            | Displays the docker version information                   |

#### Docker Logging

|---------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------|
|`docker logs [container_id]`			                            								| List container logs                                                           	 |
|											                                                        |															                         |
|`docker logs [container_id] --tail N`                               								| List container logs, **`--tail`** flag will show the last **N** lines of logs 	 |   
|											                                                        |															                         |
|`docker logs [container_id] --since YYYY-MM-DD`                     								| List container logs since a particular date                                   	 |
|											                                                        |															                         |
|`docker logs [container_id] --since YYYY-MM-DDTHH:MM:SS.000000000Z` 								| List container logs since a particular timestamp                              	 |
|											                                                        |															                         |
|`docker logs -f [container_id]`                                                                    | Look at the logs of a container                                               	 |
|											                                                        |															                         |
|`docker inspect [container_id]`                                                                    | Examine a container's metadata in Docker                                      	 |
|											                                                        |															                         |
|`docker inspect --format='{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' [container_id]`| Use --format to inspect specific fields from the returned container's metadata JSON| 

#### Docker Stats

|--------------------------------------------------------------------|-------------------------------------------------------------------------------|
|`docker stats`							                             | Show CPU and memory usage of all running containers                 	         |
|											                         |															                     |
|`docker stats [container_name]`						             | Show CPU and memory usage of a particular running container                   |
|											                         |															                     |
|`docker stats [container1_name] [container2_name]`			         | Show CPU and memory usage of container1, container2                           |
|											                         |															                     |
|`docker top [container_name]`			                             | Show running processes in a container                                         |
|											                         |															                     |
|`docker system df`			                                         | Show storage usage                                                            |

#### Docker Basic Queries

|-------------------------------|--------------------------------------------------------------------------|
|`docker images`                | Take a look at the container images.                                     |
|								|															               |
|`docker image ls`              | Take a look at the container images.                                     |
|								|															               |
|`docker ps`                    | List all the running containers.                                         |
|								|															               |
|`docker ps -a`                 | List all the containers, including the ones that have finished executing.|

#### Docker  Container State Change 

|-----------------------------------|---------------------------------|
|`docker run [container_name]`      | Run a container.                |
|								    |								  |
|`docker stop [container_id]`   	| Stop a container                |
|								    |								  |
|`docker restart [container_name]`  | Restart a container.            |

#### Docker Management

|------------------------------------------|-------------------------------------------------------------------|
|`docker build -t [project name] .`        | Build a Docker Image                                              |
|								           |								                                   |
|`docker run -p 8080:8080 [container_name]`| Run a container by mapping a port on docker to a port on localhost|
|								           |								                                   |
|`docker rm [container_name]`              | Remove a container with a particular container name               |
|								           |								                                   |
|`docker rm $(docker ps -aq)`              | Stop and remove all containers                                    |

#### MySQL Docker Container - Connecting to the MySQL docker image via CLI  

|------------------------------------------------------------------------|------------------------------------------------| 
|`docker exec mysql-docker mysql -usbat -psbat -e 'show databases;'`	 | Connect to MySQL image without interactive CLI.|	
|								                                         |								                  |											|
|`docker exec -it mysql-docker mysql -usbat -psbat -e 'show databases;'` | Connect to MySQL image without interactive CLI.|
|								                                         |								                  |														|
|`docker exec -it mysql-docker mysql -usbat -psbat`						 | Connect to MySQL image via interactive CLI.	  |													|

#### Docker Hub

|--------------------------------------------------------------------|-------------------------------------------------------------------| 
|`docker pull [container_name]`							             | Logout a Docker image from Docker Hub                             |
|                                                                    |                                                                   |
|`docker logout`							                         | Logout of Docker Hub from the local machine.                      |
|                                                                    |                                                                   |
|`docker login --username=YOUR_DOCKERHUB_USERNAME`	                 | Login to Docker Hub from your machine.                            |
|                                                                    |                                                                   |
|`docker tag <existing-image> <hub-user>/<repo-name>[:<tag>]`        | Re-tagging an existing local image					             |
|                                                                    |                                                                   |
|`docker commit <existing-container> <hub-user>/<repo-name>[:<tag>]` | Commit changes					                                 |
|                                                                    |                                                                   |
|`docker push <hub-user>/<repo-name>:<tag>`                          | Push this repository to the registry designated by its name or tag|