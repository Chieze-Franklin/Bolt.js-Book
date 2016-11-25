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

{

protocol: String, \/\/protocol via which Bolt can be accessed

host: String, \/\/host via which Bolt can be accessed

port: Number \| String, \/\/port on which the Bolt server is running

appPort: Number \| String, \/\/port on which this app is running

reqid: String \/\/include this in the "X-Bolt-Req-Id" custom header of requests you send to Bolt endpoints

}

You do not need to store these data as they are dynamically generated \(appPort, reqid\) or can be changed in a config file \(protocol, host, port\).

You are now free to use those data to interact with Bolt.

A Note on "X-Bolt-Req-Id" header

A Little Tip for You

