# Change User Password

## Endpoint
```ts
POST https://www.onreservy.com/api/mobile/restore-account/changePassword
```

## Use
To change the user's password, send a POST request with the restore code and the new password in the body as JSON:

```json
{
  "code": "123456",
  "newPassword": "yourNewPassword123!"
}
```


## Responses

### <span style={{color: 'rgb(161, 255, 39)'}}>Success</span>
If the password is changed successfully:

```json
{
  "message": "The password has been changed succesfully "
}
```

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

Missing new password  
```json
{
  "message": "New password is required"
}
```

Invalid password format  
```json
{
  "message": "Invalid password format"
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

Request expired  
```json
{
  "message": "Request expired"
}
```

User not found  
```json
{
  "message": "User not found"
}
```

Password is the same as previous  
```json
{
  "message": "The password must be different from the previous password"
}
```

Internal server error  
```json
{
  "message": "Error in signup route",
  "error": "..."
}
```

## Notes

- The code must be valid, not expired, and unused.
- The new password must meet the required format (see password policy).
- The new password must be different from the previous password.
- If the password is changed, the code is marked as used and cannot be reused.