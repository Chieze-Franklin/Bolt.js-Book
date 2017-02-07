# hooks

Bolt allows different parts of the system to raise/fire events to signify that something has happened. Bolt itself raises events.

With hooks apps can signify their interests in knowing about various events. A hook is simply a `POST` endpoint in the app's server.

App authors should make it easy to discover events their apps raise, and the event data that accompany them.

For a list of events raised by Bolt, see Bolt Events.



