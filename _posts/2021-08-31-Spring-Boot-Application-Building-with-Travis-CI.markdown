---
title: "Spring Boot Application Building from GitHub with Travis CI"
author: anantharajuc
categories: [ CI, Spring Boot, Travis CI, GitHub, Docker Hub ]
tags: [ CI, Spring Boot, Travis CI, GitHub, Docker Hub ]
layout: post
date: 2021-08-31 10:50
image: /assets/images/spring-boot-github-travis-ci.jpg
---

This post briefly captures the process of triggering a Spring Boot application docker image build using Travis CI and pushing the Docker image to Docker Hub when code is pushed from development machine to GitHub.

---

#### Minimum Software Requirements

- Java
- [GitHub account](https://github.com/) (FREE) 
- [Travis CI account](https://www.travis-ci.com/) (FREE) 
- [dockerhub account](https://hub.docker.com/) (FREE) 

---

#### **`Sample Project`**

[Spring Boot Minimal Web App](https://github.com/AnanthaRajuC/Spring-Boot-Minimal-Web-App) is the sample Spring Boot web application i've used to illustrate Integration Testing.  

Navigate to [http://localhost:8080/](http://localhost:8080/) to discover the application URLs.  

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/common/spring-boot-minimal-web-app.PNG" /></div>  

In the **`application.properties`** file present in the **resources** folder, set the **`spring.profiles.active`** value to **application-h2db**.  

---
