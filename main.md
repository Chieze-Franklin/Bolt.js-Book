# main

This field is optional.

This is the most important field as without it your app's server would not be started. For apps that have no servers, do not supply this field.

Notice that npm also has a field called main. The value of that field is the name of the JavaScript file Node is expected to run. That is, the file that contains your server, usually built using Express. In this case, the file is `server.js`. Bolt does not run this file because the developer typically provides the port on which the server is to be started. We have to create another file similar to `server.js`, but we are not going to specify the port we want the server to run on; Bolt will choose a port dynamically during runtime.

Create a file called `bolt-server.js` \(you can call it anything else\). Copy all the content of `server.js` into `bolt-server.js`. In `bolt-server.js` we are going to remove the following lines:

`app.listen(3000, function () {`

`console.log('Server started. Open http://localhost:3000 in your browser.');`

`});`

And replace them with:

`module.exports = app;`

