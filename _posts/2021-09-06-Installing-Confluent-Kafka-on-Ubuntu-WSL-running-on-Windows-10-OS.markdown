---
title: "Installing Confluent Kafka on Ubuntu WSL running on Windows 10 OS"
author: anantharajuc
categories: [ Confluent Kafka, WSL, Installation ]
tags: [ Confluent Kafka, WSL, Installation ]
layout: post
date: 2021-09-06 15:50
image: /assets/images/wsl-kafka.png
---

This post documents the process of installing Confluent Kafka community edition on Ubuntu WSL running on Windows 10 OS.

---

#### Introduction

**Confluent Kafka** is mainly a data streaming platform consisting of most of the Kafka features and a few other things. Its main objective is not limited to provide a pub-sub platform only but also to provide data storage and processing capabilities.

--- 

#### Goals

1. Downlod Confluent Kafka
2. Copy Confluent Kafka from Windows OS to Linux  
3. Unzip Confluent Kafka TAR file
4. Set CONFLUENT_HOME and PATH values
5. UPDATE Confluent Kafka server.properties file
6. Kafka Management (Start, Stop)
7. Cleanup (Remove) 

---

#### Minimum Requirements

- Windows 10 Operating System with WSL enabled/installed.

**Note**: *To enable/install WSL on Windows 10, refer to the following posts.*

- [Enabling Windows Subsystem for Linux on Windows 10 with Ubuntu via CLI](https://anantharajuc.github.io/Enabling-Windows-Subsystem-for-Linux-via-CLI/)  
- [Enabling Windows Subsystem for Linux on Windows 10 with Ubuntu via Settings GUI](https://anantharajuc.github.io/Enabling-Windows-Subsystem-for-Linux-via-Settings-GUI/)  

---

##### Downlod Confluent Kafka TAR file  

From a browser on your Windows 10 OS, navigate to [https://www.confluent.io/get-started?product=software](https://www.confluent.io/get-started?product=software), provide the necessary details.  

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/kafka-on-wsl/15.png" /></div>    

you will now be re-directed to [https://www.confluent.io/installation](https://www.confluent.io/installation) page. Click on the **TAR** download button to save the software on your Windows 10 OS file system. The size of the file is approximately **1.4 GB**.  

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/kafka-on-wsl/16.png" /></div>    

---

##### Copy Confluent Kafka from Windows OS to Linux  

From your Ubuntu WSL command prompt enter `ll /mnt/` to view the Windows 10 OS hard disk partions.

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/kafka-on-wsl/17.PNG" /></div>    

Copy the confluent software from the download location in Windows 10 OS to the present working directory in WSL (Ubuntu).

`cp /mnt/YOUR_DOWNLOAD_LOCATION_HERE/DOWNLOAD_FILE_NAME.tar .`

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/kafka-on-wsl/18.PNG" /></div>    

To check if the file has been moved successfully, issue the `ll` command.

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/kafka-on-wsl/19.PNG" /></div>    

---

##### Unzip Confluent Kafka TAR file  

Now that the file is present in the WSL, let's unzip the file name. `tar -zxvf DOWNLOAD_FILE_NAME.tar`

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/kafka-on-wsl/20.PNG" /></div>    

To check if the file has been unzipped successfully into a folder, issue the `ll` command again.

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/kafka-on-wsl/21.PNG" /></div>    

---

##### Set CONFLUENT_HOME and PATH values  

Issue `nano .profile` command, or use any other editor to edit the **.profile** file.  

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/kafka-on-wsl/22.PNG" /></div>    

Add **CONFLUENT_HOME** and also set **PATH** to include the kafka `/bin` folder. 

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/kafka-on-wsl/23.PNG" /></div>    

To check if **CONFLUENT_HOME** has been successfully set or not, issue `echo $CONFLUENT_HOME` command.

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/kafka-on-wsl/24.PNG" /></div>  

---

##### UPDATE Confluent Kafka server.properties file  

Edit **listeners**, **advertised.listeners** values and uncomment **listener.security.protocol.map** in Kafka `server.properties` file with the following values by issuing the following command `nano /YOUR_UNZIPPED_CONFLUENT_KAFKA_FOLDER/etc/kafka/server.properties`.

Example: `nano /home/anantharajuc/confluent-6.2.0/etc/kafka/server.properties`

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/kafka-on-wsl/25.PNG" /></div>  

---

##### Start Confluent Kafka  

Now, start the confluent services by issuing the `Start Confluent Kafka Server` command.  

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/kafka-on-wsl/26.PNG" /></div>    

In a web browser on your Windows 10 OS, navigate to **http://localhost:9021/** to view the Confluent Kafka web portal.

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/kafka-on-wsl/27.png" /></div>    

---

##### Stop Confluent Kafka  

To stop the Confluent Kafka services issue the `confluent local services stop` command.  

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/kafka-on-wsl/28.PNG" /></div>    

---
