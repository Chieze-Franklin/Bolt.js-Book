# Files \(API\)

This is a description of the API endpoints exposed by the Bolt server for interacting with public files.

The following endpoints are described here:

* [GET: /api/files/&lt;app&gt;/&lt;file&gt;](#get-apifilesappfile)

## GET: /api/files/&lt;app&gt;/&lt;file&gt;

Gets the [file object](/file-object.md) of the file being served by the app.

### response

If the file is found, the `body` field of the response should hold a [file object](/file-object.md).

