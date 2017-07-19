# Views \(UI\)

This is a description of the UI endpoints exposed by the Bolt server for interacting with views.

The following endpoints are described here:

* [GET: /](#get-)

* [GET: /download](#get-download)

* [GET: /install](#get-install)

* [GET: /login](#get-login)

* [GET: /logout](#get-logout)

* [GET: /setup](#get-setup)

* [GET: /sideload](#get-sideload)

* [GET: /uninstall](#get-uninstall)

* [GET: /update](#get-update)

* [GET: /\{\{view\}\}](#get-view)

## GET: /

This displays the home \(`/home`\), login \(`/login`\) or setup \(`/setup`\) [view](/views.md) depending on certain criteria.

### response

If there are no registered users \(Bolt will assume this is a fresh deployment\):

* The setup view is shown to guide the user in setting up the environment.

If there are registered users Bolt will check for a current session \(a logged-in user\):

* If there is no logged-in user the login view is shown.

* If there is a logged-in user the home view is shown.

---

# GET: /download

This view helps you download an app.

You have to supply the `app` query string to specify the name of the app to be downloaded.

You can supply the `version` query string to specify the version of the app to be downloaded.

You can supply the `success` query string to specify the URL \(url-encoded\) to be redirected to after the downloading is done.

For instance:

```
/download?app=bolt-admin&success=%2Fapps%2Fbolt-admin
```

---

# GET: /install

This view helps you install an app, giving you the option to either download it or sideload it.

You can supply the `app` query string to specify the name of the app to be installed.

You can supply the `version` query string to specify the version of the app to be installed.

You can supply the `success` query string to specify the URL \(url-encoded\) to be redirected to after the installation is done.

---

# GET: /login

This displays the native login view.

You can supply the `success` query string to specify the URL \(url-encoded\) to be redirected to after logging in.

You can supply the `no_query` query string to specify if query strings should \(or should not\) be appended to the return URL specified via the `success` query string. By default the login view appends a `user` query string which holds a token representing the user that just logged in. Using the `user` query string apps can determine the identity of the logged-in user.

---

## GET: /logout

This displays the native logout view.

---

## GET: /setup

This displays the native setup view. You can't access this view directly; it is shown only if there is no registered user in the database.

---

# GET: /sideload

This view helps you sideload an app.

You have to supply the `app` query string to specify the path \(in the _node\_modules_ folder\) of the app to be sideloaded.

You can supply the `success` query string to specify the URL \(url-encoded\) to be redirected to after the sideloading is done.

---

# GET: /uninstall

This view helps you uninstall an app.

You can supply the `app` query string to specify the name of the app to be uninstalled.

You can supply the `success` query string to specify the URL \(url-encoded\) to be redirected to after the uninstallation is done.

---

# GET: /update

This view helps you update an app, giving you the option to either download or sideload the update.

You can supply the `app` query string to specify the name of the app to be updated.

You can supply the `path` query string to specify the path \(in the _node\_modules_ folder\) of the update to be sideloaded. If the path is the same as the name, then you do not need to specify the path.

You can supply the `version` query string to specify the version of the update to be downloaded.

You can supply the `success` query string to specify the URL \(url-encoded\) to be redirected to after the updating is done.

---

## GET: /\{\{view\}\}

This displays the view with the specified name.

Bolt looks for an installed app that serves this view. See [extensions](/extensions.md). Obviously more than one app can register to serve this view; in that case Bolt looks for the app that has been set as the default app for the view. If no app is found for the specified view Bolt loads an appropriate native view. If no native view is found Bolt redirects to the 404 view \(`/404`\) which is also a view that can be served by an app.
