# Checks \(API\)

This is a description of the API endpoints exposed by the Bolt server for checking for various kinds of permissions.

The following endpoints are described here:

* [GET: /api/checks/visible-apps/&lt;name&gt;](#get-apichecksvisible-appsname)
* [POST: /api/checks/has-permission](#post-apicheckshas-permission)

## GET: /api/checks/visible-apps/&lt;name&gt;

Gets an array of [app objects](/app-object.md) for all apps that are visible to the user with the specified username. It is possible to _hide_ some apps from some users. The icons of such apps should not be visible to those users on standard home pages.

For instance, to get all apps visible to user _adam_:

`localhost:400/api/checks/visible-apps/adam`

### response

If there is no error during the processing of the request, the `body` field of the response should hold an array of [app objects](/app-object.md).

---

## POST: /api/checks/has-permission

Checks to see if a user has been granted a permission on an app.

### request

A standard [Bolt request](bolt-request.md).

```
{
    "app" : String, //the name of the app that owns the permission we are checking for
    "permission" : String, //the permission to check for
    "user" : String //the name of the user against whom the permission is to be checked
}
```

### response

If the check was successfully, the `body` field of the response should look like this:

```
{
    "app": String, //same as above
    "permission": String, //same as above
    "user": String, //same as above
    "result": Boolean //if true, then the user has the specified permission on the specified app
}
```



