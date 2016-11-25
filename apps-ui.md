# Apps \(UI\)

This is a description of the UI endpoints exposed by the Bolt server for interacting with apps.

The following endpoints are described here:

* [GET: \/apps\/\{\{app-name\}\}](#get-appsapp-name)

## GET: \/apps\/\{\{app-name\}\}

This endpoint runs the app with the specified name.

###response

The app is automatically started (let's say on port `500`), and the browser is redirected to `localhost:500`.

If the app specified a `bolt.index` field in its package.json at installation, the endpoint specified there will be appended to the redirect address.

So, if the package.json file looked something like this:

Then the complete redirect address would be localhost:500/my/index/endpoint

If an error occurred during the processing of the request, the browser will be redirected to the Bolt endpoint /error with extra info (like response code, error message) supplied in the query portion of the URL.

If an app with the specified name could not be found in the database, or the app was found but does not have a server (it didn't specify a bolt.main field in its package.json), the browser will be redirected to the Bolt endpoint /404 with extra info (like the specified name) supplied in the query portion of the URL.
