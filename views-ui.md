# Views \(UI\)

This is a description of the UI endpoints exposed by the Bolt server for interacting with views.

The following endpoints are described here:

* [GET: \/](#get-apiuser-roles)

* [POST: \/api\/user-roles](#post-apiuser-roles)

* [DELETE: \/api\/user-roles](#delete-apiuser-roles)


## GET: \/

This displays the home \(`/home`\), login \(`/login`\) or setup \(`/setup`\) [view](/views.md) depending on certain criteria.

### response

If there are no registered users \(Bolt will assume this is a fresh deployment\):

* The setup view is shown to guide the user in setting up the environment.

If there are registered users Bolt will check for a current session \(a logged-in user\):

* If there is no logged-in user the login view is shown.

* If there is a logged-in user the home view is shown.


---

# POST: \/api\/user-roles

Adds a user-role association to the database.

### request

A standard [Bolt request](bolt-request.md).

`{`

`"user" : String, //username of the user being referenced`

`"role" : String //name of the role being referenced`

`}`

### response

If the user-role was added successfully, the `body` field of the response should hold a user-role object.

### security

Only system apps \(and native views\) can send requests to this endpoint.

---

## DELETE: \/api\/user-roles

Deletes an array of user-role association objects for all registered user-roles matching the specified criteria.

You specify search criteria in the URL query portion. For instance, to delete all user-roles for user `user1`:

`localhost:400/api/user-roles?user=user1`

### response

If there is no error during the processing of the request, the `body` field of the response should hold an array of user-role objects.

### security

Only system apps \(and native views\) can send requests to this endpoint.

