# Why Node.js?

## **Intro**

```javascript
Node.js uses 'single-threaded', 'event-driven', 'asynchronous' programming approach
---- to handle 'Non-Blocking IO' operations efficiently ----
```

```javascript
// Why do we need it?
To create 'Highly Scalable -Web Aplications'

// How it helps the Application?
1. Node.js was created to solve the 'I/O scaling problem' (not compute scaling) 
2. Node.js provides 'Non-Blocking I/O Operations'
    - 'Asynchronous I/O operations' at OS level [open/read/write -files/db/network connections]
    - This helps to create 'Highly Scalable aplications' (capable of handling a huge number of simultaneous n/w connections)

// How it helps the team / company?    
- "JavaScript across the Stack"
    - makes software development process simple (including hiring, reuse developer resources)
    - share code between the browser and your backend
```

```javascript
// Where is it suitable?  
- Any I/O bound Applications [read/write (files, database), network/socket connections]
    - becuase 'Non-Blocking IO operation' helps to build (Highly Scalable) WebApp

// Where is it NOT suitable?  
- Node.js is NOT suitable for more "CPU-Intensive" Operations
    - `like Games, VideoProcessing (Editing, Converting), ImageProcessing`
```

## Why do we need `'Non-Blocking I/O'`  ?

* IO operations are very much slower than data processing.
* Our applications spend most of their time waiting for IO operations \(reading/writing the disk or network communications\)
* _**For example:**_ 
  * Reading just one KB of data would take 1.4 microseconds, 
    * with CPU: 2GHz and SSD: read speed of 200-730 MB/s
    * but during this time a CPU could have performed 28000 of instruction-processing cycles.
  * For network communications it can be even worse, just try and ping google.com
    * The average latency is about 44 milliseconds. 
    * Just while waiting for a packet to make a round-trip on the wire, 
    * the previously mentioned processor can perform 88 millions of cycles.

```text
$ ping google.com
64 bytes from 172.217.16.174: icmp_seq=0 ttl=52 time=33.017 ms
64 bytes from 172.217.16.174: icmp_seq=1 ttl=52 time=83.376 ms
64 bytes from 172.217.16.174: icmp_seq=2 ttl=52 time=26.552 ms
64 bytes from 172.217.16.174: icmp_seq=3 ttl=52 time=40.153 ms
64 bytes from 172.217.16.174: icmp_seq=4 ttl=52 time=37.291 ms
64 bytes from 172.217.16.174: icmp_seq=5 ttl=52 time=58.692 ms
64 bytes from 172.217.16.174: icmp_seq=6 ttl=52 time=45.245 ms
64 bytes from 172.217.16.174: icmp_seq=7 ttl=52 time=27.846 ms
```

Similarly programming languages like Java or Python uses **MultiThreading** to achieve this functionality. For example reading a file synchronously in Java or Python is a blocking operation. Your program cannot do anything else while it is waiting for the network / disk communication to finish. All you can do is to fire up a different thread then notify your main thread when the operation has finished. It is tedious, complicated, but gets the job done. 



**Solution:** is to `use 'Asynchronous IO'` operations

Most Operating Systems \(OS\) provide some kind of an **Asynchronous IO** interface, In this model _open/read/write_ operation on devices and resources \(sockets, filesystem, etc.\) managed by the file-system don't block the calling thread  and just mark the process \(in kernel/OS level data structure\). Once the requested data or events are available, it will send a notification.

## Why Node.js, why not other languages?

We saw using `'Asynchronous IO'` operations helps to avoid blocking \(or waiting time\) for the resources.

* **Java** also has **NIO** modules to handle Non-Blocking IO and Asynchronous IO operations.
* Because of its Multi-Threaded nature, It is **very complex** to handle the threads and asynchronous operations
* And also **Cost of MultiThreading** is **much higher** in terms of Context switching and Memory Hogging

whereas, Node.js uses `Single-Threaded` - `Event-Driven` approach makes it easier to achieve **Non-Blocking IO**

```bash

# Every Node application runs on a 'single thread' 
 - only one task/event is processed at a time
 - You can imagine this event loop to be a queue of callbacks that are processed by Node on every 'tick' of the event loop. 

# For every I/O bound task, 
you can simply define a callback that will get added to the event queue. 
 - The callback will fire when the I/O operation is done, 
and in the mean time, 
 - the application can continue to process other I/O bound requests without blocking the other request
 
```

* **Single-Threaded:** approach helps to avoid code accessing the same resources at the same time
* **Event-Driven:** approach makes it easier to write and understand `asynchronous code` via 'callbacks'
  * Event-Driven approach is nothing but registering the ‘Event’ and callback functions gets called when the event occurs. `[who is invoking the callback? its 'EventLoop']`
  * This approach makes it easier to achieve Asynchronous IO operations



> Sometimes this single threaded, async nature does make things complicated. But do you honestly think it's more complicated than threading? One race condition can ruin your entire month! Or empty out your thread pool due to some setting somewhere and watch your response time slow to a crawl! Not to mention deadlocks, priority inversions, and all the other gyrations that go with multithreading.

## How Node.js achieved `'Non-Blocking I/O'` ?

