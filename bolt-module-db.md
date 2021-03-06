# bolt-module-db

This module installs the `/api/db` endpoints which allows apps to use the same database Bolt uses to store their objects. This means apps don't need their own separate databases.

To install this module, navigate to the Bolt endpoint `/install`, and type in _bolt-module-db_ as the app name. Go ahead and click **Download** \(or **Sideload**, as the case may be\). Take care to install this module as a system app.

This app is marked as a module, meaning \(among other things\) that it defines no user interface. Its installation registers the routers that respond to the requests sent to the `/api/db` endpoints.

Some of the endpoints exposed by this module raise events that are dispatched only to the app whose collection is being affected at that point in time.

The following endpoints are described here:

* [DELETE: /api/db](#delete-apidb)
* [DELETE: /api/db/&lt;collection&gt;](#delete-apidbcollection)
* [POST: /api/db/&lt;collection&gt;/find](#post-apidbcollectionfind)
* [POST: /api/db/&lt;collection&gt;/findone](#post-apidbcollectionfindone)
* [POST: /api/db/&lt;collection&gt;/insert](#post-apidbcollectioninsert)
* [POST: /api/db/&lt;collection&gt;/remove](#post-apidbcollectionremove)
* [POST: /api/db/&lt;collection&gt;/replace](#post-apidbcollectionreplace)
* [POST: /api/db/&lt;collection&gt;/update](#post-apidbcollectionupdate)

## DELETE: /api/db

Drops an app's database.

To drop another app's database, specify the app's name in the `app` or `db` field of the request body. In the absence of these fields Bolt will assume you want to drop your own database.

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

### events

If the operation succeeds, the event `bolt/app-db-dropped` will be fired with the following event `body`:

```
{
    "app": String, //name of the app whose database was dropped
    "result": Boolean //the result of the operation, typically 'true'
}
```

If the operation fails, the event `bolt/app-db-drop-failed` will be fired with the following event `body`:

```
{
    "app": String, //name of the app whose database was to be dropped
    "error": Object //the error object
}
```

### security

Always include the `X-Bolt-App-Token` custom header in the request.

To drop a database, an app must be the owner of the database.

---

## DELETE: /api/db/&lt;collection&gt;

Drops a collection in the app's database.

If dealing with another app's database, specify the app's name in the `app` or `db` field of the request body. In the absence of these fields Bolt will assume you are dealing with your own database.

### request

A standard [Bolt request](bolt-request.md).

```
{
    "app": String, //(optional) name of the app whose database is to be affected
    "db": String //(optional) same as the "app" field above
}
```

### response

If there is no error during the processing of the request, the `body` field of the response should hold an boolean value of `true` \(for a successful drop\) or `false`.

### events

If the operation succeeds, the event `bolt/app-collection-dropped` will be fired with the following event `body`:

```
{
    "app": String, //name of the app whose collection was dropped
    "collection": String, //name of the collection that was dropped
    "result": Boolean //the result of the operation, typically 'true'
}
```

If the operation fails, the event `bolt/app-collection-drop-failed` will be fired with the following event `body`:

```
{
    "app": String, //name of the app whose collection was to be dropped
    "collection": String, //name of the collection that was to be dropped
    "error": Object //the error object
}
```

### security

Always include the `X-Bolt-App-Token` custom header in the request.

To drop a collection in a database, an app must either be the owner of the database or must be listed as one of the `tenants` of the collection.

---

## POST: /api/db/&lt;collection&gt;/find

Finds all the objects in the specified collection matching the given query.

If dealing with another app's database, specify the app's name in the `app` or `db` field of the request body. In the absence of these fields Bolt will assume you are dealing with your own database.

### request

A standard [Bolt request](bolt-request.md).

```
{
    "app": String, //(optional) name of the app whose database is to be affected
    "db": String, //(optional) same as the "app" field above
    "query": Object, //specifies selection filter using MongoDB query operators
    "map": Object, //(optional) specifies the fields to return using MongoDB projection operators
    "projection": Object //(optional) same as "map" above
}
```

You can also specify the selection filter of this operation in the query portion of the URL. For instance, to find all students with `admission_status` of `active`, the path could be:

`/api/db/students/find?admission_status=active`

### response

If there is no error during the processing of the request, the `body` field of the response should hold an array of objects matching the specified query.

### security

Always include the `X-Bolt-App-Token` custom header in the request.

To read from a collection in a database, an app must either be the owner of the database or must be listed as one of the`guests`of the collection.

---

## POST: /api/db/&lt;collection&gt;/findone

Finds the first object in the specified collection matching the given query.

If dealing with another app's database, specify the app's name in the `app` or `db` field of the request body. In the absence of these fields Bolt will assume you are dealing with your own database.

### request

A standard [Bolt request](bolt-request.md).

```
{
    "app": String, //(optional) name of the app whose database is to be affected
    "db": String, //(optional) same as the "app" field above
    "query": Object, //specifies selection filter using MongoDB query operators
    "map": Object, //(optional) specifies the fields to return using MongoDB projection operators
    "projection": Object //(optional) same as "map" above
}
```

You can also specify the selection filter of this operation in the query portion of the URL. For instance, to find the student with `name` of `frank`, the path could be:

`/api/db/students/findone?name=frank`

### response

If there is no error during the processing of the request, the `body` field of the response should hold the object matching the specified query.

### security

Always include the `X-Bolt-App-Token` custom header in the request.

To read from a collection in a database, an app must either be the owner of the database or must be listed as one of the`guests`of the collection.

---

## POST: /api/db/&lt;collection&gt;/insert

Inserts an object or an array of objects into the specified collection.

If dealing with another app's database, specify the app's name in the `app` or `db` field of the request body. In the absence of these fields Bolt will assume you are dealing with your own database.

### request

A standard [Bolt request](bolt-request.md).

```
{
    "app": String, //(optional) name of the app whose database is to be affected
    "db": String, //(optional) same as the "app" field above
    "object": Object | [Object], //an object or array of objects to insert
}
```

### response

If there is no error during the processing of the request, the `body` field of the response should hold a MongoDB [WriteResult](https://docs.mongodb.com/v3.2/reference/method/db.collection.insert/#writeresults-insert) object for single inserts or [BulkWriteResult](https://docs.mongodb.com/v3.2/reference/method/db.collection.insert/#bulkwriteresults-insert) object for bulk inserts.

### events

If the operation succeeds, the event `bolt/app-collection-inserted` will be fired with the following event `body`:

```
{
    "app": String, //name of the app whose collection was affected
    "collection": String, //name of the collection that was affected
    "result": Object, //the object returned from MongoDB, typically a WriteResult or BulkWriteResult object
    "meta": {
        "object": Object //the object that was inserted
    }
}
```

If the operation fails, the event `bolt/app-collection-insert-failed` will be fired with the following event `body`:

```
{
    "app": String, //name of the app whose collection was to be affected
    "collection": String, //name of the collection that was to be affected
    "error": Object, //the error object
    "meta": {
        "object": Object //the object that was to be inserted
    }
}
```

### security

Always include the `X-Bolt-App-Token` custom header in the request.

To write to a collection in a database, an app must either be the owner of the database or must be listed as one of the`tenants`of the collection.

---

## POST: /api/db/&lt;collection&gt;/remove

Removes an array of objects from the specified collection.

If dealing with another app's database, specify the app's name in the `app` or `db` field of the request body. In the absence of these fields Bolt will assume you are dealing with your own database.

### request

A standard [Bolt request](bolt-request.md).

```
{
    "app": String, //(optional) name of the app whose database is to be affected
    "db": String, //(optional) same as the "app" field above
    "query": Object, //specifies deletion criteria using MongoDB query operators
}
```

You can also specify the deletion criteria of this operation in the query portion of the URL. For instance, to remove all students with `admission_status` of `expelled`, the path could be:

`/api/db/students/remove?admission_status=expelled`

### response

If there is no error during the processing of the request, the `body` field of the response should hold a MongoDB [WriteResult](https://docs.mongodb.com/v3.2/reference/method/db.collection.remove/#writeresults-remove) object.

### events

If the operation succeeds, the event `bolt/app-collection-removed` will be fired with the following event `body`:

```
{
    "app": String, //name of the app whose collection was affected
    "collection": String, //name of the collection that was affected
    "result": Object, //the object returned from MongoDB, typically a WriteResult object
    "meta": {
        "query": Object //same as the 'query' that was specified in the request
    }
}
```

If the operation fails, the event `bolt/app-collection-remove-failed` will be fired with the following event `body`:

```
{
    "app": String, //name of the app whose collection was to be affected
    "collection": String, //name of the collection that was to be affected
    "error": Object, //the error object
    "meta": {
        "query": Object //same as the 'query' that was specified in the request
    }
}
```

### security

Always include the `X-Bolt-App-Token` custom header in the request.

To write to a collection in a database, an app must either be the owner of the database or must be listed as one of the`tenants`of the collection.

---

## POST: /api/db/&lt;collection&gt;/replace

Updates an array of objects from the specified collection by deleting all their existing fields and replacing them with the fields in the `values` object.

If dealing with another app's database, specify the app's name in the `app` or `db` field of the request body. In the absence of these fields Bolt will assume you are dealing with your own database.

### request

A standard [Bolt request](bolt-request.md).

```
{
    "app": String, //(optional) name of the app whose database is to be affected
    "db": String, //(optional) same as the "app" field above
    "query": Object, //specifies selection criteria using MongoDB query operators
    "values": Object, //the modifications to apply
    "upsert": Boolean, //(optional) if true, creates a new document when no document matches the query criteria
    "multi": Boolean //(optional) if true, updates multiple documents (not just one) that meet the query criteria
}
```

You can also specify the selection criteria of this operation in the query portion of the URL. For instance, to replace all students with `admission_status` of `expelled`, the path could be:

`/api/db/students/replace?admission_status=expelled`

### response

If there is no error during the processing of the request, the `body` field of the response should hold a MongoDB [WriteResult](https://docs.mongodb.com/v3.2/reference/method/db.collection.update/#writeresults-update) object.

### events

If the operation succeeds, the event `bolt/app-collection-replaced` will be fired with the following event `body`:

```
{
    "app": String, //name of the app whose collection was affected
    "collection": String, //name of the collection that was affected
    "result": Object, //the object returned from MongoDB, typically a WriteResult object
    "meta": {
        "query": Object, //same as the 'query' that was specified in the request
        "values": Object, //same as the 'values' that was specified in the request
        "options": {
            "upsert": Boolean, //same as the 'upsert' that was specified in the request
            "multi": Boolean //same as the 'multi' that was specified in the request
        }
    }
}
```

If the operation fails, the event `bolt/app-collection-replace-failed` will be fired with the following event `body`:

```
{
    "app": String, //name of the app whose collection was to be affected
    "collection": String, //name of the collection that was to be affected
    "error": Object, //the error object
    "meta": {
        "query": Object, //same as the 'query' that was specified in the request
        "values": Object, //same as the 'values' that was specified in the request
        "options": {
            "upsert": Boolean, //same as the 'upsert' that was specified in the request
            "multi": Boolean //same as the 'multi' that was specified in the request
        }
    }
}
```

### security

Always include the `X-Bolt-App-Token` custom header in the request.

To write to a collection in a database, an app must either be the owner of the database or must be listed as one of the`tenants`of the collection.

---

## POST: /api/db/&lt;collection&gt;/update

Updates an array of objects from the specified collection by updating the values of their existing fields with the values of the corresponding fields in the `values` object. Unlike [/api/db/&lt;collection&gt;/replace](#post-apidbcollectionreplace) which wipes out all the existing fields of the matching objects, this method only touches fields in the matching objects which have counterparts in the `values` field of the request object.

If dealing with another app's database, specify the app's name in the `app` or `db` field of the request body. In the absence of these fields Bolt will assume you are dealing with your own database.

### request

A standard [Bolt request](bolt-request.md).

```
{
    "app": String, //(optional) name of the app whose database is to be affected
    "db": String, //(optional) same as the "app" field above
    "query": Object, //specifies selection criteria using MongoDB query operators
    "values": Object, //the modifications to apply
    "upsert": Boolean, //(optional) if true, creates a new document when no document matches the query criteria
    "multi": Boolean //(optional) if true, updates multiple documents (not just one) that meet the query criteria
}
```

You can also specify the selection criteria of this operation in the query portion of the URL. For instance, to update all students with `admission_status` of `expelled`, the path could be:

`/api/db/students/update?admission_status=expelled`

### response

If there is no error during the processing of the request, the `body` field of the response should hold a MongoDB [WriteResult](https://docs.mongodb.com/v3.2/reference/method/db.collection.update/#writeresults-update) object.

### events

If the operation succeeds, the event `bolt/app-collection-updated` will be fired with the following event `body`:

```
{
    "app": String, //name of the app whose collection was affected
    "collection": String, //name of the collection that was affected
    "result": Object, //the object returned from MongoDB, typically a WriteResult object
    "meta": {
        "query": Object, //same as the 'query' that was specified in the request
        "values": Object, //same as the 'values' that was specified in the request
        "options": {
            "upsert": Boolean, //same as the 'upsert' that was specified in the request
            "multi": Boolean //same as the 'multi' that was specified in the request
        }
    }
}
```

If the operation fails, the event `bolt/app-collection-update-failed` will be fired with the following event `body`:

```
{
    "app": String, //name of the app whose collection was to be affected
    "collection": String, //name of the collection that was to be affected
    "error": Object, //the error object
    "meta": {
        "query": Object, //same as the 'query' that was specified in the request
        "values": Object, //same as the 'values' that was specified in the request
        "options": {
            "upsert": Boolean, //same as the 'upsert' that was specified in the request
            "multi": Boolean //same as the 'multi' that was specified in the request
        }
    }
}
```

### security

Always include the `X-Bolt-App-Token` custom header in the request.

To write to a collection in a database, an app must either be the owner of the database or must be listed as one of the`tenants`of the collection.

