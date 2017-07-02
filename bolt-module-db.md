# bolt-module-db

This module installs the `/api/db` endpoints which allows apps to use the same database Bolt uses to store their objects. This means apps don't need their own separate databases.

To install this module, navigate to the Bolt endpoint `/install`, and type in _bolt-module-db_ as the app name. Go ahead and click **Download** \(or **Sideload**, as the case may be\). Take care to install this module as a system app.

This app is marked as a module, meaning \(among other things\) that it defines no user interface. Its installation registers the routers that respond to the requests sent to the `/api/db` endpoints.

The following endpoints are described here:

* [DELETE: /api/db](#delete-apidb)

## DELETE: /api/db

Drops an app's database.

To drop your own database, include the `X-Bolt-App-Token` custom header in the request. To drop another app's database, specify the app's name in the `app` or `db` field of the request body.

### request

A standard [Bolt request](bolt-request.md).

```
{
    "app": String, //(optional) name of the app whose database is to be dropped
    "db": String //(optional) same as the app field above
}
```

### response

If there is no error during the processing of the request, the `body` field of the response should hold an boolean value of true \(for a successful drop\) or false.

### security

To drop a database, an app must either be the owner of the database or must be listed as one of the `tenants` of the database.

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

You specify search criteria in the URL query portion. For instance, to delete all app-roles for app _settings_:

`localhost:400/api/app-roles?app=settings`

### response

If there is no error during the processing of the request, the `body` field of the response should hold an array of app-role objects.

### security

Only system apps \(and native views\) can send requests to this endpoint.

