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

![Services]({{ site.baseurl }}/assets/images/aws-rds-mysql/1.png)   

![Databases]({{ site.baseurl }}/assets/images/aws-rds-mysql/2.PNG)   

- In the following page, configure the database settings.

##### Database Creation

- **`Database creation method`** : **Standard create**  
- **`Engine Type`** : **MySQL**  
- **`Edition`** : **MySQL Community**  
- **`Version`** : **MySQL 8.0.23** *(or whatever is the latest avaialable version)*  

![Database Creation method]({{ site.baseurl }}/assets/images/aws-rds-mysql/3.PNG)  

![Database Creation Details]({{ site.baseurl }}/assets/images/aws-rds-mysql/4.PNG)  

##### Templates
		
- **`Templates`** : **Free Tier**  
		
![Templates]({{ site.baseurl }}/assets/images/aws-rds-mysql/5.PNG)  		
		
##### Settings, Credentials Settings
		
- **`DB instance identifier`** : **some_identifier**  
- **`Master Username`** : **some_username**  
- **`Master Password`** : **some_password**  
- **`Confirm Password`** : **some_password** 

![Settings]({{ site.baseurl }}/assets/images/aws-rds-mysql/6.PNG)  	 

##### Connectivity
		
- **`Virtual private cloud`** : **Default VPC**  
- **`Subnet group`** : **default**  
- **`Public access`** : **Yes**  
- **`VPC security group`** : **Choose existing**  

![Connectivity]({{ site.baseurl }}/assets/images/aws-rds-mysql/9.PNG)  	 
		
##### Database authentication
		
- **`Database Authentication`** : **Password authentication**

![Database authentication]({{ site.baseurl }}/assets/images/aws-rds-mysql/11.PNG)  	 

##### Additional Configuration
		
- **`Initial database name`** : **Schema name** *(ex: sbmwa_aws)*  

![Additional Configuration]({{ site.baseurl }}/assets/images/aws-rds-mysql/12.PNG)  	 
	
- Finally, at the end of the page click on the **`Create database`** button.

![Create database]({{ site.baseurl }}/assets/images/aws-rds-mysql/13.PNG)  

---
