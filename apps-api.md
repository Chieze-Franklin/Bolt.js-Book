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

## GET:\/api\/apps\/{{app-name}}

## POST: \/api\/apps

## POST: \/api\/apps\/reg

## POST: \/api\/apps\/start

## POST: \/api\/apps\/stop

