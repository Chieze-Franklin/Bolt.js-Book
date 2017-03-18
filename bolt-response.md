# Bolt Response

Bolt always returns a JSON response \(except for the UI endpoints which return HTML responses\). Every such response is returned with a HTTP status code of 200. This means that if the request got to Bolt, the response would containing status code 200. Every JSON response contains the following fields:

* \[code\]\(\#code
  \)
* ~~type~~
* ~~message~~

If a response body is to be returned to the user, the JSON response will contain the following fields:

* \[body\]\(\#body
  \)

If an error occurs during the processing of a request, the JSON response will contain the following fields:

* [error](#error)
* errorTraceId
* errorUserTitle
* errorUserMessage

### body

This is the actual body of the response \(every other field can be viewed as meta-data\). It may be undefined if the endpoint called does not return a body.

### code

This field contains the [Bolt response code](/bolt-response-codes.md) of the response.

### error

This field contains the error object that was thrown during the processing of a request. It may be undefined if no error was thrown.

### errorTraceId

This field contains a value that can be used to locate the trace log for the error thrown. It may be undefined if no error was thrown or if the version of the Bolt server in use does not support it.

### errorUserMessage

This field contains a message that can be displayed to the user in the event of an error. The language of the message is based on the locale of the [Bolt request](/bolt-request.md). It may be undefined if no error was thrown or if the version of the Bolt server in use does not support it.

### errorUserTitle

This field contains a short title that can be displayed to the user in the event of an error. The language of the title is based on the locale of the [Bolt request](/bolt-request.md). It may be undefined if no error was thrown or if the version of the Bolt server in use does not support it.

