# Setting Up Bolt

## Get Bolt

Bolt is built on Node.js, so ensure you have Node \(and npm\) installed.

To get Bolt you need to download the compressed files, pull or clone it from its [GitHub repository](https://github.com/Chieze-Franklin/Bolt.js).

After that, navigate to the root folder \(the folder containing _bolt.js_\) and run `npm install` to install dependencies.

Download the appropriate MongoDB files into the appropriate folder in _\/sys\/bins\/mongodb_.

Ensure the path _\/sys\/data\/mongodb_ exists.

Configure Bolt as required in \/_sys\/server\/config.json_.

Run `node bolt`.

On your browser, navigate to `{{config-host}}:{{config-port}}` to start working in the Bolt environment. Using the default config values, that should be `localhost:400`. \(The remainder of this book will use `localhost:400` as the default location of Bolt.\)

And that's all there is to it.

## Setup View

The very first time you run Bolt you will be shown the setup view.

The setup view registers the first user with administrative privilege.

After that you are directed to `localhost:400/settings`. Since there may currently be no installed app that serves that endpoint, the native settings view will be shown to you. This view will encourage you to install the official settings app.

After installing the official settings app you will then be able to perform various administrative tasks like:

* Add new roles \(in addition to the admin role that was auto-created\).
* Add new users, and assign them roles. A user can be assigned more than one role.

* Install new apps. You can use this opportunity to install apps that serve common endpoints like `localhost:400/home`.


