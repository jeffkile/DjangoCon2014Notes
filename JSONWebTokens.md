


http://bit.ly/djangocon-jwt

#Auth
- Traditional
    - Cookie based
- Modern
    - Token based
    - Good for AJAX because only using HTTP headers
    - Dont have to guard against cross site forgeries
    - No "cookie containers" in mobile apps

#Javascript Web Tokens
* JSON object signed using JSON Web Signature
* JSON Web Algorithms
    - JSON Web Key
    - JSON Web Token
    - JSON Web Signature
        - Prevents Tamporing payload
        - Prevents man in in the middle
    - JSON Web Encryption
        - Prevents payload being read


Internet draft is good to read

#Tokens
* Do not build your own use a 3rd party library
    - Use PyJWT
* Base 64 encoded strings
* Token structure
    - `header`.`payload`.`signature`
* Header
    - `typ: JWT`
    - `alg: HS256` - Hash algorithm used
* Paylod
* Signature
    - Secret Key

#PyJWT
* Install
    - pip install pyjwt
* 3 years old, well tested
Useage:
``` scret_key = "abc123"
paytload = {"data": 123}
jwt_token = jwt.encode(payload, secret)
payload = jwt.decode(jwt_token, secret)
```

#View mixin
`JsonWebTokenAuthMixin` can be used in class based views

#Django Rest Framework, JSON
* 1.01
    - Support for django 1.7
* `pip install djangorestframework-jwt`
* `JSONwebTokenAuthentication`

# Recap
* Good for client side heavy apps
    - When its good to be stateless
    - REST APIs
* It is a standard
* Its easy
* Third party libraries
* Single sign on
* Action links
* Authentication
    - CORS 
    - Stateless
    - No CSRF 
    - CDN 
        - Faster
    - Mobile/Websockets

