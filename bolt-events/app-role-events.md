# App-Role Events

These are the event raised by the [/api/app-roles](/app-roles-api.md) endpoint.

* [bolt/app-role-created](#boltapp-role-created)
* [bolt/app-role-deleted](#boltapp-role-deleted)

## bolt/app-role-created

This event is raised when an [app-role association](/app-role-object.md) is created.

### event object

A standard [Bolt event](/bolt-event.md).

```
{
    "name": String, //the name of the event, in this case 'app-role-created'
    "publisher": String, //the name of the app that published, in this case 'bolt'
    "body": Object //an object representing the app-role that has just been created
}
```

---

## bolt/app-role-deleted

This event is raised when an [app-role association](/app-role-object.md) is deleted.

### event object

A standard [Bolt event](/bolt-event.md).

```
{
    "name": String, //the name of the event, in this case 'app-role-deleted'
    "publisher": String, //the name of the app that published, in this case 'bolt'
    "body": Object //an object representing the app-role that has just been deleted
}
```



