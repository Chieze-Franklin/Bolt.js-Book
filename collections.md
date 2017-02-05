# collections

While SQL databases use tables, MongoDB uses collections. When an app needs to store a collection of objects \(like a list of contacts or a collection of phone numbers\) it defines a `collections` object. Bolt will automatically create a database for the app, naming the database after the app.

Say you are working on a _Students Managment System_, and you need to store a collection of students, your `collections` could look like this:

`"collections": {`

```
"students": "*"
```

`}`

The value on the left \(in this case `students`\) is the name of the collection while the value on the right represents what other apps are allowed to read from the collection. \(Only the app that owns a collection is allowed to write to the collection.\) The `"*"` means every app is allowed to read from the collection. You can specify an array of apps that are allowed to read from the collection, as shown below:

`"collections": {`

```
"students": ["bolt-settings", ""ctl-sms-home"]
```

`}`

From the above snippet, only the apps named _bolt-settings_ and _ctl-sms-home_ are allowed to read from the collection. \(Of course, the app that owns a collection is allowed to read from the collection.\)

The above snippet can also be rewritten as shown below:

`"collections": {`

```
"students": {
    "guests": ["bolt-settings", ""ctl-sms-home"]
}
```

`}`

Using the above syntax, you can give every app read access to the collection as shown below:

`"collections": {`

```
"students": {
    "guests": "*"
}
```

`}`

For how to store data to \(write\) and retrieve data from \(read\) collections, see [bolt-module-db](/bolt-module-db.md).

