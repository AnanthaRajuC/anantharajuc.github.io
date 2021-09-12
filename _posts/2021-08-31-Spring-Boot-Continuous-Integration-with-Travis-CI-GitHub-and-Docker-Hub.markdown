---
title: "Spring Boot Application Continuous Delivery with Travis CI, GitHub and Docker Hub"
author: anantharajuc
categories: [ CI, Spring Boot, Travis CI, GitHub, Docker Hub, Continuous Delivery ]
tags: [ CI, Spring Boot, Travis CI, GitHub, Docker Hub, Continuous Delivery ]
layout: post
date: 2021-08-31 10:50
image: /assets/images/spring-boot-github-travis-ci.jpg
---

This post briefly captures the process of triggering a Spring Boot application docker image build using Travis CI and pushing the Docker image to Docker Hub when code is pushed from development machine to GitHub.

---

#### Goals

1. Developer pushes code to GitHub
2. Job is triggered in Travis CI  
3. Travis CI builds Docker Image and pushes to Docker Hub  
	
<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/travis-ci-dockerhhub/continuous-delivery-with-travis-ci-architecture.png" /></div>  
	
---

#### Minimum Software Requirements

- Java
- Maven
- [GitHub account](https://github.com/) (FREE) 
- [Travis CI account](https://www.travis-ci.com/) (FREE) 
- [dockerhub account](https://hub.docker.com/) (FREE) 

---

#### Introduction

**GitHub** is a provider of Internet hosting for software development and version control using Git. It offers the distributed version control and source code management functionality of Git, plus its own features.

**Travis CI** is a hosted continuous integration service used to build and test software projects hosted on GitHub and Bitbucket.

**Docker Hub** Docker Hub is a service provided by Docker for finding and sharing container images with your team. It is the world’s largest repository of container images with an array of content sources including container community developers, open source projects and independent software vendors (ISV) building and distributing their code in containers.

---

#### **`Sample Project`**

[Spring Boot Minimal Web App](https://github.com/AnanthaRajuC/Spring-Boot-Minimal-Web-App) is the sample Spring Boot web application i've used to illustrate Integration Testing.  

Navigate to [http://localhost:8080/](http://localhost:8080/) to discover the application URLs.  

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/common/spring-boot-minimal-web-app.PNG" /></div>  

In the **`application.properties`** file present in the **resources** folder, set the **`spring.profiles.active`** value to **application-h2db** since we will be running the tests before initiating the build process which is dependent on all the tests passing.  

*Note*: **`mvn package -Dmaven.test.skip=true`** Command to build the project by skipping all tests.

*Noticed an issue with this Sample Project? Open an [issue](https://github.com/AnanthaRajuC/Spring-Boot-Minimal-Web-App/issues) or a [PR](https://github.com/AnanthaRajuC/Spring-Boot-Minimal-Web-App/pulls) on GitHub!*

---

#### **`Step 1 - Add Dockerfile file to the project.`**

<script src="https://gist.github.com/AnanthaRajuC/cb8ff191f322dd8d2220a2f2cb870fbc.js"></script>

#### **`Step 2 - Add .travis.yml file to the project.`**  

<script src="https://gist.github.com/AnanthaRajuC/1a3588a49b06b4623c793001913c557c.js"></script>

#### **`Step 3 - Generate Access Token from Docker Hub`**  

In the **`Security`** section of your Docker Hub account **`Settings`** page, click on the **`New Access Token`** button to generate a new access token with **`Read`**, **`Write`**, **`Delete`** scope. If you prefer using an existing access token, use it.

*Note* : This access token will be used as the value for the *DOCKER_PASS* **`Environment Variables`** key.

*Reference* : [https://docs.docker.com/docker-hub/access-tokens/#create-an-access-token](https://docs.docker.com/docker-hub/access-tokens/#create-an-access-token)

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/travis-ci-dockerhhub/6-docker-hub-access-token.png" /></div>

#### **`Step 4 - Activate GitHub Repository in Travis CI`**  

Login to [https://app.travis-ci.com](https://app.travis-ci.com) and activate the repository of interest.

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/travis-ci-dockerhhub/1-travis-ci-login.png" /></div>

Approve & Install Travis CI on the selected repository.

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/travis-ci-dockerhhub/2-github-approve-install-travis-ci.png" /></div>

Confirm  Travis CI installation by entering the GitHub account password.

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/travis-ci-dockerhhub/3-confirm-access.png" /></div>

In Travis CI dashboard, under the repositories tab click on the settings button associated with the repository.

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/travis-ci-dockerhhub/4-repositories.png" /></div>

In the **`Environment Variables`** section of **`Settings`** tab of the selected repository, add Docker Hub user details.

*DOCKER_USER* : *YOUR_DOCKER_HUB_USERNAME*  
*DOCKER_PASS* : *YOUR_DOCKER_HUB_ACCESS_TOKEN*  

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/travis-ci-dockerhhub/5-docker-hub-credentials.png" /></div>

#### **`Step 5 - Push Code to GitHub`**  

Now that we've configured the sample Spring Boot Application with necessary files (Dockerfile, .travis.yml) and the required services (Travis CI, Docker Hub) with necessary environment variables and access tokens, we can push the code changes from our local development machine to our remote GitHub repository. 

```shell
git push origin main
```

#### **`Outcome: Travis CI`**  

We can now expect travis ci to run the tests, build the docker image of the application and push the same to dockerhub.

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/travis-ci-dockerhhub/7-travis-ci-job-status.png" /></div>

#### **`Outcome: Docker Hub`**  

Finally, the lastest docker image of the application must be present in your docker hub registry.

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/travis-ci-dockerhhub/8-docker-hub-image.PNG" /></div>

---
