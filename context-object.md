# Context Object

This object represents information about the environment in which an app is running. It is returned primarily by the Bolt endpoint [POST: /api/apps/start](/apps-api.md).

### Schema

```
{
    "app": Object, //the app running in this context
    "host": String, //the host or IP address of the app server (available only for non-system apps)
    "name": String, //same as the name field of the app object running in this context
    "path": String, //same as the path field of the app object running in this context
    "pid": Number, //the ID of the process within which this context situates (for non-system apps only)
    "port": Number //the port on which the app server is running (for non-system apps only)
}
```



