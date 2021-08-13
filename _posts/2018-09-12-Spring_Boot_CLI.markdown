---
layout: post
title: "Generating Spring Boot Skeleton Project via Spring Boot CLI"
author: anantharajuc
categories: [ Spring Boot, CLI ]
tags: [ Spring Boot, CLI ]
date: 2018-09-12 07:30
image: /assets/images/spring-boot-logo.jpg
---

Using the Spring Boot CLI to Generate Spring Boot Skeleton Project


- [CLI](#cli)
- [Installation](#installation)
- [Using the CLI](#using-the-cli)
- [Running the Jar](#running-the-jar)
- [Other Commands](#other-commands)

---

## CLI

A command-line interface or command language interpreter (CLI), also known as command-line user interface, console user interface and character user interface (CUI), is a means of interacting with a computer program where the user (or client) issues commands to the program in the form of successive lines of text (command lines). A program which handles the interface is called a command language interpreter or shell (computing)

## Installation 

* 	Pre-requisites
    - [Java SDK ](https://www.java.com/en/) v1.8 or higher

* 	Spring Boot CLI [Download Link](https://docs.spring.io/spring-boot/docs/current/reference/html/getting-started-installing-spring-boot.html#getting-started-manual-cli-installation)
 
* 	Installation Steps

    - Set **`SPRING_HOME`** to point to the Spring CLI folder
    - Add **`SPRING_HOME/bin`** to your **`PATH`** environment variable
    - To test if you have successfully installed the CLI you can run either of the following commands: 
		-	**`spring --version`** or **`spring version`**

* 	No specific environment variables are required to run the CLI

## Using the CLI

*	**`spring`**  
A help screen is displayed.

*	**`spring help`**  
Get more details about any of the supported commands.

*	**`spring init --dependencies=web,data-jpa my-example-project`**  
Create a new maven based spring boot project, **my-example-project** with **spring-boot-starter-web** and **spring-boot-starter-data-jpa** dependencies.

*	**`spring init --list`**  
List all the capabilities of Spring Starter.

*	**`spring init --build=maven --java-version=1.8 --dependencies=web,data-jpa --packaging=jar my-example-project.zip`**  
Create a maven project that uses Java 8 and jar packaging.

*	**`spring shell`**  
Command to launch an integrated shell on a Windows machine. From inside the embedded shell, you can run other commands directly. **`$ version`**

## Running the Jar

*	**`Java -jar Application-Jar-Name.Jar`**  
Running the Spring Boot Application Jar

*	**`Java -jar -Dserver.port=9090 Application-Jar-Name.Jar`**  
Running Multiple Instances of Spring Boot Project on Different Ports

## Other Commands

*	**`jcmd`**  
lists all running Java processes

*	**`Taskkill /PID PROCESS_ID_OF_RUNNING_APP /F`**  
replace the **PROCESS_ID_OF_RUNNING_APP** with the actual process id of the running jar found out from executing the previous command to shutdown the running jar.

*	**`jps -lv`**    
displays information about running java processes

*	**`echo %JAVA_HOME%`**  
prints environment variable **JAVA_HOME**