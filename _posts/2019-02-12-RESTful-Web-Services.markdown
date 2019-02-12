---
title: "RESTful Web Services architecture style"
layout: post
date: 2019-02-12 12:30
image: /assets/images/reading.jpg
headerImage: true
tag:
- Web Services
- REST
star: true
category: blog
author: Anantha Raju C
description: RESTful Web Services
---

## Summary:

RESTful Web Services Concepts.

<a href="https://en.wikipedia.org/wiki/Roy_Fielding" target="_blank" >Roy Fielding</a>'s doctoral <a href="https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm" target="_blank" >disseration</a> on Representational State Transfer (REST).

### Classification

- [REST Architectural Constraints](#rest-architectural-constraints)
- [HTTP Methods](http-methods)
- [HTTP Status Codes](#http-status-codes)
- [Resources](#resources)

## REST Architectural Constraints/Guiding Principles

- Client–server
- Stateless
- Cacheable
- Uniform interface
- Layered system
- Code on demand (optional)

## HTTP Methods

- **GET** - (CRUD - Read)
- **PUT** - (CRUD - Update/Replace)
- **POST** - (CRUD - Create)
- **DELETE** - (CRUD - Delete)
- **PATCH** - (CRUD - Partial Update/Modify)
- **HEAD**
- **CONNECT**
- **OPTIONS**
- **TRACE**

## HTTP Status Codes

The following are the top 10 common HTTP status codes and their meaning

- **1xx: Informational** : Communicates transfer protocol-level information.
- **2xx: Success**	     : Indicates that the client’s request was accepted successfully.
- **3xx: Redirection**	 : Indicates that the client must take some additional action in order to complete their request.
- **4xx: Client Error**	 : This category of error status codes points the finger at clients.
- **5xx: Server Error**	 : The server takes responsibility for these error status codes.

---

- **200 OK** - General status code. Most common code used to indicate success.
- **201 Created** - Successful creation occurred (via either POST or PUT). Set the Location header to contain a link to the newly-created resource (on POST). Response body content may or may not be present.
- **204 No Content** - Status when wrapped responses (e.g. JSEND) are not used and nothing is in the body (e.g. DELETE).
- **304 Not Modified** - Used for conditional GET calls to reduce band-width usage. If used, must set the Date, Content-Location, ETag headers to what they would have been on a regular GET call. There must be no body on the response.
- **400 Bad Request** - General error when fulfilling the request would cause an invalid state. Domain validation errors, missing data, etc. are some examples.
- **401 Unauthorized** - Error code response for missing or invalid authentication token.
- **403 Forbidden** - Error code for user not authorized to perform the operation or the resource is unavailable for some reason (e.g. time constraints, etc.)
- **404 Not Found** - Used when the requested resource is not found, whether it doesn't exist or if there was a 401 or 403 that, for security reasons, the service wants to mask.
- **409 Conflict** - Whenever a resource conflict would be caused by fulfilling the request. Duplicate entries and deleting root objects when cascade-delete is not supported are a couple of examples.
- **500 Internal Server Error** - The general catch-all error when the server-side throws an exception.

Relevant Resources 
- <https://www.restapitutorial.com/httpstatuscodes.html>
- IETF <a href="https://www.ietf.org/assignments/http-status-codes/http-status-codes.xml" target="_blank">Hypertext Transfer Protocol (HTTP) Status Code Registry</a>

## Resources

- <a href="https://www.restapitutorial.com/" target="_blank" >REST API Tutorial</a>
- <a href="https://www.w3.org/TR/ws-gloss/" target="_blank" >Web Services Glossary</a> - This document is a glossary of Web services terms defined and used in the Web Services Architecture
- <a href="https://tools.ietf.org/html/rfc7231" target="_blank" >Hypertext Transfer Protocol (HTTP/1.1): Semantics and Content</a>
