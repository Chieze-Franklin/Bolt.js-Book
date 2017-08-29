# bolt-module-dashboard

This module installs the `/api/dashboard` endpoints. These endpoints are responsible for raising dashboard events that apps can listen to in order to create real-time dashboards.

To install this module, navigate to the Bolt endpoint `/install`, and type in _bolt-module-dashboard_ as the app name. Go ahead and click **Download** \(or **Sideload**, as the case may be\). Take care to install this module as a system app.

This app is marked as a module, meaning \(among other things\) that it defines no user interface. Its installation registers the routers that respond to the requests sent to the `/api/dashboard` endpoints.

The following endpoints are described here:

* [POST: /api/dashboard/card](#post-apidashboardcard)
* [POST: /api/dashboard/tile](#post-apidashboardtile)
* [POST: /api/dashboard/view](#post-apidashboardview)
* [DELETE: /api/dashboard/card](#delete-apidashboardcard)
* [DELETE: /api/dashboard/tile](#delete-apidashboardtile)
* [DELETE: /api/dashboard/view](#delete-apidashboardview)

### POST: /api/dashboard/card

Send a request to this endpoint in order to notify dashboards to show the card for the app. Dashboards are expected to show only one card per app.

#### request

A standard [Bolt request](bolt-request.md). All the fields are optional \(this may change in the future\).

```
{
    "background" : String, //the background colour (for type='text') or image (for type='image') of the card
    "message": String, //the main content of the card (for type='text')
    "query": String, //the query to be appended to the URL of the app that made this request
    "route": String, //the route to be appended to the URL of the app that made this request
    "subject": String, //the caption of the card
    "type" : String//the type of card, possible values are: 'text' (default), 'image'
}
```

Typically a card \(or a button on the card\) can be clicked. When clicked, the user should be redirected to the root URL of the app that created the card. If you want to add an endpoint to that URL, specify it with the `route` field. If you want to add a query to that URL, specify it with the `query` field.

#### events

The event `bolt/dashboard-card-posted` will be fired with the following event `body`:

```
{
    "app": String, //the name of the app that owns this card
    "background" : String, //same as above
    "message": String, //same as above
    "query": String, //same as above
    "route": String, //same as above
    "subject": String, //same as above
    "type" : String//same as above
}
```

#### security

Always include the `X-Bolt-App-Token` custom header in the request.

---

### POST: /api/dashboard/tile

Send a request to this endpoint in order to notify dashboards to show the tile for the app. Dashboards are expected to show only one tile per app.

#### request

A standard [Bolt request](bolt-request.md). All the fields are optional \(this may change in the future\).

```
{
    "background" : String, //the background colour (for type='text') or image (for type='image') of the tile
    "message": String, //the main content of the tile (for type='text')
    "query": String, //the query to be appended to the URL of the app that made this request
    "route": String, //the route to be appended to the URL of the app that made this request
    "subject": String, //the caption of the tile
    "type" : String//the type of tile, possible values are: 'text' (default), 'image'
}
```

Typically a tile \(or a button on the tile\) can be clicked. When clicked, the user should be redirected to the root URL of the app that created the tile. If you want to add an endpoint to that URL, specify it with the `route` field. If you want to add a query to that URL, specify it with the `query` field.

#### events

The event `bolt/dashboard-tile-posted` will be fired with the following event `body`:

```
{
    "app": String, //the name of the app that owns this tile
    "background" : String, //same as above
    "message": String, //same as above
    "query": String, //same as above
    "route": String, //same as above
    "subject": String, //same as above
    "type" : String//same as above
}
```

#### security

Always include the `X-Bolt-App-Token` custom header in the request.

---

### POST: /api/dashboard/view

Send a request to this endpoint in order to notify dashboards to show the web page \(view\) for the app. Dashboards are expected to show only one view per app.

#### request

A standard [Bolt request](bolt-request.md). All the fields are optional \(this may change in the future\).

```
{
    "height" : String | Number, //the preferred height of the view
    "query": String, //the query to be appended to the URL of the app that made this request
    "route": String, //the route to be appended to the URL of the app that made this request
    "subject": String, //the caption of the view
    "width" : String | Number//the preferred width of the view
}
```

Typically a view \(or a button on the view\) can be clicked. When clicked, the user should be redirected to the root URL of the app that created the view. If you want to add an endpoint to that URL, specify it with the `route` field. If you want to add a query to that URL, specify it with the `query` field.

#### events

The event `bolt/dashboard-view-posted` will be fired with the following event `body`:

```
{
    "app": String, //the name of the app that owns this view
    "height" : String, //same as above
    "query": String, //same as above
    "route": String, //same as above
    "subject": String, //same as above
    "width" : String//same as above
}
```

#### security

Always include the `X-Bolt-App-Token` custom header in the request.

---

### DELETE: /api/dashboard/card

Send a request to this endpoint in order to notify dashboards to remove the card for the app.

#### events

The event `bolt/dashboard-card-deleted` will be fired with the following event `body`:

```
{
    "app": String //the name of the app that owns this card
}
```

#### security

Always include the `X-Bolt-App-Token` custom header in the request.

---

### DELETE: /api/dashboard/tile

Send a request to this endpoint in order to notify dashboards to remove the tile for the app.

#### events

The event `bolt/dashboard-tile-deleted` will be fired with the following event `body`:

```
{
    "app": String //the name of the app that owns this tile
}
```

#### security

Always include the `X-Bolt-App-Token` custom header in the request.

---

### DELETE: /api/dashboard/view

Send a request to this endpoint in order to notify dashboards to remove the view for the app.

#### events

The event `bolt/dashboard-view-deleted` will be fired with the following event `body`:

```
{
    "app": String //the name of the app that owns this view
}
```

#### security

Always include the `X-Bolt-App-Token` custom header in the request.

