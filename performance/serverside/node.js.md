# Node.js \[eTODO\]

**Though JavaScript has the highest number of developers in its community with respect to any other language on earth at this moment; there are a lot of misconceptions, shallow knowledge, bad assumptions among the community members. In this article we have come up with a list of tips, which can make your javascript application faster.**

This article is not about dev-ops and doesn’t discuss on things like minify your files or setup redis or use docker and kubernetes to make your application performant. This article is about coding in JavaScript to make the performance better.

I am majorly discussing about JavaScript, but few of the points are related to node.js only, or few may be only for client side JavaScript. However, as majority of the JavaScript developers are full-stack these days, I assume you can understand these easily.

### Background

The JavaScript engine used by Node.js, V8, compiles JavaScript into machine code and runs it as native code. The engine uses three components to try achieve [both low start-up time and peak performance](https://blog.chromium.org/2010/12/new-crankshaft-for-v8.html):

1. A generic compiler that compiles JavaScript to machine code as fast as possible.
2. A runtime profiler that tracks how much time is spent running which parts of code and identifies code that could be worth to optimize.
3. An optimizing compiler that attempts to optimize the previously identified code.
4. When the assumptions made by the optimizer compiler were too optimistic, it supports deoptimization \(deopt\).

The optimizing compiler achieves the best performance but not all JavaScript code will be selected for optimization: there are code patterns the optimizing compiler will refuse to optimize.

You can use [this ticket from Google Chrome DevTools team](https://github.com/GoogleChrome/devtools-docs/issues/53) as a guide for patterns which will cause the code to not be optimized by V8, with possible workarounds. Some examples include:

* Functions with try-catch statements.
* Reassigning an argument value while using the `arguments` field.

Even though the optimizing compiler will make your code run significantly faster, in an IO-intensive application most of the performance improvements revolve around how to reorder the instructions and use less expensive calls to allow more operations per second, as we will see in the following sections.

Node.js provides an event-driven architecture and a non-blocking I/O API that optimizes your application throughput and scalability. One notable feature of Node.js is that it contains a built-in library to allow applications to act as a Web server without software such as Apache HTTP Server or IIS. You should expect more and more web development projects shifting towards a uniform web language with Node.js leading the way.

Given the increasing ubiquity of JavaScript and the Node.js platform, you’ll want to be up-to-date on the latest optimizations and best practices. In this article, we’ll take a look at 7 Node.js performance tips that should be running under the hood to get the most out of your applications.

### 1. Implement a Reverse Proxy Server

We at NGINX, Inc. are always a bit horrified when we see application servers directly exposed to incoming Internet traffic, used at the core of high‑performance sites. This includes many [WordPress‑based sites](https://www.nginx.com/blog/9-tips-for-improving-wordpress-performance-with-nginx/), for example, as well as Node.js sites.

Node.js, to a greater extent than most application servers, is designed for scalability, and its web server side can handle a lot of Internet traffic reasonably well. But web serving is not the raison d’etre for Node.js – not what it was really built to do.

If you have a high‑traffic site, the first step in increasing application performance is to put a reverse proxy server in front of your Node.js server. This protects the Node.js server from direct exposure to Internet traffic and allows you a great deal of flexibility in using multiple application servers, in load balancing across the servers, and in caching content.

![](https://www.nginx.com/wp-content/uploads/2015/11/nginx-as-reverse-proxy.png)

Putting NGINX in front of an existing server setup as a [reverse proxy server](https://www.nginx.com/resources/glossary/reverse-proxy-server/), followed by additional uses, is a core use case for NGINX, implemented by [tens of millions of websites](http://news.netcraft.com/archives/2015/10/16/october-2015-web-server-survey.html) all over the world.

There are specific advantages to [using NGINX as a Node.js reverse proxy server](http://www.nikola-breznjak.com/blog/nodejs/using-nginx-as-a-reverse-proxy-in-front-of-your-node-js-application/), including:

* Simplifying privilege handling and port assignments
* More efficiently serving static images \(see [next tip](https://www.nginx.com/blog/5-performance-tips-for-node-js-applications/cache)\)
* Managing Node.js crashes successfully
* Mitigating DoS attacks

**Note**: These tutorials explain how to use NGINX as a reverse proxy server in [Ubuntu 14.04](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-node-js-application-for-production-on-ubuntu-14-04) or [CentOS](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-node-js-application-for-production-on-centos-7)environments, and they are useful overview for anyone putting NGINX in front of Node.js.

### 2. Keep code small and light

In the age of mobile where application performance is so critical, it’s especially important to keep your Node.js code base as compact as possible to reduce latency and speed things up. [One article](http://engineering.linkedin.com/nodejs/blazing-fast-nodejs-10-performance-tips-linkedin-mobile) provides some organizing questions that are worth asking in the development stage: “Do we really need this module?”, “Why are we using this framework? Is it worth the overhead?”, “Can we do this in a simpler way?” Another way to optimize application performance is by minifying and concatenating multiple JS files into one. For example, if your app has five JavaScript files the browser will make five separate HTTP requests to fetch them. To avoid the block and wait time, an alternative approach would be to minify and concatenate those 5 files into one streamlined one.

### 3. Don’t use Node.js to render static assets

One critical performance tip would be to render your static assets, such as CSS and images, on a standard webserver like Nginx. By arranging Nginx to serve your static content you will significantly reduce the load on your Node.js instance and in the process increase your performance.

### 4. Employ client side rendering

Thanks to powerful new client side MVC frameworks like AngularJS and BackboneJS, it has become much easier for developers to create dynamic, one-page apps. These frameworks expose APIs that send JSON responses directly to the client rather than through the server. If you let Node.js render server-side then this sends back an HTML page for every request. Using client side rendering in your Node.js environment can dramatically save bandwidth and reduce latency.

### 5. CPU Profiling

There are several CPU profilers, Node.js provides one out-of-the-box that is good enough for most cases. The [built-in Node.js profiler](https://nodejs.org/en/docs/guides/simple-profiling/) takes advantage of the [profiler inside V8](https://github.com/v8/v8/wiki/V8%20Profiler), sampling the stack at regular intervals during the execution. You can generate V8 tick file using the –prof flag to run node.

Then, you can process the profiling session output to aggregate the information and convert it into something readable by humans, [using the –prof-process flag](https://nodejs.org/api/cli.html#cli_prof_process):

`$ node --prof-process isolate-0xnnnnnnnnnnnn-v8.log > processed.txt`

Opening the processed text file in an editor will give you information divided into sections.

Look up for the “Summary” section in the file that will look something like this:

`[Summary]:`

`ticks  total  nonlib name`

`20109  41.2%  45.7% JavaScript`

`23548  48.3%  53.5% C++`

`805   1.7%   1.8% GC`

`4774   9.8%         Shared libraries`

`356   0.7%         Unaccounted`

The values represent how many of the samples gathered occurred in JavaScript / C++ code / Garbage collector and will vary depending on the code you are profiling. Then you can navigate to the corresponding subsection of the file \(e.g. \[JavaScript\], \[C++\], …\) to see the details of the samples order by occurrence.

There is an additional section in the processed file of the profiling session, \[Bottom up \(heavy\) profile\], that is especially useful. It provides information about the primary callers of each function, in a tree-like structure. Take the following snippet for example:

`223 32%     LazyCompile: *function1 lib/file1.js:223:20`

`221 99%       LazyCompile: ~function2 lib/file2.js:70:57`

`221 100%        LazyCompile: *function3 /lib/file3.js:58:74`

The percentage shows the share of a particular caller in the total amount of its parent calls. An asterisk before a function name means that time is being spent in an optimized function, while tilde means not optimized function.

In the example, 99% of the function1 calls has been made by function2, for which function3 is responsible for 100% of the calls to function2, according to the profiling sample.

CPU profiling sessions and [flame graphs](http://www.brendangregg.com/blog/2014-09-17/node-flame-graphs-on-linux.html) are useful tools to understand what is in the stack most of the time and which methods are spending CPU time, in order to spot low-hanging fruit. But it’s important to understand that it won’t tell you the whole story: you could be preventing higher degrees of parallelism in your application and the asynchronous IO operations could make it hard to identify.

### 6. Implement SSL/TLS and HTTP/2

More and more sites are using SSL/TLS to secure all user interaction on the site. It’s your decision whether and when to make this move, but if and when you do, NGINX supports the transition in two ways:

1. You can terminate an SSL/TLS connection to the client in NGINX, once you’ve set up NGINX as a reverse proxy. The Node.js server sends and receives unencrypted requests and content back and forth with the NGINX reverse proxy server.
2. Early indications are that using [HTTP/2](https://www.nginx.com/blog/7-tips-for-faster-http2-performance/), the new version of the HTTP protocol, may largely or completely offset the performance penalty that is otherwise imposed by the use of SSL/TLS. NGINX supports HTTP/2 and you can terminate HTTP/2 along with SSL/TLS, again eliminating any need for changes in the Node.js application server\(s\).

Among the implementation steps you need to take are updating the URL in the Node.js configuration file, establishing and optimizing secure connections in your NGINX configuration, and using SPDY or HTTP/2 if desired. Adding HTTP/2 support means that browser versions that support HTTP/2 communicate with your application using the new protocol; older browser versions continue to use HTTP/1.x.

![](https://www.nginx.com/wp-content/uploads/2015/09/http2-backward-compatibility.png)

The following configuration code is for a Ghost blog using SPDY, as described [here](http://pnommensen.com/2014/09/07/high-performance-ghost-configuration-with-nginx/#comment-14). It includes advanced features such as OCSP stapling. For considerations around using NGINX for SSL termination, including the OCSP stapling option, see [here](https://www.nginx.com/blog/nginx-ssl/). For a general overview of the same topics, see [here](https://l.morioh.com/b0a3f595aa?r=https://www.nginx.com/resources/admin-guide/nginx-ssl-termination/).

You need make only minor alterations to configure your Node.js application and to upgrade from SPDY to HTTP/2, now or when SPDY support goes away in early 2016.

```text
    server {
    server_name domain.com;
    listen 443 ssl spdy;
    spdy_headers_comp 6;
    spdy_keepalive_timeout 300;
    keepalive_timeout 300;
    ssl_certificate_key /etc/nginx/ssl/domain.key;
    ssl_certificate /etc/nginx/ssl/domain.crt;
    ssl_session_cache shared:SSL:10m;
    ssl_session_timeout 24h;
    ssl_buffer_size 1400;
    ssl_stapling on;
    ssl_stapling_verify on;
    ssl_trusted_certificate /etc/nginx/ssl/trust.crt;
    resolver 8.8.8.8 8.8.4.4 valid=300s;
    add_header Strict-Transport-Security 'max-age=31536000; includeSubDomains';
    add_header X-Cache $upstream_cache_status;
<pre><code>location / {
proxy_cache STATIC;
proxy_cache_valid 200 30m;
proxy_cache_valid 404 1m;
proxy_pass http://ghost_upstream;
proxy_ignore_headers X-Accel-Expires Expires Cache-Control;
proxy_ignore_headers Set-Cookie;
proxy_hide_header Set-Cookie;
proxy_hide_header X-powered-by;
proxy_set_header X-Real-IP $remote_addr;
proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
proxy_set_header X-Forwarded-Proto https;
proxy_set_header Host $http_host;
expires 10m;
}

location /content/images {
alias /path/to/ghost/content/images;
access_log off;
expires max;
}

location /assets {
alias /path/to/ghost/themes/uno-master/assets;
access_log off;
expires max;
}

location /public {
alias /path/to/ghost/built/public;
access_log off;
expires max;
}

location /ghost/scripts {
alias /path/to/ghost/core/built/scripts;
access_log off;
expires max;
}

location ~ ^/(?:ghost|signout) {
proxy_set_header X-Real-IP $remote_addr;
proxy_set_header Host $http_host;
proxy_pass http://ghost_upstream;
add_header Cache-Control "no-cache, private, no-store,
must-revalidate, max-stale=0, post-check=0, pre-check=0";
proxy_set_header X-Forwarded-Proto https;
}
}
</code>
```

### 7. Use Realtime App Monitor to Analysis your App

![](https://cdn-images-1.medium.com/max/800/1*gjhkikuEdV-iRSGGacOyVg.jpeg)

Real Time Monitoring is a third-party application that allows admins to maintain and monitor the system from any disruptions or problems that arise in web applications in real time. This lets you immediately respond to any errors or bugs that occur. In Node JS you can use Newrelic, Stackify, Ruxit, LogicMonitor and Monitis, to record traces and activities quickly, concisely and reliably. With this monitoring, you can analyze and find out more detail issues, especially the effectiveness and health of node.js when accessed by multiple users.

### 8. Web-workers & Shared buffer

JavaScript is single threaded. The same thread is used for event-loop. So your new request handling in node.js and dom rendering in browser, everything is processed in a non-parallel way.

So, whenever you have a task which takes more computing time, you should delegate it to some web-workers. In case of node.js, there is no in built worker, but you can use an npm module or spawn a new process for the same.

One common problem working with workers can be how to sync with them \(without posting a message after finish\). Well, `SharedArrayBuffer` can be a handy way for that.

It seems SharedArrayBuffer is disabled by default since 5th January 2018; but this \(or kind of this\) is already in [stage 4 as ECMA proposal](https://l.morioh.com/b0a3f595aa?r=https://github.com/tc39/ecmascript_sharedmem).

### 9. setImmediate over setTimeout\(fn,0\)

This is a point only for node.js developer. Many of the developers don’t use setImmediate or process.nextTick and go with `setTimeout(fn, 0)` to make a part of their program asynchronous.

Well, some of our [experiments about setImmediate vs setTimeout\(fn, 0\)](https://l.morioh.com/b0a3f595aa?r=http://voidcanvas.com/nodejs-event-loop#snippet-2-understanding-timers-better) says, setImmediate can be upto 200 times \(yes, times, not just percent\) faster than setTimeout\(fn, 0\).

So use setImmediate more frequently than setTimeout; but be cautious about using process.nextTick unless you understand how it works.

### 10. System call

Libuv exposes a platform-independent API that is used by Node.js to perform non-blocking IO and your application IO \(sockets, file system, …\) ultimately translates into system calls.

There is a significant cost in scheduling those system calls. You should try to minimize the amount of syscalls by can grouping / batching writes.

When using a socket or a file stream, instead of issuing a write every time, you can buffer and flush the data from time to time.

You can use a write queue to process and group your writes. The logic for a write queue implementation should be something like:

* While there are items to write and we are within the window size
* Push the buffer to the “to-write list”
* Concatenate all the buffers in the list and write it to the wire.

You can define a window size based either on the total buffer length or the amount of time that passed since the first item was queued. Defining a window size is tradeoff between the latency of a single write and the average latency of all writes. You should also consider the maximum amount of write requests to be grouped and the overhead of generating each write request.

You would generally want to flush writes of buffers in the order of kilobytes. We found a sweet spot around 8 kilobytes, but your mileage may vary. You can check out the [implementation in the client driver](https://l.morioh.com/b0a3f595aa?r=https://github.com/datastax/nodejs-driver/blob/v3.1.6/lib/writers.js#L159) for a complete implementation of a write queue.

Grouping or batching writes will translate into higher throughput thanks to less system calls.

### 11. Node.js timers

[Node.js timers](https://l.morioh.com/b0a3f595aa?r=https://nodejs.org/api/timers.html), which have the same API as [window timers](https://l.morioh.com/b0a3f595aa?r=https://developer.mozilla.org/es/docs/Web/API/WindowTimers/setTimeout) in Web API, are very useful, easy to schedule / deschedule and are used extensively across the entire ecosystem.

As such, it’s likely that there may be a large amount of timeouts scheduled at any given time in an application.

Similar to other [hashed wheel timers](https://l.morioh.com/b0a3f595aa?r=http://cseweb.ucsd.edu/users/varghese/PAPERS/twheel.ps.Z), Node.js [uses a hash table and a linked list](https://l.morioh.com/b0a3f595aa?r=https://github.com/nodejs/node/blob/master/lib/timers.js) to maintain the timers instances. But unlike other wheel timers, instead of having a fixed-length hash table, it keys each list of timers by duration.

When the key exists \(a timer with the same duration exist\), it is appended to the bucket as a O\(1\) operation.

When a key does not exist, a bucket is created and the timer is appended to it.

With that in mind, you have to make sure you reuse the existing buckets, trying to avoid removing a whole bucket and creating a new one. For example, if you are using sliding delays you should create the new timeout \(setTimeout\(\)\) before removing \(clearTimeout\(\)\) the previous one.

In our case, by [scheduling the idle timeout \(heartbeat\)](https://l.morioh.com/b0a3f595aa?r=https://github.com/datastax/nodejs-driver/blob/v3.1.6/lib/connection.js#L434-L443) before removing the previous one, we make sure the scheduling and descheduling of idle timeouts are O\(1\) operations.

### Conclusion

Increasing your server’s configuration, scaling it out, distributing the services are some of the very well known processes to make your application performant.

But if your code is causing memory leaks or sequential processing; all those dev-ops steps will not able to save your server getting slowed down or even crashed.

Thus, while coding \(irrespective of the language\), you must be aware of all good practices, edge cases and performance points.

_Originally published by **https://socialdribbler.com**_

=============================

