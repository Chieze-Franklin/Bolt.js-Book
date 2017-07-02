# User Object

This object represents information about a user. It is returned primarily by the [users api](/users-api.md) endpoints.

### Schema

```
{
    "dateCreated": Date, //the date the user was registered
    "description": String, //the description of the app, same as the description field in the package.json
    "displayName": String, // the display name of the user
    "displayPic": String, //the URL of the user's display picture, relative to the base URL of the Bolt server
    "email": String, //the email address of the user
    "name": String, //the system-unique name of the user
    "order": Number, //same as the bolt.order field in the package.json
    "package": Object, //the entire package.json
    "path": String, //the path to the root folder of the app, relative to the node_modules folder
    "main": String, //same as the bolt.main field in the package.json
    "system": Boolean, //same as the bolt.system field in the package.json
    "tags": [String], //same as the bolt.tags filed in the package.json
    "version": String //the version of the app, same as the version field of the package.json
}
```



