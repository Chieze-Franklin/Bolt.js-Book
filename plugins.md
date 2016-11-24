# plugins

Plugins allow Bolt to expose interfaces \(endpoints\) without providing their implementations; instead, Bolt delegates their implementations to installed apps.

`plugins` is simply an object in which each key\/field specifies a Bolt endpoint and the corresponding value specifies an endpoint exposed by the app's server that is to be called whenever a user navigates to the Bolt endpoint specified in the afore-mentioned key\/field.

An example to make things clearer.

The notes app exposes the endpoint:`GET: /notes` while Bolt exposes the endpoint`GET: /home`. So, you could have your `plugins` look like this:

`"plugins": {`

```
"/home": "/notes"
```

`}`

After this app is installed, if the user navigates to `localhost:400/home`, your app will automatically be started \(let's say on port 500\), and the user will automatically be redirected to `localhost:500/notes`. If you think about it, plugins are a really cool feature of Bolt. You can have as many key-value pairs in your `plugins` object.

### Default Plugins

More than one app can specify the same Bolt endpoint in their `plugins`. For instance, another installed app could have:

`"plugins": {`

`"/home": "/my/own/end/point?source=bolt",`

`}`

Bolt allows end users to specify the default plugin for a Bolt endpoint. Likewise, with the user's permission, you can set your plugin as the default. More on this later.

### A Little Tip for You

One day we may allow apps to specify external endpoints \(endpoints defined on actual web services\/websites\) in plugins.

