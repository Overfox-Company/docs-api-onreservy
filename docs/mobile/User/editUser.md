# Edit User

## Endpoint
```ts
POST https://www.onreservy.com/api/mobile/user/editUser
```

## Usage
To update the user, you must provide the session token in the request header:
```ts
Authorization: Bearer token
```

## Editable Parameters

You can send one or more of the following parameters in the JSON body:

| Parameter        | Type    | Description                                                                 |
|------------------|---------|-----------------------------------------------------------------------------|
| `user_name`      | string  | New username.                                                               |
| `phone`          | string  | New phone number.                                                           |
| `email`          | string  | New email address. Requires a verification code (see below).                |
| `code`           | string  | Verification code required to change the email address.                     |
| `like_lists`     | object  | Actions for managing favorite business lists (see below).                   |
| `notifications`  | object  | Actions for managing user notifications (see below).                        |

---

### Change Email

To change the user's email, you must provide both the new email and a valid verification code in the request body:

```json
{
  "email": "new@email.com",
  "code": "123456"
}
```

If the `code` is missing or invalid, the API will return an error.

---

### Likes

#### Create list
```json
{
  "like_lists": {
    "action": "create-list",
    "name": "string"
  }
}
```

#### Delete list
```json
{
  "like_lists": {
    "action": "delete-list",
    "id": "string"
  }
}
```

#### Add business to list
```json
{
  "like_lists": {
    "action": "add-business",
    "list_id": "string",
    "business_id": "string"
  }
}
```

#### Remove business from list
```json
{
  "like_lists": {
    "action": "delete-business",
    "list_id": "string",
    "business_id": "string"
  }
}
```

---

### Notifications

#### Mark notification as read
```json
{
  "notifications": {
    "action": "read",
    "id": "string"
  }
}
```

#### Delete notification
```json
{
  "notifications": {
    "action": "delete",
    "id": "string"
  }
}
```

---

## Responses

### <span style={{color: "rgb(161, 255, 39)"}}>Success</span>
The API will return a message, the user data, and status. [client_user_schema](../../models/clientUser#client-user-schema)

```ts
{
  message: "User updated successfully",
  client_user: client_user_schema
}
```

Or for specific actions:
```ts
{
  message: "List created successfully",
  client_user: client_user_schema
}
```
```ts
{
  message: "Notification deleted",
  client_user: client_user_schema
}
```
```ts
{
  message: "Notification read",
  client_user: client_user_schema
}
```

---

### <span style={{color: "rgb(255, 39, 39)"}}>Failure</span>

Token not sent or invalid  
```json
{
  "message": "Unauthorized"
}
```

User not found by token  
```json
{
  "message": "User not found"
}
```

Empty body  
```json
{
  "message": "Empty body"
}
```

Invalid JSON  
```json
{
  "message": "Invalid JSON"
}
```

Invalid action in like_lists  
```json
{
  "message": "Invalid action"
}
```

Missing name when creating list  
```json
{
  "message": "Name is required"
}
```

Missing ID when deleting list or notification  
```json
{
  "message": "ID is required"
}
```

No lists to operate  
```json
{
  "message": "No lists found"
}
```

List not found  
```json
{
  "message": "List not found"
}
```

Missing IDs when adding/removing business to/from list  
```json
{
  "message": "List ID and Business ID are required"
}
```

Business already in the list  
```json
{
  "message": "Business already in list"
}
```

Business not found in the list  
```json
{
  "message": "Business not found in list"
}
```

Notification not found  
```json
{
  "message": "Notification not found"
}
```

Invalid email format  
```json
{
  "message": "Invalid email format"
}
```

Code is required for change email  
```json
{
  "message": "Code is required for change email"
}
```

Invalid or expired code  
```json
{
  "message": "Invalid or expired code"
}
```
