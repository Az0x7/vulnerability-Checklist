## Authentication Bypass
[ ] 
```
1. Check if post authentication URLs are directly accessible and do not have any session bound to it.
2. In case the URL is stolen/guessable/brute-forceable, it can lead to account takeover.
```

[ ] CAPTCHA Bypass - X-Forwarded-For
```
1. Bypass the CAPTCHA check by injecting a random value into the **X-Forwarded-For header
```

[ ] Lack of Password Confirmation
```
Test if password confirmation is necessary with these actions:
- Change Email Address
- Change Password
- Delete Account
- Manage 2FA
```

[ ] Lack of Verification Email
```
1. Check that during the registration process, an email verification is necessary
```


[ ] No Rate Limiting on a Form
```
1. Send a form and intercept the request with Burp proxy
2. Send the request to intruder
3. Repeat sending the same request 20-30 times
4. Observe that all of these forms are sent without any restrictions
```


[ ] No Rate Limiting or Captcha on Login Page
```
1. Go to login page and send the unsuccessful login attempt request to Burp Intruder
2. Change the password values for brute force as random values
3. Observe that the response to the 20 or 30th request doesn't change and the account is not locked.
```

[ ] Username Email Address Enumeration
```
1. Go to password reset/login/register or any other area that allows writing username or email address input
2. Write an existing username/email address with wrong password to observe error message
3. Write a non-existing username/email address to observe error message
4. See if error message leaks the information of the existence of username/email addresses
```

[ ] Weak Password Policy
```
1. Change password to only numerical
2. Change password to only lower case
3. Change password to common passwords
4. Change password to short passwords
5. Observe that the application has weak or no password policy
```

[ ] Weak Registration Implementation over HTTP
```
1. Intercept the request during the registration to the application via Burp
2. Observe that registration request is sent over HTTP
```

[ ] secure data transport
```
1. search on login page 
2. Send a form and intercept the request with Burp proxy
3. intercept the request with wireshark
4. make sure that the data transport is encryption or not 
```

[ ] Username enumeration
```
1. Status codes
2. Error messages
3. Response times 
   X-Forwarded-For: 
```
   
[ ] Broken Authentication Session Token Bug
```
1. Create a courier account or use existing one.
2. Confirm Your email address.
3. Now log out from your account and request for password reset code for your account .
4. Don't use the code that has been sent to your email address.
5. In new tab or new browser log in back to your account.
6. Go to account setting and change your password .
7. Now go to email and check the password reset code that we requested in step 3.
8. Change Your password using that reset password code .
9. You can see that your password has been changed.
```

[ ] Broken Authentication and Session Management
```
1. Create a Phabricator account having email address "a@x.com".
2. Now Logout and ask for password reset link. Don't use the password reset link sent to your mail address.
3. Login using the same password back and update your email address to "b@x.com" and verify the same. Remove "a@x.com".
4. Now logout and use the password reset link which was mailed to "a@x.com" in step 2.
5. Password will be changed.
```


