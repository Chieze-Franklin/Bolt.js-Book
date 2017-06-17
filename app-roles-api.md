# App-Roles \(API\)

An app-role object is an object that represents an association between an app and a role. Such an association determines if users that have been assigned that role can start an app, access features in the app, access files in the app.

This is a description of the API endpoints exposed by the Bolt server for interacting with app-roles.

The following endpoints are described here:

* [GET: /api/app-roles](#get-apiapp-roles)

* [POST: /api/app-roles](#post-apiapp-roles)

* [DELETE: /api/app-roles](#delete-apiapp-roles)

## GET: /api/app-roles

Gets an array of app-role association [objects](/objects.md) for all registered app-roles matching the specified criteria.

You specify search criteria in the URL query portion. For instance, to get all app-roles for role admin:

`localhost:400/api/app-roles?role=admin`

### response

If there is no error during the processing of the request, the `body` field of the response should hold an array of app-role [objects](objects.md).

---

# POST: /api/app-roles

Adds an app-role association to the database.

### request

A standard [Bolt request](bolt-request.md).

`{`

`"app" : String, //name of the app being referenced`

`"role" : String //name of the role being referenced`

`}`

### response

If the app-role was added successfully, the `body` field of the response should hold an app-role object.

### security

Only system apps \(and native views\) can send requests to this endpoint.

---

## DELETE: /api/app-roles

Deletes an array of app-role association objects for all registered app-roles matching the specified criteria.

You specify search criteria in the URL query portion. For instance, to delete all app-roles for app app`1`:

`localhost:400/api/app-roles?app=app1`

### response

If there is no error during the processing of the request, the `body` field of the response should hold an array of app-role objects.

### security

Only system apps \(and native views\) can send requests to this endpoint.

