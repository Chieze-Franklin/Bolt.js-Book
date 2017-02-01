# The package.json File

This document describes what a typical _package.json_ file should look like, and the relevance of the fields in the file.

As far as integrating your app with Bolt is concerned, this is the starting point. The _package.json_ file can be thought of as the manifest for your application \(you know, like the AndroidManifest.xml in your Android projects\). This is what Bolt will consult during the installation of an app.

This _package.json_ is expected to be in the root folder of your app. It is no different from the _package.json_ for npm modules, except that a few more fields have been added to it.

Open the _package.json_ file; it's time to start editing.

First, let us go through some npm-specific fields to see what they mean to Bolt.

As far as Bolt is concerned, the most important npm-specific fields are:

* `name`: This is the name with which Bolt will identify your app. Other apps can also identify/communicate with your app using that name. App names must be unique through out the system.
* `version`: The version of your app.
* `description`: A description of your app..

Let us now begin to add Bolt-specific fields.

Every Bolt-specific field must be contained in an object called `bolt`. So add the following:

`"bolt": {}`

The following are fields expected inside `bolt`:

* [main](/main.md)
* [checks](/checks.md)
* dependencies: String \/\/the same format as npm dependencies but lists apps \(not modules\) that this app depends on
* displayName: String \/\/a user-friendly caption for your app 
* [extensions](/extensions.md)
* [files](/files.md)
* [index](/package-index.md)
* [ini](/ini.md)
* [install](/install.md)
* order: Number \/\/\(default: 0\) provides another way for dashboards\/desktops\/launchers to sort apps
* [public](/public.md)
* startup: Boolean \/\/\(default: false\) set to true if you want your app to be started as soon as Bolt boots up
* system: Boolean \/\/\(default: false\) set to true if you want your app to have root privilege
* [tags](/tags.md)

Note that users have the final say concerning the startup and system attributes of your app.

