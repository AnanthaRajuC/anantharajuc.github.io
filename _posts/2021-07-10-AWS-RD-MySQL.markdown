---
title: "AWS Relational Database : MySQL"
author: anantharajuc
categories: [ Cloud, AWS, MySQL ]
tags: [ Cloud, AWS, MySQL ]
layout: post
date: 2021-07-08 09:50
image: /assets/images/aws/aws-rds-mysql.jpg
---

This post briefly documents the process of creating **MySQL** Database via the AWS **RDS** service.

---

#### Introduction

**Amazon Relational Database Service (RDS)** is a distributed relational database service by Amazon Web Services. It is a web service running "in the cloud" designed to simplify the setup, operation, and scaling of a relational database for use in applications. 

**MySQL** is an open-source relational database management system (RDBMS). A relational database organizes data into one or more data tables in which data types may be related to each other; these relations help structure the data. SQL is a language programmers use to create, modify and extract data from the relational database, as well as control user access to the database. 

---

#### Goals

1. Database Configuration  
	1.1 Database Configuration  
	1.2 Templates
	1.3 Settings, Credentials Settings  
	1.4 Connectivity  
	1.5 Database authentication  
	1.6 Additional Configuration  
2. Connectivity and security
	2.1 Connectivity and security Configuration  
	2.2 Security Groups  
	2.3 Edit inbound rules  
	2.4 Add rules  
	2.5 Inbound rules  
3. Accessing the Database via MySQL Workbench
	3.1 Setup new connection  
	3.2 MySQL connection result  
	3.3 MySQL Workbench  

---

#### **`Minimum Requirements`**

- Access to [AWS Management Console](https://aws.amazon.com/console/)

---

#### **`Database Configuration`**

- From the services drop down from the Navigation bar, select the **`RDS`** service from the Database section.

![Services]({{ site.baseurl }}/assets/images/aws/aws-rds-mysql/1.png)   

--- 

![Databases]({{ site.baseurl }}/assets/images/aws/aws-rds-mysql/2.PNG)   

- In the following page, configure the database settings.

--- 

##### **`Database Creation`**

- **`Database creation method`** : **Standard create**  
- **`Engine Type`** : **MySQL**  
- **`Edition`** : **MySQL Community**  
- **`Version`** : **MySQL 8.0.23** *(or whatever is the latest avaialable version)*  

![Database Creation method]({{ site.baseurl }}/assets/images/aws/aws-rds-mysql/3.PNG)  

--- 

![Database Creation Details]({{ site.baseurl }}/assets/images/aws/aws-rds-mysql/4.PNG)  

--- 

##### **`Templates`**
		
- **`Templates`** : **Free Tier**  
		
![Templates]({{ site.baseurl }}/assets/images/aws/aws-rds-mysql/5.PNG)  		

--- 

##### **`Settings, Credentials Settings`**

- **`DB instance identifier`** : **some_identifier** *(ex: sbmwa)*    
- **`Master Username`** : **some_username** *(ex: sbmwa_aws_user)*    
- **`Master Password`** : **some_password** *(ex: sbmwa_aws_pwd)*    
- **`Confirm Password`** : **some_password** *(ex: sbmwa_aws_pwd)*   

![Settings]({{ site.baseurl }}/assets/images/aws/aws-rds-mysql/6.PNG)  	 

--- 

##### **`Connectivity`**
		
- **`Virtual private cloud`** : **Default VPC**  
- **`Subnet group`** : **default**  
- **`Public access`** : **Yes**  
- **`VPC security group`** : **Choose existing**  

![Connectivity]({{ site.baseurl }}/assets/images/aws/aws-rds-mysql/9.PNG)  	 

--- 

##### **`Database authentication`**

- **`Database Authentication`** : **Password authentication**

![Database authentication]({{ site.baseurl }}/assets/images/aws/aws-rds-mysql/11.PNG)  	 

--- 

##### **`Additional Configuration`**

- **`Initial database name`** : **Schema name** *(ex: sbmwa_aws)*  

![Additional Configuration]({{ site.baseurl }}/assets/images/aws/aws-rds-mysql/12.PNG)  	 

--- 
	
- Finally, at the end of the page click on the **`Create database`** button.

![Create database]({{ site.baseurl }}/assets/images/aws/aws-rds-mysql/13.PNG)  

---

#### **`Connectivity and security`**

##### **`Connectivity and security Configuration`**

![Connectivity and security]({{ site.baseurl }}/assets/images/aws/aws-rds-mysql/15.PNG)  

--- 

##### **`Security Groups`**

![Security Groups]({{ site.baseurl }}/assets/images/aws/aws-rds-mysql/16.PNG)  

--- 

##### **`Edit inbound rules`**

![Edit inbound rules]({{ site.baseurl }}/assets/images/aws/aws-rds-mysql/17.PNG) 

--- 

##### **`Add rules`**

![Add rules]({{ site.baseurl }}/assets/images/aws/aws-rds-mysql/19.PNG) 

--- 

##### **`Inbound rules`**

![Inbound rules]({{ site.baseurl }}/assets/images/aws/aws-rds-mysql/20.PNG) 

---

#### **`Accessing the Database via MySQL Workbench`**

##### **`Setup new connection`**

![Setup new connection]({{ site.baseurl }}/assets/images/aws/aws-rds-mysql/21.PNG) 

--- 

##### **`MySQL connection result`**

![MySQL connection result]({{ site.baseurl }}/assets/images/aws/aws-rds-mysql/22.PNG) 

--- 

##### **`MySQL Workbench`**

![MySQL Workbench]({{ site.baseurl }}/assets/images/aws/aws-rds-mysql/23.PNG) 

---
