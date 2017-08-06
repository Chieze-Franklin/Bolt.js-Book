# Apps Without Servers

Bolt has limited support for apps without servers.

If your app has no server but needs to render a GUI, follow the steps below:

1. Ensure the index file is public. This means it should be one of the files copied to your app's [public](/public.md) directory.
2. Give it the name _**index**_ in your named public [files](/files.md).

Assuming that the first file you want to render is _home.html_, located in _views_ folder which itself is in your root folder, your package.json should look something like this:

```
{
    "bolt": {
        "public": [ "views/home.html" ] //or simply "public": [ "views" ] to make the entire "views" folder public
        "files": {
            "index": "views/home.html"
        }
    }
}
```

When one attempts to run your app by typing \(assuming Bolt is running on port 400\) `localhost:400/apps/your-app-name`, Bolt will redirect the request to `localhost:400/files/your-app-name/index`. This will fetch the file with the name **index** which in this case is _views/home.html_. Bolt will then render the public file with that path `localhost:400/public/your-app-name/views/home.html`. You may also need to ensure that all dependencies of this file \(_views/home.html_\) are also publicly accessible.

