---
title: "Spring Boot Web Application Integrating Testing with JUnit, AssertJ and Mockito (BDDMockito)"
author: anantharajuc
categories: [ Testing, Spring Boot ]
tags: [ Testing, Spring Boot, featured]
layout: post
date: 2021-08-30 15:30
image: /assets/images/spring-boot-testing.jpg
---

This post briefly captures the process of writing integration tests for a Spring Boot based Web application using JUnit, AssertJ and Mockito (BDDMockito) framework.

Unit test's targets small units of code ex: a method, a class. Integration Test covers multiple units because it tests the interaction between two or more components. 

Spring Boot Web Applications are built in multiple layers. 

- Web Controller Layer  
- Business Service Layer  
- Data Repository Layer  

**`given-when-then`** human readable test methodology is followed here. It lends more clarity to our tests as we are following a natural language that is easy to read.

- **`given`**  
pre-conditions and requirements for actions.  

- **`when`**  
action we want to test.  

- **`then`**  
verification of what should happen after execution of action.  

---

#### Minimum Software Requirements

- Java
- [H2DB](https://www.h2database.com/html/main.html)
- [AssertJ](https://assertj.github.io/doc/)
- [Mockito](https://site.mockito.org/)
- [JUnit5](https://junit.org/junit5/)
- [Lombok](https://projectlombok.org/)

*Note*: Ensure JUnit5 is on the project build path.

---

#### **`Sample Project`**

[Spring Boot Minimal Web App](https://github.com/AnanthaRajuC/Spring-Boot-Minimal-Web-App) is the sample Spring Boot web application i've used to illustrate Integration Testing.  

Navigate to [http://localhost:8080/](http://localhost:8080/) to discover the application URLs.  

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/common/spring-boot-minimal-web-app.PNG" /></div>  

In the **`application.properties`** file present in the **resources** folder, set the **`spring.profiles.active`** value to **application-h2db**.  

*Noticed an issue with this Sample Project? Open an [issue](https://github.com/AnanthaRajuC/Spring-Boot-Minimal-Web-App/issues) or a [PR](https://github.com/AnanthaRajuC/Spring-Boot-Minimal-Web-App/pulls) on GitHub!*

---

#### Dependencies

This implementation has a dependency on **spring-boot-starter-test**, **h2**, **lombok** dependencies. The **maven**/**gradle** dependencies of the same are mentioned below.

<script src="https://gist.github.com/AnanthaRajuC/c045ba794147177ae597218f685e6132.js"></script>

---

#### Repository Layer Testing

<script src="https://gist.github.com/AnanthaRajuC/9e296dda506d9680cfeb5e8591a8a659.js"></script>

---

#### Service Layer Testing

<script src="https://gist.github.com/AnanthaRajuC/f9a2dd9181be4107c0f3d464525c1c3c.js"></script>

---

#### Controller Layer Testing

<script src="https://gist.github.com/AnanthaRajuC/160cd6892908f1b225bd1eee7de73c72.js"></script>

---
