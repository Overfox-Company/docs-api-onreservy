# Login With Code

## Endpoint
```ts
POST https://www.onreservy.com/api/mobile/restore-account/loginWhitCode
```

## Use
To log in using only your email and a previously validated code, send a POST request with the following JSON body:

```json
{
  "email": "user@email.com",
  "code": "123456"
}
```

---

## Responses

### <span style={{color: 'rgb(161, 255, 39)'}}>Success</span>
If the login is successful:

```json
{
  "message": "Login success",
  "token": "jwt_token_here",
  "client_user": client_user_schema
}
```

- `token`: JWT token for authenticated requests.
- `client_user`: The user object.

---

### <span style={{color: 'rgb(255, 39, 39)'}}>Failure</span>

Invalid JSON  
```json
{
  "message": "Invalid JSON"
}
```

Missing code  
```json
{
  "message": "Code is required"
}
```

Missing email  
```json
{
  "message": "Email is required"
}
```

Code not found  
```json
{
  "message": "Code not found"
}
```

Code already used  
```json
{
  "message": "Code already used"
}
```

User not found  
```json
{
  "message": "User not found"
}
```

Request expired  
```json
{
  "message": "Request expired"
}
```

Internal server error  
```json
{
  "message": "Error in signup route",
  "error": "..."
}
```

---

## Notes

- The code must be valid, not expired, and unused.
- The email must match the user associated with the code.
- On success, you will receive a JWT token for authenticated requests.