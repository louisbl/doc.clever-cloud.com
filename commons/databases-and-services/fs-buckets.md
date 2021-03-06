---
title: File System Buckets
position: 3
---
## FS Buckets: keep and manage data files <span class="cc-beta pull-right" title="Currently in Beta version"></span>

<div class="alert alert-hot-problems">
  <h5>Note for Beta Version</h5>
  <div>FS Buckets are free during the beta period. No credits will be charged.</div>
</div>

When you deploy an application on any PaaS, a new application is created, the previous is deleted. If your application generates data, for example if you let users upload pictures and you do not store it on external services like S3, you will loose data.

The Git deployment does not allow you to keep generated data files between deployments. To avoid the loss of your data, you have to mount a persistent filesystem. This is why we created File System Buckets.

You will be able to retrieve generated data between two deployments.

### Create a FS Bucket

[This article](/databases-and-services/add-service/) describes the process to add a File System Bucket on Clever Cloud.


### Configure your application

To configure your application to use buckets, use the
`clevercloud/buckets.json` file.

The `clevercloud` folder must be located at the root of your application.

The `buckets.json` file must contain the following structure:

```javascript
[
  {
    "bucket" : "bucketId",
    "folder" : "/myFolder"
  }
]
```


It's a json array containing objects with two fields:

* **bucket**
: The bucket id you received by email which begins with `bucket_`.

* **folder**
: The folder you want the bucket to be mounted in. Using the example
*myFolder*, you can access your buckets via the *myFolder* folder at
the root of your application or via */app/myFolder*.

<div class="alert alert-hot-problems">
  <h5>Important note about target folder</h5>
  <p>
    If the folder **already exists** and is not empty nor is an **existing directory**, the mount of your bucket will be ignored.
  </p>
</div>

### Video demo
<p>
  <iframe style="width:640px" height="360" src="http://www.youtube.com/embed/6rJ8zQqIhUw?rel=0&autohide=1&showinfo=0" frameborder="0" controls="0"  allowfullscreen="allowfullscreen"> </iframe>
</p>