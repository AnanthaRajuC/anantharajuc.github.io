---
title: "Amazon Web Services : Elastic Beanstalk"
author: anantharajuc
categories: [ Cloud, AWS ]
tags: [ Cloud, AWS ]
layout: post
date: 2021-08-10 19:15
image: /assets/images/aws-elastic-beanstalk.png
---

This post briefly documents the process of deploying a Spring Boot based web application on the AWS Elastic Beanstalk platform. This application will be connected to an AWS managed MySQL Relational Database system.

---

#### Minimum Requirements

- Access to [AWS Management Console](https://aws.amazon.com/console/)

---

#### Sample Project

[Spring Boot Minimal Web App](https://github.com/AnanthaRajuC/Spring-Boot-Minimal-Web-App) is the sample Spring Boot app i've used to deploy on the AWS Elastic Beanstalk platform.

---

#### AWS RDS MySQL Creation and Configuration

- Refer the following post detailing the process of creating **MySQL** Database via the AWS **RDS** service.

[https://anantharajuc.github.io/AWS-RD-MySQL/](https://anantharajuc.github.io/AWS-RD-MySQL/)

#### AWS Beanstalk - Creating Environment

##### Create a new environment

![Create a new environment]({{ site.baseurl }}/assets/images/aws-elastic-beanstalk/1.PNG) 

##### Select environment tier

![Select environment tier]({{ site.baseurl }}/assets/images/aws-elastic-beanstalk/2.PNG) 

##### create a web server environment

![create a web server environment]({{ site.baseurl }}/assets/images/aws-elastic-beanstalk/3.PNG) 

##### Environment information

![Environment information]({{ site.baseurl }}/assets/images/aws-elastic-beanstalk/4.PNG) 

##### Platform

![Platform]({{ site.baseurl }}/assets/images/aws-elastic-beanstalk/5.PNG) 

##### Application code

![Application code]({{ site.baseurl }}/assets/images/aws-elastic-beanstalk/6.PNG) 

##### Log

![Log]({{ site.baseurl }}/assets/images/aws-elastic-beanstalk/7.PNG) 

