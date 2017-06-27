# App-Role Object

This object represents information about the relationship between an app and a role. It is returned primarily by the [app-roles api](/app-roles-api.md) endpoints.

### Schema

```
{
    "app": String, //the name of the app in this relationship
    "app_id": ObjectId, //the ID of the app in this relationship
    "role": String, //the name of the role in this relationship
    "role_id": ObjectId, //the ID of the role in this relationship
    "dateCreated": Date, //the date this relationship was created
    "permissions": [String] //an array of the names of the permissions granted to the role in this relationship
}
```



