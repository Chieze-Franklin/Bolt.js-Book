# Apps Without Servers

Bolt has limited support for apps without servers.

If your app has no server but needs to render a GUI, follow the steps below:

1. Ensure the index file is public. This means it should be one of the files copied to your app's [public](/public.md) directory.

Also ensure the index file is one your public files...

More on this later.

Bolt will redirect \/apps\/:name to \/files\/:name\/index...

