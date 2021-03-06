# The Setup View

Whenever you attempt to log into Bolt, a check is made to see if there is any registered user in the database. If there is no registered user Bolt assumes this is a fresh install, and proceeds to register you as a system administrator. To do this Bolt displays the _setup_ view. In addition to allowing you to register as an administrator, the setup view also allows you to perform some other setup actions \(like installing needed apps, creating needed roles,...\), as defined in [setup.json](/setting-up-bolt/setup.json.md). The setup view is a [native view](/views.md).

In this section we will talk about a few of the important actions performed by the setup view, and how those actions are performed. The goal here is to introduce you to some Bolt [endpoints](/bolt-server-endpoints.md) you can use in your app.

## Registering a User

![](/assets/registering-a-user.png)

To register a new user with Bolt, send a `POST` request to the Bolt endpoint [/api/users](/users-api.md). The body of the request is typically a `FormData` object \(which can be created in JavaScript by typing `var form = new FormData();`\).

This is how the setup view registers you as a user: it takes all the values you typed into the various fields, puts them in a programmatically created `FormData` object, and makes a `POST` request to `/api/users`. That endpoint is a sensitive endpoint, so Bolt already grants requests \(to that endpoint\) that are coming from system apps. This is why every `POST` request to /api/users must include the `X-Bolt-App-Token` custom header with which Bolt can determine if the app making the request is a system app or not. See [Bolt Request](/bolt-request.md) for more information on `X-Bolt-App-Token`.

See [/api/users](/users-api.md) for more information.

## Creating a Role

Bolt employs a role-based access control mechanism: your capabilities on Bolt are determined by the roles you assume.

To create a role, send a `POST` request to [/api/roles](/roles-api.md). This endpoint is also a sensitive endpoint and available only to system apps, so every `POST` request to it must include the `X-Bolt-App-Token` custom header.

See [/api/roles](/roles-api.md) for more information.

## Assigning a Role to a User

![](/assets/registered-as-admin.png)

With a user created, and a role created, the next step is to associate the user with the role. Note that Bolt allows you to associate more than one role with a user.

To assign a role to a user, send a `POST` request to [/api/user-roles](/user-roles-api.md). This endpoint is available only to system apps, so every `POST` request to it must include the `X-Bolt-App-Token` custom header.

See [/api/user-roles](/user-roles-api.md) for more information.

## Performing the Steps in setup.json

![](/assets/download-core-modules.png)

The steps in [setup.json](/setting-up-bolt/setup.json.md) are simply requests to the Bolt server. Any valide request can be specified.

