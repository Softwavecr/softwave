+++ 
draft = false
date = 2025-02-15T19:45:42-05:00
title = "To microservice or not to microservice, that is the question"
description = "Great discussion on how we can fall in the microservice trap"
slug = ""
authors = []
tags = []
categories = []
externalLink = ""
series = []
+++

## Scenario
You are planning the next sprint, and navigating through the backlog suddenly find 3 stories that seem related

1. New Riders need to __upload__ a profile or avatar __image__.

2. New Drivers need to __upload__ their __drivers licence__.

3. Employees need to __upload__ their __receipts__ for expense reports.

You may consider the idea of having a dedicated file [micro]service solely for handling file storage(pictures). But, 
__do we really need it? Well, it depends__.

## Why not?

1. __Unnecessary Complexity__: A separate file service adds another layer of communication and management, increasing the overall complexity of the system.
2. __Performance Overhead__: Inter-service communication introduces latency, which can negatively impact performance, especially when dealing with large files or frequent file operations.
3. __Maintenance Burden__: Maintaining a dedicated file service requires additional effort in terms of development, deployment, and monitoring.
4. __Reinventing the Wheel__: Cloud storage providers offer mature and highly optimized solutions for file management, making a custom service redundant.

## Although

While a dedicated file service might not always be the best solution, there are specific scenarios where it could be justified:

1. __Complex File Processing__: If the application requires extensive file manipulation (e.g., image processing), a dedicated service might be useful to offload these tasks from the main application.
2. __Abstraction and Encapsulation__: A file service can provide a layer of abstraction, shielding the application from the specifics of the underlying storage implementation. This can be beneficial if you anticipate needing to switch storage providers in the future.
3. __Security and Access Control__: In some cases, a file service might be used to enforce specific security policies or access control rules for file storage.

# In Short
While not a universally applicable rule, the advice to avoid creating a file [micro]service in most cases is sound.  However, the counters explore the exceptions and nuances of the issue, adding valuable context.
As with any architectural decision, careful consideration of the specific requirements and constraints of the project is crucial.