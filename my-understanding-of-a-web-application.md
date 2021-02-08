#Full stack with web application

What does a web app typically consist of ? Front End and Back End.

What is Front End? It is usually the web browsers where the users of your application will see and interact with.

What is Back End? It is usually the server that will service the requests for your web application, which can be when user first enter the url of your website to get the initial HTML page and your Front End starts handling user interaction, sending request to the server to process and return a response. The most common communication protocol for Web app is HTTP.

A web server is needed to service requests from your users. It usually contains the application that handles the business logic and computation of a request. The server usually listens to a particular port on the machine.

###Front End Architecture
------
When your HTML page is served, it will contain the document object model (DOM) which describes the UI structure of your application that your user will see. It contains CSS script that describes the style of the DOM elements and Javascript that handles the logic of your application and user interaction with it. Without JS, your page will just be static content that user will not be able to interact with. There are 2 types of UI application, single page application (SPA) and multi page application. SPA loads the HTML once from the server and will handle the remaining of logic and interaction entirely on the front end. Multi page application will refresh and fetch a new page of html every time it needs something from the server.
Any SPA with enough complexity on the front end will be using the help of a UI framework. A UI framework typically consist of **router**, **store**, **components**.

**Router:** define different routes an application will have, and provide a handler for each route that an application might transition into. The definition of SPA is that it contains only 1 html page, which is tied to a url, so navigation of pages on SPA is just an illusion that updates the hash of the url (see HTML5 history API) which does not trigger a page refresh.

**State:** An application will usually have state, whether it’s global or local. A popular that is used to store state right now is a globally available singleton store. The reason is because it promotes having single source of truth, which can avoid multiple component holding multiple copies of the same data that can get stale and hard to keep in sync.

**Component:** There can be many parts to a SPA UI which we can logically group each section as a component. The benefit of having a component is that we can encapsulate logic within a component and design them in a reusable way so that the same component can have different configuration and be powered by different types of data. A component will typically have to talk to each other. So it will receive inputs from other components as well as feeding its output to other components.

**Data flow:** To make it easier to reason data flow, we usually follow the pattern of using one way data flow instead of both ways, which could quickly increase the number of communication channels needed between components in the app. So data flows from parent to child and also from global store to components. Inputs will usually be passed into components as parameters when we create a component. Then children components will passed back information as needed through even emitters to parent components. The benefit is child component does not need to know about their parents as it just triggers an event and the parent component can handle the events using the same pattern of DOM event handling.

**Server communicate:** Instead of requesting for a new html page, SPA uses AJAX which asynchronously communicate with server so that the main thread is not blocked from receiving user input.

_Other topics to cover: Local storage, cookies, security_

###Back End Architecture
------
Back end is where the web server that services client request and the database server that stores application data resides at.

**Web server:** To service a request, the application will have to define a handler for a particular url route to the application. Application will need to be mindful of how long a request can take.
Tasks: If there is a non urgent and computationally expensive task in a request, it would be better to farm that out to a task in the background, so that the handler can process the next request.

**Load balancer:** Having a single web server might not be scalable to millions of requests, and vertical scaling has a ceiling, so there will be times where you will need more than 1 server. In cases like that, you would also need to handle which server a particular request will be going to. This is where we can use a load balancer to distribute the requests among a group of servers. Multiple servers also help avoid single point of failure. Reverse proxy can also be used to beef up security by having a public facing IP that is not your servers, that way you can also change up your server configurations without affecting the main website.

**Database :** Application needs to persist data so it is written to the database (DB) that stores it on the disk. Instead of 1 database which is prone to single point of failure, we should have a master DB and multiple slaves DB. We can even go further to have write DBs and read DBs to avoid contention on reading and writing.A write to the master write DB will stream the data to the write slaves and read slaves.

**Sharding:** There will be a time where having 1 master DB does not scale vertically, so you will need more than 1 master DB. Sharding will be needed to distribute data across multiple DBs and to be able to get query them successfully. A consistent sharing algorithm should be used to ensure shard count does not affect the computed shard number so that a piece of data will always belong to the same shard number.

**Logging:** Application will also proactively log the operations it does, especially on the unexpected cases. It is always good to do that because if there is ever a need to troubleshoot later, these are usually critical information and the only information you would have snapshotted at the time of the incidents. In a complex application, we would have log servers that takes the log output and does additional processing or tagging that enables further analysis on the output.

**Monitoring:** As we build software systems, we would also want to monitor the health of the system. This can help alert us of potential issues or areas of improvement, and diagnose problems quicker before system is crippled. Examples of monitoring can be by integrating log outputs with chart analysis, tracking status code of the client responses, measuring the latency of api requests. For each of these metrics, we can set up a threshold after measuring the baseline of your system and sent out alerts when threshold is exceeded.

_Other topics to cover: Caching, gzip compression, static files, error handling. Users, sessions. Full text search. CDN. database queries._
