# public

Bolt is designed around the idea of allowing developers to break large complex apps into smaller simpler parts, and develop those parts independently. However, sometimes these independent parts need to share resources. To allow for this cross-app resource sharing Bolt provides apps with the ability to mark certain files and\/or directories as public.

A simple way of declaring public files\/directories is by passing an array of the \(relative\) paths of such files\/directories to the `bolt.public` field.

`{`

`"bolt": {`

`"public": [ "favicon.ico", "assets", "lib/js" ]`

`}`

`}`

In this instance you are making the file _favicon.ico_, as well as the directories _assets_ and _lib\/js_, publicly accessible. During installation of your app these files and folders will be copied to a physical directory _public\/your-app-name_. Now any app can get your icon by sending a `GET` request to \(assuming Bolt is running on port 400\) `localhost:400/public/your-app-name/favicon.ico`. Assuming you had a file located at _assets\/img\/icon.png_, that file can be retrieved at  `localhost:400/public/your-app-name/assets/img/icon.png` . In similar fashion any app will be able to get and use the CSS, JS and other files you make public.

Sometimes you may want more control over how your public files\/directories are transferred to the _public\/your-app-name_ folder. In that case you need a more robust `public` field.

`{`

`"bolt": {`

`"public": {`

`"clean": true, //(default: false) if true empties/clears the public/your-app-name directory`

`"move": true, //(default: false) if true moves (instead of just copying) the public files/directories to the public/your-app-name directory`

`"overwrite": true, //(default: true) if true overwrites/replaces already-existing files in public/your-app-name with the new files being copied`

`"paths" :  [ "favicon.ico", "assets", "lib/js" ]`

`}`

`}`

`}`

