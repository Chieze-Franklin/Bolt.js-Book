# Introducing Bolt

![](/assets/152.png)

## What is Bolt

Bolt is a runtime environment for web apps. Bolt seeks to provide a rich environment containing all the features you need to run a web app. If it can run on a browser then there is a very good chance it can run on Bolt.  Bolt is built on top of Node.js, so if it can run on Node then there is a very good chance it can run on Bolt too. Currently JavaScript apps are heavily supported \(via Node\) but there are plans to support apps that require other servers, like PHP apps.

## When should I use Bolt

* When creating complex apps. Bolt allows you to break an app into small pieces. Each piece can then be developed individually, with very little coupling between any two pieces.
* When you need to deploy an app in batches. Not only those Bolt allow you to develop an app in batches, you can also deploy your app in batches. You can deploy your app with missing components and Bolt will still be able to present it to your users in a graceful manner. Missing components do not make the system crash; Bolt handles all exceptions with grace. This means you can start testing certain parts of your apps before other needed parts are ready.

* When you need to develop an app others can extend. Sometimes it may be better to give other developers the opportunity to extend your app by adding new features to it. Bolt supports this out-of-the-box with little or no effort on your part.

* When you need to extend other people's apps. With Bolt it is very easy to create plugins for other apps, and a plugin created for one Bolt app may work seemlessly on another Bolt app.

* When you want to use web technologies to work in a desktop-like environment.


## Advantages of using Bolt

* Bolt serves as a scaffold for your app, handling tasks that are necessary for secondary to your business requirements, like user authentication, access control, local-remote synchronization...
* Bolt allows you to develop apps with losely-coupled components. This makes unit testing a lot easier, and generally means failure in one part of your app does not bring other parts down.
* Bolt makes it possible for you deploy your app in batches. You don't need a complete app before deployment, and the update process \(the process via which your users install missing components or replace existing components\) is very smooth. This process is largely dependent on the very popular and trusted Node Package Manager \(npm\).

* Bolt is highly customizable. You can built any kind of app on Bolt, from school management systems to runtime environments that look like operating systems. Certain core functionalities in Bolt can be handled by third-party components, which means you can override various default behaviours in Bolt.

* When you build plugins for a Bolt app you have the advantage of those plugins being reusable in other Bolt apps with little or no modification.

* Bolt does not care much about your development methodologies. It does not enforce the use of any design pattern, nor are you limited to any JavaScript framework \(although use of Express is encouraged\). So, built your app in any manner, from Express to Angular to ionic to React; if it can run on a browser then it can run on Bolt.


