---
description: Where Node.js Should Be Used? and Where Node.js Shouldn’t Be Used?
---

# Where Node.js Fits?





```bash
# Where Node.js Should Be Used
- Any 'I/O bound Applications' [read/write (files, database), network/socket connections]
- becuase 'Non-Blocking IO operation' helps to build ('Highly Scalable') WebApp

- "Server-Side Web Applications"
    # Examples:
    
    - Real-Time Chat Application
    - API based Application - on top of Object DB (Mongo DB)
    - Proxy Application (Just Pass Through)
    - Queued Inputs Application
    - Data Streaming Application
    - Data Intensive Real-time Applications (DIRT)
       - Brokerage - Stock Trader’s Dashboard
       - Application Monitoring Dashboard
       - System Monitoring Dashboard

# Where Node.js Shouldn’t Be Used
- Heavy "ServerSide Computation" - "CPU-Intensive" Operations 
    # Examples:
    - Video Games, VideoProcessing (Editing, Converting), ImageProcessing
    - Complex Algorithms, Fibonacci computations



```

###  <a id="examples-of-where-nodejs-should-be-used"></a>

## Where Node.js Should Be Used

### Server-Side Web Applications

Node.js with Express.js can also be used to create classic web applications on the server-side. However, while possible, this request-response paradigm in which Node.js would be carrying around rendered HTML is not the most typical use-case. There are arguments to be made for and against this approach. Here are some facts to consider:

Pros:

* If your application doesn’t have any CPU intensive computation, you can build it in Javascript top-to-bottom, even down to the database level if you use JSON storage Object DB like MongoDB. This eases development \(including hiring\) significantly.
* Crawlers receive a fully-rendered HTML response, which is far more SEO-friendly than, say, a Single Page Application or a websockets app run on top of Node.js.

Cons:

* Any CPU intensive computation will block Node.js responsiveness, so a threaded platform is a better approach. Alternatively, you could try scaling out the computation \[\*\].
* Using Node.js with a relational database is still quite a pain \(see below for more detail\). Do yourself a favour and pick up any other environment like Rails, Django, or ASP.Net MVC if you’re trying to perform relational operations.

_\[\*\] An alternative to these CPU intensive computations is to create a highly scalable MQ-backed environment with back-end processing to keep Node as a front-facing ‘clerk’ to handle client requests asynchronously._

## Examples of Where Node.js Should Be Used

### Real-Time Chat Application

Chat is the most typical real-time, multi-user application. From IRC \(back in the day\), through many proprietary and open protocols running on non-standard ports, to the ability to implement everything today in Node.js with websockets running over the standard port 80.

The chat application is really the sweet-spot example for Node.js: it’s a lightweight, high traffic, data-intensive \(but low processing/computation\) application that runs across distributed devices. It’s also a great use-case for learning too, as it’s simple, yet it covers most of the paradigms you’ll ever use in a typical Node.js application.

Let’s try to depict how it works.

In the simplest example, we have a single chatroom on our website where people come and can exchange messages in one-to-many \(actually all\) fashion. For instance, say we have three people on the website all connected to our message board.

On the server-side, we have a simple Express.js application which implements two things:

1. A `GET /` request handler which serves the webpage containing both a message board and a ‘Send’ button to initialize new message input, and
2. A websockets server that listens for new messages emitted by websocket clients.

On the client-side, we have an HTML page with a couple of handlers set up, one for the ‘Send’ button click event, which picks up the input message and sends it down the websocket, and another that listens for new incoming messages on the websockets client \(i.e., messages sent by other users, which the server now wants the client to display\).

When one of the clients posts a message, here’s what happens:

1. Browser catches the ‘Send’ button click through a JavaScript handler, picks up the value from the input field \(i.e., the message text\), and emits a websocket message using the websocket client connected to our server \(initialized on web page initialization\).
2. Server-side component of the websocket connection receives the message and forwards it to all other connected clients using the broadcast method.
3. All clients receive the new message as a push message via a websockets client-side component running within the web page. They then pick up the message content and update the web page in-place by appending the new message to the board.

