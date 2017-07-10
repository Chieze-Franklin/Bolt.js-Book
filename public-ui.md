# Public \(UI\)

This is a description of the UI endpoints exposed by the Bolt server for interacting with public files.

Public files are files that can be easily accessed by anyone, no authentication or authorization needed. Most of these files are created when registering a user or installing an app.

The following endpoints are described here:

* [GET: /public/\*](#get-public)
* [POST: /public/upload](#post-publicupload)

## GET: /public/\*

This returns the content of the appropriate public file.

## POST: /public/upload

Uploads a file or collection of files to Bolt.

## request

A standard [Bolt request](bolt-request.md).

The body is typically a `form` object containing the files to upload.

## response

If the files were uploaded successfully, the body of the response object should contain an array of the paths to which the files were uploaded, as shown below.

![](/assets/public-upload.png)

Append each of the paths to the Bolt URL to get the files, as shown below.

![](/assets/public-upload-2.png)

