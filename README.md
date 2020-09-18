Notes for aws-certified-solutions-architect-associate exam
https://medium.com/towards-artificial-intelligence/aws-certified-solutions-architect-associate-exam-tips-2019-3fc034efdebe

https://gist.github.com/leonardofed/bbf6459ad154ad5215d354f3825435dc
http://www.cloudforest.in/2016/09/pass-aws-certification-exam-in-10-days.html


IAM
IAM is universal. It consists of users, groups, roles, policies
Root account is created during the first aws account, it has complete admin access.
New users have no permission when first created.
New users are assigned Access key ID and secret access keys when first created for programmatic access (API/Console access).
Always set up an MFA for root user and pwd rotation policies.
S3
Simple Storage system: Oldest aws service
Object based storage and allows you to upload files.
Each file can be 0 to 5 TB in size to upload and there is unlimited storage.
Files are stored in bucket which is basically a directory
Bucket name is unique across aws globally
HTTP 200 code is received when file upload is successful in S3.
S3 Guarantees 99.99 availability.
Storage Tiers: Standard, Intelligent, Standard-IA, One Zone IA, Glacier, Glacier deep Archive.
Not suitable to install OS on S3.
Key Fundamentals of S3 are
Key - name of object
Value - data made of sequences of bytes
Version ID - imp for versioning
Version ID - data about data
Subresources - ACLs, Torrents
Consistency Model - Read after write for PUTS of new objects & Eventual consistency for overwrite PUTS and DELETES
S3 storage classes
S3 standard - 99.99% availability, 99.999999999% durability, stored redundantly across multiple devices in multiple facilities. Most expensive.
S3 - IA - For data that is accessed less frequently but needs rapid access when needed. Lower fee than standard.
S3 One Zone - IA - lower cost option for infrequently accessed data, but does not require the multiple AZ data resilience.
S3 - Intelligent Tiering - optimize cost by automatically moving data to the most cost effective access tier, without performance impact or operational overhead.
S3 Glacier - low cost storage for data archiving.
S3 Glacier Deep Archive - lowest cost storage when retrieval time of 12 hours is acceptable.
Encryption in transit is achieved by SSL/TLS
Encryption at rest is achieved by S3 managed keys, AWS KMS, SSE-Customer provided key
S3 Prefixes - you can get better performance by spreading your reads across different prefixes. These are subfolders inside the buckets. 
Control access to buckets using bucket policies or bucket acls.
S3 lifecycle management allows you to automate moving objects between the different storage tiers and can be used in conjunction with versioning.
S3 Object lock & Glacier Vault lock
Store object using worm method - write once, read many
Helps prevent objects from being deleted.
Locks objects for regulatory requirements.
Two modes: Government and Compliance mode.
Sharing S3 buckets across aws accounts
Using bucket policies and iam
Cross account iam roles
Using bucket acls
S3 Cross Region replication
Versioning must be enabled on both source and destination buckets
Files in existing buckets are not replicated automatically
All subsequent updated files will be replicated
Delete operations are not replicated
Deleting individual or delete markers will not be replicated
S3 Transfer Acceleration - use edge location to transfer to s3 bucket faster
AWS Datasync - Used to move large amounts of data from on-premises to AWS using an agent. Can be used to replicate from EFS to EFS.
CloudFront - Content Distribution Network - used to cache your large contents closer to your customer locations
Edge Location - location where content will be cached. This is separate to aws regions/AZ
Origin - Origin of all files that the CDN will distribute. Can be either S3, EC2, ELB or route53.
Distribution - name given to to the CDN which consists of collection of edge locations
Web distribution - used for websites
RTMP - used for media streaming
Cloudfront signed urls and cookies
Use signed urls and cookies when you want to secure content so that only the people you authorize are able to access it.
A signed url is for individual files, 1 fille = 1 URL
A signed cookie is for multiple files. 1 cookie = multiple files
If you origin is ec2, then use cloudfront


Snowball
It is a petabyte-scale data transport solution.
Consider a snowball when data is more than 2 TB and not possible to transfer using the internet.
It can import to/from s3
Storage Gateway - Enables you to securely store data to the aws cloud for scalable and cost effective storage.
Three types of storage gateway - File Gateway (NFS & SMB); Volume Gateway (iSCSI); Tape Gateway (VTL)
File Gateway - for flat files. stored directly to s3
Volume Gateway - stored volume - whole data set is stored on site and synchronously backed up to s3; cached volume - entire data set is stored on s3 and frequently access data is cached on-site
Athena Vs Macie
Athena is an interactive query service to read data from s3 using standard sql . serverless, No ETL process, directly works with S3
Macie is an AI to detect any suspicious activity on S3, analyze data and identify PII (PII is personal data like credit card#, SSN, DOB, etc). Includes dashboard, reports and alerting.
Virtual style url for s3 contents puts your bucket name 1st, s3 2nd, and the region 3rd. Path style puts s3 1st and your bucket as a subdomain. Legacy Global endpoint has no region. S3 static hosting can be your own domain or your bucket name 1st, s3-website 2nd, followed by the region. AWS are in the process of phasing out Path style, and support for Legacy Global Endpoint format is limited and discouraged. However it is still useful to be able to recognize them should they show up in logs.
How many S3 buckets can I have per account by default: 100

EC2 - Elastic Compute Cloud
EC2 is a web service that provides resizable compute capacity in the cloud.
EC2 pricing model
On-demand - allows you to pay a fixed rate by the hour with no commitment
Reserved
Spot instances
Dedicated Hosts
