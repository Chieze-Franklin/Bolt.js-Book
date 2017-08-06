# Roles \(API\)

A role encapsulates rights and capabilities.

This is a description of the API endpoints exposed by the Bolt server for interacting with roles.

The following endpoints are described here:

* [GET: /api/roles](#get-apiroles)

* [GET: /api/roles/&lt;name&gt;](#get-apirolesname)

* [POST: /api/roles](#post-apiroles)

* [DELETE: /api/roles](#delete-apiroles)

* [DELETE: /api/roles/&lt;name&gt;](#delete-apirolesname)

* [PUT: /api/roles](#put-apiroles)

* [PUT: /api/roles/&lt;name&gt;](#put-apirolesname)

## GET: /api/roles

Gets an array of [role objects](/role-object.md) for all registered roles matching the specified criteria.

You specify search criteria in the URL query portion. For instance, to get all roles with administrative privileges:

`localhost:400/api/roles?isAdmin=true`

### response

If there is no error during the processing of the request, the `body` field of the response should hold an array of [role objects](/role-object.md).

---

## GET: /api/roles/&lt;name&gt;

Gets the role with the specified name.

### response

If the role is successfully found, the `body` field of the response should hold a role object.

# POST: /api/roles

Adds a role to the database.

### request

A standard [Bolt request](bolt-request.md).

```
{
    "name" : String, //the name with which the role can be gotten internally
    "displayName" : String, //user-friendly text for the role
    "description" : String, //user-friendly description for the role
    "isAdmin" : Boolean //determines if this role should be granted administrative privileges
}
```

### response

If the role was added successfully, the `body` field of the response should hold a role object.

### security

Only system apps \(and native views\) can send requests to this endpoint.

---

## DELETE: /api/roles

Deletes an array of roles matching the specified criteria.

You specify search criteria in the URL query portion. For instance, to delete all roles with administrative privileges :

`localhost:400/api/roles?isAdmin=true`

### response

If there is no error during the processing of the request, the `body` field of the response should hold an array of role objects.

### security

Only system apps \(and native views\) can send requests to this endpoint.

---

## DELETE: /api/roles/&lt;name&gt;

Deletes the role with the specified name.

### response

If the role is successfully deleted, the `body` field of the response should hold a role object.

### security

Only system apps \(and native views\) can send requests to this endpoint.

---

## PUT: /api/roles

Updates an array of roles matching the specified criteria.

You specify search criteria in the URL query portion. For instance, to update all roles with administrative privileges :

`localhost:400/api/roles?isAdmin=true`

### request

A standard [Bolt request](bolt-request.md).

```
{
    "displayName" : String,
    "description" : String,
    "isAdmin" : Boolean
}
```

### response

If the role was updated successfully, the `body` field of the response should hold a role object.

### security

Only system apps \(and native views\) can send requests to this endpoint.

---

## PUT: /api/roles/&lt;name&gt;

Updates the role with the specified name.

### request

A standard [Bolt request](bolt-request.md).

```
{
    "displayName" : String,
    "description" : String,
    "isAdmin" : Boolean
}
```

### response

If the role is successfully updated, the `body` field of the response should hold a role object.

### security

Only system apps \(and native views\) can send requests to this endpoint.

