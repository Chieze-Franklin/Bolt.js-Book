# collections

While SQL databases use tables, MongoDB uses collections. When an app needs to store a collection of objects \(like a list of contacts or a collection of phone numbers\) it defines a `collections` object. Bolt will automatically create the necessary collections for the app, prefixing the name of each collection with the name of the app. So, a collection called `students` owned by an app call `ctl-sms-students` with have the full name `ctl-sms-students/students`.

Say you are working on a _Students Managment System_, and you need to store a collection of students, your `collections` could look like this:

```
"collections": {
    "students": "*"
}
```

The value on the left \(in this case `students`\) is the name of the collection while the value on the right represents what other apps are allowed to read from the collection. The `"*"` means every app is allowed to read from the collection. You can specify an array of apps that are allowed to read from the collection, as shown below:

```
"collections": {
    "students": ["bolt-settings", "ctl-sms-home"]
}
```

From the above snippet, only the apps named _bolt-settings_ and _ctl-sms-home_ are allowed to read from the collection. \(Of course, the app that owns a collection is allowed to read from the collection.\)

The above snippet can also be rewritten as shown below:

```
"collections": {
    "students": {
        "guests": ["bolt-settings", "ctl-sms-home"]
    }
}
```

Using the above syntax, you can give every app read access to the collection as shown below:

```
"collections": {
    "students": {
        "guests": "*"
    }
}
```

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

You can specify an `options` field for your collections. This is the same `options` MongoDB uses when [creating a collection](https://docs.mongodb.com/manual/reference/method/db.createCollection/). In the options object you can cap a collection or [specify validation rules](https://docs.mongodb.com/manual/core/document-validation/).

For instance, to specify that every document in the `students` collection must have the following fields:

* a `name`, 
* an `id`, 
* a `dateOfBirth`,
* and either a `phone` or an `email`

```
"collections": {
    "students": {
        "guests": ["bolt-settings", "ctl-sms-home"],
        "options": {
            "validator": {
                "$and": [
                    { "name": { "$type": "string" } },
                    { "id": { "$type": "number" } },
                    { "dateOfBirth": { "$type": "date" } },
                    {"$or": [
                        { "phone": { "$type": "string" } },
                        { "email": { "$regex": /@gmail\.com$/ } }
                    ]}
                ]
            }
        }
    }
}
```

To get a list of data types to use in your validator, see [here](https://docs.mongodb.com/manual/reference/operator/query/type/).

To read more on validation see [this article](https://www.mongodb.com/blog/post/document-validation-part-1-adding-just-the-right-amount-of-control-over-your-documents) and [its sequel](https://www.mongodb.com/blog/post/document-validation-part-2-putting-it-all-together-a-tutorial).

You can also create a [capped collection](https://docs.mongodb.com/manual/core/capped-collections/).

```
"collections": {
    "student-scores-associations": {
        "tenants": ["scores-app", "classes-app"],
        "options": {
            "capped": true,
            "size": 5242880,
            "max": 5000
        }
    }
}
```

For how to store data to \(write\) and retrieve data from \(read\) collections, see [bolt-module-db](/bolt-module-db.md).

