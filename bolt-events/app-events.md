# App Events

These are the events raised by the [/api/apps](/apps-api.md) endpoints.

The following events are described here:

## bolt/app-started

This event is raised when an app is started.

### event object

A standard [Bolt event](/bolt-event.md).

```
{
    "name": String, //the name of the event, in this case 'app-started'
    "body": Object, //an object representing the context of the app
    "publisher": String //the name of the app that published, in this case 'bolt'
}
```

/

