---
title: "Docker and DockerHub integration with Maven build process"
author: anantharajuc
categories: [ Docker, Docker Hub, Maven ]
tags: [ Docker, Docker Hub, Maven ]
layout: post
date: 2021-07-05 20:10
image: /assets/images/maven-docker-hub.png
---

This post briefly documents the process of using [dockerfile-maven](https://github.com/spotify/dockerfile-maven), a Maven tool for integrating Docker build process with the Maven build process. Here we use the aforementioned plugin to build and push docker images from local development environment/machine to DockerHub.

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/maven-docker-hub/illustration.png" /></div>

---

#### Minimum Requirements

- Java 7 or later 
- [Apache Maven](https://maven.apache.org/) 3 or later
- [Docker Desktop](https://www.docker.com/products/docker-desktop)
- [dockerfile-maven](https://github.com/spotify/dockerfile-maven)
- [dockerhub account](https://hub.docker.com/) (FREE) 

#### Sample Project

[Spring Boot Minimal Web App](https://github.com/AnanthaRajuC/Spring-Boot-Minimal-Web-App) is the sample Spring Boot web application i've used to illustrate the usage of [dockerfile-maven](https://github.com/spotify/dockerfile-maven)

Navigate to [http://localhost:8080/](http://localhost:8080/) to discover the application URLs.

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/common/spring-boot-minimal-web-app.PNG" /></div>

#### Dependencies

A java project does not necessarily have any library dependency in order to create and push docker image of that project.

However, in the plugins section of the **`pom.xml`** dependency management file there must be the [dockerfile-maven plugin](https://github.com/spotify/dockerfile-maven).

<script src="https://gist.github.com/AnanthaRajuC/3d29af2443cb258798e9c660418d0a6a.js"></script>

*Reference code*: [pom.xml](https://github.com/AnanthaRajuC/Spring-Boot-Minimal-Web-App/blob/main/pom.xml)

In the same **`pom.xml`** file, add the following details as well. 

~~~xml
<artifactId>spring-boot-minimal-web-app</artifactId>
<version>latest</version>
<packaging>jar</packaging>
~~~

*Note*: **artifactId** must be in lower case and must match the repository name created on Docker Hub.

Ensure that you are able to package the project into an executable jar. If there's an issue at this step, make sure you have the following plugin in your pom.xml file to build the project.

~~~xml
<!-- Package as an executable jar/war. -->
<plugin>
	<groupId>org.springframework.boot</groupId>
	<artifactId>spring-boot-maven-plugin</artifactId>
</plugin>
~~~

#### Basic Usage

Create a file named **`Dockerfile`** in the root of your project with the following details.

<script src="https://gist.github.com/AnanthaRajuC/cb8ff191f322dd8d2220a2f2cb870fbc.js"></script>

*Reference code*: [Dockerfile](https://github.com/AnanthaRajuC/Spring-Boot-Minimal-Web-App/blob/main/Dockerfile)

##### Docker Hub

- Create a account on [Docker Hub](https://hub.docker.com/) if you don't already have one.

- Create a repository with a name matching the project's **artifactId**. For this example, the Docker Hub repository name is **spring-boot-minimal-web-app**  

*Note*: DockerHub repository name supports only lower case letters and the _ character

**Important**: Authenticate your machine for pushing images to dockerhub

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/maven-docker-hub/docker-login.PNG" /></div>

[docker login documentation](https://docs.docker.com/engine/reference/commandline/login/)

##### Maven

From the command line, navigate to project directory where the **pom.xml** file is present.

**`mvn install`**  
*In the execution section of the above described plugin, we have mentioned the usage of* **install** *phase with the* **build** *and* **push** *goals. This will run the tests, build the jar file, build the docker image as per the Dockerfile and push the image to the specified [Docker Hub Repository](https://hub.docker.com/r/anantha/spring-boot-minimal-web-app) of the specified [Docker Hub User](https://hub.docker.com/u/anantha).*

This step will club multiple other steps into a single step and ease the entire process.

![MVN Install]({{ site.baseurl }}/assets/images/maven-docker-hub/1-mvn-install.PNG)  

![MVN Tests]({{ site.baseurl }}/assets/images/maven-docker-hub/2-mvn-tests.PNG)  

![MVN Dockerfile]({{ site.baseurl }}/assets/images/maven-docker-hub/3-mvn-dockerfile.PNG)  

![MVN Dockerfile Push]({{ site.baseurl }}/assets/images/maven-docker-hub/4-mvn-dockerfile-push.PNG)  

---