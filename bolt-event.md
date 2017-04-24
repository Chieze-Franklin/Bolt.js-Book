# Bolt Event

The event object that will be _POSTed_ to your hooks has the following schema:

```
{
    "name": String, //the name of the event
    "body": Object, //the actual payload of the event
    "publisher": String, //the name of the app that raised the event
    "time": Date, //the time the event was published
    "token": String //identifies this instance of event object
}
```

Every instance of an event object has a `token` field whose value matches the app token of the app to which it is dispatched. Using the `token` of the event object, you can verify if that event object was actually sent from Bolt before proceeding. To check if the event object is genuinely from Bolt, see if its `token` matches your app token. This works with the assumption that the only other entity that should know your app token is Bolt.



