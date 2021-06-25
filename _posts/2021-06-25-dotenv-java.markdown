---
title: "Loading Environment Variables via dotenv-java"
author: anantharajuc
categories: [ Spring Boot, Java ]
layout: post
date: 2021-06-25 08:10
image: /assets/images/dotenv-java.png
---

This post documents the usage of **dotenv-java** library which aids in loading **Environment Variables** which are often using to store confidential configuration values such as *API keys*, *Database passwords* etc., instead of directly adding these values in the codebase. 

This library is available in both Java and [Kotlin](https://github.com/cdimascio/dotenv-kotlin) flavours and also supports usage in Android. 

We are consciously avoiding using **`System.getenv(...)`** to do the same.

---

#### Minimum Software Requirements

- Java 8 or higher
- [dotenv-java](https://github.com/cdimascio/dotenv-java#install) library (Maven/Gradle)

#### Sample Project

[Spring Boot Minimal Web App](https://github.com/AnanthaRajuC/Spring-Boot-Minimal-Web-App) is the sample Spring Boot app i've used to illustrate the usage of the aforementioned tool.

| *Method*   |    |  *URL*                                 |
|------------|----|----------------------------------------|
| **GET**    |    | **`http://localhost:8080/index.html`** |
| **GET**    |    | **`http://localhost:8080/`**           |
| **PUT**    |    | **`http://localhost:8080/`**           | 
| **POST**   |    | **`http://localhost:8080/`**           | 
| **DELETE** |    | **`http://localhost:8080/`**           |

#### Dependencies

##### dotenv-java

~~~xml
<!-- https://mvnrepository.com/artifact/io.github.cdimascio/dotenv-java -->
<dependency>
    <groupId>io.github.cdimascio</groupId>
    <artifactId>dotenv-java</artifactId>
    <version>2.2.0</version>
</dependency>
~~~

or

~~~txt
// https://mvnrepository.com/artifact/io.github.cdimascio/dotenv-java
implementation group: 'io.github.cdimascio', name: 'dotenv-java', version: '2.2.0'
~~~

#### Basic Usage

Create a **`.env`** file in the root of your project with the following structure.

~~~txt
# formatted as key=value
MY_ENV_VAR1=some_value
MY_ENV_VAR2=some_value
~~~

Initialize the library and get the environment variables as per the need.

~~~java
Dotenv dotenv = Dotenv.load();
dotenv.get("MY_ENV_VAR1")
~~~

#### Notes

To edit the **`.env`** file you could simply navigate to project's directory and open the file by a text editor. 

Eclipse IDE by default doesn't show dot files in the **Project Explorer** tab. To enable this functionality follow the below mentioned steps.

**`Project Explorer -> View Menu -> Filters -> uncheck .* resources`**

![Eclipse IDE .*resources]({{ site.baseurl }}/assets/images/eclipse-ide-dot-resources.png)  

#### Links

- Queries regarding *best practices*, *multi-line values*, *multiple .env files*, *usage in PRODUCTION environment* and other frequently asked questions have been addressed by the authors of the project [here](https://github.com/cdimascio/dotenv-java#faq).
