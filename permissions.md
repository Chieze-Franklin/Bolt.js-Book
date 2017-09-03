# permissions

Apps can define various permissions, and later check if the current user has the required permissions.

To define permissions, create a `bolt.permissions` object in the _package.json_ file.

```
"permissions": {
    "create-student": {
        "displayName": "Permission to create a student",
        "description": "This grants you the permission to create a new student in the system"
    }
}
```

In the above snippet the developer defines a permission called `create-student`, and gives it a user-friendly `displayName` and a `description`.

A shorter format simply specifies and name and display name for the permission.

```
"permissions": {
    "create-student": {
        "displayName": "Permission to create a student",
        "description": "This grants you the permission to create a new student in the system"
    },
    "delete-student": "Permission to delete student"
}
```

The permission called `delete-student` has a `displayName` set to `Permission to delete student` but no `description`.

Permissions usually are granted to users during run-time.

To check if a user has been granted a certain permission defined by an app, see the [Checks \(API\)](/checks-api.md).



