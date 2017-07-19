# Apps \(UI\)

This is a description of the UI endpoints exposed by the Bolt server for interacting with apps.

The following endpoints are described here:

* [GET: /apps/\{\{name\}\}](#get-appsname)

## GET: /apps/\{\{name\}\}

This endpoint runs the app with the specified name.

### response

The app is automatically started, and the browser is redirected to the address on which the app is running.

If the app specified a [bolt.index](/package-index.md) field in its [package.json](/packagejson.md) at installation, the endpoint specified there will be appended to the redirect address.

So, if the package.json file looked something like this:

```
{
"name": "Notes",
...
"bolt": {
"main": "bolt-server.js",
"index": "/my/index/endpoint"
}
}
```

Then the complete redirect address would be `localhost:500/my/index/endpoint` \(assuming the app is running on `localhost:500`\).

If an error occurred during the processing of the request, the browser will be redirected to the Bolt endpoint `/error` with extra info \(like response code, error message\) supplied in the query portion of the URL.

If an app with the specified name could not be found in the database, or the app was found but does not have a server \(it didn't specify a `bolt.main` field in its package.json\), the browser will be redirected to `/files/{app-name}/index` with the assumption that the app has a [file](/files.md) called index, which is also [public](/public.md).
