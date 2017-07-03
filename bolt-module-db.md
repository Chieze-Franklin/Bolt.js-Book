# bolt-module-db

This module installs the `/api/db` endpoints which allows apps to use the same database Bolt uses to store their objects. This means apps don't need their own separate databases.

To install this module, navigate to the Bolt endpoint `/install`, and type in _bolt-module-db_ as the app name. Go ahead and click **Download** \(or **Sideload**, as the case may be\). Take care to install this module as a system app.

This app is marked as a module, meaning \(among other things\) that it defines no user interface. Its installation registers the routers that respond to the requests sent to the `/api/db` endpoints.

The following endpoints are described here:

* [DELETE: /api/db](#delete-apidb)
* [DELETE: /api/db/{{collection}}](#delete-apidbcollection)
* POST: /api/db/{{collection}}/find

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

If there is no error during the processing of the request, the `body` field of the response should hold an boolean value of `true` \(for a successful drop\) or `false`.

### security

To drop a database, an app must be the owner of the database.

---

# DELETE: /api/db/{{collection}}

Drops a collection in the app's database.

If dealing with your own database, include the `X-Bolt-App-Token` custom header in the request. If dealing with another app's database, specify the app's name in the `app` or `db` field of the request body.

### request

A standard [Bolt request](bolt-request.md).

```
{
    "app": String, //(optional) name of the app whose database is to be affected
    "db": String //(optional) same as the app field above
}
```

### response

If there is no error during the processing of the request, the `body` field of the response should hold an boolean value of `true` \(for a successful drop\) or `false`.

### security

To drop a collection in a database, an app must either be the owner of the database or must be listed as one of the `tenants` of the collection.

---

## POST: /api/db/{{collection}}/find

Finds all the objects in the specified collection matching the given query.

If dealing with your own database, include the `X-Bolt-App-Token` custom header in the request. If dealing with another app's database, specify the app's name in the `app` or `db` field of the request body.

### request

A standard [Bolt request](bolt-request.md).

```
{
    "app": String, //(optional) name of the app whose database is to be affected
    "db": String, //(optional) same as the app field above
    "query": Object, //(optional) specifies selection filter using MongoDB query operators.
    "map": Object, //(optional) specifies the fields to return using MongoDB projection operators.
    "projection": Object //(optional) same as "map" above
}
```

### response

If there is no error during the processing of the request, the `body` field of the response should hold an array of objects matching the specified query.security

### security

To read from a collection in a database, an app must either be the owner of the database or must be listed as one of the`guests`of the collection.

