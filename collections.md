# collections

While SQL databases use tables, MongoDB uses collections. When an app needs to store a collection of objects \(like a list of contacts or a collection of phone numbers\) it defines a `collections` object. Bolt will automatically create the necessary collections for the app, prefixing the name of each collection with the name of the app. So, a collection called `students` owned by an app call `ctl-sms-students` with have the full name `ctl-sms-students/students`.

Say you are working on a _Students Managment System_, and you need to store a collection of students, your `collections` could look like this:

`"collections": {`

```
"students": "*"
```

`}`

The value on the left \(in this case `students`\) is the name of the collection while the value on the right represents what other apps are allowed to read from the collection. The `"*"` means every app is allowed to read from the collection. You can specify an array of apps that are allowed to read from the collection, as shown below:

`"collections": {`

```
"students": ["bolt-settings", "ctl-sms-home"]
```

`}`

From the above snippet, only the apps named _bolt-settings_ and _ctl-sms-home_ are allowed to read from the collection. \(Of course, the app that owns a collection is allowed to read from the collection.\)

The above snippet can also be rewritten as shown below:

`"collections": {`

```
"students": {
    "guests": ["bolt-settings", "ctl-sms-home"]
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

By default only the app that created a collection has the right to write to that collection. To give other apps write privilege, provide a `tenants` field for the collection object, as shown below:

```
"collections": {
    "student-guardian-associations": {
        "tenants": "*"
    },
    "student-scores-associations": {
        "tenants": ["scores-app", "classes-app"]
    }
}
```

From the snippet above, the collection`student-guardian-associations` can be written to by every app, while the collection `student-scores-associations` can be written to by the apps named `scores-app` and `classes-app` \(in addition to the app that owns the collection\). Tenants of a collection, just like the app that owns the collection, have both read and write access to the collection.

For how to store data to \(write\) and retrieve data from \(read\) collections, see [bolt-module-db](/bolt-module-db.md).

