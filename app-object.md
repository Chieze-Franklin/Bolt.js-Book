# App Object

This object represents information about an app. It is returned primarily by the [apps api](/apps-api.md) endpoints.

### Schema

```
{
    "controlledVisibility": Boolean, //determines if the app is visible to all users (when set to false)
    "dateCreated": Date, //the app the app was installed (or updated)
    "description": String, //the description of the app, same as the description field in the package.json
    "displayName": String, // the display name of the app, same as the bolt.displayName field in the package.json
    "files": Object, //same as the bolt.files field in the package.json
    "index": String, //same as the bolt.index field in the package.json
    "main": String, //same as the bolt.main field in the package.json
    "module": String, //same as the bolt.module field in the package.json
    "name": String, //the system-unique name of the app, same as the name field in the package.json
    "order": Number, //same as the bolt.order field in the package.json
    "package": Object, //the entire package.json
    "path": String, //the path to the root folder of the app, relative to the node_modules folder
    "main": String, //same as the bolt.main field in the package.json
    "system": Boolean, //same as the bolt.system field in the package.json
    "tags": [String], //same as the bolt.tags filed in the package.json
    "version": String //the version of the app, same as the version field of the package.json
}
```



