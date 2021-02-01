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

In order to build great web applications, I recommend to follow the Clean Architecture Template: developers and customers will appreciate this decision given its readability, scalability, and maintainability, which will translate into efficiency and a positive cost/benefit ratio.

![Solution Architecture](/images/CA.png)


0. Prerequites:
    * 0.1. IDE(VS Code, Vim, or Notepad)
    * 0.2. Net Core SDK (3.1+)
    * 0.3. Node.js
    * 0.4. Git	
1. $ dotnet new --install Clean.Architecture.Solution.Template::1.1.4 to install the project template

2. $ mkdir "NAME" and cd into it (choose "NAME", this will be assigned to the project)

3. $ dotnet new ca-sln to create a new project

4. $ export ASPNETCORE_Environment=Development

5. $ cd src/WebUI

6. $ dotnet build

7. $ dotnet run

8. $ cd ClientApp

9. $ npm start

Then browse https://localhost:5001

At this point we want to create our custom work, in this case we will create a Contact management page.

For this purpose we need to create the DBTable script, Entity, DTO and Events to handle CRUD actions. 

https://github.com/Softwavecr/jCoreDemoApp/pull/3/commits/a0592878af6405bf625b5ff7d4c41bb7152044ec
https://github.com/Softwavecr/jCoreDemoApp/pull/3/commits/f41a03b25ff4f42426151b5f18bcfdd1d174d1a7
https://github.com/Softwavecr/jCoreDemoApp/pull/3/commits/9d3c77377f80697a6502cb0e8ffbf877b128b06d

Finally, we will have to create the Front End, in this case, via Angular 10 CLI:

open a console and navigate to the app folder and run

$ ng generate component contact --module app.module

The --module parameter might not be necessary, it was in my case(notice that it is  two dashes not one).


![Solution Architecture](/images/dependency_diagramX.png)

## REFERENCE
* [ASP.NET Core 3.1 - Simple API for Authentication (09/2020)](https://jasonwatmore.com/post/2019/10/14/aspnet-core-3-simple-api-for-authentication-registration-and-user-management)
* [The Clean Code Blog (08/2012)](http://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html)
* [Clean Architecture (09/2020)](https://github.com/jasontaylordev/CleanArchitecture)




