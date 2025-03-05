# TAMPERING

## 🏴 Flag
```
03a944b434d5baff05f46c4bede5792551a2595574bcafc9a6e25f67c382ccaa 
```

## 📌 Extract

Page: [http://{IP}/?page=survey](http://{IP}}/?page=survey)  
Modification: Inspect the `<select>` input and change a value.

```html
<option value="1000">10</option>
```

The website assumes the `<select>` value is trustworthy. Since it is **client-side**, you can modify it before submission. Here, changing "10" to "100" allows sending an unexpected value.

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

### 📖 [Home page](https://github.com/hugo-bourgeon/darkly#README)

