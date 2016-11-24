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

-its a regular npm package.json, but has a few extra stuff added to it

-set it to serve \/home

