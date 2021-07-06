---
title: "Docker and dockerhub with Maven"
author: anantharajuc
categories: [ Cloud, AWS ]
layout: post
date: 2021-07-05 20:10
image: /assets/images/maven-docker-hub.PNG
---

This post briefly documents the process of using [dockerfile-maven](https://github.com/spotify/dockerfile-maven), a Maven tool for integrating Docker build process with the Maven build process.

---

#### Minimum Requirements

- Java 7 or later 
- [Apache Maven](https://maven.apache.org/) 3 or later
- [Docker Desktop](https://www.docker.com/products/docker-desktop)
- [dockerfile-maven](https://github.com/spotify/dockerfile-maven)
- [dockerhub account](https://hub.docker.com/) (FREE) 

#### Sample Project

[Spring Boot Minimal Web App](https://github.com/AnanthaRajuC/Spring-Boot-Minimal-Web-App) is the sample Spring Boot app i've used to illustrate the usage of [dockerfile-maven](https://github.com/spotify/dockerfile-maven)

| *Method*   |    |  *URL*                                 |
|------------|----|----------------------------------------|
| **GET**    |    | **`http://localhost:8080/index.html`** |
| **GET**    |    | **`http://localhost:8080/`**           |
| **PUT**    |    | **`http://localhost:8080/`**           | 
| **POST**   |    | **`http://localhost:8080/`**           | 
| **DELETE** |    | **`http://localhost:8080/`**           |

#### Dependencies

A java project does not necessarily have any library dependency in order to create and push docker image of that project.

However, in the plugins section of the **`pom.xml`** dependency management file there must be the dockerfile-maven plugin.

~~~xml
<!--  Plugin for building and pushing Docker image to Docker Hub. -->      	        
<plugin>
	<groupId>com.spotify</groupId>
	<artifactId>dockerfile-maven-plugin</artifactId>
	<version>1.4.13</version>
	<configuration>
		<repository>YOUR_DOCKER_HUB_USERNAME/${project.artifactId}</repository>
		<tag>${project.version}</tag>
		<buildArgs>
			<JAR_FILE>target/${project.artifactId}-${project.version}.jar</JAR_FILE>
		</buildArgs>
	</configuration>
	<executions>
		<execution>
			<id>default</id>
			<phase>install</phase>
			<goals>
				<goal>build</goal>
				<goal>push</goal>
			</goals>
		</execution>
	</executions>
</plugin>  	       
~~~

*code*: [pom.xml](https://github.com/AnanthaRajuC/Spring-Boot-Minimal-Web-App/blob/main/pom.xml)

In the same **`pom.xml`** file, add the following details as well. 

~~~xml
<artifactId>spring-boot-minimal-web-app</artifactId>
<version>latest</version>
<packaging>jar</packaging>
~~~

*Note*: artifactId must be in lower case.

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

##### Docker Hub

- Create a account on Docker Hub if you don't already have one.

- Create a repository with a name matching the project's **artifactId**. For this example, the Docker Hub repository name is **spring-boot-minimal-web-app**

##### Maven

From the command line, navigate to project directory where the **pom.xml** file is present.

**`mvn install`**  
*In the execution section of the above described plugin, we have mentioned the usage of* **install** *phase with the* **build** *and* **push** goals. This will build the docker image as per the Dockerfile and push the image to the specified Docker Hub repository of the specified Docker Hub user.

---