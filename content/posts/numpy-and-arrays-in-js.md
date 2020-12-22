---
title: "Numpy and Arrays in Js"
date: 2020-12-22T15:48:59-05:00
draft: true
---

ASYNCHRONOUS FUNCTIONS

In Python 3.4+, asynchronous functions are supported by the asyncio library.

Comparison by Topic,	JavaScript,	Python

define async named function	
    async function fnName(params) { ... }	
    
    async def fnName(params):

define async anonymous function	
    const fnName = async (params) => { ... }	
    
    not supported

async call with await	
    const result = await name(args); #often wrapped in a try block	
    
    result = await name(args)

async call with then and catch	
    name(args).
    then(result => { ... }).
    catch(err => { ...});	

    n/a