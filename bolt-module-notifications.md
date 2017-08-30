# bolt-module-notifications

This module installs the `/api/notifications` endpoints. These endpoints are responsible for raising notification events that apps can listen to in order to create real-time notifications.

To install this module, navigate to the Bolt endpoint `/install`, and type in _bolt-module-notifications_ as the app name. Go ahead and click **Download** \(or **Sideload**, as the case may be\). Take care to install this module as a system app.

This app is marked as a module, meaning \(among other things\) that it defines no user interface. Its installation registers the routers that respond to the requests sent to the `/api/notifications` endpoints.

The following endpoints are described here:



