# Permissions \(API\)

This is a description of the API endpoints exposed by the Bolt server for interact with app permissions.

The following endpoints are described here:

* GET: /api/permissions

## GET: /api/permissions

Gets an array of [permission objects](/permission-object.md) matching the specified criteria.

You specify search criteria in the URL query portion. For instance, to get all permissions for the app _bolt-admin_:

`localhost:400/api/permissions?app=bolt-admin`

### response

If there is no error during the processing of the request, the `body` field of the response should hold an array of [permission objects](/permission-object.md).

