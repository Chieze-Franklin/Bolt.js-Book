# User-Roles \(API\)

A user-role object is an object that represents an association between a user and a role.

This is a description of the API endpoints exposed by the Bolt server for interacting with user-roles.

The following endpoints are described here:

* [GET: /api/user-roles](#get-apiuser-roles)

* [POST: /api/user-roles](#post-apiuser-roles)

* [DELETE: /api/user-roles](#delete-apiuser-roles)

## GET: /api/user-roles

Gets an array of [user-role association objects](/user-role-object.md) for all registered user-roles matching the specified criteria.

You specify search criteria in the URL query portion. For instance, to get all user-roles for user `user1`:

`localhost:400/api/user-roles?user=user1`

### response

If there is no error during the processing of the request, the `body` field of the response should hold an array of [user-role objects](/user-role-object.md).

---

# POST: /api/user-roles

Adds a user-role association to the database.

### request

A standard [Bolt request](bolt-request.md).

`{`

`"user" : String, //username of the user being referenced`

`"role" : String //name of the role being referenced`

`}`

### response

If the user-role was added successfully, the `body` field of the response should hold a user-role object.

### security

Only system apps \(and native views\) can send requests to this endpoint.

---

## DELETE: /api/user-roles

Deletes an array of user-role association objects for all registered user-roles matching the specified criteria.

You specify search criteria in the URL query portion. For instance, to delete all user-roles for user `user1`:

`localhost:400/api/user-roles?user=user1`

### response

If there is no error during the processing of the request, the `body` field of the response should hold an array of user-role objects.

### security

Only system apps \(and native views\) can send requests to this endpoint.

