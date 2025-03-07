# SQL Injection

### 🏴 Flag

```
f2a29020ef3132e01dd61df97fd33ec8d7fcd1388cc9601e7db691d17d4d6188
```

## 📌 Extract

Page: [http://{IP}/?page=member](http://{ip}}/?page=survey)

Look at the previous chapter to see how to get all data, the data.

This is the interesting image.

```
Surname : 5
borntosec.ddns.net/images.png
Hack me ?
If you read this just use this md5 decode lowercase then sha256 to win this flag ! : 1928e8083cf461a51303633093573c46
```

Decode the input with md5, it gives us “albatroz”

and then albatroz in sha256 is: 

f2a29020ef3132e01dd61df97fd33ec8d7fcd1388cc9601e7db691d17d4d6188

## 🎯 Use

This vulnerability lets attackers manipulate SQL queries to gain unauthorized access to the database. Without proper validation, they can:

- **Access sensitive data** such as user credentials or personal information.
- **Modify or delete data** to disrupt the application's functionality.
- **Escalate privileges** by altering database permissions.
- **Bypass authentication** mechanisms to gain unauthorized access.

## 🔒 Prevention

1. **Use Prepared Statements:** Always use parameterized queries to separate SQL code from data.
2. **Input Validation:** Validate and sanitize all user inputs to prevent malicious SQL code.
3. **Least Privilege Principle:** Limit database permissions to only what is necessary.
4. **Stored Procedures:** Use stored procedures to abstract SQL queries from user input.
5. **Regular Audits:** Monitor and audit database access and queries for suspicious activity.

## 📚 Documentation

📖 [OWASP](https://owasp.org/www-community/attacks/SQL_Injection)

### 📖 [Home page](https://github.com/hugo-bourgeon/darkly#readme)