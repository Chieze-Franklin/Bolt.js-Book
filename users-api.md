# Users \(API\)

This is a description of the API endpoints exposed by the Bolt server for interacting with users.

The following endpoints are described here:

* [GET: \/api\/users](#get-apiusers)

* [GET: \/api\/users\/@current](#get-apiuserscurrent)

* [GET: \/api\/users\/@live](#get-apiuserslive)

* [GET: \/api\/users\/\{\{name\}\}](#get-apiusersname)

* [POST: \/api\/users](#post-apiusers)

* [POST: \/api\/users\/login](#post-apiuserslogin)

* [POST: \/api\/users\/logout](#post-apiuserslogout)

* [DELETE: \/api\/users](#delete-apiusers)

* [DELETE: \/api\/users\/\{\{name\}\}](#delete-apiusersname)

* [PUT: \/api\/users](#put-apiusers)

* [PUT: \/api\/users\/\{\{name\}\}](#put-apiusersname)

## GET: \/api\/users

Gets an array of user [objects](/objects.md) for all registered users matching the specified criteria.

You specify search criteria in the URL query portion. For instance, to get all users who have visited \(logged into\) the service 7 times:

`localhost:400/api/users?visits=7`

### response

If there is no error during the processing of the request, the `body` field of the response should hold an array of user [objects](objects.md).

---

## GET: \/api\/users\/@current

Gets the logged-in user for the current session.

### response

If the logged-in user for the current session is successfully found, the `body` field of the response should hold a user object.

### note

This endpoint works for native views only.

---

## GET: \/api\/users\/@live

Gets an array of user objects for all currently logged-in users.

### response

If there is no error during the processing of the request, the `body` field of the response should hold an array of user objects.

### note

This may not work well in scenarios where Bolt is **not** expected to be _always on_.

---

## GET: \/api\/users\/\{\{name\}\}

Gets the user with the specified name.

### response

If the user is successfully found, the `body` field of the response should hold a user object.

---

## POST: \/api\/users

Adds a user to the database.

### request

A standard [Bolt request](bolt-request.md).

`{`

`"name" : String,`

`"password" : String,`

`"displayName": String`

`}`

### response

If the user was added successfully, the `body` field of the response should hold a user object.

### security

Only system apps \(and native views\) can send requests to this endpoint.

---

## POST: \/api\/users\/login

Logs a user into the system for the current session.

### request

A standard [Bolt request](bolt-request.md).

`{`

`"name" : String,`

`"password" : String`

`}`

### response

If the user was logged in successfully, the `body` field of the response should hold a user object.

### security

Only system apps \(and native views\) can send requests to this endpoint.

---

## POST: \/api\/users\/logout

Logs a user out of the system for the current session.

### response

If the user was logged out successfully, the `body` field of the response should hold a user object.

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


