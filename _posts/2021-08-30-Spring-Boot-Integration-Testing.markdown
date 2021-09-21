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

---

#### Introduction

**Unit** testing is a type of software testing where individual units or components (ex: a method, a class) of a software are tested .

**Integration testing** is the phase in software testing in which individual software modules are combined and tested as a group. Integration Test covers multiple units because it tests the interaction between two or more components. 

---

**JUnit** is a unit testing framework for the Java programming language. 

**AssertJ** is a Java library that provides a rich set of assertions and truly helpful error messages, improves test code readability.

**Mockito**  is a testing framework that allows the creation of test double objects in automated unit tests for the purpose of test-driven development or behavior-driven development. 

---

#### Goals

1. Data/Repository Layer Testing  
2. Business/Service Layer Testing  
3. Web/Controller Layer Testing  

---

#### Test Methodology

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

Repositories are classes or components that encapsulate the logic required to access data sources. They centralize common data access functionality, providing better maintainability and decoupling the infrastructure or technology used to access databases from the domain model layer

<script src="https://gist.github.com/AnanthaRajuC/9e296dda506d9680cfeb5e8591a8a659.js"></script>

---

#### Service Layer Testing

Service layer is an architectural pattern, which aims to organize the services, within a service inventory, into a set of logical layers. Services that are categorized into a particular layer share functionality.

<script src="https://gist.github.com/AnanthaRajuC/f9a2dd9181be4107c0f3d464525c1c3c.js"></script>

---

#### Controller Layer Testing


The Controller layer is the conductor of operations for a request. It controls the transaction scope and manages the session related information for the request. The controller first dispatches to a command and then calls the appropriate view processing logic to render the response.

<script src="https://gist.github.com/AnanthaRajuC/160cd6892908f1b225bd1eee7de73c72.js"></script>

---
