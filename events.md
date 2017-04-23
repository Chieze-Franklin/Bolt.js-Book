# Events

An event is an occurence at a particular time, of which you may want to be notified. A number of events happen during the lifetime of a Bolt application. Examples include when a user logs into the system, when an app is started, when a new role is created, or when the system is shutting down. To get notifications about an event, you subscribe to \(or listen for\) that event. Also interesting is the fact that any app can raise its own events \(not just Bolt\). We will discuss both how to listen for events and how to raise your own events.

## hooks

You listen for events by creating [hooks](/hooks.md). A hook is simply a `POST` endpoint in your app's server. When a event occurs every necessary info needed to process the event will be _POSTed_ to the registered endpoints.

To register endpoints for events, create the `bolt.hooks` field in your _package.json_ to follow the format shown below:

```
"hooks" : {
    "bolt/user-logged-in": "hooks/bolt/user-logged-in",
    "bolt/app-started": "hooks/bolt/app-started",
    "camera/photo-saved": "hooks/my-favorite-event"
}
```

The _keys_ \(on the left\) in the `hooks` object define the event you are interested in. The _values_ \(on the right\) in the `hooks` object are endpoints to which event data will be _POSTed_. For more info see [hooks](/hooks.md).

## event data

The event object that will be _POSTed_ to your hooks has the following schema:

```
{
    "name": String, //the name of the event
    "body": Object, //the actual payload of the event
    "publisher": String, //the name of the app that raised the event
    "time": Date, //the time the event was published
    "id": String //identifies this instance of event object
}
```

**Note:** Currently `id` is undefined but will be present in future versions of Bolt, and will be used to check the authenticity of event objects. Different `id` values will be generated for different apps, for every event dispatched.

The module actually responsible for dispatching to appropriate hooks is [bolt-module-events](/bolt-module-events.md).

how to raise an event, includiing the schema of the object u send and subscribers to determine who gets the event

u can use events to create real time apps...socket.io...see examples: console app and chat app

