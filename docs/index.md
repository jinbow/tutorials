# PO.DAAC Tutorials

## Tutorial Table of Contents

All notebook tutorials can be found at <https://github.com/podaac/tutorials/tree/master/notebooks>

## FAQs

* [Can i browse PO.DAAC buckets directly from Amazon or through other AWS command line tools?](#can-i-browse-podaac-buckets-directly-from-amazon-or-through-other-aws-command-line-tool)
* Will datasets ever (always?) be stored in different s3 buckets?
* Is there a concept of "path" inside a bucket?

### Can I browse PO.DAAC buckets directly from Amazon or through other AWS command line tools

Not yet. We are working to iron out some permission issues and constraints on this feature, but hope to offer it soon. Many tools and data analysis kits are built for distributed access over many files in parallel, and we want to enable this same analysis on our data archive.

### Will datasets ever (always?) be stored in different s3 buckets?

Collection data are all stored in 1 of 3 buckets: private, protected, and public. Protected buckets are for data files which require Earthdata Login access. Public buckets store files which are things like metadata, browse images, documents and the like that don’t require Earthdata Login. Private buckets which are things that **no** users have access to, things like ‘bad granules’ can be moved here to prevent any user accessing. In reality, a single granule (data +  metadata) is actually split over multiple buckets: the data in protected buckets and the metadata in public buckets.

### Is there a concept of "path" inside a bucket?

The concept of a path does not exist in amazon S3. In AWS S3, you have a bucket and a key. When viewing an S4 bucket from the AWS Console, Amazon ‘fakes’ a path-like structure by visually separating a key with slashes (/) in it when you browse the data manually.PO.DAAC currently supports the collection short name in the key name, e.g. s3://bucket/collection_short_name/filename. In the future, we may end up adding something like shortname/year/doy/filename or shortname/cycle/filename to the key, as we gather information and understanding of how data are accessed by our users in the cloud. From a tooling standpoint, there is 0 difference by adding in those /path/ parts when using something like cmr, boto3 or any other AWS SDK to access to data
