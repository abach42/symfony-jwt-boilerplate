# Symfony 6 JWT 

## Get started

1. Change passphrases 

```
# .env
APP_SECRET=CHANGE_ME
JWT_PASSPHRASE=CHANGE_ME
```

2. Run composer
```
composer install
```

3. Generate keypair
```
symfony console lexik:jwt:generate-keypair
```

4. Start database
```
docker compose up
```

5. Load fixtures
```
symfony console doctrine:migrations:migrate
symfony console doctrine:fixtures:load
```

6. Start symfony server
```
symfony serve
```

## Use 
You could use fixture.http in your IDE (Some IDE plugin required).

1. Send credentials to get JWT token.
```
###

POST https://localhost:8000/api/login_check HTTP/1.1
Content-Type: application/json

{
    "email": "my@example.com",
    "password": "test"
}

###
```

2. Validate token by sending token in request header. (Replace {token} by token from response above).
```
###
 
GET https://localhost:8000/home HTTP/1.1
Authorization: Bearer {token}

###
```

### Example
```
###
 
GET https://localhost:8000/home HTTP/1.1
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJpYXQiOjE2ODc0NTk2NzksImV4cCI6MTY4NzU4OTI3OSwicm9sZXMiOlsiUk9MRV9VU0VSIl0sImVtYWlsIjoibXlAZXhhbXBsZS5jb20ifQ.j6Mmrn8spg1PKN8JCrQAmxx11-yULFKeYayH3lFVTZPRPNJwVsJ1JzAl66qt7ozAx1OLBYRfUc7iXuDC6i5561yemrhI0Fr-88vUO8Iofpuk6yy9K2YuVbdFciu6jvsz2Tp1nCswCYpKO--F83abLdx6w6nflq2Ol9b4wH2XA1H4HTVGage2jaOczM5rpWf5iOEjN13K-KhKdHIVLmaJ03A2m9_JzJK31EovxvWnFWSx6BEygkl7DnYzGTD4tcI4DpNPOKrzAEfIa3cdHEJkiA7QAaop0ebVT2Mr_AAtlo5y1yda-sv5fZUhzdmtZzIfMf1qYb8HTSsKCsnBsNKmrw

###
```

### Response could be
```
{
    "iat": 1234567890,
    "exp": 1234567890,
    "roles": [
        "ROLE_USER"
    ],
    "email": "my@example.com"
}
```