# module

`module` \(default: false\) is a boolean field that determines if an app is a full-blown app or just installed for the side effects its installation produces. Modules do not have user interfaces or servers, therefore they cannot be started or run. They are only installed because, like normal apps, their installation produces certain side effects. For instance, during installation modules can install routers, install hooks, define collections, create public files, etc.

A module cannot do the following:

* A module can't have a [main](/main.md)
* A module can't have an [index](/package-index.md)
* A module can't have startup privilege
* A module can't register [extensions](/extensions.md)
* Although a module can create [hooks](/hooks.md), they cannot be server hooks.
* A module can't have [permissions](/permissions.md)

If you define any of the following items listed above in your [package.json](/packagejson.md) for a module they will be ignored.

If all an app does is extend Bolt \(without having a UI of its own\), consider making it a module.

