# files

`files` is simply an object in which each key/field specifies a name and the corresponding value specifies the \(relative\) path of the file that name refers to.

An example to make this clearer.

Apps are expected to define a file called _icon_. \(Another expected file is _index_.\)

`{`

`"bolt": {`

`"files": {`

`"icon": "assets/img/icon.png",`

`"index": "views/home.html"`

`}`

`}`

`}`

To get the icon for the app now becomes as simple as \(assuming Bolt is running on port 400\) `localhost:400/files/your-app-name/icon`. This will fetch the appropriate [public](/public.md) file, in this case `localhost:400/public/your-app-name/assets/img/icon.png`.

### A Little Tip for You

Note that all files exposed by the app must be [public](/public.md) files.

