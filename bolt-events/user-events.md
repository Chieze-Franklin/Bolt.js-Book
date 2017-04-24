# User Events

These are the events raised by the [/api/users](/users-api.md) endpoint.

The following events are described here:

* [bolt/user-logged-in](#boltuser-logged-in)

## bolt/user-logged-in

This event is raised when a user logs into Bolt.

### event object

A standard [Bolt event](/bolt-event.md).

```
{
    "name": String, //the name of the event, in this case 'user-logged-in'
    "body": Object, //an object representing the user that has just logged in
    "publisher": String, //the name of the app that published, in this case 'bolt'
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
    "publisher": String, //the name of the app that published, in this case 'bolt'
}
```



