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
    "isBlocked": Boolean, //determines if the user has been blocked/suspended from accessing the system
    "lastVisit": Date, //the date of the user's last log into the system
    "phone": String, //the phone number of the user
    "visits": Number //the number of times the user has logged into the system
}
```