![Diagram of client and server websockets in a Node.js application](https://uploads.toptal.io/blog/image/52/toptal-blog-2_B.png)

This is the [simplest example](http://net.tutsplus.com/tutorials/javascript-ajax/real-time-chat-with-nodejs-socket-io-and-expressjs/). For a more [robust solution](http://jinzhang.me/posts/2013/sockjs-redis-nodejs-tutorial/), you might use a simple cache based on the Redis store. Or in an even more advanced solution, a message queue to handle the routing of messages to clients and a more robust delivery mechanism which may cover for temporary connection losses or storing messages for registered clients while they’re offline. But regardless of the improvements that you make, Node.js will still be operating under the same basic principles: reacting to events, handling many concurrent connections, and maintaining fluidity in the user experience.

### API based Application - on top of Object DB

Although Node.js really shines with real-time applications, it’s quite a natural fit for exposing the data from object DBs \(e.g. MongoDB\). JSON stored data allow Node.js to function without the impedance mismatch and data conversion.

For instance, if you’re using Rails, you would convert from JSON to binary models, then expose them back as JSON over the HTTP when the data is consumed by Backbone.js, Angular.js, etc., or even plain jQuery AJAX calls. With Node.js, you can simply expose your JSON objects with a REST API for the client to consume. Additionally, you don’t need to worry about converting between JSON and whatever else when reading or writing from your database \(if you’re using MongoDB\). In sum, you can avoid the need for multiple conversions by using a uniform data serialization format across the client, server, and database.

### Proxy Application \(Just Pass Through\)

Node.js is easily employed as a server-side proxy where it can handle a large amount of simultaneous connections in a non-blocking manner. It’s especially useful for proxying different services with different response times, or collecting data from multiple source points.

An example: consider a server-side application communicating with third-party resources, pulling in data from different sources, or storing assets like images and videos to third-party cloud services.

Although dedicated proxy servers do exist, using Node instead might be helpful if your proxying infrastructure is non-existent or if you need a solution for local development. By this, I mean that you could build a client-side app with a Node.js development server for assets and proxying/stubbing API requests, while in production you’d handle such interactions with a dedicated proxy service \(nginx, HAProxy, etc.\).

### Queued Inputs Application

If you’re receiving a high amount of concurrent data, your database can become a bottleneck. As depicted above, Node.js can easily handle the concurrent connections themselves. But because database access is a blocking operation \(in this case\), we run into trouble. The solution is to acknowledge the client’s behavior before the data is truly written to the database.

With that approach, the system maintains its responsiveness under a heavy load, which is particularly useful when the client doesn’t need firm confirmation of a the successful data write. Typical examples include: the logging or writing of user-tracking data, processed in batches and not used until a later time; as well as operations that don’t need to be reflected instantly \(like updating a ‘Likes’ count on Facebook\) where [eventual consistency](http://www.allthingsdistributed.com/2007/12/eventually_consistent.html) \(so often used in NoSQL world\) is acceptable.

Data gets queued through some kind of caching or message queuing infrastructure—like RabbitMQ or ZeroMQ—and digested by a separate database batch-write process, or computation intensive processing backend services, written in a better performing platform for such tasks. Similar behavior can be implemented with other languages/frameworks, but not on the same hardware, with the same high, maintained throughput.

![Diagram of a database batch-write in Node.js with message queuing](https://uploads.toptal.io/blog/image/53/toptal-blog-3_B.png)

In short: with Node, you can push the database writes off to the side and deal with them later, proceeding as if they succeeded.

### Data Streaming Application

In more traditional web platforms, HTTP requests and responses are treated like isolated event; in fact, they’re actually streams. This observation can be utilized in Node.js to build some cool features. For example, it’s possible to process files while they’re still being uploaded, as the data comes in through a stream and we can process it in an online fashion. This could be done for [real-time audio or video encoding](https://transloadit.com/blog/2010/12/realtime-encoding-over-150x-faster), and proxying between different data sources \(see next section\).

### Data Intensive Real-time Applications \(DIRT\)

#### BROKERAGE - STOCK TRADER’S DASHBOARD <a id="brokerage---stock-traders-dashboard"></a>

Let’s get back to the application level. Another example where desktop software dominates, but could be easily replaced with a real-time web solution is brokers’ trading software, used to track stocks prices, perform calculations/technical analysis, and create graphs/charts.

Switching to a real-time web-based solution would allow brokers to easily switch workstations or working places. Soon, we might start seeing them on the beach in Florida.. or Ibiza.. or Bali.

#### APPLICATION MONITORING DASHBOARD <a id="application-monitoring-dashboard"></a>

Another common use-case in which Node-with-web-sockets fits perfectly: tracking website visitors and visualizing their interactions in real-time.

You could be gathering real-time stats from your user, or even moving it to the next level by introducing targeted interactions with your visitors by opening a communication channel when they reach a specific point in your funnel. _\(If you’re interested, this idea is already being productized by_ [_CANDDi_](http://canddi.com/)_.\)_

Imagine how you could improve your business if you knew what your visitors were doing in real-time—if you could visualize their interactions. With the real-time, two-way sockets of Node.js, now you can.

#### SYSTEM MONITORING DASHBOARD <a id="system-monitoring-dashboard"></a>

Now, let’s visit the infrastructure side of things. Imagine, for example, an SaaS provider that wants to offer its users a service-monitoring page, like GitHub’s status page. With the Node.js event-loop, we can create a powerful web-based dashboard that checks the services’ statuses in an [asynchronous](https://www.toptal.com/javascript/asynchronous-javascript-async-await-tutorial) manner and pushes data to clients using websockets.

Both internal \(intra-company\) and public services’ statuses can be reported live and in real-time using this technology. Push that idea a little further and try to imagine a [Network Operations Center \(NOC\)](https://en.wikipedia.org/wiki/Network_operations_center) monitoring applications in a telecommunications operator, cloud/network/hosting provider, or some financial institution, all run on the open web stack backed by Node.js and websockets instead of Java and/or Java Applets._Note: Don't try to build hard real-time systems in Node \(i.e., systems requiring consistent response times\)._ [_Erlang is probably a better choice_](http://nodeguide.com/convincing_the_boss.html) _for that class of application._

###  <a id="where-nodejs-can-be-used"></a>

####  <a id="server-side-web-applications"></a>

## Where Node.js Shouldn’t Be Used

### Heavy "ServerSide Computation" - "CPU-Intensive" Operations

When it comes to heavy computation, Node.js is not the best platform around. No, you definitely don’t want to build a [Fibonacci computation server in Node.js](http://zef.me/4561/node-js-and-the-case-of-the-blocked-event-loop). In general, any `CPU intensive operation` annuls all the throughput benefits Node offers with its event-driven, non-blocking I/O model because any incoming requests will be blocked while the thread is occupied with your number-crunching—assuming you’re trying to run your computations in the same Node instance you’re responding to requests with.

As stated previously, Node.js is `single-threaded` and uses only a `single CPU core`. When it comes to adding concurrency on a `multi-core server`, there is some work being done by the Node core team in the form of a `cluster module` \[ref: http://nodejs.org/api/cluster.html\]. You can also run several Node.js server instances pretty easily behind a [reverse proxy via nginx](http://blog.argteam.com/coding/hardening-node-js-for-production-part-2-using-nginx-to-avoid-node-js-load/).

With clustering, you should still offload all heavy computation to background processes written in a more appropriate environment for that, and having them communicate via a message queue server like `RabbitMQ`.

Even though your background processing might be run on the same server initially, such an approach has the potential for very high scalability. Those background processing services could be easily distributed out to separate worker servers without the need to configure the loads of front-facing web servers.

Of course, you’d use the same approach on other platforms too, but with Node.js you get that high reqs/sec throughput we’ve talked about, as each request is a small task handled very quickly and efficiently.

### Server-Side Web Application W/ A Relational Db Behind

In olden days, Relational DB tools for Node.js were limited. On the other hand, Java, Python, Rails has much more better support

But now things have changed. [Sequelize](http://sequelizejs.com/), [TypeORM](https://github.com/typeorm/typeorm), and [Bookshelf](https://github.com/bookshelf/bookshelf) have gone a long way towards becoming mature ORM solutions.  Now Node.js also has capability to generate SQL from GraphQL queries using [Join Monster](https://github.com/acarl005/join-monster)



## Conclusion

We’ve discussed Node.js from theory to practice, beginning with its goals and ambitions, and ending with its sweet spots and pitfalls. When people run into problems with Node, it almost always boils down to the fact that **blocking operations are the root of all evil**—99% of Node misuses come as a direct consequence.

