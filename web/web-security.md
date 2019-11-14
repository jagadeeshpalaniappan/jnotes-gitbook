# Web Security

{% tabs %}
{% tab title="" %}
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
{% endtab %}

{% tab title="First Tab" %}
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
{% endtab %}

{% tab title="Second Tab" %}
{% embed url="https://www.youtube.com/watch?v=c6mqdsfWdmE" %}
{% endtab %}

{% tab title="" %}


{% embed url="https://portswigger.net/web-security" %}
{% endtab %}
{% endtabs %}





## 1. Cross-site scripting \(XSS\)

{% tabs %}
{% tab title="First Tab" %}


{% embed url="https://www.veracode.com/security/xss" %}
{% endtab %}

{% tab title="Simple" %}
{% embed url="https://www.youtube.com/watch?v=ns1LX6mEvyM" %}
{% endtab %}

{% tab title="Detailed" %}
{% embed url="https://www.youtube.com/watch?v=t161cahMAZc" %}

{% embed url="https://www.youtube.com/watch?v=IuzU4y-UjLw" %}
{% endtab %}
{% endtabs %}

\*\*\*\*

## 2. Cross-Site Request Forgery **\(**_CSRF\)_

{% tabs %}
{% tab title="" %}


```text
CSRF (Cross Site Request Forgery)
   - If user is authenticated and logged in to abc.com, The abc.com authtoken or JSESSIONID is stored on Cookie
   - If the 'loggedInUser' hits some hacker.com URL, hacker.com appln can read all the cookies of the user and can make legitimate request to abc.com without letting the user know
     (the URL can be recieved via email/sms/...)
     // soln: backend sends unique csrfToken to client for each request, then backend expects the csrfToken
     // - if frontend not sending those token, then that is not an legitimate request 
```
{% endtab %}

{% tab title="First Tab" %}
{% embed url="https://www.youtube.com/watch?v=eWEgUcHPle0" %}
{% endtab %}

{% tab title="Second Tab" %}
{% embed url="https://www.youtube.com/watch?v=vRBihr41JTo" %}
{% endtab %}
{% endtabs %}

## HTTP Header Injection

