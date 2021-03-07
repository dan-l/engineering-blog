# Web API

Application Programming Interface (API) is a way for programs to talk to each other. It defines the interactions that can be exchange between 2 programs.

Most data-driven applications have Web APIs to manipulate their data. The Web API will define a collection of endpoints communicated via request-response style messages and is commonly exposed via a HTTP-based web server.  2 common types of HTTP API are REST and RPC.


### [REST](https://www.restapitutorial.com/lessons/whatisrest.html)

Great for modelling your domain with CRUD operations, although it is not only restricted to this purpose.

Constraints of a REST architecture

- Uniform interface

Individual resources are identified in requests using URI as resouce identifiers.
Client delivers state via body contents, query-string params, request headers and requested URI.
Service delivers state to client via body contents, response codes, and response headers.

- Stateless

State can vary across clients and it is not scalable for services to have to maintain that. Concept like session are used to maintain state across multiple requests. Client will include the state on each request, resending them to server.

- Cacheable

Client can cache responses so services should define if responses are cacheable and for how long. This can eliminate client-server interaction and further improve performance and scalability.

- Client-Server

Uniform interface decouples client and server so that they each are responsible for their own domain and can be developed independently.

- Layered System

Client should not assume it is connected to the end system because intermediate servers can be deployed with load balancing for scalability.

- Code on Demand (optional)


### Remote Procedure Call (RPC)

RPCs are like function calls in the context of HTTP API. The method name would be in URL and the params are in query string or body. Great when you are doing actions but are not necessarily tie to updating a resource.


### Cookies

- Mechanism to have state in http request/response
- Once server set, browser will return cookie on subsequent requests


### Follow up
Cross origin resource sharing



