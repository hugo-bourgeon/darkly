# LOCAL_FILE_INCLUSION

## 🏴 Flag
```
b9e775a0291fed784a2d9680fcfad7edd6b8cdf87648da647aaf4bba288bcab3 
```

## 📌 Extract

Page: [http://{IP}/](http://{IP}/)  
Modification: Inspect the `<a href>` and change `site=facebook` by `site=whatever`, then click on facebook icon link to get flag..

```html
<a href="index.php?page=redirect&amp;site=whatever" class="icon fa-facebook"></a>
```

The site parameter in the URL `index.php?page=redirect&site=facebook` can be modified. This means the server redirects the user based on **user-side-controlled** input without proper validation.

## 🎯 Use

- **🎣 Phishing:** An attacker can replace facebook with a malicious URL, tricking users into believing they are visiting a legitimate site.  

- **Data Exfiltration:** If used in a context where session tokens or sensitive parameters are passed in the URL.  

- **Security Bypass:** It can be exploited to redirect users to restricted or unintended resources.

## 🔒 Prevention

Validate and **restrict redirection** destinations to an allowlist.

Never allow **uncontrolled user input** in redirects.

Use **tokens** or **internal mappings** instead of directly modifiable parameters.

## 📚 Documentation

[stackhawk.com (what-is-open-redirect)](https://www.stackhawk.com/blog/what-is-open-redirect/)  
[learn.snyk.io (open-redirect)](https://learn.snyk.io/lesson/open-redirect/)  
[brightsec.com (open-redirect-vulnerabilities)](https://brightsec.com/blog/open-redirect-vulnerabilities/)

### 📖 [Home page](https://github.com/hugo-bourgeon/darkly#README)

