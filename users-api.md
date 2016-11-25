# Users \(API\)

This is a description of the API endpoints exposed by the Bolt server for interacting with users.

The following endpoints are described here:

* [GET: \/api\/users](#get-apiusers)
* [GET: \/api\/users\/@current](#get-apiuserscurrent)
* [POST: \/api\/apps\/reg](#post-apiappsreg)
* [POST: \/api\/apps\/start](#post-apiappsstart)
* [POST: \/api\/apps\/stop](#post-apiappsstop)

## GET: \/api\/users

Gets an array of user [objects](/objects.md) for all registered users matching the specified criteria.

You specify search criteria in the URL query portion. For instance, to get all users who have visited \(logged into\) the service 7 times:

`localhost:400/api/users?visits=7`

### response

If there is no error during the processing of the request, the `body` field of the response should hold an array of user [objects](objects.md).

---

## GET: \/api\/users\/@current

Gets an array of context objects for all running contexts.

### response

If there is no error during the processing of the request, the `body` field of the response should hold an array of context objects.

---

## GET: \/api\/apps\/@live

Gets an array of context objects for all running contexts.

### response

If there is no error during the processing of the request, the `body` field of the response should hold an array of context objects.

---

## POST: \/api\/apps

Installs an app from an online repository \(current only npm is supported\).

This endpoint is still experimental.

---

## POST: \/api\/apps\/reg

Installs an app from an local repository \(current only the node\_modules folder is supported\).

### request

A standard [Bolt request](bolt-request.md).

`{`

`"path" : String //the path of the folder contain the _package.json_, relative to the node_modules folder`

`}`

### response

If the app installed successfully, the `body` field of the response should hold an app object.

### security

Any app can send a request to this endpoint provided:

* The user has granted the app [permission](user-permissions.md) to perform an installation.

* The user has administrative privileges.


---

## POST: \/api\/apps\/start

Starts the server of the app with the specified name.

### request

A standard [Bolt request](bolt-request.md).

`{`

`"app" : String //the nameh of the app to start`

`}`

### response

If the app is started successfully, the `body` field of the response should hold a context object.

* To know if a server was started for the app, check if their is a defined `port` field for the context object.

* To know if a server was started on another process, check if there is a defined `pid` field for the context object.


### security

A check is made to see if the current user has the right to start an app. For startup apps, no such check may be made.

### note

Calling this endpoint multiple times for a particular app does not start multiple servers for it; if an app's server is already running a new one will **not** be started.

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

