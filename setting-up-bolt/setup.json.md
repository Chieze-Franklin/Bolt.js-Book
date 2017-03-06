# setup.json

This file is located at _/sys/server/setup.json_. This file determines the requests that should be sent to the Bolt server during inital setup. If you need to add default users or create predefined roles, this is where you do it.

This file consists of 2 main fields:

* `redirect`: This is the endpoint to which the user is redirected after all the setup steps have been run.
* `steps`: This is an array of steps that will be presented to the user during setup. Each step consists of:
* * `title`: This is presented to the user as the title of the step.
  * `message`: This explains what that step accomplishes.
  * `requests` or `requestsSync`: This is an array of requests to be sent to the Bolt server if the user chooses to run the step. The requests can be sent asychronously \(`requests`\) or synchronously \(`requestsSync`\). Each request consists of:
  * * `method`: Any supported `HTTP` method \(like `GET` or `POST`\) with which the request is to be sent.
    * `endpoint`: The endpoint to which the request is to be sent, for instance `/api/apps`.
    * `body` \(optional\): The JSON body of the request.



