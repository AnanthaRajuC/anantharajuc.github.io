---
title: "Flyway version control for Relational Databases with Spring Boot"
author: anantharajuc
categories: [ Spring Boot, Java ]
layout: post
date: 2021-06-25 10:40
image: /assets/images/spring-boot-flyway.jpg
---

This post briefly documents the usage of **Flyway** for Relational Database version control. Flyway supports some of the most popular DBs available today, the list of the same can found [here](https://flywaydb.org/documentation/database/aurora-mysql).

---

#### Minimum Software Requirements

- Java
- [Flyway Core](https://mvnrepository.com/artifact/org.flywaydb/flyway-core) library (Maven/Gradle)
- [H2DB](https://mvnrepository.com/artifact/com.h2database/h2) library (Maven/Gradle) or any of the several other supported RDBMS.


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

##### Flyway

~~~xml
<!-- https://mvnrepository.com/artifact/org.flywaydb/flyway-core -->
<dependency>
    <groupId>org.flywaydb</groupId>
    <artifactId>flyway-core</artifactId>
    <version>7.10.0</version>
</dependency>
~~~

or

~~~txt
// https://mvnrepository.com/artifact/org.flywaydb/flyway-core
implementation group: 'org.flywaydb', name: 'flyway-core', version: '7.10.0'
~~~

##### H2DB

~~~xml
<!-- https://mvnrepository.com/artifact/com.h2database/h2 -->
<dependency>
    <groupId>com.h2database</groupId>
    <artifactId>h2</artifactId>
    <version>1.4.200</version>
</dependency>
~~~

or

~~~txt
// https://mvnrepository.com/artifact/com.h2database/h2
testImplementation group: 'com.h2database', name: 'h2', version: '1.4.200'
~~~

#### Basic Usage

In the resources folder of the project create additional folders with the following hierarchy **`data\h2db\migrations`**. 

Inside the **`migration`** folder for **`h2db`**, create multiple **`.sql`** files describing the table structure and the data to be populated in those tables. 

*Note*: The names of these **`.sql`** files should be prefixed with **`V0_0_i__`** where **`i`** represents numbers, the order in which the files are to be executed. 

In this project there are two files, **`V0_0_1__SBMWA_structure.sql`** (First file to be executed) and **`V0_0_2__SBMWA_data.sql`** (Second file to be executed). 

	- *V0_0_1__SBMWA_structure.sql* describes the structure of the tables and is the first file to be executed since the file name contains the number **`1`**.  
	- *V0_0_2__SBMWA_data.sql* has the insert statements of the data that is to be loaded during initialization and is the second file to be executed since the file name contains the number **`2`**.  

In the **`application.properties`** file add the following properties. 

*Data Migration Properties*

~~~txt
# Whether to enable flyway.
spring.flyway.enabled=true
# Locations of migrations scripts. Can contain the special "{vendor}" placeholder to use vendor-specific locations.
spring.flyway.locations=classpath:/data/h2db/migrations
~~~

*Data Source Properties*

~~~txt
# JDBC URL of the database.
spring.datasource.url=jdbc:h2:mem:sbmwa;MODE=MySQL;DB_CLOSE_ON_EXIT=FALSE
# Fully qualified name of the JDBC driver. Auto-detected based on the URL by default.
spring.datasource.driverClassName=org.h2.Driver
# Username of the database to execute DML scripts (if different).
spring.datasource.username=sa
# Password of the database to execute DML scripts (if different).
spring.datasource.password=
~~~

*JPA Properties (JpaBaseConfiguration, HibernateJpaAutoConfiguration)*

~~~txt
# Name of the target database to operate on, auto-detected by default. Can be alternatively set using the "Database" enum.
spring.jpa.database-platform=org.hibernate.dialect.H2Dialect
# DDL mode. This is actually a shortcut for the "hibernate.hbm2ddl.auto" property. Defaults to "create-drop" when using an embedded database and no schema manager was detected. Otherwise, defaults to "none".
spring.jpa.hibernate.ddl-auto=none
~~~

*H2 Web Console (H2ConsoleProperties)* (Necessary only when using H2DB as database)

~~~txt
# Whether to enable the console.
spring.h2.console.enabled=true
# Path at which the console is available.
spring.h2.console.path=/h2-console/
# Whether to enable trace output.
spring.h2.console.settings.trace=false
# Whether to enable remote access.
spring.h2.console.settings.web-allow-others=false
~~~

H2DB can be accessed via a web console at **`http://localhost:8080/h2-console`**

![H2DB Console]({{ site.baseurl }}/assets/images/spring-boot-flyway/sbmwa-h2-console.PNG)  

Upon execution of the program for the first, a table named **flyway_schema_history** will be created and it will maintain the history of database migrations.

![H2DB Flyway Schema History Table]({{ site.baseurl }}/assets/images/spring-boot-flyway/sbmwa-h2-flyway_schema_history.PNG)  

The actual tables and the necessary data to be populated into those tables as defined in the **`.sql`** files will also be available for use by the application. 

![Tables and Data]({{ site.baseurl }}/assets/images/spring-boot-flyway/sbmwa-h2-tabel-data.PNG)  

#### Links

- [Flyway](https://flywaydb.org/)