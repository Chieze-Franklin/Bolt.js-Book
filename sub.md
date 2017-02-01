# Introducing Bolt

![](/assets/152.png)

## What is Bolt

Bolt is a JavaScript runtime environment for apps built on the ME\*N \(MongoDB-Express-Whatever-Node\) stack. Bolt works with any front-end technology, be it Angular \(MEAN\) or React \(MERN\). Bolt seeks to provide a rich environment containing all the features you need to run a ME\*N app. Bolt is NOT a framework. Bolt does NOT introduce new ways of building applications. There is no new JavaScript library/framework you need to learn. If your app can run on a browser then there is a very good chance it can run on Bolt. Bolt simply provides a rich everything your app needs to run in one neat box, from MongoDB to Socket.io, while handling common tasks \(like authentication, authorization, data storage, events, messaging, logging, ...\) on your behalf so that you get to focus on solving your real business problems. Bolt also makes it easy to develop your app in modules, handling module installation and uninstallation on your behalf.

## When should I use Bolt

* When creating complex apps with _many moving parts_. Bolt allows you to break an app into small pieces. Each piece can then be developed individually, with very little coupling between any two pieces. This makes your app more like a collection of _micro-apps_.
* When building multi-tenant apps, especially when different users are to have different roles. Bolt provides access control out of the box, reducing the work you have to do to ensure only authorized users access certain parts of the app.
* When you need to run the app both offline and online. This may mean that the app is used in a local area network \(like within a school or an office\) but has a cloud backup. Again, Bolt provides this with no extra effort on the part of the developer.
* When you need to deploy an app in batches. Not only does Bolt allow you to develop an app in batches, you can also deploy your app in batches. You can deploy your app with missing components and Bolt will still be able to present it to your users in a graceful manner. Missing components do not make the system crash; Bolt handles all exceptions with grace. This means you can start testing certain parts of your apps before other needed parts are ready.

* When you need to develop an app others can extend. Sometimes it may be better to give other developers the opportunity to extend your app by adding new features to it. Bolt supports this out-of-the-box with little or no effort on your part.

* When you need to extend other people's apps. With Bolt it is very easy to create plugins for other apps, and a plugin created for one Bolt app may work seemlessly on another Bolt app.

* When you want to use web technologies to work in a desktop-like environment.

* A typical example of a solution where you may consider using Bolt is an enterprise resource planning solution like a school management systems, hotel management system, hospital management system, just to name a few.

## Advantages of using Bolt

* Bolt serves as a scaffold for your app, handling tasks that are necessary but secondary to your business requirements, like user authentication, access control, local-remote synchronization...
* Bolt allows you to develop apps with losely-coupled components. This makes unit testing a lot easier, and generally means failure in one part of your app does not bring other parts down.
* Bolt makes it possible for you deploy your app in batches. You don't need a complete app before deployment, and the update process \(the process via which your users install missing components or replace existing components\) is very smooth. This process is largely dependent on the very popular and trusted Node Package Manager \(npm\) and does **not** require Bolt to be restarted.

* Bolt is highly customizable. You can built any kind of app on Bolt, from school management systems to runtime environments that look like operating systems. Certain core functionalities in Bolt can be handled by third-party components, which means you can override various default behaviours in Bolt.

* When you build plugins for a Bolt app you have the advantage of those plugins being reusable in other Bolt apps with little or no modification.

* Bolt does not care much about your development methodologies. It does not enforce the use of any design pattern, nor are you limited to any JavaScript front-end framework. So, build your app in any manner, from React to Angular to Ionic; if it can run on a browser then it can run on Bolt.

## What You Can Build with Bolt

In theory you can build about any kind of app with Bolt but Bolt really shines when you need to build enterprise-grade, multi-tenant, real-time, offline-first, cloud-aware apps. Concrete examples include:

* Content Management Systems \(CMS\)
* Chat apps
* Desktop-like environments



