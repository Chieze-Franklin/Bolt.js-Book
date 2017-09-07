# Deploying to Heroku

One of the easiest ways to run Bolt online is to deploy to a cloud service like [Heroku](https://www.heroku.com).

The steps are follow here are similar to those listed in [Setting Up Bolt](/setting-up-bolt.md).

Bolt also relies on MongoDB, so ensure you have [MonogoDB](https://www.mongodb.com/) up and running. Since this is an online deployment, you will be using one of the numerous MongoDB cloud service providers, like [mlab](https://mlab.com). After you successfully provision a MongoDB database instance and create a user with read-write access to the database, you should be given a connection string, usually following format: `mongodb://<user>:<password>@ds056789.mlab.com:56789/bolt`.

In the end Bolt is just a Node.js app, and you deploy it to Heroku like you deploy any other Node app. See this [article](https://devcenter.heroku.com/articles/deploying-nodejs) for help.

Next you set up environment variables. I have deployed a Bolt instance to Heroku under the name _guarded-journey-25495_. The app is now available at [https://guarded-journey-25495.herokuapp.com](https://guarded-journey-25495.herokuapp.com).

![](/assets/heroku-home.png)

Navigate to your Heroku [dashboard](https://dashboard.heroku.com/) and click on the app.

![](/assets/heroku-dashboard.png)

Click on **Settings**, then **Reveal Config Vars** to view and create environment variables.

![](/assets/heroku-settings.png)

You can see that I have created the necessary environment variables. Notice the variable _MONGODB\_URI_ which points to an online MongoDB instance being hosted by [mlab](https://mlab.com).

![](/assets/heroku-config.png)

On the terminal/console, execute the following commands to deploy on Heroku:

* `heroku config:set NODE_MODULES_CACHE=false` :  This command is optional. Execute it if you want Heroku to recreate the _node\_modules_ folder instead of using a cached version. Note that this may not be what you want, especially when syncing local deployment with Heroku deployment.
* `heroku features:enable http-session-affinity` : This command is necessary because Bolt makes use of the _socket.io_ module.
* `git commit -am '{{message}}'` : Commit your changes. You can add the `--allow-empty` option to this command to make an empty commit.
* `git push heroku master` : Push to Heroku.
* `heroku config:unset NODE_MODULES_CACHE` : This command is optional. Execute it if you want  to unset \(reset?\) the configuration variable `NODE_MODULES_CACHE` which you may have set to `false` a few lines above.



