# The package.json File

As far as integrating your app with Bolt is concerned, this is the starting point. The _package.json_ file can be thought of as the manifest for your application. This is what Bolt will consult during the installation of an app.

This _package.json_ is expected to be in the root folder of your app. It is no different from the _package.json_ for npm modules, except that a few more fields have been added to it.

Open the _package.json_ file; it's time to start editing.

First, let us go through some npm-specific fields to see what they mean to Bolt.

As far as Bolt is concerned, the most important npm-specific fields are:

* `name`: This is the name with which Bolt will identify your app. Other apps can also identify\/communicate with your app using that name. App names must be unique through out the system.
* `version`: Self-descriptive.
* `description`: Self-descriptive.

Let us now begin to add Bolt-specific fields.

Every Bolt-specific field must be contained in an object called `bolt`. So add the following:

`"bolt": {}`

The following are fields expected inside `bolt`:

* main

### main

This field is optional.

This is the most important field as without it your app's server would not be started. For apps that have no servers, do not supply this field.

Notice that npm also has a field called main. The value of that field is the name of the JavaScript file Node is expected to run. That is, the file that contains your server, usually built using Express. In this case, the file is `server.js`. Bolt does not run this file because the developer typically provides the port on which the server is to be started. We have to create another file similar to `server.js`, but we are not going to specify the port we want the server to run on; Bolt will choose a port dynamically during runtime.

Create a file called `bolt-server.js` \(you can call it anything else\). Copy all the content of `server.js` into `bolt-server.js`. In `bolt-server.js` we are going to remove the following lines:

`app.listen(3000, function () {`

` console.log('Server started. Open http://localhost:3000 in your browser.');`

`});`

And replace them with:

`module.exports = app;`



