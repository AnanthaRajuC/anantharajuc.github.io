---
title: "Spring Boot and Swagger UI REST API Documentation Tool"
author: anantharajuc
categories: [ Spring Boot, Swagger UI ]
tags: [ Spring Boot, Swagger UI ]
layout: post
date: 2021-06-27 18:40
image: /assets/images/spring-boot-swagger-ui.jpg
---

This post briefly documents the usage of **Swagger UI**, a visual documentation tool making it easy for back end implementation and client side consumption. 

---

#### Minimum Software Requirements

- Java
- [SwaggerDoc Open API UI](https://swagger.io/tools/swagger-ui/) Java Library
- Swagger Annotations Java Library

#### Sample Project

[Spring Boot Minimal Web App](https://github.com/AnanthaRajuC/Spring-Boot-Minimal-Web-App) is the sample Spring Boot app i've used to illustrate the usage of the aforementioned tool.

#### Dependencies

This implementation has two dependencies, **springdoc-openapi-ui** and **swagger-annotations**. The **maven**/**gradle** dependencies of the same are mentioned below.

##### SwaggerDoc Open API UI

~~~xml
<!-- https://mvnrepository.com/artifact/org.springdoc/springdoc-openapi-ui -->
<dependency>
    <groupId>org.springdoc</groupId>
    <artifactId>springdoc-openapi-ui</artifactId>
    <version>1.5.9</version>
</dependency>
~~~

or

~~~txt
// https://mvnrepository.com/artifact/org.springdoc/springdoc-openapi-ui
implementation group: 'org.springdoc', name: 'springdoc-openapi-ui', version: '1.5.9'
~~~

##### Swagger Annotations

~~~xml
<!-- https://mvnrepository.com/artifact/io.swagger/swagger-annotations -->
<dependency>
    <groupId>io.swagger</groupId>
    <artifactId>swagger-annotations</artifactId>
    <version>1.6.1</version>
</dependency>
~~~

or

~~~txt
// https://mvnrepository.com/artifact/io.swagger/swagger-annotations
implementation group: 'io.swagger', name: 'swagger-annotations', version: '1.6.1'
~~~

#### Properties

In the application.properties file configure the following optional key-values.

~~~txt
# https://springdoc.org/properties.html

# For custom path of the swagger-ui HTML documentation
# http://localhost:8080/spring-boot-minimal-webapp.html
springdoc.swagger-ui.path=/spring-boot-minimal-webapp.html

# To enable/disable the swagger-ui endpoint
springdoc.swagger-ui.enabled=true
~~~

#### Basic Usage

Swagger provides with annotations specific to class types (**Controller**, **Model** etc.,) which are to be placed and populated with appropriate values.

##### Model Class Annotations

**`@ApiModel(description="Simple JavaBean domain object representing RESTcontrollerResponse")`**  
This annotation essentially describes what exactly a model is.  

**`@Schema(description="RESTcontrollerResponse content", example="HTTP Method Handled.", required=true)`**  
Each attribute of the model captures a specific feature. We can describe, provide and examplr and indicate if the attribute is mandatory when initializing the object.  

##### Controller Class Annotations

**`@Operation(summary="HTTP GET Operation")`**  
This annotation describes the particular functionality a REST endpoint offers.  

**`@ApiResponse(responseCode = "200", description = "Found the person", content = {@Content(mediaType = "application/json", schema = @Schema(implementation = Person.class))})`**  
This annotation describes the API response.  

##### URLs

- *Visual Documentation* : [http://localhost:8080/swagger-ui.html](http://localhost:8080/swagger-ui.html)

![Swagger UI]({{ site.baseurl }}/assets/images/spring-boot-swagger/swagger-ui.png)  

- *OpenAPI description in json format* : [http://localhost:8080/v3/api-docs](http://localhost:8080/v3/api-docs)

![OpenAPI Description]({{ site.baseurl }}/assets/images/spring-boot-swagger/swagger-api.png)  

---