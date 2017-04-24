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

## event object

The event object that will be _POSTed_ to your hooks has the following schema:

```
{
    "name": String, //the name of the event
    "body": Object, //the actual payload of the event
    "publisher": String, //the name of the app that raised the event
    "time": Date, //the time the event was published
    "token": String //identifies this instance of event object
}
```

Every instance of an event object has a `token` field whose value matches the app token of the app to which it is dispatched. Using the `token` of the event object, you can verify if that event object was actually sent from Bolt before proceeding. To check if the event object is genuinely from Bolt, see if its `token` matches your app token. This works with the assumption that the only other entity that should know your app token is Bolt.

The module actually responsible for dispatching to appropriate hooks is [bolt-module-events](/bolt-module-events.md).

## raising an event

how to raise an event, includiing the schema of the object u send and subscribers to determine who gets the event. note that only Bolt servers that have bolt-module-events installed can do this evnt thingy

u can use events to create real time apps...socket.io...see examples: console app and chat app

