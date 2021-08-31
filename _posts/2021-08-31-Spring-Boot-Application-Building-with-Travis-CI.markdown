---
title: "Spring Boot Application Docker Image Building & Pushing to Docker Hub from GitHub code push trigger with Travis CI"
author: anantharajuc
categories: [ CI, Spring Boot, Travis CI, GitHub, Docker Hub ]
tags: [ CI, Spring Boot, Travis CI, GitHub, Docker Hub ]
layout: post
date: 2021-08-31 10:50
image: /assets/images/spring-boot-github-travis-ci.jpg
---

This post briefly captures the process of triggering a Spring Boot application docker image build using Travis CI and pushing the Docker image to Docker Hub when code is pushed from development machine to GitHub.

1. Developer pushes code to GitHub
2. Job is triggered in Travis CI  
	2.1 Travis CI builds Docker Image and pushes to Docker Hub  

---

#### Minimum Software Requirements

- Java
- Maven
- [GitHub account](https://github.com/) (FREE) 
- [Travis CI account](https://www.travis-ci.com/) (FREE) 
- [dockerhub account](https://hub.docker.com/) (FREE) 

---

#### **`Sample Project`**

[Spring Boot Minimal Web App](https://github.com/AnanthaRajuC/Spring-Boot-Minimal-Web-App) is the sample Spring Boot web application i've used to illustrate Integration Testing.  

Navigate to [http://localhost:8080/](http://localhost:8080/) to discover the application URLs.  

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/common/spring-boot-minimal-web-app.PNG" /></div>  

In the **`application.properties`** file present in the **resources** folder, set the **`spring.profiles.active`** value to **application-h2db** since we will be running the tests before initiating the build process which is dependent on all the tests passing.  

*Note*: **`mvn package -Dmaven.test.skip=true`** Command to build the project by skipping all tests.

---

#### **`Dockerfile`**

Add a a **`Dockerfile`** file to the project.

<script src="https://gist.github.com/AnanthaRajuC/cb8ff191f322dd8d2220a2f2cb870fbc.js"></script>

#### **`.travis.yml`**

Add a **`.travis.yml`** file to the project.

<script src="https://gist.github.com/AnanthaRajuC/1a3588a49b06b4623c793001913c557c.js"></script>

#### **`Travis CI`**

Login to (https://app.travis-ci.com)[https://app.travis-ci.com] and activate the repository of interest.

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/travis-ci-dockerhhub/1-travis-ci-login.PNG" /></div>

Approve & Install Travis CI on the selected repository.

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/travis-ci-dockerhhub/2-github-approve-install-travis-ci.PNG" /></div>

Confirm  Travis CI installation by entering the GitHub account password.

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/travis-ci-dockerhhub/3-confirm-access.PNG" /></div>

In Travis CI dashboard, under the repositories tab click on the settings button associated with the repository.

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/travis-ci-dockerhhub/4-repositories.PNG" /></div>

In the **`Environment Variables`** section of **`Settings`** tab of the selected repository, add Docker Hub user details.

-	`DOCKER_USER` : `YOUR_DOCKER_HUB_USERNAME`  
-	`DOCKER_PASS` : `YOUR_DOCKER_HUB_ACCESS_TOKEN`  

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/travis-ci-dockerhhub/5-docker-hub-credentials.PNG" /></div>










