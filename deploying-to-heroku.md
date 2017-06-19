# Deploying to Heroku

One of the easiest ways to run Bolt online is to deploy to a cloud service like [Heroku](https://www.heroku.com).

The steps are follow here are similar to those listed in [Setting Up Bolt](/setting-up-bolt.md).

Bolt also relies on MongoDB, so ensure you have [MonogoDB](https://www.mongodb.com/) up and running. Since this is an online deployment, you will be using one of the numerous MongoDB cloud service providers, like [mlab](https://mlab.com). After you successfully provision a MongoDB database instance and create a user with read-write access to the database, you should be given a connection string, usually following format: mongodb://&lt;user&gt;:&lt;password&gt;@ds056789.mlab.com:56789/bolt.

