# Validate Password Restore Code

## Endpoint
```ts
POST https://www.onreservy.com/api/mobile/restore-account/validateCode
```

## Use
To validate a password restore code, send a POST request with the code in the body as JSON:

```json
{
  "code": "123456"
}
```


## Responses

### <span style={{color: 'rgb(161, 255, 39)'}}>Success</span>
If the code is valid and not expired or used:

```json
{
  "message": "correct"
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

Code not found  
```json
{
  "message": "Code not found"
}
```

Code expired  
```json
{
  "message": "Code expired"
}
```

Code already used  
```json
{
  "message": "Code already used"
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

- The code must be a valid, not expired, and unused restore code.
- The code is a 6-digit number generated previously by the restore code endpoint.
- If the code is valid, you can proceed to reset the password.