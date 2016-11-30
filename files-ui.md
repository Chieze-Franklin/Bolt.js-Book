# Files \(UI\)

This is a description of the UI endpoints exposed by the Bolt server for interacting with public files.

The following endpoints are described here:

* [GET: \/files\/\{\{app\}\}\/\{\{file\}\}](#get-filesappfile)

## GET: \/files\/\{\{app\}\}\/\{\{file\}\}

This loads a file being served by an app.

### security

The current user must have \(been given\) the right to access the file.