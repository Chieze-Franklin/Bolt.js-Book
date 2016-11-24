# Apps \(API\)

This is a description of the API exposed by the Bolt server for interacting with apps.

The following endpoints are described here:

\* \[POST: \/api\/app\/get\]\(\#post-apiappget\)

\* \[POST: \/api\/app\/reg\]\(\#post-apiappreg\)

\* \[POST: \/api\/app\/start\]\(\#post-apiappstart\)

\* \[POST: \/api\/app\/stop\]\(\#post-apiappstop\)

\* \[GET: \/api\/app-info\/:app\]\(\#get-apiapp-infoapp\)

\#\# POST: \/api\/app\/get

Installs an app from an online repository \(current only npm is supported\).

This endpoint is still experimental.

\#\# POST: \/api\/app\/reg

Installs an app from an local repository \(current only the node\_modules folder is supported\).

\#\#\#request

A standard \[Bolt request\]\(bolt-request\).

&lt;pre&gt;

{

 "path" : String \/\/the path of the folder contain the \*package.json\*, relative to the \*node\_modules\* folder

}

&lt;\/pre&gt;

\#\#\#response

\* If the app installed successfully, the &lt;code&gt;code&lt;\/code&gt; field of the response should be &lt;code&gt;0&lt;\/code&gt; and the &lt;code&gt;body&lt;\/code&gt; field of the response should hold an \[app object\]\(objects\#app\).

\* If the app did not install successfully, the &lt;code&gt;code&lt;\/code&gt; field of the response should not be &lt;code&gt;0&lt;\/code&gt; and the &lt;code&gt;error&lt;\/code&gt; field of the response should hold an \[error object\]\(objects\#error\).

\#\#\#security

Any app can send a request to this endpoint provided:

\* The user has granted the app \[permission to perform an installation\]\(user-permissions\#action.install\).

\* The user has administrative privileges.

\#\# POST: \/api\/app\/start

Starts the server of the app with the specified name.

\#\#\#request

A standard \[Bolt request\]\(bolt-request\).

&lt;pre&gt;

{

 "app" : String \/\/the name of the app to start

}

&lt;\/pre&gt;

\#\#\#response

\* If the app is found, the &lt;code&gt;code&lt;\/code&gt; field of the response should be &lt;code&gt;0&lt;\/code&gt; and the &lt;code&gt;body&lt;\/code&gt; field of the response should hold a \[context object\]\(objects\#context\).

 \* To know if a server was started for the app, check if their is a defined &lt;code&gt;port&lt;\/code&gt; field for the context object.

 \* To know if a server was started on another process, check if their is a defined &lt;code&gt;pid&lt;\/code&gt; field for the context object.

\* If the app is not found, the &lt;code&gt;code&lt;\/code&gt; field of the response should not be &lt;code&gt;0&lt;\/code&gt; and the &lt;code&gt;error&lt;\/code&gt; field of the response should hold an \[error object\]\(objects\#error\).

\#\#\#security

A check is made to see if the current user has the right to start an app. For startup apps, no such check is made.

\#\#\#note

Calling this endpoint multiple times for a particular app does not start multiple servers for it; if an app's server is already running a new one will &lt;b&gt;not&lt;\/b&gt; be started.

\#\# POST: \/api\/app\/stop

Stops the server of the app with the specified name.

\#\#\#request

A standard \[Bolt request\]\(bolt-request\).

&lt;pre&gt;

{

 "app" : String \/\/the name of the app to stop

}

&lt;\/pre&gt;

\#\#\#response

\* If the app is found to be running, the &lt;code&gt;code&lt;\/code&gt; field of the response should be &lt;code&gt;0&lt;\/code&gt; and the &lt;code&gt;body&lt;\/code&gt; field of the response should hold a \[context object\]\(objects\#context\).

\* If the app is not found to be running, the &lt;code&gt;code&lt;\/code&gt; field of the response should not be &lt;code&gt;0&lt;\/code&gt; and the &lt;code&gt;error&lt;\/code&gt; field of the response should hold an \[error object\]\(objects\#error\).

\#\#\#security

A check is made to see if the current user has the right to stop an app. For startup apps, no such check is made.

This is the same check made when starting an app. The rationale is that you should be able to stop only apps you have the right to start.

\#\#\#note

Although this may change, currently, trying to stop an app that is not running may return a \[Bolt response\]\(bolt-response\) with \[response code\]\(bolt-response-codes\) &lt;code&gt;420&lt;\/code&gt;. Code &lt;code&gt;420&lt;\/code&gt; means the port on which an app should be running cannot be found. The rationale is that you can only stop apps running on ports, so trying to stop an app that is not running \(for which no port can be found\) will result in an error with code &lt;code&gt;420&lt;\/code&gt;.

\#\# GET: \/api\/app-info\/:app

Gets the app info of the app with the specified name.

\#\#\#response

\* If the app is found, the &lt;code&gt;code&lt;\/code&gt; field of the response should be &lt;code&gt;0&lt;\/code&gt; and the &lt;code&gt;body&lt;\/code&gt; field of the response should hold an \[app object\]\(objects\#app\).

\* If the app is not found, the &lt;code&gt;code&lt;\/code&gt; field of the response should not be &lt;code&gt;0&lt;\/code&gt; and the &lt;code&gt;error&lt;\/code&gt; field of the response should hold an \[error object\]\(objects\#error\).

