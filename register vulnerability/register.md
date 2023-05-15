## register vulnerability
[ ] Duplicate registration overwrite existing user
```
1. create first account in application with email say abc@gmail.com and password
2. logout of the account and create another account with same email and different password
3. you can even try to change email case like from abc2gmail.com to Abc@gmail.com
4. finish the creation proccess and see that it succceed
5. now go back and try to login with email and the new password ,you are seccess logged in
```
[ ] Dos at name /password field in sign up page
```
1. go to sign up form
2. fill the form and enter a long string in password 
3. click on enter and you will get 500 internal server error if it is vulnerability
```

[ ] no rate limit at signup page
```
1. enter your details in signuo form and submit the form
2. capture the signuo request and send it to intruder
3. add $$ to email parameter
4. in the payload add different email address
5. fire up intruder and check whether it return 200 ok
```

[ ] xss in username,email
```
xss can be test in any of parameter
1. payload for text field:
2. payload for email field:
3. you can use bypassing filter
```

[ ] email varification can be easily bypassed with following method
```
1. response manipulation change the bad respone with good one like false to true
2. status code manipulation change the 403 to 200
```

[ ] weak register implemntation
```
1. check whether the allows disposable email addresses
2. register form on non-hhtps page
```

[ ] weak password policy
```
1. check whether application allows easily guessable passsword like 123456
2. check if you can use username same as the email address
3. check if can use password same as that email address
4. improperly implemented password recovery link functionality
```

[ ] Path Overwrite
```
If an application allows users to check their profile with direct path /{username} always try to signup with system reserved file names, such as index.php, signup.php, login.php, etc. In some cases what happens here is, when you signup with username: index.php, now upon visiting target.tld/index.php, your profile will comeup and occupy the index.php page of an application. Similarly, if an attacker is able to signup with username login.php, Imagine login page getting takeovered.
```
