# Roles \(API\)

A role encapsulates rights and permissions.

This is a description of the API endpoints exposed by the Bolt server for interacting with roles.

The following endpoints are described here:

* [GET: \/api\/roles](#get-apiroles)

* [POST: \/api\/user-roles](#post-apiuser-roles)


## GET: \/api\/roles

Gets an array of role [objects](/objects.md) for all registered roles matching the specified criteria.

You specify search criteria in the URL query portion. For instance, to get all roles with administrative privileges:

`localhost:400/api/roles?isAdmin=true`

### response

If there is no error during the processing of the request, the `body` field of the response should hold an array of role [objects](objects.md).

---

# POST: \/api\/roles

Adds a role to the database.

### request

A standard [Bolt request](bolt-request.md).

`{`

`"name" : String, //the name with which the role can be gotten internally`

`"title" : String, //user-friendly text for the role`

`"description" : String, //user-friendly description for the role`

`"isAdmin" : Boolean //determines if this role should be granted administrative privileges`

`}`

### response

If the role was added successfully, the `body` field of the response should hold a role object.

### security

Only system apps \(and native views\) can send requests to this endpoint.

