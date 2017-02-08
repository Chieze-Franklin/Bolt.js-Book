# ini

This is the first API endpoint that will be visited when your app is started.

This endpoint must be implemented as a `POST`.

Assuming you set your `ini` as shown below:

`{`

`"name": "Notes",`

`....`

`"bolt": {`

`"main": "bolt-server.js",`

`"ini": "/api/ini"`

`}`

`}`

Then, whenever your app is started \(let's say on port 500\), necessary information will be `POSTed` to `localhost:500/api/ini`.

The `JSON` body of the `POST` will look something like this:

`{`

`protocol: String, //protocol via which Bolt can be accessed`

`host: String, //host via which Bolt can be accessed`

`port: Number | String, //port on which the Bolt server is running`

`appName: String, //the name of the app`

`appPort: Number | String, //port on which this app is running`

`appToken: String //include this in the "X-Bolt-App-Token" custom header of requests you send to Bolt endpoints`

`}`

You do not need to store these data as they are dynamically generated \(`appPort`,`appToken`\) or can be changed in a config file \(`protocol`, `host`, `port`\).

You are now free to use those data to interact with Bolt.

### A Note on "X-Bolt-App-Token" header

Not all requests to Bolt server need to have the `X-Bolt-App-Token` header; only critical/sensitive requests \(where the origin of the request is important\) need to include this header. Bolt uses this header to identify your app as the origin of the request. Bolt then denies or grants the request only if your app has the right to make that request. An example of such an endpoint is `POST: /api/apps` which is used to install new apps. Bolt needs to be sure that the user has given your app the right to perform such an action, and the `X-Bolt-App-Token` header is the starting point of that security check.

To be safe though, it doesn't hurt to include the `X-Bolt-App-Token` in all your requests to Bolt but ensure you don't send such requests to other apps so that other apps don't use your app token to fool Bolt into treating them like your app.

### A Little Tip for You

The `ini` field was initially `init` but later changed because `init` is a reserved word in MongoDB. Bolt uses MongoDB.

