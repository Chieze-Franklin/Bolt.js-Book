# Bolt Modules

To keep the Bolt server slim the idea of Bolt modules was introduced. Instead of coming with every possible endpoint, the Bolt server will come only with core endpoints, endpoints that are vital to the core ideas behind Bolt. These are the endpoints discussed in [Bolt Server Endpoints](/bolt-server-endpoints.md). Every other endpoint will be packaged into modules and installed if needed.

Modules are not too different from other apps installed on Bolt, and you just as easily create your own modules. A module is basically an app that is not expected to be run/executed. It does not have a UI, for instance. We install modules for the side effects they create during installation. One of such side effects is the installation of [routers](/routers.md). A router is simply an object that adds endpoints to the Bolt server.

Note that even regular apps \(not just modules\) can install their own routers.

Also note that an app needs system privilege to install routers. This is because routers integrate deeply with Bolt \(Bolt does not distinguish an endpoint that was built into Bolt from one added by a router\). External routers \(those installed by modules\) have as much access to every Bolt resource as do built-in routers. Be careful to be sure that routers are installed by only apps/modules you trust.

The following are core Bolt modules:

* bolt-module-dashboard
* bolt-module-db
* bolt-module-notifications
* bolt-module-system



