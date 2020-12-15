---
title: "AWS API Gateway: HTTP vs REST"
date: 2020-12-15T15:51:53-05:00
draft: true
---

## Summary

HTTP is 70% faster, and way cheaper, but lacks most of features from REST and WebSockets, therefore, choose HTTP if WebSockets were not required, nor REST API features.

![Decission Making](/images/aws-api-http-rest.png)

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
* [AWS API Gateway: HTTP vs REST (09/2020)](https://www.learnaws.org/2020/09/12/rest-api-vs-http-api/)
* [Building faster, lower cost, better APIs – HTTP APIs now generally available (09/2020)](https://aws.amazon.com/blogs/compute/building-better-apis-http-apis-now-generally-available/)
* [Choosing between HTTP APIs and REST APIs (04/2019+?)](https://docs.aws.amazon.com/apigateway/latest/developerguide/http-api-vs-rest.html)
* [Introducing HTTP APIs: A Better, Cheaper, Faster Way to Build APIs (04/2020)](https://pages.awscloud.com/Introducing-HTTP-APIs-A-Better-Cheaper-Faster-Way-to-Build-APIs_2020_0304-SRV_OD.html)
* [FAQs](https://aws.amazon.com/api-gateway/faqs/)
* [AWS API Gateway By Example](https://codeburst.io/aws-api-gateway-by-example-3733d7792635)

