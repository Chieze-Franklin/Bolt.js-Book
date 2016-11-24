# Apps \(API\)

This is a description of the API exposed by the Bolt server for interacting with apps.

The following endpoints are described here:

* [GET: \/api\/apps](#get-apiapps)
* [GET: \/api\/apps\/@live](#get-apiappslive)
* [GET: \/api\/apps\/{{app-name}}](#getapiappsapp-name)
* [POST: \/api\/apps](#post-apiapps)
* [POST: \/api\/apps\/reg](#post-apiappsreg)
* [POST: \/api\/apps\/start](#post-apiappsstart)
* [POST: \/api\/apps\/stop](#post-apiappsstop)

## GET: \/api\/apps
Gets an array of app objects for all installed apps matching the specified criteria.

You specify search criteria in the URL query portion. For instance, to get all apps that have a version of `1.1`:

`localhost:400/api/apps?version=1.1`

To get all apps that have `settings` as one of their tags:

`localhost:400/api/apps?tags=settings`

### response

If there is no error during the processing of the request, the `body` field of the response should hold an array of app objects.

---

## GET: \/api\/apps\/@live
Gets an array of context objects for all running contexts.

### response

If there is no error during the processing of the request, the `body` field of the response should hold an array of context objects.

---


## GET:\/api\/apps\/{{app-name}}

Gets the app object of the app with the specified name.

### response

If the app is found, the `body` field of the response should hold an app object.

---

## POST: \/api\/apps

Installs an app from an online repository \(current only npm is supported\).

This endpoint is still experimental.

---

## POST: \/api\/apps\/reg

Installs an app from an local repository \(current only the node\_modules folder is supported\).

###request

A standard [Bolt request](bolt-request.md).

`{`

`"path" : String //the path of the folder contain the _package.json_, relative to the node_modules folder`

`}`

## POST: \/api\/apps\/start

## POST: \/api\/apps\/stop

