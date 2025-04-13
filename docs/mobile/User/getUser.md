# Get User

## Endpoint
```ts
GET https://www.onreservy.com/api/mobile/user/getUser
```

## Use
In order to get the user data, you need to provide the session token through the request header like this:
```ts
Authorization: Bearer token
```

## Responses

###   <span style={{color: "rgb(161, 255, 39)"}}>Success</span>
The API will return the message, the user data, status and the session token. [client_user_schema](../../models/clientUser#client-user-schema)


```ts
{
    message: "login google succes",
    token: token,
    client_user: client_user_schema
}
```

### <span style={{color: "rgb(255, 39, 39)"}}>Failure</span>

In the event that a token is not sent or is invalid, the API will return a 401 status code with the following message:

```json
{
     "message": "Unauthorized"
}
```
in case a user with the token id is not found:
```json
{
     "message": "User not found"
}
```