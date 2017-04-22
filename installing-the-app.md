# Installing the App

Let's get back to the _My Notebook_ app we are dealing with.

Here is what your _package.json_ file should look like:

```
{
    "name": "notes",
    "version": "1.0.0",
    "description": "Note-Keeping App",
    "main": "server.js",
    "repository": {
        "type": "git",
        "url": "https://github.com/ionic-in-action/chapter3.git"
    },
    "author": "Jeremy Wilken",
    "license": "MIT",
    "bugs": {
        "url": "https://github.com/ionic-in-action/chapter3/issues"
    },
    "homepage": "https://github.com/ionic-in-action/chapter3",
    "dependencies": {
        "body-parser": "^1.9.3",
        "express": "^4.10.2"
    },
    
    "bolt": {
        "displayName": "My Notebook",
        "main": "bolt-server.js",
        "index": "/"
    }
}
```

Feel free to put different values for fields like `author` and `license`.

Like you read in [The package.json File](/packagejson.md), most of the fields are not needed by Bolt.

Now, create a new file named _bolt-server.js_ in the root directory. This is the file Bolt will run. Copy everything from _server.js_ into _bolt-server.js_, but delete/comment out the last 3 lines, replacing them with `module.exports = app;` as shown below:

```
/*app.listen(3000, function () {
    console.log('Server started. Open http://localhost:3000 in your browser.');
});*/

module.exports = app;
```

Your _server.js_ should now simply import the _bolt-server.js_, as shown below:

```
var app = require('./bolt-server');

app.listen(3000, function () {
    console.log('Server started. Open http://localhost:3000 in your browser.');
});
```

navigate to /install

start the app by /apps/notes \("notes" being the name of the app, as specified in the package.json\)

