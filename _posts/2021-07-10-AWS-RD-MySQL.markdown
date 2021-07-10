---
title: "AWS Relational Database : MySQL"
author: anantharajuc
categories: [ Cloud, AWS, MySQL ]
layout: post
date: 2021-07-08 09:50
image: /assets/images/aws-rds-mysql.jpg
---

This post briefly documents the process of creating **MySQL** Database via the AWS **RDS** service.

---

#### Minimum Requirements

- Access to [AWS Management Console](https://aws.amazon.com/console/)

#### Database Configuration

- From the services drop down from the Navigation bar, select the **`RDS`** service from the Database section. 

- In the following page, configure the settings.

##### Database Creation

		- Database creation method : Standard create  
		- Engine Type : MySQL  
		- Edition : MySQL Community  
		- Version : MySQL 8.0.23 (or whatever is the latest avaialable version)  

##### Templates
		
		- Templates : Free Tier  
		
##### Settings
		
		- DB instance identifier : some_identifier  
		
###### Credentials Settings
		
		- Master Username : some_username  
		- Master Password : some_password  
		- Confirm Password : some_password  

##### Connectivity
		
		- Virtual private cloud : Default VPC  
		- Subnet group : default  
		- Public access : Yes  
		- VPC security group : Choose existing  
		
##### Database authentication
		
		- Database Authentication : Password authentication

##### Database options
		
		- Initial database name : Schema name  
	
- Finally, at the end of the page click on the **`Create database`** button.

---
