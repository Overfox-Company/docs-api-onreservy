# Invalidate User

## Endpoint
```ts
GET https://www.onreservy.com/api/mobile/user/invalidateUser
```

## Use
To deactivate (invalidate) the user's account, send a GET request to this endpoint.  
You must include the user's session token in the request header:

```ts
Authorization: Bearer token
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