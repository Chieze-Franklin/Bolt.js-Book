# Files \(API\)

This is a description of the API endpoints exposed by the Bolt server for interacting with public files.

The following endpoints are described here:

* [GET: /api/files/\{\{app\}\}/\{\{file\}\}](#get-apifilesappfile)

## GET: /api/files/\{\{app\}\}/\{\{file\}\}

Gets the file [object](/objects.md) of the file being served by the app.

### response

If the file is found, the `body` field of the response should hold a file object.

### security

The current user must have \(been given\) the right to access the file.

