# App-Role Events

These are the event raised by the [/api/app-roles](/app-roles-api.md) endpoint.

* [bolt/app-role-created](#boltapp-role-created)
* [bolt/app-role-deleted](#boltapp-role-deleted)

## bolt/app-role-created

This event is raised when an app-role association is created.

### event object

A standard [Bolt event](/bolt-event.md).

```
{
    "name": String, //the name of the event, in this case 'app-role-created'
    "body": Object, //an object representing the app-role that has just been created
    "publisher": String //the name of the app that published, in this case 'bolt'
}
```

---

## bolt/app-role-deleted

This event is raised when an app-role association is deleted.

### event object

A standard [Bolt event](/bolt-event.md).

```
{
    "name": String, //the name of the event, in this case 'app-role-deleted'
    "body": Object, //an object representing the app-role that has just been deleted
    "publisher": String //the name of the app that published, in this case 'bolt'
}
```


