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
4. Load fixtures
```
symfony console doctrine:migrations:migrate
```
5. 
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

```json
{
    "iat": 1234567890,
    "exp": 1234567890,
    "roles": [
        "ROLE_USER"
    ],
    "email": "my@example.com"
}
```