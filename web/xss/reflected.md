# Reflected xss

**Reflected xss**

its is the simplest variety of cross-site scripting. It arises when an application receives data in an HTTP request and includes that data within the immediate response in an unsafe way. 

 https://insecure-website.com/status?message=All+is+well.

<p>Status: All is well.</p>

The application doesn't perform any other processing of the data, so an attacker can easily construct an attack like this:
```html
https://insecure-website.com/status?message=<script>/*+Bad+stuff+here...+*/</script>

<p>Status: <script>/* Bad stuff here... */</script></p>
```
If the user visits the URL constructed by the attacker, then the attacker's script executes in the user's browser, in the context of that user's session with the application. At that point, the script can carry out any action, and retrieve any data, to which the user has access. 


**Reflected XSS in different contexts**

there are differen varieties of reflected xss. the location of the reflected data determine what type of payload is required to exploit.

In addition, if the application performs any validation or other processing on the submitted data before it is reflected, this will generally affect what kind of XSS payload is needed. 

* *xss context between HTML tags*

When the XSS context is text between HTML tags, you need to introduce some new HTML tags designed to trigger execution of JavaScript

example:
```html
<script>alert(document.domain)</script>
<img src=1 onerror=alert(1)> 
```

-sometimes some html tags and attributes are blocked , then you have to build payloads based on that.

* *xss into javascript*

When the XSS context is some existing JavaScript within the response, a wide variety of situations can arise, with different techniques necessary to perform a successful exploit. 

sometimes it in variables or other places.