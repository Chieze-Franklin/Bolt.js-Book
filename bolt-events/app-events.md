# App Events

These are the events raised by the [/api/apps](/apps-api.md) endpoints.

The following events are described here:

* [bolt/app-downloaded](#boltapp-downloaded)
* [bolt/app-installed](#boltapp-installed)
* [bolt/app-router-loaded](#boltapp-router-loaded)
* [bolt/app-started](#boltapp-started)
* [bolt/app-stopped](#boltapp-stopped)

## bolt/app-downloaded

This event is raised when an [app](/app-object.md) is downloaded, before the actual installation happens.

### event object

A standard [Bolt event](/bolt-event.md).

```
{
    "name": String, //the name of the event, in this case 'app-downloaded'
    "body": String, //the name of the app that has just been downloaded
    "publisher": String //the name of the app that published, in this case 'bolt'
}
```

---

## bolt/app-installed

This event is raised when an [app](/app-object.md) is installed.

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

## bolt/app-router-loaded

This event is raised when an [external router](/router-object.md) is loaded.

### event object

A standard [Bolt event](/bolt-event.md).

```
{
    "name": String, //the name of the event, in this case 'app-router-loaded'
    "body": Object, //an object representing the router that has just been loaded
    "publisher": String //the name of the app that published, in this case 'bolt'
}
```

---

## bolt/app-started

This event is raised when an [app](/app-object.md) is started. The `body` field of the event object is a context object.

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

This event is raised when an [app](/app-object.md) is stopped.

### event object

A standard [Bolt event](/bolt-event.md). The `body` field of the event object is a context object.

```
{
    "name": String, //the name of the event, in this case 'app-stopped'
    "body": Object, //an object representing the context of the app that has just been stopped
    "publisher": String //the name of the app that published, in this case 'bolt'
}
```



