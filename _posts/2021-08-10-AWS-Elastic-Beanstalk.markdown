---
title: "Spring Boot Web Application Deployment on AWS Elastic Beanstalk with AWS RDS"
author: anantharajuc
categories: [ Cloud, AWS, Spring Boot ]
tags: [ Cloud, AWS,  Spring Boot, featured]
layout: post
date: 2021-08-10 19:15
image: /assets/images/aws/aws-elastic-beanstalk.png
---

This post briefly documents the process of deploying a Spring Boot based web application on the AWS Elastic Beanstalk platform. This application will be connected to an AWS managed MySQL Relational Database system.

---

#### Introduction

**AWS Elastic Beanstalk** is an orchestration service offered by Amazon Web Services for deploying applications which orchestrates various AWS services, including EC2, S3, Simple Notification Service, CloudWatch, autoscaling, and Elastic Load Balancers. 

**Amazon Relational Database Service (RDS)** is a distributed relational database service by Amazon Web Services. It is a web service running "in the cloud" designed to simplify the setup, operation, and scaling of a relational database for use in applications. 

---

#### Goals

1. Amazon Relational Database Service (MySQL) Creation and Configuration  
2. AWS Beanstalk - Creating Environment  
	2.1 Create a new environment  
	2.2 Select environment tier  
	2.3 Create a web server environment  
	2.4 Environment information  
	2.5 Platform  
	2.6 Application code  
	2.7 Log  
3. Edit inbound rules for the web app deployed on Elastic Beanstalk to access the Database  
4. Environment Overview  
	4.1 Environment setup complete  
	4.2 Application  
	4.3 Configuration  
	4.4 Monitoring  
	4.5 Events  
5. Output
	5.1 Web Page  
	5.2 API Endpoint  
	5.3 API In Action  
6. Cleanup  
	6.1 Terminate Environment  
	6.2 Confirm Environment Termination  
		
--- 

##### **`Minimum Requirements`**

- Access to [AWS Management Console](https://aws.amazon.com/console/)

---

##### **`Sample Project`**

[Spring Boot Minimal Web App](https://github.com/AnanthaRajuC/Spring-Boot-Minimal-Web-App) is the sample Spring Boot web application i've used to deploy on the AWS Elastic Beanstalk platform.

Navigate to [http://localhost:8080/](http://localhost:8080/) to discover the application URLs.

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/common/spring-boot-minimal-web-app.PNG" /></div>

Find details on how to build an executable jar [here](https://github.com/AnanthaRajuC/Spring-Boot-Minimal-Web-App/blob/main/documents/INSTALLATION.MD#building-the-jar).

In the **`application.properties`** file present in the **resources** folder, set the **`spring.profiles.active`** value to **mysql-aws**.

In the **`application-mysql-aws.properties`** file, set the **`server.port`** value to **5000**. Also, set the **`aws.rds.database.endpoint`** value in the same file to the database endpoint generated after following the steps in the next section.

*Noticed an issue with this Sample Project? Open an [issue](https://github.com/AnanthaRajuC/Spring-Boot-Minimal-Web-App/issues) or a [PR](https://github.com/AnanthaRajuC/Spring-Boot-Minimal-Web-App/pulls) on GitHub!*

---

##### **`Step 1 - AWS RDS MySQL Creation and Configuration`**

Refer the following post detailing the process of creating **MySQL** Database via the AWS **RDS** service. This is an essential part of the process since the sample application will be connected to a relational database.

[https://anantharajuc.github.io/AWS-RD-MySQL/](https://anantharajuc.github.io/AWS-RD-MySQL/)

---

##### **`Step 2 - AWS Beanstalk - Creating Environment`**

###### **`Step 2.1 - Create a new environment`**

![Create a new environment]({{ site.baseurl }}/assets/images/aws/aws-elastic-beanstalk/1.PNG) 

---

###### **`Step 2.2 - Select environment tier`**

![Select environment tier]({{ site.baseurl }}/assets/images/aws/aws-elastic-beanstalk/2.PNG) 

---

###### **`Step 2.3 - Create a web server environment`**

![create a web server environment]({{ site.baseurl }}/assets/images/aws/aws-elastic-beanstalk/3.PNG) 

---

###### **`Step 2.4 - Environment information`**

![Environment information]({{ site.baseurl }}/assets/images/aws/aws-elastic-beanstalk/4.PNG) 

---

###### **`Step 2.5 - Platform`**

![Platform]({{ site.baseurl }}/assets/images/aws/aws-elastic-beanstalk/5.PNG) 

---

###### **`Step 2.6 - Application code`**

![Application code]({{ site.baseurl }}/assets/images/aws/aws-elastic-beanstalk/6.PNG) 

---

###### **`Step 2.7 - Log`**

![Log]({{ site.baseurl }}/assets/images/aws/aws-elastic-beanstalk/7.PNG) 

---

##### **`Step 3 - Edit inbound rules for the web app deployed on Elastic Beanstalk to access the Database`**

###### **`Edit inbound rules`**

![Edit inbound rules]({{ site.baseurl }}/assets/images/aws/aws-elastic-beanstalk/12.PNG) 

---

##### **`Environment Overview`**

###### **`Step 4 - Environment setup complete`**

![Environment setup complete]({{ site.baseurl }}/assets/images/aws/aws-elastic-beanstalk/8.PNG) 

---

###### **`Step 4.1 - Application`**

![Application]({{ site.baseurl }}/assets/images/aws/aws-elastic-beanstalk/16.PNG) 

---

###### **`Step 4.2 - Configuration`**

![Configuration]({{ site.baseurl }}/assets/images/aws/aws-elastic-beanstalk/17.PNG) 

---

###### **`Step 4.3 - Monitoring`**

![Monitoring]({{ site.baseurl }}/assets/images/aws/aws-elastic-beanstalk/20.PNG) 

---

###### **`Step 4.4 - Events`**

![Monitoring]({{ site.baseurl }}/assets/images/aws/aws-elastic-beanstalk/23.PNG) 

---

##### **`Step 5 - Output`**

###### **`Step 5.1 - Web Page`**

![Log]({{ site.baseurl }}/assets/images/aws/aws-elastic-beanstalk/10.PNG) 

---

###### **`Step 5.2 - API Endpoint`**

![Log]({{ site.baseurl }}/assets/images/aws/aws-elastic-beanstalk/9.PNG) 

---

###### **`Step 5.3 - API In Action`**

![Log]({{ site.baseurl }}/assets/images/aws/aws-elastic-beanstalk/11.PNG) 

---

##### **`Step 6 - Cleanup`**

###### **`Step 6.1 - Terminate Environment`**

![Terminate Environment]({{ site.baseurl }}/assets/images/aws/aws-elastic-beanstalk/24.png) 

---

###### **`Step 6.2 - Confirm Environment Termination`**

![Terminate Environment]({{ site.baseurl }}/assets/images/aws/aws-elastic-beanstalk/25.PNG) 

---












