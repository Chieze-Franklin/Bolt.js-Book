# hooks

Bolt allows different parts of the system to raise/fire events to signify that something has happened. Bolt itself raises events.

With hooks apps can signify their interests in knowing about various events. A hook is simply a `POST` endpoint in the app's server. When a event occurs every necessary info needed to process the event will be _POSTed_ to the registered endpoints.

To register endpoints for events, create the `bolt.hooks` field to follow the format shown below:

`"hooks": {`

`"bolt/user-logged-in": "hooks/bolt/user-logged-in",`

`"bolt/app-started": "hooks/bolt/app-started",`

`"camera/photo-saved": "hooks/my-favorite-event"`

`}`

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

App authors should make it easy to discover events their apps raise, and the event data that accompany them.

For a list of events raised by Bolt, see [Bolt Events](/bolt-events.md).

For how to raise events, see [bolt-module-events](/bolt-module-events.md).

### note

Note that publishers \(apps that raise events\) can determine what apps they want to be notified of their events. See [bolt-module-events](/bolt-module-events.md).

