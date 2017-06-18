# System Events

These are the event raised by the /api/app-users endpoint.

* [bolt/app-role-created](#boltapp-user-created)
* [bolt/app-role-deleted](#boltapp-user-deleted)

## bolt/app-user-created

This event is raised when an [app-user association](/app-user-object.md) is created.

### event object

A standard [Bolt event](/bolt-event.md).

```
{
    "name": String, //the name of the event, in this case 'app-user-created'
    "body": Object, //an object representing the app-user that has just been created
    "publisher": String //the name of the app that published, in this case 'bolt'
}
```

---

## bolt/app-user-deleted

This event is raised when an [app-user association](/app-user-object.md) is deleted.

### event object

A standard [Bolt event](/bolt-event.md).

```
{
    "name": String, //the name of the event, in this case 'app-user-deleted'
    "body": Object, //an object representing the app-user that has just been deleted
    "publisher": String //the name of the app that published, in this case 'bolt'
}
```



