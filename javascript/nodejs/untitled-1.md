# Event Loop & Libuv

## 

## 

## nextTick

* Every Node application runs on a single thread. -- only one task/event is processed at a time
* You can imagine this event loop to be a queue of callbacks that are processed by Node on every **tick** of the event loop. 
* So, even if you are running Node on a multi-core machine, you will not get any parallelism in terms of actual processing - all events will be processed only one at a time. 
* This is why Node is a great fit for I/O bound tasks, and definitely not for CPU intensive tasks. 
* For every I/O bound task, you can simply define a callback that will get added to the event queue. 
* The callback will fire when the I/O operation is done, and in the mean time, the application can continue to process other I/O bound requests.







{% embed url="https://medium.com/swlh/understanding-the-node-js-event-loop-181c2cbfcbb1" %}

{% embed url="https://howtonode.org/understanding-process-next-tick" %}



{% embed url="https://github.com/deenjohn/NodeRevision/blob/master/6-Concurrency%20model%20and%20event%20loop%20-part%20B.md" %}



{% embed url="https://www.youtube.com/watch?v=PNa9OMajw9w" %}

{% embed url="https://drive.google.com/file/d/0B1ENiZwmJ\_J2a09DUmZROV9oSGc/view" %}



