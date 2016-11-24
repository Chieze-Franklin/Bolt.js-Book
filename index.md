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

