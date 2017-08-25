# Uploading to AWS S3

Bolt has first-class support for uploading files to Amazon Web Services [Simple Storage Service](/docs.aws.amazon.com/AmazonS3/latest/dev/Welcome.html) \(AWS [S3](https://aws.amazon.com/s3/)\). This is necessary because some of the environments on which Bolt runs have [ephemeral file systems](/deploying-to-heroku/ephemeral-file-system.md).

### Setting Up Bolt for AWS S3

The fine details of setting up your AWS S3 are beyond the scope of this book but there is more than enough material on it online.

* In your S3 account [create a bucket](http://docs.aws.amazon.com/AmazonS3/latest/gsg/CreatingABucket.html) to which Bolt will upload files. Note the name and the region of the bucket.
* [Create an IAM user](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_create.html) for Bolt. Note the _Access Key ID_ and the _Secret Access Key_. The IAM user should have the right to upload files to your bucket.
* Create the environment variable `AWS_ACCESS_KEY_ID` to hold the access key ID mentioned above.
* Create the environment variable `AWS_SECRET_ACCESS_KEY` to hold the secret access key mentioned above.
* Create the environment variable `S3_BUCKET` to hold the name of the bucket.
* Create the environment variable `S3_REGION` to hold the region of the bucket.

You can find a list of AWS regions [here](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-regions-availability-zones.html). Bolt signs requests to AWS S3 with [signature version 4](http://docs.aws.amazon.com/general/latest/gr/signature-version-4.html), so please use regions that support signature version 4 authentication \(which is [pretty much every region](http://support.s3mediamaestro.com/article/177-bucket-regions-and-aws-signature-version-4)\) . Now Bolt will upload files to your S3 buckets. The URL of such files are in the format: `https://s3.<region>.amazonaws.com/<bucket>/<file name randomly set by Bolt>`.

## note

Uploading to AWS S3 has been tested against only one region, us-east-2, which is US East \(Ohio\).

