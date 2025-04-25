# Edit User

## Endpoint
```ts
POST https://www.onreservy.com/api/mobile/user/editUser
```

## Use
In order to update the user, you need to provide the session token through the request header like this:
```ts
Authorization: Bearer token
```
### Likes

#### Creatye lists
```json
{
    "like_lists": 
        {
            "action": "create-list",
            "name": "string"
        },
}
```
#### Delete lists
```json
{
    "like_lists": 
        {
            "action": "delete-list",
            "id": "string"
        },
    
}
```

#### Add business to list
```json
{
    "like_lists": 
        {
            "action": "add-business",
            "list_id": "string",
            "business_id": "string"
        },
}
```

## Responses
### <span style={{color: "rgb(161, 255, 39)"}}>Success</span>
The API will return the message, the user data, status and the session token. [client_user_schema](../../models/clientUser#client-user-schema)

```ts
{
    message: "User updated successfully",
    client_user: client_user_schema
}
```

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

Missing ID when deleting list  
  ```json
  {
    "message": "ID is required"
  }
  ```

No lists to delete or add  
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
Missing IDs when adding business to list  
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
