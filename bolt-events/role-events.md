# Role Events

These are the events raised by the [/api/roles](/roles-api.md) endpoints.

The following events are described here:

* [bolt/role-created](#boltrole-created)
* [bolt/role-deleted](#boltrole-deleted)
* [bolt/role-updated](#boltrole-updated)

## bolt/role-created

This event is raised when a [role](/role-object.md) is created.

### event object

A standard [Bolt event](/bolt-event.md).

```
{
    "name": String, //the name of the event, in this case 'role-created'
    "body": Object, //an object representing the role that has just been created
    "publisher": String //the name of the app that published, in this case 'bolt'
}
```

---

## bolt/role-deleted

This event is raised when a [role](/role-object.md) is deleted.

### event object

A standard [Bolt event](/bolt-event.md).

```
{
    "name": String, //the name of the event, in this case 'role-deleted'
    "body": Object, //an object representing the role that has just been deleted
    "publisher": String //the name of the app that published, in this case 'bolt'
}
```

---

## bolt/role-updated

This event is raised when a [role](/role-object.md) is updated.

### event object

A standard [Bolt event](/bolt-event.md).

```
{
    "name": String, //the name of the event, in this case 'role-updated'
    "body": Object, //an object representing the role that has just been updated
    "publisher": String //the name of the app that published, in this case 'bolt'
}
```



