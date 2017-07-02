# Events \(API\)

talk about the body sent to /api/events by a publisher \(body, subscribers, headers\)

This is a description of the API endpoints exposed by the Bolt server for interacting with publishing and subscribing to events.

The following endpoints are described here:

* [POST: /api/events/\{\{name\}\}](#post-apieventsname)

* POST: /api/events/\*

* DELETE: /api/events/\*

## POST: /api/events/\{\{name\}\}

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
"route": String, //the
}
```

### response

If the app-user was added successfully, the `body` field of the response should hold an app-user object.

### security

Only system apps \(and native views\) can send requests to this endpoint.

---

## DELETE: /api/events/\*

In as much as Bolt destroys transient hooks at certain times, you may want to manually destroy such hooks at a time of your choosing. To do so, send a DELETE request to this endpoint, replacing the `*` character with whatever you used when creating the hook.

### response

If there is no error during the processing of the request, the `body` field of the response should hold an array of app-user objects.

### security

Only system apps \(and native views\) can send requests to this endpoint.
