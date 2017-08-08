# System Events

These are the event raised by certain internal processes.

* [bolt/system-db-connected](#boltsystem-db-connected)
* [bolt/system-started](#boltsystem-started)

## bolt/system-db-connected

This event is raised when Bolt connects to the system database.

### event object

A standard [Bolt event](/bolt-event.md).

```
{
    "name": String, //the name of the event, in this case 'system-db-connected'
    "publisher": String, //the name of the app that published, in this case 'bolt'
    "body": Object //an empty object
}
```

## bolt/system-started

This event is raised when Bolt is done booting.

### event object

A standard [Bolt event](/bolt-event.md).

```
{
    "name": String, //the name of the event, in this case 'system-started'
    "publisher": String, //the name of the app that published, in this case 'bolt'
    "body": Object //an empty object
}
```

## Note

There are more system events fired by modules like [bolt-module-system](/bolt-module-system.md).

