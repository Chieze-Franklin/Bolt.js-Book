# App Database Events

These are the event raised by [bolt-module-db](/bolt-module-db.md).

* [bolt/app-db-dropped](#boltapp-db-dropped)
* [bolt/app-db-dropping](#boltapp-db-dropping)

## bolt/app-db-dropped

This event is raised when an app's database is dropped.

### event object

A standard [Bolt event](/bolt-event.md).

```
{
    "name": String, //the name of the event, in this case 'app-db-dropped'
    "publisher": String, //the name of the app that published, in this case 'bolt'
    "body": {
        "app": String, //the name of the app whose database was dropped
        "db": String //same as the app field above
    }
}
```

---

## bolt/app-db-dropping

This event is raised when an app's database is about to be dropped. This event is targeted only to the app whose database is about to be dropped; no other app can receive the event.

### event object

A standard [Bolt event](/bolt-event.md).

```
{
    "name": String, //the name of the event, in this case 'app-db-dropping'
    "publisher": String, //the name of the app that published, in this case 'bolt'
    "body": {
        "app": String, //the name of the app whose database is about to be dropped
        "db": String //same as the app field above
    }
}
```



