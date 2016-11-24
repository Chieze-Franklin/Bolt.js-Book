# main

This field is optional.

This is the most important field as without it your app's server would not be started. For apps that have no servers, do not supply this field.

Notice that npm also has a field called main. The value of that field is the name of the JavaScript file Node is expected to run. That is, the file that contains your server, usually built using Express. In this case, the file is `server.js`. Bolt does not run this file because the developer typically provides the port on which the server is to be started. We have to create another file similar to `server.js`, but we are not going to specify the port we want the server to run on; Bolt will choose a port dynamically during runtime.

Create a file called `bolt-server.js` \(you can call it anything else\). Copy all the content of `server.js` into `bolt-server.js`. In `bolt-server.js` we are going to remove the following lines:

`app.listen(3000, function () {`

`   console.log('Server started. Open http://localhost:3000 in your browser.');`

`});`

And replace them with:

`module.exports = app;`

Now, set the `main` field of the `bolt` object to `"bolt-server.js"`.

Your package.json should look something like this:

`{`

`"name": "Notes",`

`....`

`"bolt": {`

`"main": "bolt-server.js"`

`}`

`}`

Note that the file extension can be omitted: `"main": "bolt-server"`.

And we are done with `main`.

### A Little Tip for You

Instead of repeating codes in _server.js_ and _bolt-server.js_, you can instead create and export the app in _bolt-server.js_ \(as you have already done\) and import \(require\) it in _server.js_. In fact, behind-the-scene, this is exactly how Bolt gets the server for your app.

So, your entire _server.js_ becomes:

`var app = require('./bolt-server');`

`app.listen(3000, function () {`

`    console.log('Server started. Open http://localhost:3000 in your browser.');`

`});`

This way, your can run the app on Bolt via bolt-server.js and still run it with Node via server.js.

