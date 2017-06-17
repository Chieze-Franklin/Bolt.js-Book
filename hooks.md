# hooks

Bolt allows different parts of the system to raise/fire [events](/events.md) to signify that something has happened. Bolt itself raises events.

With hooks apps can signify their interests in knowing about various events. A hook is simply a `POST` endpoint in the app's server. When a event occurs every necessary info needed to process the event will be _POSTed_ to the registered endpoints.

To register endpoints for events, create the `bolt.hooks` field to follow the format shown below:

```
"hooks" : {
    "bolt/user-logged-in": "hooks/bolt/user-logged-in",
    "bolt/app-started": "hooks/bolt/app-started",
    "camera/photo-saved": "hooks/my-favorite-event"
}
```

The _keys_ \(on the left\) in the `hooks` object define the event you are interested in. The event has to be written in this format:

`{{name-of-app-raising-the-event}}/{{name-of-event}}`

When there is no `"/"` character in the event, the text provided is the name of the event. In this case you are interested in all events having that name, irrespective of the app raising the event. The `"*"` character can be used to match all apps or all events. For instance:

`"hooks": {`

`"photo-saved": "this-will-be-notified-of-all-photo-saved-events",`

`"*": "this-will-be-notified-of-all-events",`

`"*/*": "this-will-be-notified-of-all-events-raised-by-all-apps",`

`"*/photo-saved": "this-will-be-notified-of-all-photo-saved-events",`

`"camera/*": "this-will-be-notified-of-all-events-raised-by-camera"`

`}`

The _values_ \(on the right\) in the `hooks` object are endpoints to which event data will be _POSTed_.

In the above examples the endpoints to which the event data will be _POSTed_ reside in the app defining the hooks. Every time the listed events occur the app will be started \(if it wasn't already started\), and the event data will be _POSTed_ appropriately. Sometimes this isn't what you want. There are 2 other scenarios covered by Bolt:

* When the endpoint resides on an external server.
* When you want to handle the event in a function without having to start the app.

### When the endpoint resides on an external server.

Sometimes you want Bolt to dispatch the event data to an endpoint on an external server. To do this, the value \(on the right\) of an event field in the `hooks` object should be defined as an object \(not string\), and should have 2 fields, `route` which is the URL to which the event will be _POSTed_, and `type` which must be set to `"web"`. For example,

```
"hooks": {
    "photo-saved": {
        "route": "https://my-photo-catalog.herokuapp.com/photos-from-bolt",
        "type": "web"
    }
}
```

If the route value does not start with _http://_ or _https://_, Bolt will assume it to be a HTTP route.

More details later.

### When you want to handle the event in a function without having to start the app.

This is in line with the _serverless_ architecture. Just create functions, and Bolt will execute those functions at the appropriate time, as relevant events occur.

More details later.

### In Conclusion,

App authors should make it easy for others to discover events their apps raise, and the event data that accompany them.

For a list of events raised by Bolt, see [Bolt Events](/bolt-events.md).

For how to raise events, see [Events](/events.md) and [Events \(API\)](/events-api.md).

### note

Note that publishers \(apps that raise events\) can determine what apps they want to be notified of their events. See [Events](/events.md) and [Events \(API\)](/events-api.md).

