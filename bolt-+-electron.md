# Bolt + Electron

You can run Bolt on [Electron](https://electron.atom.io/).

* First, ensure you have Electron installed. A simple `npm i electron` will do. You can install Electron globally or locally.
* Ensure the Bolt server is up and running.

* In the Bolt directory run `electron .` \(if you installed Electron globally\) or `.\node_modules.bin\electron .` \(if you installed Electron locally\) to run Bolt in Electron. Alternatively you can run `npm run start-in-electron` to run Bolt in Electron.

### jQuery and Electron

JQuery doesn't play well with Electron. To make jQuery work well with Electron:

* Include this script before importing jQuery into your web page: `<script>if (typeof module === 'object') {window.module = module; module = undefined;}</script>`
* Include this script after importing jQuery into your web page: `<script>if (window.module) module = window.module;</script>`

So, you may have something like this:

![](/assets/jquery+electron.png)



