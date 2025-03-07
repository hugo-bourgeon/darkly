# TAMPERING_BYPASS_RESTRICTION

## 🏴 Flag
```
1d4855f7337c0c14b6f44946872c4eb33853f40b2d54393fbe94f49f1e19bbb0 
```

## 📌 Extract

Page: [http://{IP}/?page=recover](http://{IP}/?page=recover)  
Modification: Inspect the `<input>`   change `value="webmaster@borntosec.com"` by `value="whatever"`, then click submit buttom to get flag.

```html
<input type="hidden" name="mail" value="whatever" maxlength="15">
```

## 🎯 Use

This vulnerability lets attackers manipulate client-side values that the application trusts. Without proper validation, they can:

- Modify **scores** or **ratings** to gain unfair advantages.

- Change **prices** in e-commerce platforms to pay less.

- Escalate **privileges** by altering user roles.

- **Bypass restrictions** by submitting unexpected values.

## 🔒 Prevention

1. **Server-Side Validation:** Always validate user input before processing.  

2. **Do Not Trust Client-Side Data:** Forms, URLs, cookies, and hidden fields can be manipulated.  

3. **Enforce Authentication & Authorization:** Restrict modifications to authorized users.  

4. **Integrity Checks:** Use cryptographic signatures or tokens to protect data.  

5. **Log & Monitor:** Detect abuse by tracking unusual parameter values and actions.

## 📚 Documentation

[imperva.com (parameter-tampering)](https://www.imperva.com/learn/application-security/parameter-tampering/)

### 📖 [Home page](https://github.com/hugo-bourgeon/darkly#readme)
