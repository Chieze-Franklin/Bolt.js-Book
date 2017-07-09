# Client-Side Events

Thus far we have handled events by creating hooks, which are mostly endpoints on app servers. But sometimes you want the app client to also get an event. So, there is a need to propagate events from server to client without needing the client to make a request first. To achieve this Bolt uses the popular library [socket.io](https://socket.io/).

To receive events on the client, first include the JavaScript file _/socket.io/socket.io.js_. Then include the JavaScript file _{{bolt\_address}}/public/bolt/native/js/bolt.events.js_. This file introduces the object `Bolt.Events` which allows you to publish and subscribe to events on the client side. The `{{bolt_address}}` is a variable which holds the value of the environment variable `BOLT_ADDRESS` \(which the client can get from its server, or which can easily be passed from server to client using a templating engine like _express-handlebars_\). 

To subscribe to events, use the `on` method of the `Bolt.Events` object. The `on` method accepts two compulsory arguments: the name of the event to subscribe to and a callback function \(which takes an `event` object as parameter\) to be executed whenever that event occurs.

The snippet below listens for when a user has logged into Bolt, and appends the user's ID to a HTML element on the client page.

![](/assets/bolt.events.png)

Note that only events your server subscribes to will be propagated down to your client.

### Event Propagation for Non-System Apps

If an app is running as a system app, event propagation from server to client is automatic. This is not the case for a non-system app due to a number of reasons \(like the fact that a non-system app runs on a different process and different port from the Bolt server\).

For a non-system app, having created a hook for the event of interest, in the handler function for that hook you have to get all the sockets attached to the app server, and use the send method of each socket to propagate the event to the client, as shown below.

![](/assets/sockets-getsockets.png)

Yeah, you have to `JSON.stringify` the event before sending it.

Note that you **cannot** use `sockets.getSockets()` to get the sockets for another app: at best you will get an empty array.

### Client-Side Event Publishing

Raising events from the client-side is really nothing special; you simply make a `POST` to _/api/events/{{event}}_. Bolt.Events, however, provides a convenient way of raising events: the `emit` method.

The `Bolt.Events.emit` method accepts four arguments: the event name, the event data, the app token of the app emitting the event, and a callback function. Behind the scene the `Bolt.Events.emit` method uses `Bolt.Env` and `Bolt.Request`, and these objects are introduced by including the files _{{bolt\_addess}}/public/bolt/native/js/bolt.env.js _and_ {{bolt\_address}}/public/bolt/native/js/bolt.request.js._

![](/assets/bolt.env.png)

talk about unsubscribing \(u must supply a name to 'on' and use that name in 'remove'\)

### Client-Side Unsubscribing from Event

To be able to unsubscribe from an event, you must supply a name as the third argument of the `on` method of `Bolt.Events` and use that name in the `remove` method of `Bolt.Events`.

![](/assets/bolt.remove.png)



