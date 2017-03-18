# The App Server

The app server is a regular Node server, usually built using Express \(other Node frameworks may be supported in the future, most especially Sails\). In the app server you do **NOT** specify the port you want the server to run on; Bolt will choose a port dynamically during runtime.

Refer to the [bolt.main](/main.md) field of the [package.json](/packagejson.md) file to see how the app server is used.



