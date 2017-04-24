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



The module actually responsible for dispatching to appropriate hooks is [bolt-module-events](/bolt-module-events.md).

## raising an event

To raise an event, send a `POST` request to the `/api/events/{{event-name}}` endpoint of the Bolt server. This endpoint does **NOT** come with Bolt by default; you must install the [bolt-module-events](/bolt-module-events.md) module to have it. For instance, to raise an event called `photo-saved`, perform a `POST: localhost:400/api/events/photo-saved` \(assuming the Bolt server is running on port 400\). The body of the `POST` should look this:

```
{
    "body": Object, //the actual payload of the event
    "subscribers": [String] //(optional) a collection of the names of the apps you want this event to be dispatched to
}
```

By default an event is dispatched to all apps that have registered to listen for it \(all subscribers\). This may not always be what you want. Sometimes you want an event to be dispatched only to certain apps. For instance, imagine you have a chat app with raises an event every time a user posts a chat/message. You probably don't want every app receiving this event \(with the user's message\). In situations like this you specify a collection of the names of the apps you want the event to be sent to in the `subscribers` field of your `POST` body; all other apps not listed will be ignored, even if they registered to listen for that event.

There are different ways to use events in Bolt, and the apps presented in this section demonstrate those ways.

