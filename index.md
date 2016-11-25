# index

This is the first UI endpoint that will be navigated to when your a UI for your app needs to be displayed.

This endpoint must be implemented as a `GET`.

Assuming you set your `index` as shown below:

`{`

`"name": "Notes",`

`....`

`"bolt": {`

`"main": "bolt-server.js",`

`"index": "/notes"`

`}`

`}`

Then, whenever the user navigates to a UI endpoint like `localhost:400/apps/Notes`, your app will automatically be started \(let's say on port 500\), and the user will automatically be redirected to `localhost:500/notes`.

Also note that necessary information will be sent in the query portion of the URL:

* `userid`: user ID of the logged-in user in the current session \(we pass user ID to avoid passing usernames\/emails in URL\)

To get the user from the userid:

`GET: localhost:400/api/users?_id={{userid}}`

This will return an array of users with that ID. Since the ID is unique, it should not contain more than one user.

### A Little Tip for You

Future versions of Bolt will send important information \(like the port on which Bolt is running\) to apps as URL queries to the `index` endpoint. So, whenever the user navigates to a UI endpoint like `localhost:400/apps/Notes`, your app will automatically be started \(let's say on port 500\), and the user may automatically be redirected to `localhost:500/Notes?port=400&host=localhost`.  Locale info may also be sent:  `localhost:500/Notes?port=400&host=localhost&locale=en-us` .

