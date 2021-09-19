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

##### **`AWS RDS MySQL Creation and Configuration`**

Refer the following post detailing the process of creating **MySQL** Database via the AWS **RDS** service. This is an essential part of the process since the sample application will be connected to a relational database.

[https://anantharajuc.github.io/AWS-RD-MySQL/](https://anantharajuc.github.io/AWS-RD-MySQL/)

##### **`AWS Beanstalk - Creating Environment`**

###### **`Create a new environment`**

![Create a new environment]({{ site.baseurl }}/assets/images/aws/aws-elastic-beanstalk/1.PNG) 

###### **`Select environment tier`**

![Select environment tier]({{ site.baseurl }}/assets/images/aws/aws-elastic-beanstalk/2.PNG) 

###### **`Create a web server environment`**

![create a web server environment]({{ site.baseurl }}/assets/images/aws/aws-elastic-beanstalk/3.PNG) 

###### **`Environment information`**

![Environment information]({{ site.baseurl }}/assets/images/aws/aws-elastic-beanstalk/4.PNG) 

###### **`Platform`**

![Platform]({{ site.baseurl }}/assets/images/aws/aws-elastic-beanstalk/5.PNG) 

###### **`Application code`**

![Application code]({{ site.baseurl }}/assets/images/aws/aws-elastic-beanstalk/6.PNG) 

###### **`Log`**

![Log]({{ site.baseurl }}/assets/images/aws/aws-elastic-beanstalk/7.PNG) 

##### **`Edit inbound rules for the web app deployed on Elastic Beanstalk to access the Database`**

###### **`Edit inbound rules`**

![Edit inbound rules]({{ site.baseurl }}/assets/images/aws/aws-elastic-beanstalk/12.PNG) 

##### **`Environment Overview`**

###### **`Environment setup complete`**

![Environment setup complete]({{ site.baseurl }}/assets/images/aws/aws-elastic-beanstalk/8.PNG) 

###### **`Application`**

![Application]({{ site.baseurl }}/assets/images/aws/aws-elastic-beanstalk/16.PNG) 

###### **`Configuration`**

![Configuration]({{ site.baseurl }}/assets/images/aws/aws-elastic-beanstalk/17.PNG) 

###### **`Monitoring`**

![Monitoring]({{ site.baseurl }}/assets/images/aws/aws-elastic-beanstalk/20.PNG) 

###### **`Events`**

![Monitoring]({{ site.baseurl }}/assets/images/aws/aws-elastic-beanstalk/23.PNG) 

##### **`Output`**

###### **`Web Page`**

![Log]({{ site.baseurl }}/assets/images/aws/aws-elastic-beanstalk/10.PNG) 

###### **`API Endpoint`**

![Log]({{ site.baseurl }}/assets/images/aws/aws-elastic-beanstalk/9.PNG) 

###### **`API In Action`**

![Log]({{ site.baseurl }}/assets/images/aws/aws-elastic-beanstalk/11.PNG) 

##### **`Cleanup`**

###### **`Terminate Environment`**

![Terminate Environment]({{ site.baseurl }}/assets/images/aws/aws-elastic-beanstalk/24.png) 

###### **`Confirm Environment Termination`**

![Terminate Environment]({{ site.baseurl }}/assets/images/aws/aws-elastic-beanstalk/25.PNG) 














