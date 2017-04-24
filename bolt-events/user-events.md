# User Events

These are the events raised by the [/api/users](/users-api.md) endpoint.

The following events are described here:

* [bolt/user-created](#boltuser-created)
* [bolt/user-deleted](#boltuser-deleted)
* [bolt/user-logged-in](#boltuser-logged-in)
* [bolt/user-logged-out](#boltuser-logged-out)
* [bolt/user-updated](#boltuser-updated)

## bolt/user-created

This event is raised when a user is created.

### event object

A standard [Bolt event](/bolt-event.md).

```
{
    "name": String, //the name of the event, in this case 'user-created'
    "body": Object, //an object representing the user that has just been created
    "publisher": String //the name of the app that published, in this case 'bolt'
}
```

---

## bolt/user-deleted

This event is raised when a user is deleted.

### event object

A standard [Bolt event](/bolt-event.md).

```
{
    "name": String, //the name of the event, in this case 'user-deleted'
    "body": Object, //an object representing the user that has just been deleted
    "publisher": String //the name of the app that published, in this case 'bolt'
}
```

---

## bolt/user-logged-in

This event is raised when a user logs into Bolt.

### event object

A standard [Bolt event](/bolt-event.md).

```
{
    "name": String, //the name of the event, in this case 'user-logged-in'
    "body": Object, //an object representing the user that has just logged in
    "publisher": String //the name of the app that published, in this case 'bolt'
}
```

---

## bolt/user-logged-out

This event is raised when a user logs out of Bolt.

### event object

A standard [Bolt event](/bolt-event.md).

```
{
    "name": String, //the name of the event, in this case 'user-logged-out'
    "body": Object, //an object representing the user that has just logged out
    "publisher": String //the name of the app that published, in this case 'bolt'
}
```

---

## bolt/user-updated

This event is raised when a user is updated.

### event object

A standard [Bolt event](/bolt-event.md).

```
{
    "name": String, //the name of the event, in this case 'user-updated'
    "body": Object, //an object representing the user that has just been updated
    "publisher": String //the name of the app that published, in this case 'bolt'
}
```



