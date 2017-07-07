# Client-Side Events

Thus far we have handled events by creating hooks, which are mostly endpoints on app servers. But sometimes you want the app client to also get an event. So, there is a need to propagate events from server to client without needing the client to make a request first. To achieve this Bolt uses the popular library [socket.io](https://socket.io/).

To receive events on the client, first include the JavaScript file _/socket.io/socket.io.js_. Then include the JavaScript file _\{\{bolt_address\}\}/public/bolt/native/js/events.js_. This file introduces the object Bolt.EventManager which allows you to publish and subscribe to events on the client side. The `{{bolt_address}}` is a variable which holds the value of the environment variable `BOLT_ADDRESS` \(which the client can get from its server, or which can easily be passed from server to client using a templating engine like _express-handlebars_\).

The snippet below listens for when a user has logged into Bolt, and appends the user's ID to a HTML element on the client page.

talk about including the native events.js

talk about listening for events...note that only events u have registered hooks for will be sent to ur client

talk about the extra step u hv to do on the server if ur app is running on another process to send events from server to client

talk about publishing/raising events

