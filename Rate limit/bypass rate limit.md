Where to look for Bugs
```
- login
- reset password
- 2fA
- Confirmation codes
- Sign up
```

using Null Chars

```
%00, %0d%0a, %09, %0C, %20, %0
```
```
>brute force using abc@xyz.com
	after some time
	you got blocked
>try abc@xyz.com%00
```

Host Header injection

```
Change Host:www.newsite.com
Change Host:localhost
Change Host:127.0.0.1
```


Changing cookies
```
For example if it blocks by 15 Requests
Change session on 14 req and try 
```


X-forwaded-forwaded-For
```
X-Forwarded: <IP>
X-Forwarded-For: <IP>
X-Forwarded-Host: <IP>
X-Client-IP: <IP>
X-Remote-IP: <IP>
X-Remote-Addr: <IP>
X-Host: <IP>
X-Originating-IP: <IP>
```

X-forwaded-forwaded-For
```
add 2 headers
add Header X-Forwaded-For:
add Header X-Forwaded-For:198.168.43.1
```
