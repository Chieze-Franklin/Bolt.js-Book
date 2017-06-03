# The Setup View

When ever you attempt to log into Bolt, a check is made to see if there is any registered user in the database. If there is no registered user Bolt assumes this is a fresh install, and proceeds to register you as a system administrator. To do this Bolt displays the _setup_ view. In addition to allowing you to register as an administrator, the setup view also allows you to perform some other setup actions \(like installing needed apps, creating needed roles,...\), as defined in [setup.json](/setting-up-bolt/setup.json.md). The setup view is a [native view](/views.md).

In this section we will talk about a few of the important actions performed by the setup view, and how those actions are performed. The goal here is to introduce you to some Bolt [endpoints](/bolt-server-endpoints.md) you can use in your app.

Registering a User

Creating a Role

Assigning a Role to a User

Performing the Steps in setup.json

