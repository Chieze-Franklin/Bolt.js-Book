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

### Tip

Although not foolproof, you can use `permissions` to limit features in your app in the demo or trial versions. To achieve this, provide a _package.json_ that does not list a particular permission. For instance, the code snippet above does not list a permission named `edit-student`. Because the permission is not listed in the _package.json_ it can never be granted to any user. This means whenever you [check](/checks-api.md) if a user has been granted the `edit-student` permission, the result will always be false. On the other hand, you can include the `edit-student` permission in the _package.json_ of the full app so that it can be granted to users.

Also, you can simply check if the permission is returned by [/api/permissions?app=&lt;your app name&gt;](/permissions-api.md). If the permission is missing in the returned array then you can conclude that the version of your app the user is running is the trial or demo version.

