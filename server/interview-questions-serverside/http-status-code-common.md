# HTTP - Status Code

```c
### Most Commonly Used:

- 200 OK (success)
- 201 Created (New resource is successfully created)
- 202 Accepted (request is accepted for processing (but not completed processing fully)
- 206 Partial Content (server is returning partial data of the size requested)


- 301 (Redirect: requested page has moved permanently to a new url)
- 302 (Redirect: requested page has moved temporarily to a new url)


- 400 Bad Request (Invalid req.body) (validation failed)

- 401 Unauthorized (Not Authenticated)***
- 403 Forbidden (Not Authorized to access the requested content)***

- 404 Not Found (requested page not available) 


- 500 Internal Server Error (server met an unexpected condition)
- 502 Bad Gateway (server was not able to get resp from upstream server)
- 503 Service Unavailable (server is temporarily down or overloaded)
- 504 Gateway Timeout (server does not receive a timely response from another server) or (unable to fullfill the request in timely manner)

```

* **1xx: Informational** 
  * It means the request has been received and the process is continuing.
* **2xx: Success** 
  * It means the action was `successfully received`, `understood`, and `accepted`.
* **3xx: Redirection** 
  * It means `further action must be taken` in order to complete the request.
* **4xx: Client Error** 
  * It means the request contains `incorrect syntax` or `cannot be fulfilled`.
* **5xx: Server Error** 
  * It means the `server failed` to fulfill an apparently valid request

### 1xx: Information

| Message | Description |
| :--- | :--- |
| 100 Continue | Only a part of the request has been received by the server, but as long as it has not been rejected, the client should continue with the request. |
| 101 Switching Protocols | The server switches protocol. |

### 2xx: Successful

<table>
  <thead>
    <tr>
      <th style="text-align:left">Message</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><code>200 OK</code>
      </td>
      <td style="text-align:left">The request is OK.</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>201 Created</code>
      </td>
      <td style="text-align:left">The request is complete, and a <code>new resource is created</code> .</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>202 Accepted</code>
      </td>
      <td style="text-align:left">
        <p>The request is <code>accepted for processing</code>,</p>
        <p>but the processing is <code>not complete</code>.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">203 Non-authoritative Information</td>
      <td style="text-align:left">
        <p>The information in the entity header is from a local or third-party copy,</p>
        <p>not from the original server.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">204 No Content</td>
      <td style="text-align:left">
        <p>A status code and a header are given in the response,</p>
        <p>but there is no entity-body in the reply.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">205 Reset Content</td>
      <td style="text-align:left">The browser should clear the form used for this transaction for additional
        input.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b><code>206 Partial Content</code></b>
      </td>
      <td style="text-align:left">
        <p>The server is <code>returning partial data</code> of the size requested.</p>
        <p>Used in response to a request specifying a Range header.</p>
        <p>The server must specify the range included in the response with the Content-Range
          header.</p>
      </td>
    </tr>
  </tbody>
</table>### 3xx: Redirection

<table>
  <thead>
    <tr>
      <th style="text-align:left">Message</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">300 Multiple Choices</td>
      <td style="text-align:left">
        <p>A link list. The user can select a link and go to that location.</p>
        <p>Maximum five addresses .</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>301 Moved Permanently</code>
      </td>
      <td style="text-align:left">The requested page has <code>moved permanently</code> to a new url .</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>302 Found</code>
      </td>
      <td style="text-align:left">The requested page has <code>moved temporarily</code> to a new url .</td>
    </tr>
    <tr>
      <td style="text-align:left">303 See Other</td>
      <td style="text-align:left">The requested page can be found under a different url .</td>
    </tr>
    <tr>
      <td style="text-align:left">304 Not Modified</td>
      <td style="text-align:left">
        <p>This is the response code to an If-Modified-Since</p>
        <p>or If-None-Match header, where the URL has not been modified since the
          specified date.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">305 Use Proxy</td>
      <td style="text-align:left">The requested URL must be accessed through the proxy mentioned in the
        Location header.</td>
    </tr>
    <tr>
      <td style="text-align:left">306 Unused</td>
      <td style="text-align:left">
        <p>This code was used in a previous version.</p>
        <p>It is no longer used, but the code is reserved.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">307 Temporary Redirect</td>
      <td style="text-align:left">The requested page has moved temporarily to a new url.</td>
    </tr>
  </tbody>
</table>### 4xx: Client Error

<table>
  <thead>
    <tr>
      <th style="text-align:left">Message</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><code>400 Bad Request</code>
      </td>
      <td style="text-align:left">The server did not understand the request. <code>(Invalid Req. Body)</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>401 Unauthorized</code>
      </td>
      <td style="text-align:left">
        <p>The requested page needs a username and a password.</p>
        <p>(Not Authenticated)</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">402 Payment Required</td>
      <td style="text-align:left">You can not use this code yet.</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>403 Forbidden</code>
      </td>
      <td style="text-align:left">
        <p>Access is forbidden to the requested page.</p>
        <p><code>(Not Authorized to access this content)</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>404 Not Found</code>
      </td>
      <td style="text-align:left">The server can not find the requested page.</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>405 Method Not Allowed</code>
      </td>
      <td style="text-align:left">The method specified in the request is not allowed.</td>
    </tr>
    <tr>
      <td style="text-align:left">406 Not Acceptable</td>
      <td style="text-align:left">The server can only generate a response that is not accepted by the client.</td>
    </tr>
    <tr>
      <td style="text-align:left">407 Proxy Authentication Required</td>
      <td style="text-align:left">You must authenticate with a proxy server before this request can be served.</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>408 Request Timeout</code>
      </td>
      <td style="text-align:left">The request took longer than the server was prepared to wait.</td>
    </tr>
    <tr>
      <td style="text-align:left">409 Conflict</td>
      <td style="text-align:left">The request could not be completed because of a conflict.</td>
    </tr>
    <tr>
      <td style="text-align:left">410 Gone</td>
      <td style="text-align:left">The requested page is no longer available .</td>
    </tr>
    <tr>
      <td style="text-align:left">411 Length Required</td>
      <td style="text-align:left">
        <p>The &quot;Content-Length&quot; is not defined.</p>
        <p>The server will not accept the request without it .</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">412 Precondition Failed</td>
      <td style="text-align:left">The pre condition given in the request evaluated to false by the server.</td>
    </tr>
    <tr>
      <td style="text-align:left">413 Request Entity Too Large</td>
      <td style="text-align:left">
        <p>The server will not accept the request,</p>
        <p>because the request entity is too large.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">414 Request-url Too Long</td>
      <td style="text-align:left">
        <p>The server will not accept the request, because the url is too long.</p>
        <p>Occurs when you convert a &quot;post&quot; request to a &quot;get&quot;
          request with a long query information .</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">415 Unsupported Media Type</td>
      <td style="text-align:left">The server will not accept the request, because the mediatype is not supported
        .</td>
    </tr>
    <tr>
      <td style="text-align:left">416 Requested Range Not Satisfiable</td>
      <td style="text-align:left">The requested byte range is not available and is out of bounds.</td>
    </tr>
    <tr>
      <td style="text-align:left">417 Expectation Failed</td>
      <td style="text-align:left">The expectation given in an Expect request-header field could not be met
        by this server.</td>
    </tr>
  </tbody>
</table>### 5xx: Server Error

<table>
  <thead>
    <tr>
      <th style="text-align:left">Message</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><code>500 Internal Server Error</code>
      </td>
      <td style="text-align:left">
        <p>The request was not completed.</p>
        <p>The server met an unexpected condition.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">501 Not Implemented</td>
      <td style="text-align:left">
        <p>The request was not completed.</p>
        <p>The server did not support the functionality required.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>502 Bad Gateway</code>
      </td>
      <td style="text-align:left">
        <p>The request was not completed.</p>
        <p>The server received an <code>invalid response from the upstream server</code>.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>503 Service Unavailable</code>
      </td>
      <td style="text-align:left">
        <p>The request was not completed.</p>
        <p>The <code>server is</code> temporarily overloading or <code>down</code>.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">504 Gateway Timeout</td>
      <td style="text-align:left">
        <p>when one server does not receive a timely response from another server</p>
        <p>that acts as a gateway or proxy.</p>
        <p>In short, it means the server was unable to complete the request within
          the given time frame</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">505 HTTP Version Not Supported</td>
      <td style="text-align:left">The server does not support the &quot;http protocol&quot; version.</td>
    </tr>
  </tbody>
</table>