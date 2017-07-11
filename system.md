# system

`system` \(default: false\) is a boolean field that determines if an app should have root privileges. This can be set at the point of installation or at any other point in time.

System apps run on the same port and the same process as the Bolt server. As such, they full access to Bolt, and can do pretty much anything. It then goes without saying that you should grant this privilege only to apps you trust.

Non-system apps run on new processes \(actually sub- or child-processes\) and on new ports.

Another difference between system apps and non-system apps is that system apps have access to all environment variables while sensitive environment variables \(like _MONGODB\_URI_ or _BOLT\_SESSION\_SECRET_ which may contain passwords\) are hidden from non-system apps.

A big advantage of system apps is that the request object that gets to a system app is the same request object that was modified by Bolt. Such a request object has a `bolt` field which contains the following fields \(amongst others\):

* _user_: When defined, this is an object representing the currently logged-in user.
* _session_: When defined this represents the current session between a client \(like a browser\) and the Bolt server. The session object also contains a `user` field which is also the currently logged-in user. So, as a system app, to get the currently logged-in user from the request object to your endpoint, you can do either `request.user` or `request.session.user`.

Another big advantage of system apps is that no new port or process is created in order to run them. This means they get to run on pretty much any hosting or cloud service that supports Node. You do not have to worry about the possibility of the service preventing you from creating new processes or opening new ports.

As a developer, how do you know if your app is running as a system app or not? Check for the variable `BOLT_CHILD_PROC`.

```
if (process.env.BOLT_CHILD_PROC) {
    console.log("I am running on a child process, therefore I am not currently a system app.");
} else {
    console.log("I am currently a system app.");
}
```

If an app is running as a non-system app, then its server may be located at `127.0.0.1:500`, where the port `500` was chosen for it. On the other hand, if an app is running as a system app, then its server is swallowed into the Bolt server, and it runs on the same port as Bolt. The server of such a system app may be located at \(assuming Bolt is running on port `400`\) `127.0.0.1:400/x/{{app-name}}`, where `app-name` is the name of the app.

