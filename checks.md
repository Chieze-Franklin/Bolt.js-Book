# checks

`checks` is simply an array of files whose integrity you want to monitor. Before your app starts Bolt checks to be sure non of the files have been modified. If any is seen to have been modified your app will not be started.

Currently Bolt checks the integrity of the files only during app startup but later versions will continuously monitor the files, taking appropriate actions when such files are seen to have been tampered with.

### Note

Note that only _local files_ \(files in the app's folder in the Bolt _node\_modules_ folder\) are checked. [Public](/public.md) files are not checked. So, before including a file in the `checks` array, be sure it will not be **moved** to the Bolt _public_ folder.

