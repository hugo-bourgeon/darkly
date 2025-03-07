# Stored XSS

## 🏴 Flag

```
0fbb54bbf7d099713ca4be297e1bc7da0173d8b3c21c1811b916a3a86652724e
```

## 📌 Extract

Page: [http://{IP}/?page=feedback](http://{ip}}/?page=survey)

In the textarea balise we can type an input for the next comment. And we can see that a comment is built like this:

```html
<tr><td>Comment : This is the best site EVER</td></tr>
```

We just have to close the <td> block with </td> as input and implement a script just after

```html
<tr><td>Comment : </td><script>alert("pwned")</script></tr>
```

We modify the website and everybody will see the alert

## **🎯 Use**

This vulnerability lets attackers inject malicious scripts into stored data that the application trusts. Without proper validation, they can:

- Modify **content** or **comments** to display malicious scripts.
- Change **user profiles** to inject harmful code.
- Escalate **privileges** by altering stored data.
- **Bypass restrictions** by submitting unexpected scripts.

## **🔒 Prevention**

1. **Input Sanitization:** Always sanitize user input to remove potentially malicious scripts.
2. **Do Not Trust Stored Data:** Any data that can be modified by users should be treated as untrusted.
3. **Enforce Authentication & Authorization:** Restrict modifications to authorized users.
4. **Content Security Policy (CSP):** Implement CSP headers to prevent execution of unauthorized scripts.
5. **Log & Monitor:** Detect abuse by tracking unusual script injections and actions.

## 📚 Documentation

📖 [OWASP](https://owasp.org/www-project-web-security-testing-guide/v41/4-Web_Application_Security_Testing/07-Input_Validation_Testing/02-Testing_for_Stored_Cross_Site_Scripting.html)

### 📖 [Home page](https://github.com/hugo-bourgeon/darkly#readme)