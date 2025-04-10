# Credentials

This is a simple example of how to use credentias to login or register an user in a React Native app.




## Login


### Requiriments
 If you want to use this endpoint, you need send the following parameters in format JSON:

- `email`: The email of the user.
- `password`: The password of the user.

> **⚠️ NOTE:**  
> The `password` must:
> - Be at least **6 characters long**.
> - Contain at least **one uppercase letter**.
> - Contain at least **one lowercase letter**.
> - Contain at least **one number**.
> - Contain at least **one special character**.

### Endpoint
```typescript
POST https://www.onreservy.com/api/mobile/login/credentials
```

### Use
```json
{
    email: string,
    password: string,
}
```

### Responses

####   <span style={{color: "rgb(161, 255, 39)"}}>Success</span>
The API will return the message, the user data, status and the session token.
[client_user_schema](../../models/clientUser#client-user-schema)

```typescript
{
    message: "Login credentials success",
    token: token,
    client_user: client_user_schema
}
```

#### <span style={{color: "rgb(255, 39, 39)"}}>Failure</span>

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
In case all parameters are not provided:

```json
{
    "message": "You need all fields"
}
```
In case the user is not found:
```json
{
    "message": "User not found"
}
```

In case it is not a valid email:
```json
{
   "message": "Invalid email format"
}
```

In case the password does not meet any requirements:

```json
{
    "message": "Invalid password format"
}
```

In case the password is not correct:
```json
{
    "message": "Incorrect password"
}
```
## Register

### Endpoint
### Requiriments
 If you want to use this endpoint, you need send the following parameters in format JSON:

- `email`: The email of the user.
- `password`: The password of the user.
- `repeat_password`: The same `password` of the user.

> **⚠️ NOTE:**  
> The `password` and `repeat_password` must:
> - Be at least **6 characters long**.
> - Contain at least **one uppercase letter**.
> - Contain at least **one lowercase letter**.
> - Contain at least **one number**.
> - Contain at least **one special character**.

### Endpoint
```typescript
POST https://www.onreservy.com/api/mobile/register/credentials
```

### Use
```json
{
    email: string,
    password: string,
    repeat_password: string,
}
```
### Responses

####   <span style={{color: "rgb(161, 255, 39)"}}>Success</span>
The API will return the message, the user data, status and the session token. 
[client_user_schema](../../models/clientUser#client-user-schema)

    ```typescript
{
    message: "Register credentials success",
    token: token,
    client_user: client_user_schema
}
```
#### <span style={{color: "rgb(255, 39, 39)"}}>Failure</span>

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
In case all parameters are not provided:

```json
{
    "message": "You need all fields"
}
```
In case the user is founded:
```json
{
    "message": "This email has already been registered"
}
```

In case it is not a valid email:
```json
{
   "message": "Invalid email format"
}
```

In case the password does not meet any requirements:

```json
{
    "message": "Invalid password format"
}
```

In case passwords are not the same
```json
{
    "message": "Passwords do not match"
}
```
In case the password or email is too long
```json
{
    "message": "Input too long"
}
```