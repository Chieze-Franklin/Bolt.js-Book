# Publishing the App

Different platforms have their various _app stores_ where developers publish their apps so consumers can download and install them. So does Bolt. However, Bolt hasn't built an entirely new app store but uses a popular source code repository called [npm](https://npmjs.com/). Originally npm is typically used to distribute JavaScript _modules_ used in Node-based applications. This is where you will [publish your Bolt apps](https://docs.npmjs.com/getting-started/publishing-npm-packages) to.

Recall that on the install view \(`localhost:400/install`, assuming Bolt is running on port 400\) there are two ways to install an app: **Download** and **Sideload**. We treated sideloading [earlier](/installing-the-app.md). When you choose to download, you are choosing to download the app directly from the npm online repository. This is a much better option than sideloading because:

* You always get the most current version of the app.
* You get a copy of the app that hasn't been altered by the wrong party.
* Along with the app comes every module it depends on.

However, the option of sideloading is there to make the transfer of already downloaded apps possible. Just make sure the files aren't altered in any way.

