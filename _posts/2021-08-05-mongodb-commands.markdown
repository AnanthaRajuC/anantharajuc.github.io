---
layout: post
title: "MongoDB Commands" 
author: anantharajuc
categories: [ MongoDB, Database, CLI ]
tags: [ MongoDB, Database, CLI ]
date: 2021-08-05 19:00
image: assets/images/mongodb.png
---

MongoDB is a source-available cross-platform document-oriented database program. Classified as a NoSQL database program, MongoDB uses JSON-like documents with optional schemas.

The following is a non-exhaustive list of commonly used MongoDB Commands for quick reference.

#### Commands

*	**`show dbs`** or **`show databases`**  
Print a list of all databases on the server.   

*	**`use <db>`**  
Switch current database to `<db>`. If this database doesn’t exist, it will be newly created.   

*	**`db`**  
View the current database.  

*	**`show collections`** or **`db.getCollectionNames()`**  
Get the list of all collections in the current database. 

*	**`db.dropDatabase()`**  
Drops the current database.  

*	**`db.<collection name>.insertOne(<JSON>)`**   
Insert JSON to the collection of the current DB.  
*Example*: **db.student.insertOne( {x:1} )**

*	**`db.<collection name>.find()`**    
View the contents of a collection.   
*Example*: **db.student.find()**   

*	**`db.<collection name>.find().pretty()`**   
View the contents of a collection nicely formatted.  
*Example*: **db.student.find().pretty()**  


