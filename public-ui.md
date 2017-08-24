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

If the files were uploaded successfully, the body of the response object should contain an array of objects, each object containing the `original` name of the file and the `url` to which the file was uploaded, as shown below:

![](/assets/local-upload.png)

Append each of the paths to the Bolt URL to get the files, as shown below:

![](/assets/local-upload-2.png)

Objects in the returned array may also contain the error field if an error occurs during uploads. For instance, if I attempt to upload to AWS S3 without internet connect, I can the below output:

![](/assets/local-upload-error.png)

If you are going to be running Bolt on a service like Heroku, you will want to [upload your files to AWS S3](/uploading-to-aws-s3.md). This is because a service like Heroku has an [ephemeral file system](/deploying-to-heroku/ephemeral-file-system.md).

\[insert pictures of post man and picture\]

