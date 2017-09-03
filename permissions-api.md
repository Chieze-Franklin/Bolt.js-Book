# Permissions \(API\)

This is a description of the API endpoints exposed by the Bolt server for interact with app permissions.

The following endpoints are described here:

* GET: /api/permissions

## GET: /api/permissions

Gets an array of [permission objects](/permission-object.md) for all apps that are visible to the user with the specified username. It is possible to _hide_ some apps from some users. The icons of such apps should not be visible to those users on standard home pages.

For instance, to get all apps visible to user _adam_:

`localhost:400/api/checks/visible-apps/adam`

### response

If there is no error during the processing of the request, the `body` field of the response should hold an array of [app objects](/app-object.md).

