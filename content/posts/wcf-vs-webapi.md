+++ 
draft = false
date = 2020-12-10T15:55:31-05:00
title = "WCF vs WebAPI"
description = "Comparison"
slug = ""
authors = []
tags = []
categories = []
externalLink = ""
series = []
+++


   Scenario | WCF 4.5 | Web API
------------|---------|--------
       Requires support for scenarios like Message queues, end to end message security, duplex communication, distributed transactions, etc.|YES|NO|
       When you already have existing working WCF services and Wants to add HTTP support additionally.|YES|NO|
       One code base to provide support both SOAP and RESTful endpoints.|YES|NO|
       Wants to create a resource-oriented service over HTTP.|NO|YES|
       Your project is an MVC application and wants some functionality over HTTP.|NO|YES|
       You want to build only an HTTP / RESTful services|NO|YES|


