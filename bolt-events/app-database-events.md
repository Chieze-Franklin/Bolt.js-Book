# App Database Events

These are the event raised by [bolt-module-db](/bolt-module-db.md).

* bolt/app-db-dropped
* [bolt/app-db-dropping](#boltapp-db-dropping)

## bolt/app-db-dropping

This event is raised when an app's database is about to be dropped. This event is targeted only to the app whose database is about to be dropped; no other app can receive the event.

### event object

A standard [Bolt event](/bolt-event.md).

```
{
    "name": String, //the name of the event, in this case 'app-downloaded'
    "publisher": String, //the name of the app that published, in this case 'bolt'
    "body": String //the name of the app that has just been downloaded
}
```