```javascript
- Node.js uses 'libuv', it helps to perform 'Asynchronous I/O operations' at OS level.
- Node.js is 'single-threaded', 'non-blocking', 'event-driven' programming
- It handles 'asynchronous' operations via 'callbacks/promises'
- 

This helps to achieve 'very memory efficient'
```

## Why Node.js team decided to use JavaScript ?

* because JavaScript is 

```bash
## 1. Single Threaded 
## 2. Easy to Handle Asynchronous operations
    - It uses simple 'event-driven' & 'callbacks' approach to handle asynchronous operations
    - This approach is much easier than multi-thread approach
    - Also Cost of mutlithreading is much higher interms of Context switching and Memory Hogging
```

* Node.js was created to solve the 'I/O scaling problem' \(not compute scaling\)
* Node.js was created explicitly as an experiment in async processing.  
* Doing async processing on a single thread could provide more performance and scalability under typical web loads than the typical thread-based implementation. Node.js can run thousands more concurrent connections than Apache or IIS or other thread-based servers.

## How `'Single-Threaded'`  `'Non-Blocking I/O'` helps to create 'Highly Scalable application'?

```bash
#In Traditional approach,
- "Each Request creates a - New Thread" 
- Once RAM size is over, Request has to wait to get a New Thread or You loose the connection
- Loosing the connection means, you lost that user request


#In Node.js,
- All Request handled by a Single-Thread
- Node.js accepts all the user request network connections in a 'Asynchrnous' - 'Non-Blocking' way 
- And executes one by one by using 'Event Loop'
- This approach helps to achieve 'Huge Number Of Concurrent Connections' - which makes the system "Highly Scalable"

```

Javascript is a single-threaded, event-driven language. This means that we can attach listeners to events, and when a said event fires, the listener executes the callback we provided.

Whenever you call `setTimeout`, `http.get` or `fs.readFile`, Node.js sends these operations to a different thread allowing V8 to keep executing our code. Node also calls the callback when the counter has run down or the IO / http operation has finished.

These callbacks can enqueue other tasks and those functions can enqueue others and so on. This way you can read a file while processing a request in your server, and then make an http call based on the read contents without blocking other requests from being handled. This programming model helps to achieve `Non-Blocking -I/O operations` 

* Compared to traditional web-serving techniques where each connection \(request\) spawns a new thread, taking up system RAM and eventually maxing-out at the amount of RAM available, 
* Node.js operates on a single-thread, using non-blocking I/O calls, allowing it to support tens of thousands of concurrent connections held in the event loop.

![Diagram of traditional vs. Node.js server thread](https://uploads.toptal.io/blog/image/50/toptal-blog-1_B.png)



## Why '**WebApp' should use Node.js backends ?**

* Most of the **WebApp - backends** does **`IO operations`** __more
  * read/write \(files, database\), and \(accepts or make new Network/Socket connections\)
  * it doesn't do heavy computations \(CPU intensive tasks\)

> You definitely don’t want to use Node.js for CPU-intensive operations \(heavy computation\). Where Node really shines is in building **fast**, **scalable network applications,** as it’s capable of handling a **huge number of simultaneous connections** with **high throughput**, which equates to **high scalability**.



## Summary

```bash
######################## SUMMARY ########################
Node.js uses 'single-threaded', 'event-driven', 'asynchronous' programming approach
---- to handle 'Non-Blocking IO' operations efficiently
###########################################################
```

```bash
# REMEMBER #
- "JavaScript is NOT Asynchronous" -- JavaScript is always Synchronous
- Some of the JavaScript or Node.js functions are 'Asynchronous'
    - 'setTimeout', 'fs.readFile', 'http.get'....
- Node.js Apps sends an [Asynchronous Task]  to [Event Loop]  --along with a (callbackFn)
- [Event Loop]  effectively manages the Thread Pool and executes the [AysnchronousTasks]
- When [AysnchronousTasks] completes –the appropriate (callbackFn) will be called
```

## Additional Resources

* Node.js uses asynchronous programming!
* A common task for a web server can be to open a file on the server and return the content to the client.

```bash
# Here is how PHP or ASP handles a file request:
    1.Sends the task to the computers file system.
    2.Waits while the file system opens and reads the file.
    3.Returns the content to the client.
    4.Ready to handle the next request.

#Here is how Node.js handles a file request:
    1.Sends the task to the computer's file system.
    2.Ready to handle the next request.
    3.When the file system has opened and read the file, 
        -the server returns the content to the client.
```

* Node.js eliminates the waiting, and simply continues with the next request.
* Node.js runs single-threaded, non-blocking, asynchronously programming, which is very memory efficient.

{% embed url="http://debuggable.com/posts/understanding-node-js:4bd98440-45e4-4a9a-8ef7-0f7ecbdd56cb" %}

{% embed url="https://www.toptal.com/nodejs/why-the-hell-would-i-use-node-js" %}

{% embed url="https://www.freecodecamp.org/news/what-exactly-is-node-js-ae36e97449f5/" %}

{% embed url="https://www.slideshare.net/marcusf/nonblocking-io-event-loops-and-nodejs" %}

