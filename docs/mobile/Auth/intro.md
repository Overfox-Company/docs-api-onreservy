---
sidebar_position: 1
---

# OAuth google v2

This is a simple example of how to use OAuth 2.0 with Google in a React Native app.

## Endpoint

```typescript
POST https://www.onreservy.com/api/mobile/login/google
```

## Requiriments
 If you want to use this endpoint, you need send the following parameters:

- `google_token`: The token you get from Google after the user has logged in.

## Use
you make a request to the endpoint with the token you get from Google after the user has logged in, when google returns you the token id you must send it in JSON format as follows:
```json
{
  "google_token": "token"
}
```

## Responses

###   <span style={{color: "rgb(161, 255, 39)"}}>Success</span>
The API will return the message, the user data, status and the session token, in case the user does not exist, it will be created automatically.

    ```typescript
{
    "message": "login google succes",
    "token": token,
    "client_user": {
        "_id":string,
        "user": string,
        "email": string,
        "name": string,
        "password": string,
        "lastName": string,
        "phone": string | null,
        "avatar": string | null,
        "googleId": string | null,
        "createdAt": string,
        "updatedAt": string,
    }
}
```
### <span style={{color: "rgb(255, 39, 39)"}}>Failure</span>

In case the request body is empty:
```json
{
    "message": "Empty body"
}
```
In case a json format is not sent in the request body:

```json
{
    "message": "Invalid JSON"
}
```
In case **`google_token`** parameter is not provided

```json
{ 
    "message": "No token provided"
}
```
In case the token is invalid:

```json
{
    "message": "Invalid token"
}
```
In case the token is expired:

```json
{
    "message": "Token used too late"
}
```