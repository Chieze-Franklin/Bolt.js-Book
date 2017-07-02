# bolt-module-db

This module installs the `/api/db` endpoints which allows apps to use the same database Bolt uses to store their objects. This means apps don't need their own separate databases.

To install this module, navigate to the Bolt endpoint `/install`, and type in _bolt-module-db_ as the app name. Go ahead and click **Download** \(or **Sideload**, as the case may be\). Take care to install this module as a system app.

This app is marked as a module, meaning \(among other things\) that it defines no user interface. Its installation registers the routers that respond to the requests sent to the `/api/db` endpoints.

The following endpoints are described here:



