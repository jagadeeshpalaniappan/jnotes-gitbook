# Web Security

{% tabs %}

```javascript
Cross Site (Attack)
 - XSS (Cross Site Scripting)
   - Injecting hackers JavaScript code part of the HTML
   - textInput userid ==> "'myuser' or 1=1"
 - CSRF (Cross Site Request Forgery)
   - If abc.com 'loggedInUser' hits some hacker.com URL in different tab, hacker.com appln can read all the cookies of the user browser and can make legitimate request to abc.com without letting the user know
     // soln: backend sends unique csrfToken to client for each request, then backend expects the csrfToken
     // - if frontend not sending those token, then that is not an legitimate request 

CORS (Cross-Origin Resource Sharing):
 - soln: use this req.header `Access-Control-Allow-Origin: http://siteA.com`

 SQL Injection:
  - Injecting hackers SQL statement part of the valid SQL statement
  - textInput userid ==> "'myuser' or 1=1"
  - SELECT userid, name FROM users WHERE userid = 'myuser' or 1=1;
```

```text
Clickjacking (UI redressing)
Testing for WebSockets security vulnerabilities
        What are WebSockets?
        Cross-site WebSocket hijacking
HTTP request smuggling
        Finding HTTP request smuggling vulnerabilities
        Exploiting HTTP request smuggling vulnerabilities
Server-side request forgery (SSRF)
        Blind SSRF vulnerabilities
SQL injection
        SQL injection UNION attacks
        Examining the database in SQL injection attacks
        Blind SQL injection
        SQL injection cheat sheet
Cross-site scripting
        Reflected XSS
        Cross-site scripting contexts
        XSS cheat sheet
        Stored XSS
        DOM-based XSS
        Exploiting cross-site scripting vulnerabilities
Cross-site request forgery (CSRF)
        Defending against CSRF with SameSite cookies
        XSS vs CSRF
        CSRF tokens
XML external entity (XXE) injection
        XML entities
        Finding and exploiting blind XXE vulnerabilities
OS command injection
Directory traversal
Want to track your progress and have a more personalized learning experience? (It's free!)
```



{% embed url="https://www.youtube.com/watch?v=c6mqdsfWdmE" caption="" %}



{% embed url="https://portswigger.net/web-security" caption="" %}

## 1. Cross-site scripting \(XSS\)

{% tabs %}



{% embed url="https://www.veracode.com/security/xss" caption="" %}



{% embed url="https://www.youtube.com/watch?v=ns1LX6mEvyM" caption="" %}



{% embed url="https://www.youtube.com/watch?v=t161cahMAZc" caption="" %}

{% embed url="https://www.youtube.com/watch?v=IuzU4y-UjLw" caption="" %}

\*\*\*\*

## 2. Cross-Site Request Forgery **\(**_CSRF\)_

{% tabs %}

```text
CSRF (Cross Site Request Forgery)
   - If user is authenticated and logged in to abc.com, The abc.com authtoken or JSESSIONID is stored on Cookie
   - If the 'loggedInUser' hits some hacker.com URL, hacker.com appln can read all the cookies of the user and can make legitimate request to abc.com without letting the user know
     (the URL can be recieved via email/sms/...)
     // soln: backend sends unique csrfToken to client for each request, then backend expects the csrfToken
     // - if frontend not sending those token, then that is not an legitimate request
```



{% embed url="https://www.youtube.com/watch?v=eWEgUcHPle0" caption="" %}

{% embed url="https://www.youtube.com/watch?v=vRBihr41JTo" caption="" %}

## HTTP Header Injection





### [Clarification on the security implications of httpOnly](https://forums.fauna.com/t/do-i-need-a-backend-api-between-faunadb-and-my-app-what-are-the-use-cases-of-an-api/95/6)

Since I mentioned httpOnly cookies, it makes sense that we also explain the extra advantage that brings and the different approaches. There are many ways to store keys in memory.

* **local storage** [vulnerable to XSS](https://dev.to/rdegges/please-stop-using-local-storage-1i04)
* **regular cookies** vulnerable to CSRF and cookies could be read by the client making them also vulnerable by XSS. It’s much more nuanced than that though, [a good explanation on this](https://blog.yeswehack.com/2018/01/22/the-dark-side-of-xss-revealed/).
* **in memory \(in a JavaScript variable\)** vulnerable to XSS … but this is actually safer than localstorage and regular cookies, and that security is indeed security by obfuscation which is questionable \(yet often still a good idea\). The idea here is that an automatic attack that briefly gets in and quickly copies over your cookies or localstorage content will not have any success. If it’s a manual attack he’ll have to do a significant effort before he finds an in-memory secret compared to localstorage or cookies which are, of course, easy to find. **However**, in memory is annoying since it logs you out on each refresh!
* **httpOnly cookies** Protected from XSS, vulnerable to CSRF \(but there are other ways to protect against that\) Cookies that can’t be read from JavaScript \(if your browser supports it and handles it correctly, there are always [some subtle security things](https://resources.infosecinstitute.com/cookies-httponly-flag-problem-browsers/#gref) you have to know\). These require a backend for the endpoints where you want to use the data that is stored in the cookie. Which is logical since the whole point is that JS can’t access this data.

