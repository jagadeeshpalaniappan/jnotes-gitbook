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

