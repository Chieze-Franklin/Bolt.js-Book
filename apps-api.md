# Apps \(API\)

This is a description of the API exposed by the Bolt server for interacting with apps.

The following endpoints are described here:

* [GET: \/api\/apps](#get-apiapps)
* [GET: \/api\/apps\/@live](#get-apiappslive)
* [GET: \/api\/apps\/{{app-name}}](#get-apiappsapp-name)

\* \[POST: \/api\/app\/get\]\(\#post-apiappget\)

\* \[POST: \/api\/app\/reg\]\(\#post-apiappreg\)

\* \[POST: \/api\/app\/start\]\(\#post-apiappstart\)

\* \[POST: \/api\/app\/stop\]\(\#post-apiappstop\)

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

## GET: \/api\/apps\/{{app-name}}

Gets the app object of the app with the specified name.

### response

If the app is found, the `body` field of the response should hold an app object.