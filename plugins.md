# plugins

Plugins allow Bolt to expose interfaces \(endpoints\) without providing their implementations; instead, Bolt delegates their implementations to installed apps.

`plugins` is simply an object in which each key\/field specifies a Bolt endpoint and the corresponding value specifies an endpoint exposed by the app's server that is to be called whenever a user navigates to the Bolt endpoint specified in the afore-mentioned key\/field.

An example to make things clearer.



### A Little Tip for You

One day we may allow apps to specify external endpoints \(endpoints defined on actual web services\/websites\) in plugins.

