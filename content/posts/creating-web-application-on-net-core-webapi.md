+++ 
draft = true
date = 2021-01-30T20:11:48-05:00
title = "Creating web application on net core webapi"
description = ""
slug = ""
authors = []
tags = []
categories = []
externalLink = ""
series = []
+++

## Summary

Follow the Clean Architecture Template for a well desgined, scalable, and maintainable solution.

0. Prerequites:
    * 0.1. IDE(VS Code, Vim, or Notepad)
    * 0.2. Net Core SDK (3.1+)
    * 0.3. Node.js
    * 0.4. Git	
1. Run 
dotnet new --install Clean.Architecture.Solution.Template to install the project template
2. Create a folder for your solution and cd into it (the template will use it as project name)
3. Run dotnet new ca-sln to create a new project
3. The server returns an HTTP response (output) to the browser
4. The client (the browser) receives the response


```js {linenos=table,linenostart=0}
const https = require('https');

https.get('https://api.nasa.gov/planetary/apod?api_key=DEMO_KEY', (resp) => {
  let data = '';

  // A chunk of data has been received.
  resp.on('data', (chunk) => {
    data += chunk;
  });

  // The whole response has been received. Print out the result.
  resp.on('end', () => {
    console.log(JSON.parse(data).explanation);
  });

}).on("error", (err) => {
  console.log("Error: " + err.message);
});
```

# Context: AWS API Gateway
API Gateway is a managed service that makes it easier to manage the APIs (creating, publishing, and maintaining secure APIs). API gateway has become one of the pillars of the microservices and serverless architectures. It comes in 3 flavors:

# WebSocket API
Build a WebSocket API using persistent connections for real-time use cases such as chat applications or dashboards.
Works with the following:
Lambda, HTTP, AWS Services

# HTTP API
Build low-latency and cost-effective REST APIs with built-in features such as OIDC and OAuth2, and native CORS support.
Works with the following:
Lambda, HTTP backends

# REST API
Develop a REST API where you gain complete control over the request and response along with API management capabilities.
Works with the following:
Lambda, HTTP, AWS Services

## Monthly costs
## REST 
Requests        | Price    |
----------------|----------|
        0 - 333 | $3.50    |
       334 - 1M | $2.80    |
## HTTP
Requests        | Price    |
----------------|----------|
        0 - 300 | $1.00    |
       301 - 1M | $0.90    |

## REFERENCE
* [ASP.NET Core 3.1 - Simple API for Authentication (09/2020)](https://jasonwatmore.com/post/2019/10/14/aspnet-core-3-simple-api-for-authentication-registration-and-user-management)
* [The Clean Code Blog (08/2012)](http://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html)
* [Clean Architecture (09/2020)](https://github.com/jasontaylordev/CleanArchitecture)




