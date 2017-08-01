# Apps \(API\)

This is a description of the API endpoints exposed by the Bolt server for interacting with apps.

The following endpoints are described here:

* [GET: /api/apps](#get-apiapps)

* [GET: /api/apps/@live](#get-apiappslive)

* [GET: /api/apps/{{name/}/}](#getapiappsname)

* [POST: /api/apps](#post-apiapps)

* [POST: /api/apps/package](#post-apiappspackage)

* [POST: /api/apps/readme](#post-apiappsreadme)

* [POST: /api/apps/local](#post-apiappslocal)

* [POST: /api/apps/local-package](#post-apiappslocal-package)

* [POST: /api/apps/local-readme](#post-apiappslocal-readme)

* [POST: /api/apps/start](#post-apiappsstart)

* [POST: /api/apps/stop](#post-apiappsstop)

* [DELETE: /api/apps](#delete-apiapps)

* [DELETE: /api/apps/{{name/}/}](#delete-apiappsname)

## GET: /api/apps

Gets an array of [app objects](/app-object.md) for all installed apps matching the specified criteria.

You specify search criteria in the URL query portion. For instance, to get all apps that have a version of `1.1`:

`localhost:400/api/apps?version=1.1`

To get all apps that have `settings` as one of their tags:

`localhost:400/api/apps?tags=settings`

### response

If there is no error during the processing of the request, the `body` field of the response should hold an array of [app objects](/app-object.md).

---

## GET: /api/apps/@live

Gets an array of [context objects](/context-object.md) for all running contexts.

### response

If there is no error during the processing of the request, the `body` field of the response should hold an array of [context objects](/context-object.md).

---

## GET:/api/apps/{{name/}/}

Gets the app object of the app with the specified name.

### response

If the app is found, the `body` field of the response should hold an app object.

---

## POST: /api/apps

Installs an app from an online repository \(current only the [npm](https://www.npmjs.com/) is supported\).

### request

A standard [Bolt request](bolt-request.md).

```
{
"name" : String, //the name of the app
"system" : Boolean //(optional) determines if the app should be a system app (with root privilege)
}
```

### response

If the app installed successfully, the `body` field of the response should hold an [app object](/app-object.md).

### security

Any app can send a request to this endpoint provided:

* The app is a system app.

* The user has administrative privileges.

---

## POST: /api/apps/package

Gets an object representing the _package.json_ of an app from an online repository \(current only [npm](https://www.npmjs.com/) is supported\).

This endpoint is important as you use it to fetch info about an app and show it to the user before installation. This should give the user the option of granting/denying some of the requests the app needs \(like the ability to run as a system app\).

### request

A standard [Bolt request](bolt-request.md).

```
{
"name": String //the name of the app
}
```

### response

If the _package.json_ is found, the `body` field of the response should hold an object that represent's the found _package.json_.

### security

Currently the current user needs administrative privilege for this request to be processed.

---

## POST: /api/apps/readme

Gets the data in the _readme.md_ of an app from an online repository \(current only the [npm](https://www.npmjs.com/) is supported\).

This endpoint is important as you use it to fetch info about an app and show it to the user before installation.

### request

A standard [Bolt request](bolt-request.md).

```
{
"name" : String //the name of the app
}
```

### response

If the package.json is found, the `body` field of the response should hold the data in the _readme_ file. The data will most likely be in [markdown](https://en.wikipedia.org/wiki/Markdown) format, and may need to be converted to HTML using a package like [showdown](https://www.npmjs.com/package/showdown).

### security

Currently the current user needs administrative privilege for this request to be processed.

---

## POST: /api/apps/local

Installs an app from a local repository \(current only the _node\_modules_ folder is supported\).

### request

A standard [Bolt request](bolt-request.md).

```
{
"path" : String, //the path of the folder contain the package.json, relative to the node_modules folder
"system" : Boolean //(optional) determines if the app should be a system app (with root privilege)
}
```

### response

If the app installed successfully, the `body` field of the response should hold an [app object](/app-object.md).

### security

Any app can send a request to this endpoint provided:

* The app is a system app.

* The user has administrative privileges.

---

## POST: /api/apps/local-package

Gets an object representing the _package.json_ of an app from a local repository \(current only the _node\_modules_ folder is supported\).

This endpoint is important as you use it to fetch info about an app and show it to the user before installation. This should give the user the option of granting/denying some of the requests the app needs \(like the ability to run as a system app\).

### request

A standard [Bolt request](bolt-request.md).

```
{
"path": String //the path of the folder contain the package.json, relative to the node_modules folder
}
```

### response

If the _package.json_ is found, the `body` field of the response should hold an object that represent's the found _package.json_.

### security

Currently the current user needs administrative privilege for this request to be processed.

---

## POST: /api/apps/local-readme

Gets the data in the _readme.md_ of an app from a local repository \(current only the _node\_modules_ folder is supported\). Currently it searches for a _readme_ file with extension _.md_.

This endpoint is important as you use it to fetch info about an app and show it to the user before installation.

### request

A standard [Bolt request](bolt-request.md).

```
{
"path" : String //the path of the folder contain the package.json, relative to the node_modules folder
}
```

### response

If the package.json is found, the `body` field of the response should hold the data in the _readme.md_ file. The data will most likely be in [markdown](https://en.wikipedia.org/wiki/Markdown) format, and may need to be converted to HTML using a package like [showdown](https://www.npmjs.com/package/showdown).

### security

Currently the current user needs administrative privilege for this request to be processed.

---

## POST: /api/apps/start

Starts the server of the app with the specified name.

### request

A standard [Bolt request](bolt-request.md).

`{`

`"name" : String //the name of the app to start`

`}`

### response

If the app is started successfully, the `body` field of the response should hold a context object.

* To know if a server was started for the app, check if their is a defined `port` field for the context object.

* To know if a server was started on another process, check if there is a defined `pid` field for the context object.

### note

Calling this endpoint multiple times for a particular app does not start multiple servers for it; if an app's server is already running a new one will **not** be started.

---

## POST: /api/apps/stop

Starts the server of the app with the specified name.

### request

A standard [Bolt request](bolt-request.md).

`{`

`"name" : String //the name of the app to stop`

`}`

### response

* If the app is found to be running and was stopped successfully, the `body` field of the response should hold a context object.

* If the app is not found to be running, the `error` field of the response may hold an error object. \(see **notes** below.\)

---

## DELETE: /api/apps

Deletes an array of apps matching the specified criteria.

You specify search criteria in the URL query portion. For instance, to delete all apps that have a version of `1.1`:

`localhost:400/api/apps?version=1.1`

### request

A standard [Bolt request](bolt-request.md).

```
{
"deleteDatabase" : Boolean, //(optional) if true the app's database will be deleted
"deletePublicFolder" : Boolean, //(optional) if true the folder holding the app's public files will be deleted
"deleteSourceFolder" : Boolean //(optional) if true the folder holding the app's source files will be deleted
}
```

### response

If there is no error during the processing of the request, the `body` field of the response should hold an array of the deleted [app objects](/app-object.md).

### security

Only system apps \(and native views\) can send requests to this endpoint. The logged-in user must also have administrative privilege.

---

## DELETE: /api/apps/{{name/}/}

Deletes the app with the specified name.

### request

A standard [Bolt request](bolt-request.md).

```
{
"deleteDatabase" : Boolean, //(optional) if true the app's database will be deleted
"deletePublicFolder" : Boolean, //(optional) if true the folder holding the app's public files will be deleted
"deleteSourceFolder" : Boolean //(optional) if true the folder holding the app's source files will be deleted
}
```

### response

If the user is successfully deleted, the `body` field of the response should hold the deleted app object.

### security

Only system apps \(and native views\) can send requests to this endpoint. The logged-in user must also have administrative privilege.

---

### note

Although this may change, currently, trying to stop an app that is not running may return a [Bolt response](bolt-response.md) with [response code](bolt-response-codes.md) `420`. Code `420` means the port on which an app should be running cannot be found. The rationale is that you can only stop apps running on ports, so trying to stop an app that is not running \(for which no port can be found\) will result in an error with code `420`.

