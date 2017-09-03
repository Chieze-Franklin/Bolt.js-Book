# Permission Object

This object represents a permission. It is returned primarily by the [permissions api](/permissions-api.md) endpoints.

### Schema

```
{
    "app": String, //the name of the app that owns this permission
    "name": String, //the unique name of the permission
    "description": String, //the description of the permission
    "displayName": String //the user-friendly name for the permission
}
```



