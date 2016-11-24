# index

This is the first UI endpoint that will be navigated to when your a UI for your app needs to be displayed.

Assuming you set your `index` as shown below:

`{`

`"name": "Notes",`

`....`

`"bolt": {`

`"main": "bolt-server.js",`

`"index": "/notes"`

`}`

`}`

Then, whenever the user navigates to a UI endpoint like `localhost:400/apps/Notes`, your app will automatically be started \(let's say on port 500\), and the user will automatically be redirected to `localhost:500/Notes`.

### A Little Tip for You

Future versions of Bolt will send important information \(like the port on which Bolt is running\) to apps as URL queries to the `index` endpoint. So, whenever the user navigates to a UI endpoint like `localhost:400/apps/Notes`, your app will automatically be started \(let's say on port 500\), and the user may automatically be redirected to `localhost:500/Notes?port=400&host=localhost`.  Locale info may also be sent:  `localhost:500/Notes?port=400&host=localhost&locale=en-us` .

