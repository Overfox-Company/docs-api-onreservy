# Generate Password Restore Code

## Endpoint
```ts
POST https://www.onreservy.com/api/mobile/restore-account/getCode
```

## Use
To generate a password restore code, send a POST request with the user's email in the body as JSON:

```json
{
  "email": "user@example.com"
}
```

## Responses

### <span style={{color: 'rgb(161, 255, 39)'}}>Success</span>
If the code is generated and sent successfully:

```json
{
  "message": "The password restore code has been sended"
}
```

### <span style={{color: 'rgb(255, 39, 39)'}}>Failure</span>

Invalid JSON  
```json
{
  "message": "Invalid JSON"
}
```

User not found  
```json
{
  "message": "User not found"
}
```

Pending code already exists  
```json
{
  "message": "You already have a code pending"
}
```

Error sending email  
```json
{
  "message": "Error sending email"
}
```

Missing API key (internal error)  
```json
{
  "message": "No API key"
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

- The code is a 6-digit number, generated to avoid three identical digits in a row.
- The code expires after 2 minutes and 10 seconds.
- Only one valid (not expired) code can exist per user at a time.
- The code is sent to the user's email address.