---
title: "HTTP vs SOAP vs REST"
date: 2020-12-15T13:24:06-05:00
draft: true
---

## Summary

HTTP is a communications __protocol__ that transports messages over a network.

REST is a __set of rules__ to exchange any(e.g. XML, JSON) messages that can use HTTP for transport.

SOAP is a __protocol__ to exchange XML-based messages that may use HTTP for transport. 

## Dive-in

# HTTP
The Hypertext Transfer Protocol (HTTP) is an application layer protocol for distributed, collaborative, hypermedia information systems. HTTP is the foundation of data communication for the World Wide Web, where hypertext documents include hyperlinks to other resources that the user can easily access, for example by a mouse click or by tapping the screen in a web browser.

HTTP Request / Response
Communication between clients and servers is done by requests and responses:

1. A client (a browser) sends an HTTP request to the web
2. An web server receives the request
3. The server runs an application to process the request
4. The server returns an HTTP response (output) to the browser
5. The client (the browser) receives the response

# REST
REpresentational State Transfer, or REST, is a set of constraints that ensure a scalable, fault-tolerant and easily extendible system. The world-wide-web is an example of such system (and the biggest example, one might say). REST by itself is not a new invention, but it's the documentation on such systems like the world-wide-web.

One thing that confuses people, is that REST and HTTP seem to be hand-in-hand. After all, the world-wide-web itself runs on HTTP, and it makes sense, a RESTful API does the same. However, there is nothing in the REST constraints that makes the usage of HTTP as a transfer protocol mandatory. It's perfectly possible to use other transfer protocols like SNMP, SMTP and others to use, and your API could still very well be a RESTful API

In practice, most - if not all - RESTful APIs currently use HTTP as a transport layer, since the infrastructure, servers and client libraries for HTTP are widely available already

REST is easier to use for the most part and is more flexible. Advantages vs SOAP:

* Uses easy to understand standards like swagger and OpenAPI Specification 3.0
* Smaller learning curve
* Efficient (SOAP uses XML for all messages, REST mostly uses smaller message formats like JSON)
* Fast (no extensive processing required)
* Closer to other Web technologies in design philosophy

Architectural Layer view:
1. Client-server architecture – the client is responsible for the user interface, and the server is responsible for the backend and data storage. Client and server are independent of each other, and each of them can be replaced separately.
2. Stateless – no data from the client is stored on the server-side. The session state is stored on the client-side.
3. Cacheable – clients can cache server responses to improve performance.
* 4 Layered system - 5 Code on demand - 6 Uniform interface


# SOAP
SOAP (formerly an acronym for Simple Object Access Protocol) is a messaging protocol specification for exchanging structured information in the implementation of web services in computer networks. Its purpose is to provide extensibility, neutrality, verbosity and independence. It uses XML Information Set for its message format, and relies on application layer protocols, most often Hypertext Transfer Protocol (HTTP), although some legacy systems communicate over Simple Mail Transfer Protocol (SMTP), for message negotiation and transmission.

SOAP has three major characteristics:

* Extensibility (security and WS-Addressing are among the extensions under development)
* Neutrality (SOAP can operate over any protocol such as HTTP, SMTP, TCP, UDP)
* Independence (SOAP allows for any programming model)


## COROLARY
Note that there is also a big difference between a RESTful API and a HTTP API. A RESTful API adheres ALL the REST constraints set out in its "format" documentation (in the dissertation of Roy Fielding). A HTTP API is ANY API that makes use of HTTP as their transfer protocol. This means that even SOAP can be considered a HTTP API, as long as it will use HTTP for transport, but most HTTP APIs will make more and better use of the infrastructure and possibilities of HTTP. Most HTTP APIs can be very close to becoming a truly RESTful API. This can be defined by their Richardsons maturity level.


## REFERENCE
* [REST Dissertation by RT Fielding](https://www.ics.uci.edu/~fielding/pubs/dissertation/abstract.htm)
* [Are REST and HTTP the same thing?](https://restcookbook.com/Miscellaneous/rest-and-http)