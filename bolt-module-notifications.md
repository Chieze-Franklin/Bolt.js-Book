# bolt-module-notifications

This module installs the `/api/notifications` endpoints. These endpoints are responsible for raising notification events that apps can listen to in order to create real-time notifications.

To install this module, navigate to the Bolt endpoint `/install`, and type in _bolt-module-notifications_ as the app name. Go ahead and click **Download** \(or **Sideload**, as the case may be\). Take care to install this module as a system app.

This app is marked as a module, meaning \(among other things\) that it defines no user interface. Its installation registers the routers that respond to the requests sent to the `/api/notifications` endpoints.

The following endpoints are described here:

### POST: /api/notifications

Send a request to this endpoint in order to raise a notification. A notification may be just a transient toast, a permanent notification item, or both.

#### request

A standard [Bolt request](bolt-request.md). All the fields are optional \(this may change in the future\).

```
{
    "buttons": [Object], //an array of buttons on the notification item
    "message": String | Object, //the message of the notification
    "options": {
        "sticky": Boolean, //if true, the notification does not disappear even when the close button is clicked
        "transient": Boolean //if true, the notification is not persisted in the database
    },
    "query": String, //the query to be appended to the URL of the app that made this request
    "route": String, //the route to be appended to the URL of the app that made this request
}
```

##### buttons

`buttons` is an array of buttons on the notification item. Each button object has the following schema:

```
{
    "type": String, //possible values: 'link', 'phone', 'postback'
    "text": String, //the text to appear on the button
    "data": String //the URL (for type='link'), phone number (for type='phone') or postback data (for type='postback')
}
```

If the button is of type `link`, clicking on it will redirect to the URL formed from the `data` field \(currently, it is expected that the URL be absolute, although relative paths may be supported in the future\). If the button is of type `phone`, clicking on it will attempt to make a call to the phone number formed from the `data` field. If the button is of type `postback`, clicking on it will raise an event called `bolt/notification-postback` which the app that owns the notification can listen for. Examining the body of the `bolt/notification-postback` event, the app can tell exactly what button a user clicked, and react accordingly. The `bolt/notification-postback` event has the following event body:

```
{
    "notification": Object, //the original notification object from which the post-back resulted
    "postback": {
        "notification_id": String | Number, //the _id of the original notification
        "data": String //the data of the postback button that was clicked
    },
    "user": Object //the user that clicked the postback button
}
```

Note that the postback event for a particular notification is fired only at the app that raised that notification.

##### message

`message` can either be a simple `String` or an `Object`. When message comes as a `Object`, it has the following schema:

```
{
    "type": String, //the message type, possible values are 'text', 'audio', 'file', 'image', 'video', 'page'
    "data": String //the text (for type='text') or URL (fo other message types) of the message
}
```

When message comes as a `String`, like `"message": "hello world"`, it is converted to an `Object` with `type` set to `text`:

```
{
    "type": "text",
    "data": "hello world"
}
```

Note that notifications without `message` fields are not persisted in the database.

#### events

The event `bolt/notification-posted` will be fired with the following event `body`:

```
{
    "app": String, //the name of the app that owns this card
    "buttons" : String, //same as above
    "from": { //basic info about the user from which this notification was sent
        "name": String, //the username of the 
        "displayName": String, //the display name of the user
        "displayPic": String, //the display pic of the user
    },
    "message": {
        "type": String, //the message type, possible values are 'text', 'audio', 'file', 'image', 'video', 'page'
        "data": String //the text (for type='text') or URL (fo other message types) of the message
    },
    "options": Object, //same as above
    "query": String, //same as above
    "route": String, //same as above
}
```

#### security

Always include the `X-Bolt-App-Token` custom header in the request.

