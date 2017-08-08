# Client Events

These events are available only to the clients \(they are not available to hooks\). They are still _experimental_.

* bolt/server-connected
* bolt/server-disconnected

## bolt/server-connected

This event is raised when a client connects to the Bolt server.

### event object

A standard [Bolt event](/bolt-event.md) with an empty event body.

## bolt/server-disconnected

This event is raised when a client disconnects from the Bolt server.

### event object

A standard [Bolt event](/bolt-event.md) with an empty event body.



