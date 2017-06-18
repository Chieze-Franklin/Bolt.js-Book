# App Events

These are the events raised by the [/api/apps](/apps-api.md) endpoints.

The following events are described here:

* [bolt/app-downloaded](#boltapp-downloaded)
* [bolt/app-installed](#boltapp-installed)
* [bolt/app-router-loaded](#boltapp-router-loaded)
* [bolt/app-started](#boltapp-started)
* [bolt/app-starting](#boltapp-starting)
* [bolt/app-stopped](#boltapp-stopped)
* [bolt/app-stopping](#boltapp-stopping)

## bolt/app-downloaded

This event is raised when an [app](/app-object.md) is downloaded, before the actual installation happens.

### event object

A standard [Bolt event](/bolt-event.md).

```
{
    "name": String, //the name of the event, in this case 'app-downloaded'
    "body": String, //the name of the app that has just been downloaded
    "publisher": String, //the name of the app that published, in this case 'bolt'
    "body": String //the name of the app that has just been downloaded
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
    "publisher": String, //the name of the app that published, in this case 'bolt'
    "body": Object //an object representing the app that has just been installed
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
    "publisher": String, //the name of the app that published, in this case 'bolt'
    "body": Object //an object representing the router that has just been loaded
}
```

---

## bolt/app-started

This event is raised when an [app](/app-object.md) is started. The `body` field of the event object is a [context](/context-object.md) object.

### event object

A standard [Bolt event](/bolt-event.md).

```
{
    "name": String, //the name of the event, in this case 'app-started'
    "body": Object, //an object representing the context of the app that has just been started
    "publisher": String, //the name of the app that published, in this case 'bolt'
    "body": Object //an object representing the context of the app that has just been started
}
```

---

## bolt/app-starting

This event is raised when an [app](/app-object.md) is about to be started. This event is targeted only to the app that is about to be started; no other app can receive the event.

### event object

A standard [Bolt event](/bolt-event.md).

```
{
    "name": String, //the name of the event, in this case 'app-starting'
    "publisher": String, //the name of the app that published, in this case 'bolt'
    "body": {
        "appName": String, //the name of the app (the same as the name you gave the app, except if it was tampered with)
        "appToken" String, //the unique token for the app, the value for the 'X-Bolt-App-Token' request header
        "appPort": String, //(for non-system apps only) port on which the app server is running
        "protocol": String, //(for non-system apps only) the HTTP protocol of the Bolt server
        "host": String, //(for non-system apps only) the host/IP address of the Bolt server
        "port": String //(for non-system apps only) port on which the Bolt server is running
    }
}
```

---

## bolt/app-stopped

This event is raised when an [app](/app-object.md) is stopped.

### event object

A standard [Bolt event](/bolt-event.md). The `body` field of the event object is a [context](/context-object.md) object.

```
{
    "name": String, //the name of the event, in this case 'app-stopped'
    "body": Object, //an object representing the context of the app that has just been stopped
    "publisher": String, //the name of the app that published, in this case 'bolt'
    "body": Object //an object representing the context of the app that has just been stopped
}
```

---

## bolt/app-stopping

This event is raised when an [app](/app-object.md) is about to be stopped. This event is targeted only to the app that is about to be stopped; no other app can receive the event.

### event object

A standard [Bolt event](/bolt-event.md).

```
{
    "name": String, //the name of the event, in this case 'app-stopping'
    "publisher": String, //the name of the app that published, in this case 'bolt'
    "body": Object //currently an object representing the context of the app that is about to be stopped

    "publisher": String //the name of the app that published, in this case 'bolt'
}
```



