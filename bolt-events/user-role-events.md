# User-Role Events

These are the event raised by the [/api/user-roles](/user-roles-api.md) endpoint.

* [bolt/user-role-created](#boltuser-role-created)
* [bolt/user-role-deleted](#boltuser-role-deleted)

## bolt/user-role-created

This event is raised when a [user-role association](/user-role-object.md) is created.

### event object

A standard [Bolt event](/bolt-event.md).

```
{
    "name": String, //the name of the event, in this case 'user-role-created'
    "body": Object, //an object representing the app-role that has just been created
    "publisher": String, //the name of the app that published, in this case 'bolt'
    "body": Object, //an object representing the user-role that has just been created
}
```

---

## bolt/user-role-deleted

This event is raised when an [user-role association](/user-role-object.md) is deleted.

### event object

A standard [Bolt event](/bolt-event.md).

```
{
    "name": String, //the name of the event, in this case 'user-role-deleted'
    "body": Object, //an object representing the app-role that has just been deleted
    "publisher": String, //the name of the app that published, in this case 'bolt'
    "body": Object, //an object representing the user-role that has just been deleted
}
```



