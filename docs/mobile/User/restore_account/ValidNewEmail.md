# Send Code to Change Email

## Endpoint
```ts
POST https://www.onreservy.com/api/mobile/restore-account/validNewEmai
```

## Use
To request a code for changing the user's email, send a POST request with the new email in the JSON body.  
You must include the user's session token in the request header:

```ts
Authorization: Bearer token
```

### Example Request Body

```json
{
  "email": "new@email.com"
}
```

---

## Responses

### <span style={{color: 'rgb(161, 255, 39)'}}>Success</span>
If the code is sent successfully:

```json
{
  "message": "The chage email code has been sended"
}
```

---

### <span style={{color: 'rgb(255, 39, 39)'}}>Failure</span>

No API key  
```json
{
  "message": "No API key"
}
```

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

Internal server error  
```json
{
  "message": "Error in signup route",
  "error": "..."
}
```

---

## Notes

- The user must be authenticated (send a valid session token).
- Only one active (not expired) code can exist per user at a time.
- The code will be sent to the provided email and will expire after a short period.
- This code is required to confirm the email change in the next step.