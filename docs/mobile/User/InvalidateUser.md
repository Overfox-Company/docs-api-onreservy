# Invalidate User

## Endpoint
```ts
POST https://www.onreservy.com/api/mobile/user/invalidateUser
```

## Use
To deactivate (invalidate) the user's account, send a POST request to this endpoint whit the password parameter.  
You must include the user's session token in the request header:

If the user wants to leave feedback on why he/she decides to delete the account, send the message parameter, this parameter is optional.

```ts
Authorization: Bearer token
```

```json
{
  "password": "passwrord",
  "message": "User feedback"
}
```
---

## Responses

### <span style={{color: 'rgb(161, 255, 39)'}}>Success</span>
If the account is successfully invalidated:

```json
{
  "message": "Your account has been deleted"
}
```

---

### <span style={{color: 'rgb(255, 39, 39)'}}>Failure</span>


User not found  
```json
{
  "message": "User not found"
}
```
Incorrect password  
```json
{
  "message": "Incorrect password"
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
- This action sets the user's `inactive` status to `true`, effectively deactivating the account.
- The user will not be able to use the account until it is reactivated (if supported).