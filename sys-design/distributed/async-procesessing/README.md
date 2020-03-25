# Asynchronous Processing

## Asynchronous Processing

{% tabs %}
{% tab title="First Tab" %}


```fsharp
Asynchronous Processing
    - Synchronous Processing (blocks IO operation)
    - Asynchronous Processing (doesnt block IO operation)
    
IO Operations: Network IO, File IO (read/write),...

Synchronous Code:
    - Line 1
    - Line 2 (N/w IO opeartion) 
      // currProgramExecutingThread: waits until OS fully respond back
    - Line 3
    -   :
    
Asynchronous Code:
    - Line 1
    - Line 2 (Async N/w IO opeartion) 
      // currProgramExecutingThread: will not wait for OS to respond, -instead it registers 'callbackFn'
      //  - and when OS respond 'callbackFn' will be executed by diffPgmExecutingThread
    - Line 3
    -   :
```
{% endtab %}

{% tab title="Video" %}
{% embed url="https://www.youtube.com/watch?v=BFcNDPt6SlE&t=1174s" %}
{% endtab %}
{% endtabs %}

