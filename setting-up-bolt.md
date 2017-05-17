# Setting Up Bolt

[![Build Status](https://travis-ci.org/Chieze-Franklin/Bolt.js.svg?branch=master)](https://travis-ci.org/Chieze-Franklin/Bolt.js)

## Get Bolt

To get Bolt you need to download the compressed files, pull or clone it from its [GitHub repository](https://github.com/Chieze-Franklin/Bolt.js).

Bolt is built on Node.js, so ensure you have [Node](https://nodejs.org) \(and npm\) installed.

Bolt also relies on MongoDB, so ensure you have [MonogoDB](https://www.mongodb.com/) installed and running.

Set the following environment variables:

* PORT: Set this to the port on which the Bolt server will run. You do NOT set this on Heroku, as Heroku does that for you.
* MONGODB\_URI: Set this to your MongoDB URI, like 'mongodb://&lt;user&gt;:&lt;password&gt;@ds056789.mlab.com:56789/bolt' or 'mongodb://127.0.0.1:27017/bolt'.
* BOLT\_ADDRESS: Set this to the host on which Bolt is to run, like '[https://my-bolt-app.herokuapp.com](https://my-bolt-app.herokuapp.com)' or '[http://127.0.0.1:400](http://127.0.0.1:400)' \(no trailing slash '/', but include the http\(s\) protocol\).
* BOLT\_SESSION\_SECRET: Set this to a secret \(like a password\).

Set the following optional environment variables if you want to support running apps that are not system \(root\) apps \(Note that certain cloud services may no allow Bolt run apps this way\):

* BOLT\_PROTOCOL: Set to the appropriate http/https protocol.
* BOLT\_IP: Set to the IP address on which the Bolt server will be running.

After that, navigate to the root folder \(the folder containing _bolt.js_\) and run `npm install` to install dependencies.

Configure Bolt as required in /_sys/server/config.json_.

You can also specify what you want to happen during initial setup in /_sys/server/setup.json_.

Run `npm start` or `node bolt`.

On your browser, navigate to `{{BOLT_ADDRESS}}` \(or, if you set the optional environment variables, `{{BOLT_PROTOCOL}}://{{BOLT_IP}}:{{PORT}}`\)  to start working in the Bolt environment.

And that's all there is to it.

The rest of this book assumes you are running Bolt locally `localhost:400` or `127.0.0.1:400`.

## config.json

This file is located at _/sys/server/config.json_. This file contains configuration data that should be known before Bolt starts up. See [config.json](/setting-up-bolt/config.json.md).

## setup.json

This file is located at _/sys/server/setup.json_. This file determines the requests that should be sent to the Bolt server during inital setup. If you need to add default users or create predefined roles, this is where you do it. See [setup.json](/setting-up-bolt/setup.json.md).

## Setup View

The very first time you run Bolt you will be shown the setup view.

The setup view registers the first user with administrative privilege, and then presents all the steps listed in `setup.json` to the user, with the option to skip each step.

After that you are directed to `127.0.0.1:400/settings`. Since there may currently be no installed app that serves that endpoint, the native settings view will be shown to you. This view will encourage you to install the official settings app.

After installing the official settings app you will then be able to perform various administrative tasks like:

* Add new roles \(in addition to the admin role that was auto-created\).
* Add new users, and assign them roles. A user can be assigned more than one role.

* Install new apps. You can use this opportunity to install apps that serve common endpoints like `127.0.0.1:400/home`.



