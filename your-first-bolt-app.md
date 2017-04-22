# Your First Bolt App

The next few pages will guide you through the development of your first Bolt app.

The complete source code for the app you will be working on can be found at  [https://github.com/ionic-in-action/chapter3](https://github.com/ionic-in-action/chapter3). You can go ahead and download/clone the project. Truth be told, you won't be _developing_ any app in this section, as the app has already been developed. The main objective here is to show you how easy it is to integrate an existing app into Bolt.

Bolt is built on top of Node.js. As a result, it very readily runs Express apps. The project you just downloaded is an Express app, and you can run it by:

* First navigating to the project directory: `cd the/project/directory`
* And then running: `node server.js`

On the console you should see a message like _Server started. Open _[http://localhost:3000](http://localhost:3000)_ in your browser_. Navigate to `http://localhost:3000` on your browser. You should see the app's UI now.

Now that we are sure the app works, let's integrate it into Bolt. \(This is one of the great advantages of using Bolt: you can develop various parts of your app completely independent of the rest of the app, and integrate everything when ready.\)

To integrate the app into Bolt we have to install the app. The next few pages will guide us through the few steps involved.

