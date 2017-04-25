# App Events

These are the events raised by the [/api/apps](/apps-api.md) endpoints.

The following events are described here:

## bolt/app-installed

This event is raised when an app is installed.

### event object

A standard [Bolt event](/bolt-event.md).

```
{
    "name": String, //the name of the event, in this case 'app-installed'
    "body": Object, //an object representing the app that has just been installed
    "publisher": String //the name of the app that published, in this case 'bolt'
}
```

---

## bolt/app-started

This event is raised when an app is started.

### event object

A standard [Bolt event](/bolt-event.md).

```
{
    "name": String, //the name of the event, in this case 'app-started'
    "body": Object, //an object representing the context of the app that has just been started
    "publisher": String //the name of the app that published, in this case 'bolt'
}
```

---

## bolt/app-stopped

This event is raised when an app is stopped.

### event object

A standard [Bolt event](/bolt-event.md).

```
{
    "name": String, //the name of the event, in this case 'app-stopped'
    "body": Object, //an object representing the context of the app that has just been stopped
    "publisher": String //the name of the app that published, in this case 'bolt'
}
```



