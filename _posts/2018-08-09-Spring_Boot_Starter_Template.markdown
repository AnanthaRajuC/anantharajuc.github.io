---
title: "Spring Boot Starter Template"
layout: post
date: 2018-08-09 07:30
image: /assets/images/markdown.jpg
headerImage: false
tag:
- Spring Boot
- Web Application
star: true
category: blog
author: Anantha Raju C
description: A starter Spring Boot Starter Template to Rapidly develop Web Applications
---

The only thing better than a Maven archetype is a repo you can fork with everything already setup. Skip the documentation and just fork-and-code.

Delete the sample code, replace with your own and you’re good to go.

## Built With

* 	[Bootstrap](https://getbootstrap.com/) - Bootstrap is a free and open-source CSS framework directed at responsive, mobile-first front-end web development.
* 	[Flyway](https://flywaydb.org/) - Version control for database
* 	[JDK](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) - Java™ Platform, Standard Edition Development Kit
* 	[Spring Boot](https://spring.io/projects/spring-boot) - Framework to ease the bootstrapping and development of new Spring Applications
* 	[MySQL](https://www.mysql.com/) - Open-Source Relational Database Management System
* 	[git](https://git-scm.com/) - Free and Open-Source distributed version control system
* 	[Thymeleaf](https://www.thymeleaf.org/) - Modern server-side Java template engine for both web and standalone environments.
* 	[Prometheus](https://prometheus.io/) - Monitoring system and time series database
* 	[Lombok](https://projectlombok.org/) - Never write another getter or equals method again, with one annotation your class has a fully featured builder, Automate your logging variables, and much more.
* 	[Swagger](https://swagger.io/) - Open-Source software framework backed by a large ecosystem of tools that helps developers design, build, document, and consume RESTful Web services.
* 	[Maven](https://maven.apache.org/) - Dependency Management

## External Tools Used

* 	[Postman](https://www.getpostman.com/) - API Development Environment (Testing Docmentation)
* 	[Postman Echo](https://docs.postman-echo.com/?version=latest) - A service that can be used to test your REST clients and make sample API calls. It provides endpoints for GET, POST, PUT, various auth mechanisms and other utility endpoints.
* 	[Travis CI](https://travis-ci.org/github/Spring-Boot-Framework/Spring-Boot-Application-Template) - A hosted continuous integration service used to build and test software projects hosted at GitHub and Bitbucket.
* 	[Codecov](https://codecov.io/gh/Spring-Boot-Framework/Spring-Boot-Application-Template) - A hosted tool that is used to measure the test coverage of your codebase.
*	[Dependabot](https://dependabot.com/) - Automated dependency updates.

## To-Do

* 	[x] Logger (Console, File, Mail)
* 	[x] RESTful Web Service (CRUD)
* 	[x] Bootstrap - CSS
* 	[x] Web - HTML, JavaScript (jQuery)
* 	[x] Content Negotiation
* 	[x] Security (Basic Authentication)
* 	[x] Dark Mode
* 	[x] Shut down app on button click via actuator url
* 	[ ] Material Design for Bootstrap
* 	[ ] Docker
* 	[ ] HATEOS
* 	[ ] Spring Boot Admin
* 	[ ] NoSQL (MongoDB)
* 	[ ] MySQL (Connect to Multiple Schemas)
* 	[ ] Micrometer
* 	[ ] Grafna

## Running the application locally

There are several ways to run a Spring Boot application on your local machine. One way is to execute the `main` method in the `com.arc.sbtest.SBtemplateApplication` class from your IDE.

* 	Download the zip or clone the Git repository.
* 	Unzip the zip file (if you downloaded one)
* 	Open Command Prompt and Change directory (cd) to folder containing pom.xml
* 	Open Eclipse
	* File -> Import -> Existing Maven Project -> Navigate to the folder where you unzipped the zip
	* Select the project
* 	Choose the Spring Boot Application file (search for @SpringBootApplication)
* 	Right Click on the file and Run as Java Application

Alternatively you can use the [Spring Boot Maven plugin](https://docs.spring.io/spring-boot/docs/current/reference/html/build-tool-plugins-maven-plugin.html) like so:

```shell
mvn spring-boot:run
```

## Running the application via docker container

* 	[anantha/spring-boot-application-template](https://hub.docker.com/repository/docker/anantha/spring-boot-application-template) - DockerHub Image

DockerHub Pull Command

```text
docker pull anantha/spring-boot-application-template
```

Ensure you build a jar of the application before building a docker image.  

```text
mvn package -Dmaven.test.skip=true     //skip all tests and build
```

```text
mvn clean package					   //run all tests and build
```

|  Command |  Description |
|----------|--------------| 
|docker images                                       | take a look at the container images. |
|docker ps                                           | list all the running containers.     |
|docker ps -a                                        | list all the containers, including the ones that have finished executing.|
|docker build -t spring-boot-application-template .  | Build docker image of the project    |
|docker run spring-boot-application-template         | run the project's docker container   |
|docker stop [container_id]                          | stop a container                     |
|docker rm $(docker ps -aq)                          | stop and remove all containers       |

### Security

```xml
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-security</artifactId>
</dependency>
```

~~Spring Boot Starter Security default username is `user` and a generated security password is printed in the console like `Using generated security password: 0423bec1-6759-4ed2-8e3e-e8196effadf9`~~

Refer to the `ApplicationSecurityConfig` class in `io.github.anantharajuc.sbtest.security` package to modify the preconfigured users.

|  Username     |  Password |
|---------------|-----------|
|`johnDoe`   | password  |
|`AdminUser` | password  |

### URLs

|  URL |  Method | Remarks |
|----------|--------------|--------------|
|`http://localhost:8080/index`                                   | GET | Home Page              |
|`http://localhost:8080/about`                                   | GET | About Page             |

### Web Page URLs

|  URL |  Method | Remarks |
|----------|--------------|--------------|
|`http://localhost:8080/view/bootstrap`       | GET ||
|`http://localhost:8080/view/angular`         | GET ||
|`http://localhost:8080/view/material-design` | GET ||

### Other URLs

|  URL |  Method | Remarks |
|----------|--------------|--------------|
|`http://localhost:8080/bw/tech-stack`                           | GET | Custom Response Headers|
|`http://localhost:8080/api/generic-hello`                       | GET | |
|`http://localhost:8080/api/personalized-hello/`                 | GET | |
|`http://localhost:8080/api/personalized-hello?name=spring-boot` | GET | |
|`http://localhost:8080/api/loggers`                             | GET | |

### Actuator

To monitor and manage your application

|  URL |  Method |
|----------|--------------|
|`http://localhost:8080/actuator/`| GET |
|`http://localhost:8080/actuator/health`| GET |
|`http://localhost:8080/actuator/info`| GET |
|`http://localhost:8080/actuator/prometheus`| GET |
|`http://localhost:8080/actuator/httptrace`| GET |

### Person URLs

|  URL |  Method | Remarks |
|----------|--------------|--------------|
|`http://localhost:8080/api/person`                         | GET | Header `Accept:application/json` or `Accept:application/xml` for content negotiation|
|`http://localhost:8080/api/person/1`                       | GET |                                                                                     |

## Documentation

* 	[Postman Collection](https://documenter.getpostman.com/view/2449187/RWTiwzb2) - online, with code auto-generated snippets in cURL, jQuery, Ruby,Python Requests, Node, PHP and Go programming languages
* 	[Postman Collection](https://github.com/AnanthaRajuC/Spring-Boot-Application-Template/blob/master/Spring%20Boot%20Template.postman_collection.json) - offline
* 	[Swagger](http://localhost:8080/swagger-ui.html) - `http://localhost:8080/swagger-ui.html`- Documentation & Testing

## Files and Directories

The project (a.k.a. project directory) has a particular directory structure. A representative project is shown below:

```text
.
├── Spring Elements
├── src
│   └── main
│       └── java
│           ├── io.github.anantharajuc.sbtest
│           ├── io.github.anantharajuc.config
│           ├── io.github.anantharajuc.controller
│           ├── io.github.anantharajuc.enums
│           ├── io.github.anantharajuc.exception
│           ├── io.github.anantharajuc.model
│           ├── io.github.anantharajuc.repository
│           ├── io.github.anantharajuc.security
│           ├── io.github.anantharajuc.service
│           └── io.github.anantharajuc.util
├── src
│   └── main
│       └── resources
│           ├── data
│           │   └── mysql
│           │       └── migrations
│           │           ├── V0_0_1__initialize_structure.sql
│           │           └── V0_0_2__populate_data.sql
│           ├── static
│           │   ├── css
│           │   ├── fonts
│           │   ├── images
│           │   ├── js
│           │   └── favicon.ico
│           ├── templates
│           │   ├── fragments
│           │   │   ├── body_scripts.html
│           │   │   ├── footer.html
│           │   │   ├── htmlhead.html
│           │   │   ├── navigation.html
│           │   │   └── pagetitle.html
│           │   │   
│           │   ├── pages
│           │   │   ├── about.html
│           │   │   ├── close.html
│           │   │   └── index.html
│           │   │   
│           │   ├── error.html
│           │   └── layout.html
│           │   
│           ├── application.properties
│           ├── banner.txt
│           └── log4j2.xml
├── src
│   └── test
│       └── java
├── JRE System Library
├── Maven Dependencies
├── bin
├── logs
│   └── application.log
├── src
├── target
│   └──application-0.0.1-SNAPSHOT
├── mvnw
├── mvnw.cmd
├── pom.xml
└── README.md
```

## packages

* 	`models` — to hold our entities;
* 	`repositories` — to communicate with the database;
* 	`services` — to hold our business logic;
* 	`security` — security configuration;
* 	`controllers` — to listen to the client;

* 	`resources/` - Contains all the static resources, templates and property files.
* 	`resources/static` - contains static resources such as css, js and images.
* 	`resources/templates` - contains server-side templates which are rendered by Spring.
* 	`resources/application.properties` - It contains application-wide properties. Spring reads the properties defined in this file to configure your application. You can define server’s default port, server’s context path, database URLs etc, in this file.

* 	`test/` - contains unit and integration tests

* 	`pom.xml` - contains all the project dependencies
