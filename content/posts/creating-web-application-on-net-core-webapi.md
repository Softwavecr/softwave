+++ 
draft = true
date = 2021-01-30T20:11:48-05:00
title = "Developing with .Net + WebAPI and Clean Architecture"
description = ""
slug = ""
authors = []
tags = []
categories = []
externalLink = ""
series = []
+++

## Summary

In order to build great web applications, I recommend to follow the Clean Architecture Template: developers and customers will appreciate this decission given its readibility, scalability, and maintainability, which will translate to efficiency and a positive cost/benefit outcome.

![Solution Architecture](/images/CA.png)


0. Prerequites:
    * 0.1. IDE(VS Code, Vim, or Notepad)
    * 0.2. Net Core SDK (3.1+)
    * 0.3. Node.js
    * 0.4. Git	
1. $ dotnet new --install Clean.Architecture.Solution.Template::1.1.4 to install the project template
2. Create a folder for your solution and cd into it (the template will use its name as project name)
3. $ dotnet new ca-sln to create a new project
4. $ export ASPNETCORE_Environment=Development
5. $ cd src/WebUI
6. $ dotnet build
7. $ dotnet run
8. $ cd ClientApp
9. $ npm start

Then browse https://localhost:5001

At this point we want to create our custom work, in this case we will create a Contact management page.

For this purpose we need to create the Entity, DTO and Events to handle CRUD actions. 

Finally, we will have to create the Front End, in this case, via Angular 10 CLI:

 open a console and navigate to thje app folder and run

 $:~/jCoreDemoApp/src/WebUI/ClientApp/src/app$ ng generate component contact --module app.module

The --module parameter might not be necessary, it was in my case(notice that it is  two dashes not one).


![Solution Architecture](/images/dependency_diagramX.png)

## REFERENCE
* [ASP.NET Core 3.1 - Simple API for Authentication (09/2020)](https://jasonwatmore.com/post/2019/10/14/aspnet-core-3-simple-api-for-authentication-registration-and-user-management)
* [The Clean Code Blog (08/2012)](http://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html)
* [Clean Architecture (09/2020)](https://github.com/jasontaylordev/CleanArchitecture)




