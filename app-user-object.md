# App-User Object

This object represents information about the relationship between an app and a user. It is returned primarily by the [app-users api](/app-users-api.md) endpoints.

### Schema

```
{
    "app": String, //the name of the app in this relationship
    "app_id": ObjectId, //the _id of the app in this relationship
    "user": String, //the name of the user in this relationship
    "user_id": ObjectId, //the _id of the user in this relationship
    "dateCreated": Date, //the date this relationship was created
    "starts": Number, //the number of times the user has started the app
    "lastStart": Date //the date of the last time the user started the app
}
```



