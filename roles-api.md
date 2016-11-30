# Roles \(API\)

A role encapsulates rights and permissions.

This is a description of the API endpoints exposed by the Bolt server for interacting with roles.

The following endpoints are described here:

* [GET: \/api\/roles](#get-apiroles)

* [GET: \/api\/roles\/\{\{name\}\}](#get-apirolesname)

* [POST: \/api\/user-roles](#post-apiuser-roles)

## GET: \/api\/roles

Gets an array of role [objects](/objects.md) for all registered roles matching the specified criteria.

You specify search criteria in the URL query portion. For instance, to get all roles with administrative privileges:

`localhost:400/api/roles?isAdmin=true`

### response

If there is no error during the processing of the request, the `body` field of the response should hold an array of role [objects](objects.md).

---

## GET: \/api\/roles\/\{\{name\}\}

Gets the role with the specified name.

### response

If the role is successfully found, the `body` field of the response should hold a role object.

# POST: \/api\/roles

Adds a role to the database.

### request

A standard [Bolt request](bolt-request.md).

`{`

`"name" : String, //the name with which the role can be gotten internally`

`"displayName" : String, //user-friendly text for the role`

`"description" : String, //user-friendly description for the role`

`"isAdmin" : Boolean //determines if this role should be granted administrative privileges`

`}`

### response

If the role was added successfully, the `body` field of the response should hold a role object.

### security

Only system apps \(and native views\) can send requests to this endpoint.

---

## DELETE: \/api\/users

Deletes an array of users matching the specified criteria.

You specify search criteria in the URL query portion. For instance, to delete all users who have visited \(logged into\) the service 7 times:

`localhost:400/api/users?visits=7`

### response

If there is no error during the processing of the request, the `body` field of the response should hold an array of user objects.

### security

Only system apps \(and native views\) can send requests to this endpoint.

---

## DELETE: \/api\/users\/\{\{name\}\}

Deletes the user with the specified name.

### response

If the user is successfully deleted, the `body` field of the response should hold a user object.

### security

Only system apps \(and native views\) can send requests to this endpoint.

---

## PUT: \/api\/users

Updates an array of users matching the specified criteria.

You specify search criteria in the URL query portion. For instance, to update all users who have visited \(logged into\) the service 7 times:

`localhost:400/api/users?visits=7`

### request

A standard [Bolt request](bolt-request.md).

`{`

`"displayName": String`

`"isBlocked": Boolean`

`}`

### response

If the user was updated successfully, the `body` field of the response should hold a user object.

### security

Only system apps \(and native views\) can send requests to this endpoint.

---

## PUT: \/api\/users\/\{\{name\}\}

Updates the user with the specified name.

### request

A standard [Bolt request](bolt-request.md).

`{`

`"displayName": String`

`"isBlocked": Boolean`

`}`

### response

If the user is successfully updated, the `body` field of the response should hold a user object.

### security

Only system apps \(and native views\) can send requests to this endpoint.


