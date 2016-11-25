# Users \(API\)

This is a description of the API endpoints exposed by the Bolt server for interacting with users.

The following endpoints are described here:

* [GET: \/api\/users](#get-apiusers)
* [GET: \/api\/users\/@current](#get-apiuserscurrent)
* [GET: \/api\/users\/@live](#get-apiuserslive)
* GET: \/api\/users\/username
* [POST: \/api\/users](#post-apiusers)
* [POST: \/api\/users\/login](#post-apiuserslogin)

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

This may not work well in scenarios where Bolt is **not** expected to be _always on_.

A better way of getting the logged-in user is by directing them to the \/login view, and specifying a return url to which the username will be sent.

---

## GET: \/api\/users\/@live

Gets an array of user objects for all currently logged-in users.

### response

If there is no error during the processing of the request, the `body` field of the response should hold an array of user objects.

### note

This may not work well in scenarios where Bolt is **not** expected to be _always on_.

---

## GET: \/api\/users\/username

Installs an app from an online repository \(current only npm is supported\).

This endpoint is still experimental.

---

## POST: \/api\/users

Adds a user to the database.

### request

A standard [Bolt request](bolt-request.md).

`{`

`"username" : String,`

`"password" : String`

`}`

### response

If the user was added successfully, the `body` field of the response should hold a user object.

### security

Only system apps \(and native views\) can send requests to this endpoint.

---

## POST: \/api\/users\/login

Logs a user into the system.

### request

A standard [Bolt request](bolt-request.md).

`{`

`"username" : String,`

`"password" : String`

`}`

### response

If the user was logged in successfully, the `body` field of the response should hold a user object.

### security

Only system apps \(and native views\) can send requests to this endpoint.

---

## POST: \/api\/apps\/stop

Starts the server of the app with the specified name.

### request

A standard [Bolt request](bolt-request.md).

`{`

`"app" : String //the nameh of the app to stop`

`}`

### response

* If the app is found to be running and was stopped successfully, the `body` field of the response should hold a context object.
* If the app is not found to be running, the `error` field of the response may hold an error object. \(see **notes** below.\)

### security

A check is made to see if the current user has the right to start an app. For startup apps, no such check may be made.

This is the same check made when starting an app. The rationale is that you should be able to stop only apps you have the right to start.

### note

Although this may change, currently, trying to stop an app that is not running may return a [Bolt response](bolt-response.md) with [response code](bolt-response-codes.md) `420`. Code `420` means the port on which an app should be running cannot be found. The rationale is that you can only stop apps running on ports, so trying to stop an app that is not running \(for which no port can be found\) will result in an error with code `420`.

