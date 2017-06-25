# routers

This is similar to [extensions](/extensions.md), but far more powerful.

The Bolt server comes with a number of endpoints \(routes\) like `/api/apps`, `/api/users`, and so on. To make Bolt even more modular and manageable than it already is, the ability to _load_ routes from external apps was added. By doing so, we can move some routes \(which are important but not necessarily core\) to external apps. That is where the `routers` object comes in.

`routers` allows us to load external routes unto the Bolt server. Routers are instances of `express.Router()`. Some common endpoints which are loaded this way are `/api/system`, `/api/db`, `/api/events`. Any app can register its own routers \(and, hence, routes\). For instance, to register a router that adds routes that all start with `/my/routes`:

```
"routers" : {
    "my-routes": {
        "main": "my-routes.js",
        "root": "/my/routes",
        "order": 1
    }
}
```

From the snippet above your `routers` object contains a router called _my-routes_. `main`, which in this case is _my-routes.js_, is a module that exports an instance of `express.Router()`. The `root`, which in this case is _/my/routes_, means every route added by this router must begin with _/my/routes_; so we could have routes like _/my/routes/help_ and _/my/routes/feedback_. `order` is used to sort routers. This is important as other apps may also register routers that begin with _/my/routes_. When different routers have the same path, requests are directed to the router with a lower `order`.

If your router has no `root` \(for instance, instead of _/my/routes/help_ and _/my/routes/feedback_, it registers routes _/help_ and _/feedback_\) and uses default `order` \(`0`\), then you can simple write:

```
"routers" : {
    "my-routes": "my-routes.js"
}
```

### note

A router will not be loaded if the app that installed the router is not a system app at that point in time.



