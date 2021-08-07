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

*	**`db.<collection-name>.insertOne(<JSON>)`**   
Insert JSON to the collection of the current DB.  
*Example*: **db.student.insertOne( {x:1} )**

*	**`db.<collection-name>.insert(  
[  
     { _id: 1, name: "Java Hut", description: "Coffee and cakes" },  
     { _id: 2, name: "Burger Buns", description: "Gourmet hamburgers" },  
     { _id: 3, name: "Coffee Shop", description: "Just coffee" },  
     { _id: 4, name: "Clothes Clothes Clothes", description: "Discount clothing" },  
     { _id: 5, name: "Java Shopping", description: "Indonesian goods" }  
   ]
)`**  
Bulk insert (sample) data into a collection

*	**`db.<collection-name>.find()`**    
View the contents of a collection.   
*Example*: **db.student.find()**   

*	**`db.<collection-name>.find().pretty()`**   
View the contents of a collection nicely formatted.  
*Example*: **db.student.find().pretty()**  

*	**`db.<collection-name>.createIndex( {field-name1:"text", field-name2:"text"} )`**   
**Text Index**, to support text search queries on string content.  
*Example*: **db.stores.createIndex( {name:"text", description:"text"} )**  

*	**`db.<collection-name>.find( { $text: { $search: "text to search"} } )`**   
**$text Operator**, perform text searches on a collection with a text index.  
*Example*: **db.stores.find( { $text: { $search: "java coffee shop" } } )**  







