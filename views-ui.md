# Views \(UI\)

This is a description of the UI endpoints exposed by the Bolt server for interacting with views.

The following endpoints are described here:

* [GET: \/](#get-)

* [GET: \/login](#get-login)

* [GET: \/logout](#get-logout)

* [GET: \/setup](#get-setup)
* GET: \/view

## GET: \/

This displays the home \(`/home`\), login \(`/login`\) or setup \(`/setup`\) [view](/views.md) depending on certain criteria.

### response

If there are no registered users \(Bolt will assume this is a fresh deployment\):

* The setup view is shown to guide the user in setting up the environment.

If there are registered users Bolt will check for a current session \(a logged-in user\):

* If there is no logged-in user the login view is shown.

* If there is a logged-in user the home view is shown.


---

# GET: \/login

This displays the native login view.

---

## GET: \/logout

This displays the native logout view.

---

## GET: \/setup

This displays the native setup view.

---

## GET: \/:view

This displays the \(non-native\) view with the specified name.

Bolt looks for an installed app to serves this view. See [plugins](/plugins.md). Obviously more than one app can register to serve this view; in that case Bolt looks for the app that has been set as the default app for the view. If no app is found for the specified view Bolt loads an appropriate native view. If no native view is found Bolt redirects to the 404 view \(`/404`\) which is also a view that can be served by an app.

