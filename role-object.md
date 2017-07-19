# Role Object

This object represents a role. It is returned primarily by the [roles api](/roles-api.md) endpoints.

### Schema

```
{
    "name": String, //the unique name of the role
    "description": String, //the description of the role
    "displayName": String, //the user-friendly name for the role
    "isAdmin": Boolean, //a value that determines if this role has the ability to circumvent certain restrictions
    "dateCreated": Date, //the date this relationship was created
}
```

It may be better to explicitly grant a role many permissions than to simply set its `isAdmin` field to `true`. Roles that have `isAdmin` set to `true` are implicitly granted every permission defined by every app available \(which may not be what you want\).



