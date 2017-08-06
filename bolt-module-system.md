# bolt-module-system

This module installs the `/api/system` endpoints which perform some utility functions.

To install this module, navigate to the Bolt endpoint `/install`, and type in _bolt-module-system_ as the app name. Go ahead and click **Download** \(or **Sideload**, as the case may be\). Take care to install this module as a system app.

This app is marked as a module, meaning \(among other things\) that it defines no user interface. Its installation registers the routers that respond to the requests sent to the `/api/system` endpoints.

The following endpoints are described here:

* [GET: /api/system](#get-apisystem)
* [GET: /api/system/help](#get-apisystemhelp)
* [POST: /api/system/exit](#post-apisystemexit)
* [POST: /api/system/exit/&lt;code&gt;](#post-apisystemexitcode)
* [POST: /api/system/reset](#post-apisystemreset)
* [POST: /api/system/reset/&lt;collection&gt;](#post-apisystemresetcollection)

### GET: /api/system

This endpoint simply redirects to [/api/system/help](#get-apisystemhelp).

---

### GET: /api/system/help

This endpoint returns a collection of all the paths and routes exposed by the Bolt server, as well as a few information about the environment.

---

### POST: /api/system/exit

Exits the process in which the server is running, thereby shutting down the entire system.

#### events

The event `bolt/system-exiting` will be fired with an empty event `body`.

Apps will be given a few seconds to react to this event before the system actually shuts down.

#### security

Always include the `X-Bolt-App-Token` custom header in the request. The header isn't currently checked but that may change in the future.

To exit the system, the user that initiates the action must have administrative privilege.

---

### POST: /api/system/exit/&lt;code&gt;

Exits the process in which the server is running \(with the specified exit code\), thereby shutting down the entire system.

#### events

The event `bolt/system-exiting` will be fired with the following event `body`:

```
{
    "code": String | Number //the exit code
}
```

Apps will be given a few seconds to react to this event before the system actually shuts down.

#### security

Always include the `X-Bolt-App-Token` custom header in the request. The header isn't currently checked but that may change in the future.

To exit the system, the user that initiates the action must have administrative privilege.

---

### POST: /api/system/reset

Resets \(drops\) the entire system database.

#### events

The event `bolt/system-db-resetting` will be fired with an empty event `body`.

Apps will be given a few seconds to react to this event before the database is actually dropped.

Currently Bolt does not shut down after this operation \(although that may change in the future\). It is, however, strongly advised to shut down the system at this point as it will be in a very unstable and unpredictable state.

#### security

Always include the `X-Bolt-App-Token` custom header in the request. The header isn't currently checked but that may change in the future.

To exit the system, the user that initiates the action must have administrative privilege.

---

### POST: /api/system/reset/&lt;collection&gt;

Resets \(drops\) the specified collection in the system database.

#### events

The event `bolt/system-collection-resetting` will be fired with the following event `body`:

```
{
    "collection": String //the collection being dropped
}
```

Apps will be given a few seconds to react to this event before the collection is actually dropped.

#### security

Always include the `X-Bolt-App-Token` custom header in the request. The header isn't currently checked but that may change in the future.

To exit the system, the user that initiates the action must have administrative privilege.

