# App-Users \(API\)

An app-user object is an object that represents an association between an app and a user. Such an association determines how many times a user has interacted with an app.

This is a description of the API endpoints exposed by the Bolt server for interacting with app-users.

The following endpoints are described here:

* [GET: /api/app-users](#get-apiapp-users)

* [POST: /api/app-users](#post-apiapp-users)

* [DELETE: /api/app-users](#delete-apiapp-users)

## GET: /api/app-users

Gets an array of [app-user association objects](/app-user-object.md) for all registered app-users matching the specified criteria.

You specify search criteria in the URL query portion. For instance, to get all app-users for user _adam_:

`localhost:400/api/app-users?user=adam`

### response

If there is no error during the processing of the request, the `body` field of the response should hold an array of [app-user objects](/app-user-object.md).

---

# POST: /api/app-users

Adds an app-user association to the database.

### request

A standard [Bolt request](bolt-request.md).

```
{
    "app" : String, //name of the app being referenced
    "user" : String //name of the user being referenced
}
```

### response

If the app-user was added successfully, the `body` field of the response should hold an app-user object.

### security

Only system apps \(and native views\) can send requests to this endpoint.

---

## DELETE: /api/app-users

Deletes an array of app-user association objects for all registered app-users matching the specified criteria.

You specify search criteria in the URL query portion. For instance, to delete all app-users for app _settings_:

`localhost:400/api/app-users?app=settings`

### response

If there is no error during the processing of the request, the `body` field of the response should hold an array of app-user objects.

### security

Only system apps \(and native views\) can send requests to this endpoint.

