---
title: "Java Annotation"
layout: post
date: 2019-04-11 08:30
image: /assets/images/markdown.jpg
headerImage: false
tag:
- Java
- Annotation
star: true
category: blog
author: Anantha Raju C
description: Annotations are a form of syntactic metadata that can be added to Java source code. Classes, methods, variables, parameters and packages may be annotated.
---

## Summary:

When Java source code is compiled, annotations can be processed by compiler plug-ins called annotation processors. Processors can produce informational messages or create additional Java source files or resources, which in turn may be compiled and processed.

#### `@Autowired`
- 

---

#### `@EnableCaching`
- Enables Spring Caching functionality

#### `@CacheConfig(cacheNames={"users"})`
- Tells Spring where to store cache for this class

#### `@Cacheable`
- Caches the result of the method

#### `@CachePut`
- Always lets the method execute. It is used to update the cache with the result of the method execution.

#### `@CacheEvict`
- Removes data from from the cache.

#### `@CacheEvict(allEntries = true)`
- Flush all the cache

#### `@CacheEvict(key = "#user.username")`
- Remove item by key

---

#### `@Table`
- Maps the bean to SQL table.

#### `@Column(length = 32)`
- Truncate column values to 32 characters.

#### `@Entity`
- Declares this an entity bean

#### `@GeneratedValue`
- Database will generate new primary keys, not us.

#### `@Id`
- Map this to the primary key column.

#### `@NotEmpty(message = "first name must not be empty")'
-

#### `@Email'
- 

---

