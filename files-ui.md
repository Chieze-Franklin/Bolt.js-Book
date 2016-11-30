# Files \(UI\)

This is a description of the UI endpoints exposed by the Bolt server for interacting with public files.

The following endpoints are described here:

* GET: \/files\/\{\{app\}\}\/\{\{file\}\}

## GET: \/files\/\{\{app\}\}\/\{\{file\}\}

This displays the \(non-native\) view with the specified name.

Bolt looks for an installed app that serves this view. See [plugins](/plugins.md). Obviously more than one app can register to serve this view; in that case Bolt looks for the app that has been set as the default app for the view. If no app is found for the specified view Bolt loads an appropriate native view. If no native view is found Bolt redirects to the 404 view \(`/404`\) which is also a view that can be served by an app.

### security