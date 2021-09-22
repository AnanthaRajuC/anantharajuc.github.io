---
title: "Pushing Docker Image from local machine to Amazon Elastic Container Registry Repositories"
author: anantharajuc
categories: [ Docker, AWS ]
tags: [ Docker, AWS ]
layout: post
date: 2021-09-21 18:45
image: /assets/images/aws/aws-ecs.jpg
---

This post briefly documents the process of pushing a Docker Image of a Spring Boot based Web App from local machine to [Amazon Elastic Container Registry Repositories](https://aws.amazon.com/ecr/).

---

#### Introduction

**Docker** is a set of platform as a service products that use OS-level virtualization to deliver software in packages called containers. Containers are isolated from one another and bundle their own software, libraries and configuration files; they can communicate with each other through well-defined channels.

**Amazon Elastic Container Registry (Amazon ECR)** is a fully managed container registry that makes it easy to store, manage, share, and deploy your container images and artifacts anywhere.

---

#### Goals

1. Select Elastic Container Service  
2. Create Repository  
3. Configure Repository Settings  
4. View Docker Push Commands  
5. Push the Docker Image  
6. View the pushed image & its details  

---

#### Minimum Software Requirements

- [Docker](https://www.docker.com/)  
- Access to [AWS Management Console](https://aws.amazon.com/console/)  

---

##### Getting Started 

#### Setup

Start your local Docker Instance if necessary.

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/docker-mysql/1.PNG" /></div>    

Navigate to your project folder where **Dockerfile** is present and build a Docker image of the project using the following command.

**`docker build -t YOUR_PROJECT_NAME .`**   

---

#### **`Step 1 - Select Elastic Container Service`** 

From the AWS Services, select the **Elastic Container Service** from the **Containers** section

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/aws/ecs/1.PNG" /></div>    

---

#### **`Step 2 - Create Repository`** 

On the left side navigation menu, in the **Amazon ECR** section, click on the **Repositories** option. 

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/aws/ecs/2.PNG" /></div>    

---

On the next page, click on the **Create repository** button.

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/aws/ecs/3.PNG" /></div>    

---

#### **`Step 3 - Configure Repository Settings`** 

In the **General Settings** section, choose the visibility settings for the repository to be **Private** or **Public** as per the need.

Give the repository a suitable **Name**

Click on the **Create repository** button.

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/aws/ecs/4.PNG" /></div>    

---

#### **`Step 4 - View Docker Push Commands`** 

Once, the repository is created. Click on the **View Push Commands** button made available on the top banner.

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/aws/ecs/5.PNG" /></div>    

---

As per your Operating System, copy the commands.

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/aws/ecs/6.PNG" /></div>    

---

#### **`Step 5 - Push the Docker Image`** 

execute the commands copied in the previous step in a sequential order to push the Docker image fom your local machine to **AWS ECR**.  

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/aws/ecs/7.PNG" /></div>    

#### **`Step 6 - View the pushed image & its details`** 

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/aws/ecs/8.PNG" /></div>    

---

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/aws/ecs/9.PNG" /></div>    

---

