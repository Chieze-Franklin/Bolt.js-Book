# collections

While SQL databases use tables, MongoDB uses collections. When an app needs to store a collection of objects \(like a list of contacts or a collection of phone numbers\) it defines a `collections` object. Bolt will automatically create a database for the app, naming the database after the app.

Say you are working on a Students Managment System, and you need to store a collection of students, your `collections` could look like this:

