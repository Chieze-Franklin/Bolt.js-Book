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

Now to install the app navigate to `http://localhost:400/install` \(assuming Bolt is running on port 400\). Note that you need to be logged in, and with admin privilege, for Bolt to let you successfully install an app.

Bolt gives you 2 ways to install an app: by downloading it from an online directory or by sideloading it from the local machine. Here we are going to sideload the app. \(We will address downloading when we get to [Publishing the App](/publishing-the-app.md).\)

To sideload an app, first copy its folder to the _node\_modules_ folder. In the future this step may not be necessary.

Type in the path to the folder that contains the _package.json_ file, relative to the _node\_modules_ folder. If the _package.json_ file is in the root folder \(which is very often the case\), all you need to type is the name of the root folder. Click the Sideload button, grant the app the necessary privileges, and install the app. See images below:

![](/assets/sideloading-an-app.png)

After installation, you can run the app by navigating to` http://localhost:400/apps/notes` \("notes" being the name of the app, as specified in the _package.json_\). Bolt will start the app on an appropriate port, as shown below:

![](/assets/notebook.png)

Congratulation! You have successfully installed an app on Bolt.



