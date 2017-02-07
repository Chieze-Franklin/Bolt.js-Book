# routers

This is similar to [extensions](/extensions.md), but far more powerful.

The Bolt server comes with a number of endpoints \(routes\) like `/api/apps`, `/api/users`, and so on. To make Bolt even more modular and manageable than it already is, the ability to _load_ routes from external apps was added. By doing so, we can move some routes \(which are important but not necessarily core\) to external apps. That is where the `routers` object comes in.

`routers` allows us to load external routes unto the Bolt server. Routers are instances of `express.Router()`. Some common endpoints which are loaded this way are `/api/system`, `/api/db`, `/api/events`. Any app can register its own routers \(and, hence, routes\). For instance, to register a router that adds routes that all start with `/my/routes`:

"routers" : {

}



