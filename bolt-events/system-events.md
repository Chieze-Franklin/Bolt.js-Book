# System Events

These are the event raised by [bolt-module-system](/bolt-module-system.md) and other internal processes.

* [bolt/system-collection-resetting](#boltsystem-collection-resetting)
* [bolt/system-db-connected](#boltsystem-db-connected)
* [bolt/system-db-resetting](#boltsystem-db-resetting)
* [bolt/system-exiting](#boltsystem-exiting)
* [bolt/system-started](#boltsystem-started)

## bolt/system-collection-resetting

This event is raised when an Bolt is preparing to reset \(clear\) a system collection in the system database. Apps are given a few seconds to do whatever cleanup they need to do before Bolt actually resets the database.

### event object

A standard [Bolt event](/bolt-event.md).

```
{
    "name": String, //the name of the event, in this case 'system-db-connected'
    "body": Object, //an object representing the app-user that has just been created
    "publisher": String, //the name of the app that published, in this case 'bolt'
    "body": {
        "collection": String //(may be undefined) the name of the collection about to be reset
    }
}
```

---

## bolt/system-db-connected

This event is raised when Bolt connects to the system database. This is one of the very first events that happen while Bolt is starting up.

### event object

A standard [Bolt event](/bolt-event.md).

```
{
    "name": String, //the name of the event, in this case 'system-db-connected'
    "publisher": String, //the name of the app that published, in this case 'bolt'
    "body": Object //an empty object
}
```

---

## bolt/system-db-resetting

This event is raised when an Bolt is preparing to reset \(clear\) the system database. Apps are given a few seconds to do whatever cleanup they need to do before Bolt actually resets the database.

### event object

A standard [Bolt event](/bolt-event.md).

```
{
    "name": String, //the name of the event, in this case 'system-db-resetting'
    "publisher": String, //the name of the app that published, in this case 'bolt'
    "body": Object //an empty object
}
```

---

## bolt/system-exiting

This event is raised when an Bolt is preparing to shut down. Apps are given a few seconds to do whatever cleanup they need to do before Bolt actually shuts down.

### event object

A standard [Bolt event](/bolt-event.md).

```
{
    "name": String, //the name of the event, in this case 'system-exiting'
    "body": Object, //an object representing the app-user that has just been deleted
    "publisher": String, //the name of the app that published, in this case 'bolt'
    "body": {
        "code": Number //(may be undefined) represents the Node shutdown code with which the Bolt process is exiting
    }
}
```

---

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



