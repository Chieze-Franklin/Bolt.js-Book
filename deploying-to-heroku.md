# Deploying to Heroku

One of the easiest ways to run Bolt online is to deploy to a cloud service like [Heroku](https://www.heroku.com).

The steps are follow here are similar to those listed in [Setting Up Bolt](/setting-up-bolt.md).

Bolt also relies on MongoDB, so ensure you have [MonogoDB](https://www.mongodb.com/) up and running. Since this is an online deployment, you will be using one of the numerous MongoDB cloud service providers, like [mlab](https://mlab.com). After you successfully provision a MongoDB database instance and create a user with read-write access to the database, you should be given a connection string, usually following format: `mongodb://<user>:<password>@ds056789.mlab.com:56789/bolt`.

Create a heroku app

Set up environment variables

On the terminal/console, execute the following commands:

* `heroku config:set NODE_MODULES_CACHE=false` :  This command is optional. Execute it if you want Heroku to recreate the _node\_modules_ folder instead of using a cached version.
* `heroku features:enable http-session-affinity` : This command is necessary because Bolt makes use of the _socket.io_ module.
* `git commit -am '{{message}}'` : Commit your changes. You can add the `--allow-empty` option to this command to make an empty commit.
* `git push heroku master` : Push to Heroku.
* `heroku config:unset NODE_MODULES_CACHE` : This command is optional. Execute it if you want  to unset \(reset?\) the configuration variable `NODE_MODULES_CACHE` which you may have set to `false` a few lines above.



