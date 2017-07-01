# User-Role Object

This object represents information about the relationship between a user and a role. It is returned primarily by the [user-roles api](/user-roles-api.md) endpoints.

### Schema

```
{
    "role": String, //the name of the role in this relationship
    "role_id": ObjectId, //the ID of the role in this relationship
    "user": String, //the name of the user in this relationship
    "user_id": ObjectId, //the ID of the user in this relationship
    "dateCreated": Date, //the date this relationship was created
}
```



