# Ephemeral File System

There are many articles out there that explain [how Heroku works](https://devcenter.heroku.com/articles/how-heroku-works). Heroku runs Bolt on a [dyno](https://devcenter.heroku.com/articles/dynos), which is like a lightweight Linux container. The file system in a dyno is temporary, implying that what ever files are created or uploaded on that dyno will be lost eventually. This has 2 significant implications:

1. You can't install or update an app from an online repository like npm while running on Heroku. The app's source code and public files will be lost eventually. We are hard at work to find the best solution to this problem but, for now, you should do all installations and updates on your local Bolt instance, and then push it to Heroku. More on this later.
2. You can't [upload files](/public-ui.md) to Bolt while running on Heroku. Such files will be lost eventually. However, Bolt has built-in support for [uploading to AWS S3 buckets](/uploading-to-aws-s3.md).



