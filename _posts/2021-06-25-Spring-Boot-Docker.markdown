---
title: "Spring Boot Application Containerization with Docker"
author: anantharajuc
categories: [ Spring Boot, Docker ]
tags: [ Spring Boot, Docker ]
layout: post
date: 2021-06-25 17:30
image: /assets/images/spring-boot-docker.jpg
---

This post briefly documents the creation of a [Docker](https://www.docker.com/) image from a [Spring Boot](https://spring.io/projects/spring-boot) based Java (Web Application) project.

---

#### Minimum Software Requirements

- Java
- [Maven](https://maven.apache.org/)
- [Docker Desktop](https://www.docker.com/products/docker-desktop)
- [Oracle VM VirtualBox](https://www.virtualbox.org/) or any other [hypervisor](https://en.wikipedia.org/wiki/Hypervisor)
- [Postman](https://www.postman.com/downloads/)

#### Sample Project

[Spring Boot Minimal Web App](https://github.com/AnanthaRajuC/Spring-Boot-Minimal-Web-App) is the sample Spring Boot app i've used to illustrate the creation and usage of the created docker image.

#### Dependencies

A java project does not necessarily have any library dependency in order to create a docker image of that project.

However, in the plugins section of the **`pom.xml`** dependency management file there must be a plugin to package the project as an executable **jar**/**war** file.

~~~xml
<!-- Package as an executable jar/war. -->
<plugin>
	<groupId>org.springframework.boot</groupId>
	<artifactId>spring-boot-maven-plugin</artifactId>
</plugin>
~~~

In the same **`pom.xml`** file, add the following details as well.

~~~xml
<version>latest</version>
<packaging>jar</packaging>
~~~

#### Basic Usage

Create a file named **`Dockerfile`** in the root of your project with the following details.

~~~txt
# Start with a base image containing Java runtime
FROM openjdk:8-jdk-alpine

# Add Maintainer Info
LABEL maintainer="example@domain.com"

# Add a volume pointing to /tmp
VOLUME /tmp

# Make port 8080 available to the world outside this container
EXPOSE 8080

# The application's jar file
ARG JAR_FILE=target/Spring-Boot-Minimal-Web-App-latest.jar

# Add the application's jar to the container
ADD ${JAR_FILE} Spring-Boot-Minimal-Web-App-latest.jar

# Run the jar file 
ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-jar","/Spring-Boot-Minimal-Web-App-latest.jar"]
~~~

*code*: [Dockerfile](https://github.com/AnanthaRajuC/Spring-Boot-Minimal-Web-App/blob/main/Dockerfile)

##### Maven

From the command line, navigate to project directory where the **pom.xml** file is present.

**`mvn clean`**  
*Clean the project and remove the files from the previous build.*

![Docker Build Image]({{ site.baseurl }}/assets/images/spring-boot-docker/mvn/1-clean.PNG)  

**`mvn validate`**  
*Check if all the information necessary for the build (**.jar**) are available.*

![Docker Build Image]({{ site.baseurl }}/assets/images/spring-boot-docker/mvn/2-validate.PNG)  

**`mvn package`**  
*Runs all the tests and packages/builds the project to a **.jar** file.*

**`mvn package -Dmaven.test.skip=true`**  
*To skip the tests and package/build the project directly.*

The above mentioned **.jar** file is present inside the **/target** directory.

##### Docker

##### Build 

**`docker images`**  
*Lists the already present container images.*

**`docker build -t spring-boot-minimal-web-app .`**  
*Builds the docker image of the project as per the specifications mentioned in the **Dockerfile** file.*

![Docker Build Image]({{ site.baseurl }}/assets/images/spring-boot-docker/1-docker-build.PNG)  

**`docker images`**  
*Check the docker image is generated from running the previous command.*

![List Docker Images]({{ site.baseurl }}/assets/images/spring-boot-docker/2-docker-image-list.PNG)  

**`docker inspect spring-boot-minimal-web-app`**  
*Inspect an image.*

![Inspect Docker Image]({{ site.baseurl }}/assets/images/spring-boot-docker/inspect.PNG)  

##### Run, Stop and Restart

**`docker run -p 8080:8080 --name spring-boot-minimal-web-app spring-boot-minimal-web-app`**  
*Run the newly created docker image.*

![Docker Run]({{ site.baseurl }}/assets/images/spring-boot-docker/3-docker-run.PNG)  

**`docker ps`**  
*List all the running containers.*

![List Running Containers]({{ site.baseurl }}/assets/images/spring-boot-docker/list-running-containers.PNG)  

**`docker top spring-boot-minimal-web-app`**  
*Show running processes in a container.*

![Docker Top]({{ site.baseurl }}/assets/images/spring-boot-docker/docker-top.PNG) 

**`docker stats spring-boot-minimal-web-app`**  
*Show CPU and memory usage of the running container.*

![Docker Stats]({{ site.baseurl }}/assets/images/spring-boot-docker/docker-stats.PNG) 

**`docker stop spring-boot-minimal-web-app`**  
*Stop the container of the image.*

![Stop Docker Container]({{ site.baseurl }}/assets/images/spring-boot-docker/6-stop-running-docker-container.PNG)  

**`docker ps -a`**  
*List all the containers, including the ones that have finished executing.*

![List running and stopped containers]({{ site.baseurl }}/assets/images/spring-boot-docker/list-stopped-containers.PNG)  

**`docker restart spring-boot-minimal-web-app`**  
*Restart the stopped container of the image.*

![Restart Docker Container]({{ site.baseurl }}/assets/images/spring-boot-docker/9-docker-container-restart.PNG)  

##### Logs

**`docker logs spring-boot-minimal-web-app`**  
*Lists container logs.*

![Docker Logs]({{ site.baseurl }}/assets/images/spring-boot-docker/docker-logs.PNG)  

**`docker logs spring-boot-minimal-web-app --tail N`**  
*Lists container logs. **--tail** flag will show the last **N** lines of logs.*

![Docker Logs with tail]({{ site.baseurl }}/assets/images/spring-boot-docker/docker-logs-tail.PNG)  

**`docker logs spring-boot-minimal-web-app --since YYYY-MM-DD`**  
*List container logs since a particular date.*

![Docker Logs with date]({{ site.baseurl }}/assets/images/spring-boot-docker/docker-logs-date.PNG) 

##### DockerHub

**`docker login --username=YOUR_DOCKERHUB_USERNAME`**  
*Login to Docker Hub from your machine.*

**`docker tag spring-boot-minimal-web-app anantha/spring-boot-minimal-web-app:latest`**  
*Re-tagging an existing local image to push to dockerhub.*

![Docker re-tag Existing Image]({{ site.baseurl }}/assets/images/spring-boot-docker/image-tagging.PNG)  

**`docker push anantha/spring-boot-minimal-web-app:latest`**  
*Push this repository to the registry designated by its name or tag.*

![Docker Push Image]({{ site.baseurl }}/assets/images/spring-boot-docker/docker-hub-push.PNG)  

##### Clean-up

After cleaning up your machine of the said container and the image. To start over repeat the steps mentioned from the build section.

**`docker rm spring-boot-minimal-web-app`**  
*Remove the docker container.*

![Remove Docker Container]({{ site.baseurl }}/assets/images/spring-boot-docker/4-remove-docker-container.PNG)  

**`docker image rm spring-boot-minimal-web-app`**  
*Remove the docker image.*

![Remove Docker Image]({{ site.baseurl }}/assets/images/spring-boot-docker/3-remove-docker-image.PNG)  

---


