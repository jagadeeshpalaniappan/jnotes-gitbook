# Node.js

## What is Node.js?

_Node.js is a cross-platform `JavaScript Runtime Environment`- built on top of Chrome's V8  Engine_

* Node.js is a server-side cross-platform built on Google Chrome's JavaScript Engine \(V8 Engine\) 
* For easily building fast and scalable network applications. 
* Node.js uses an event-driven, non-blocking I/O model that makes it lightweight and efficient, 
* perfect for data-intensive real-time applications that run across distributed devices.



```text
Node.js = JavaScript Runtime Environment + (Server-Side) Behavior

Node.js = V8-Engine + Libuv(Asynchronous IO) + Non-Blocking IO + Node-Core (C++ Library) + C++ Wrappers (.js files) & JavaScript Utility Function (.js files)
```

Now you can do much more with JavaScript than just making websites interactive.

JavaScript now has the capability to do things that other scripting languages like Python can do.

## What is JavaScript Runtime Environment?

![If you know Java, here&#x2019;s a little analogy.](../../.gitbook/assets/image%20%28150%29.png)



### Key Features of Node.js

Following are some of the important features that make Node.js the first choice of software architects.

* **Asynchronous and Event Driven** − All APIs of Node.js library are `asynchronous`, that is, `non-blocking`. It essentially means a Node.js based server never waits for an API to return data. The server moves to the next API after calling it and a notification mechanism of Events of Node.js helps the server to get a response from the previous API call.
* **Single Threaded but Highly Scalable** − Node.js uses a single threaded model with event looping. Event mechanism helps the server to respond in a non-blocking way and makes the server highly scalable as opposed to traditional servers which create limited threads to handle requests. Node.js uses a single threaded program and the same program can provide service to a much larger number of requests than traditional servers like Apache HTTP Server.
* **Very Fast** − Being built on Google Chrome's `V8 JavaScript Engine`, Node.js library is very fast in code execution.
* **No Buffering** − Node.js applications never buffer any data. These applications simply `output` the `data in chunks`.



## Node.js Architecture 



```text
Node.js = V8-Engine + Libuv(Asynchronous IO) + Non-Blocking IO + Node-Core (C++ Library) + C++ Wrappers (.js files) & JavaScript Utility Function (.js files)
```

![](../../.gitbook/assets/image%20%2870%29.png)



## Server-Side Behavior Added in JavaScript

```text
Node.js = JavaScript + (Server-Side) Behavior
```

* With the help of \(V8-Engine\) --Node.js has added additional features to the JavaScript \(added some C/C++ libraries\) 
* Additional Features :

  * **`Non-Blocking IO` approach**
    * Operating System's IO operations are slower \(it has 'Longer Waiting Time'\)
      * `[open/read/write (files, database, network/socket connections)]`
    * _**Use:  'Asynchronous IO' operations at OS level**_
    * Node embeds –‘libuv’ External \(C++ Library\)
    * `libuv` helps to perform Asynchronous IO operations in Node.js
    * This approach helps to achieve Non-Blocking nature in Node.js
  * **Dealing with `Internet`** \(HTTP Request & HTTP Response\) 
    * Node embeds -'http-parser' External \(C++ Library\)
  * **Dealing with `Files`** \[ Node-Core \(C++ Library\) \] 
  * **Dealing with `Databases`** \[ Node-Core \(C++ Library\) \] 

* These “additional features” help us to build an Server-Side \(Web App\) completely in JavaScript itself



* **How? Node.js has added additional features to JavaScript?**
  * \(V8-Engine\) helps Node.js to add additional \(C++\) features
  * V8 allows, JavaScript to call C++ code 
    * `var binding = process.binding('fs'); //JS calls & get File System C++ Library`
  * So Now, “Whatever C++ code can do -- JavaScript also can do the same!!” \(by calling that C++ function\)
* **NOTE: This is not the new idea, \(Adding a C++ feature to JavaScript\)**
  * Browser \(V8-Engine + Additional C++ libraries\)
  * V8-Engine: handles only pure JavaScript \(ECMA Script standards\) \(doesn’t handle DOM manipulation\)
  * Browser\(C++ Code\): handles DOM manipulation \(which means added additional features to Browser Runtime\)

