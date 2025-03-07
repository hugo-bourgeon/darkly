# SQL Injection

## 🏴 Flag

```
b3a6e43ddf8b4bbb4125e5e7d23040433827759d4de1c04ea63907479a80a6b2
```

## 📌 Extract

Page: [http://{IP}/?page=member](http://{ip}}/?page=survey)

Page login: http://{IP}/?page=signin

Look at the previous chapter to see how to get all data, the data.

This is the interesting user is:

```
ID : 1
username: root
password: 3bf1114a986ba87ed28fc1b5884fc2f8
```

Decode the password with md5, it gives us “shadow”

And then we can connect with the admin account.

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