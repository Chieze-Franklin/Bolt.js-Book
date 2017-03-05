# config.json

This file is located at _/sys/server/config.json_. This file contains configuration data that should be known before Bolt starts up.

Most of the fields in this file are self-explanatory. The most important fields are:

* `host`: This is the host \(address\) the Bolt server should run on. If running Bolt locally on a single machine, this could be `"127.0.0.1"`.
* `port`: This is the port the Bolt server should run on.
* `protocol`: This is the protocol via which the Bolt server will be accessed.
* `dbHost`: This is the host the database supporting Bolt \(usually MongoDB\) should run on.
* `dbPort`: This is the port the database should run on.



