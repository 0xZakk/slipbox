# Amazon Simple Storage Service

## Meta Data

Source:  kindle 
Author: Amazon Web Services

## Highlights

### Highlights

- Amazon S3 has a simple web services interface that you can use to store and retrieve any amount of data, at any time, from anywhere on the web.
- Overview of Amazon S3 and this guide
- Amazon S3 has a simple web services interface that you can use to store and retrieve any amount of data, at any time, from anywhere on the web.
- Advantages of using Amazon S3
- Creating buckets – Create and name a bucket that stores data. Buckets are the fundamental containers in Amazon S3 for data storage.
- Storing data – Store an infinite amount of data in a bucket. Upload as many objects as you like into an Amazon S3 bucket. Each object can contain up to 5 TB of data. Each object is stored and retrieved using a unique developer-assigned key.
- Downloading data – Download your data or enable others to do so. Download your data anytime you like, or allow others to do the same.
- Permissions – Grant or deny access to others who want to upload or download data into your Amazon S3 bucket. Grant upload and download permissions to three types of users. Authentication mechanisms can help keep data secure from unauthorized access.
- Amazon S3 concepts
- Buckets
- A bucket is a container for objects stored in Amazon S3. Every object is contained in a bucket.
- Buckets serve several purposes: They organize the Amazon S3 namespace at the highest level. They identify the account responsible for storage and data transfer charges. They play a role in access control. They serve as the unit of aggregation for usage reporting.
- Objects are the fundamental entities stored in Amazon S3.
- Objects consist of object data and metadata.
- The data portion is opaque to Amazon S3. The metadata is a set of name-value pairs that describe the object.
- An object is uniquely identified within a bucket by a key (name) and a version ID.
- A key is the unique identifier for an object within a bucket. Every object in a bucket has exactly one key.
- The combination of a bucket, key, and version ID uniquely identify each object. So you can think of Amazon S3 as a basic data map between "bucket + key + version" and the object itself.
- You can choose the geographical AWS Region where Amazon S3 will store the buckets that you create.
- You might choose a Region to optimize latency, minimize costs, or address regulatory requirements.
- Amazon S3 provides read-after-write consistency for PUTS of new objects in your S3 bucket in all Regions with one caveat. The caveat is that if you make a HEAD or GET request to a key name before the object is created, then create the object shortly after that, a subsequent GET might not return the object due to eventual consistency.
- Updates to a single key are atomic. For example, if you PUT to an existing key, a subsequent read might return the old data or the updated data, but it never returns corrupted or partial data.
- Buckets have a similar consistency model, with the same caveats.
- Amazon S3 features
- Amazon S3 offers a range of storage classes designed for different use cases. These include Amazon S3 STANDARD for general-purpose storage of frequently accessed data, Amazon S3 STANDARD_IA for long-lived, but less frequently accessed data, and S3 Glacier for long-term archive.
- Bucket policies provide centralized access control to buckets and objects based on a variety of conditions, including Amazon S3 operations, requesters, resources, and aspects of the request (for example, IP address).
- The policies are expressed in the access policy language and enable centralized management of permissions. The permissions attached to a bucket apply to all of the objects in that bucket.
- Accounts have the power to grant bucket policy permissions and assign employees permissions based on a variety of conditions. For example, an account could create a policy that gives a user write access: To a particular S3 bucket From an account's corporate network During business hours
- You can use AWS Identity and Access Management (IAM) to manage access to your Amazon S3 resources.
- You can control access to each of your buckets and objects using an access control list (ACL).
- You can use versioning to keep multiple versions of an object in the same bucket.
- Amazon S3 application programming interfaces (API)
- The Amazon S3 architecture is designed to be programming language-neutral, using AWS supported interfaces to store and retrieve objects.
- Amazon S3 is a REST service. You can send requests to Amazon S3 using the REST API or the AWS SDK (see Sample Code and Libraries) wrapper libraries that wrap the underlying Amazon S3 REST API, simplifying your programming tasks.
- The account access keys provide full access to the AWS resources owned by the account.