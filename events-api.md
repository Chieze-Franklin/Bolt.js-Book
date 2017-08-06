# Events \(API\)

This is a description of the API endpoints exposed by the Bolt server for interacting with publishing and subscribing to events.

The following endpoints are described here:

* [POST: /api/events/&lt;name&gt;](#post-apieventsname)

* [POST: /api/events/\*](#post-apievents)

* [DELETE: /api/events/\*](#delete-apievents)

## POST: /api/events/&lt;name&gt;

Publishes an event with the specified name.

### request

A standard [Bolt request](bolt-request.md).

```
{
    "body": Object, //the actual payload of the event
    "headers": Object, //(optional) custom headers to be included in every POST dispatched to the event subscribers
    "subscribers": [String] //(optional) if specified, only apps whose names are in the array will receive this event
}
```

A sample request object to this endpoint is:

```
{
    "body": {
        "appName": "app1",
        "appToken": "A456DFE562EEF10"
    },
    "headers": {
        "X-Bolt-User-Name": "frank"
    },
    "subscribers": ["app1"]
}
```

### note

Every request to this endpoint must include the `X-Bolt-App-Token` custom header. Bolt uses that header to determine the `publisher` of the event.

---

# POST: /api/events/\*

Earlier on we saw [hooks](/hooks.md) in the [package.json](/packagejson.md) as a way to create subscribe to certain events. While those hooks work well, they come with some limitations:

* Such hooks must be defined in the package.json, before the app is installed. They cannot be altered thereafter.
* Such hooks are `POSTed` to your app even if the app is not running. Your app will be started if needed, and then the event object will be `POSTed` to the specified hooks.

To dynamically create hooks during runtime \(and to receive event notifications only if your app is running\) you have to create _transient hooks_. Transient hooks are just like regular hooks \(the same dispatch rules apply\) except that they are destroyed when your app stops or when the Bolt server shuts downs, or at some other point in time.

### request

A standard [Bolt request](bolt-request.md).

```
{
    "route": String, //the endpoint to which the event will be POSTed
    "type": String //(optional) the type of the hook
}
```

When making a request to this endpoint, replace the `*` character with the event name you are listening for. For instance, to subscribe to the _photo-saved_ event raised by the _camera_ app, make the `POST` to `/api/events/camera/photo-saved`.

Bolt itself makes use of transient hooks, re-creating them every time the server starts. \(Thinking of it, this is the only way Bolt can listen for events since Bolt is not an app which can be installed.\) The following are some of the requests Bolt makes during startup \(the last 2 portions of the routes tell the events Bolt is listening for\):

* `/api/events/bolt/app-deleted`
* `/api/events/bolt/app-router-loaded`
* `/api/events/bolt/app-started`
* `/api/events/bolt/role-deleted`
* `/api/events/bolt/user-deleted`

### note

Every request to this endpoint must include the `X-Bolt-App-Token` custom header.

---

## DELETE: /api/events/\*

In as much as Bolt destroys transient hooks at certain times, you may want to manually destroy such hooks at a time of your choosing. To do so, send a DELETE request to this endpoint, replacing the `*` character with whatever you used when creating the hook. For instance, to unsubscribe from `bolt/app-deleted`:

```
DELETE: /api/events/bolt/app-deleted
```

### note

Every request to this endpoint must include the `X-Bolt-App-Token` custom header.

