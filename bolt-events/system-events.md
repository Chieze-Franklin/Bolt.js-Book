# System Events

These are the event raised by certain internal processes.

* [bolt/system-started](#boltsystem-started)

## bolt/system-started

This event is raised when an Bolt is done booting.

### event object

A standard [Bolt event](/bolt-event.md).

```
{
    "name": String, //the name of the event, in this case 'system-started'
    "body": Object, //an object representing the app-user that has just been deleted
    "publisher": String, //the name of the app that published, in this case 'bolt'
    "body": Object //an empty object
}
```

## Note

There are more system events fired by modules like [bolt-module-system](/bolt-module-system.md).



