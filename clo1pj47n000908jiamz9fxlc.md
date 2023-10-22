---
title: "Day 67: AWS S3 Bucket Creation and Management"
datePublished: Sun Oct 22 2023 16:52:50 GMT+0000 (Coordinated Universal Time)
cuid: clo1pj47n000908jiamz9fxlc
slug: day-67-aws-s3-bucket-creation-and-management
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1697993544355/8c41fbbc-ff9a-4df4-bcc6-bf5bedeee124.png
tags: aws, devops, terraform, 90daysofdevops, trainwithshubham

---

## [AWS S3 Bucket](https://github.com/LondheShubham153/90DaysOfDevOps/tree/master/2023/day67#aws-s3-bucket)

Amazon S3 (Simple Storage Service) is an object storage service that offers industry-leading scalability, data availability, security, and performance. It can be used for a variety of use cases, such as storing and retrieving data, and hosting static websites.

## [Task](https://github.com/LondheShubham153/90DaysOfDevOps/tree/master/2023/day67#task):

Create an S3 bucket using Terraform.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697991345026/810511f2-e310-4d6e-b80f-49c79d80deca.png align="center")

`provider "aws"` Block:

* This block specifies the provider you want to use, which is AWS in this case.
    
* `region = "ap-south-1"` specifies the AWS region where the resources will be created. In this case, it's the Asia Pacific (Mumbai) region.
    

`resource "aws_s3_bucket" "my_bucket"` Block:

* This block defines the creation of an AWS S3 bucket resource.
    
* `aws_s3_bucket` is the resource type, and `my_bucket` is the local name you assign to this resource for reference within your Terraform configuration.
    

`bucket = "day67taskbucket0304"`:

* This line specifies the name of the S3 bucket you want to create. The S3 bucket will be named "day67taskbucket0304."
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697991526254/4f77710c-eabc-4af6-815f-1ba4e70d22ed.png align="center")

It will create an execution plan by analyzing the changes required to achieve the desired state of your infrastructure with **terraform plan**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697991575121/3af6b938-7402-4622-938f-4a67975fb18d.png align="center")

Finally, it will apply the changes to create or update resources as needed with **terraform apply**.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697991917123/449eed98-64e5-4571-b471-fe7ce4b91db3.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697991991936/9edc9734-175b-4df2-9e4d-e66ae9072511.png align="center")

### **2\. Configure the bucket to allow public read access.**

```plaintext
resource "aws_s3_bucket_acl" "bucket_acl" {
  bucket = aws_s3_bucket.my_bucket.id
  acl    = "public-read"
}
```

To allow public read access to the S3 bucket, the code creates an ACL (access control list) resource using the "aws\_s3\_bucket\_acl" resource type. The resource is associated with the S3 bucket resource "aws\_s3\_bucket.my\_bucket" using the "bucket" parameter. The "ACL" parameter is set to "public-read", which allows public read access to the bucket.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697992034139/189a1405-b24b-4135-9a2c-acff72790689.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697992841333/09d7cf08-1aef-4046-a166-814d5bb3960e.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697993197703/b3c6a1ba-42b4-43aa-85e4-79f7ea461b25.png align="center")

### **4\. Create an S3 bucket policy that allows read-only access to a specific IAM user.**

```plaintext
resource "aws_s3_bucket_policy" "bucket_policy" {
  bucket = aws_s3_bucket.my_bucket.id
  policy = data.aws_iam_policy_document.allow_read_only_access.json
}


data "aws_iam_policy_document" "allow_read_only_access" {
  statement {
    principals {
      type        = "AWS"
      identifiers = ["683633011377"]
    }

    actions = [
      "s3:GetObject",
      "s3:ListBucket",
    ]

    resources = [
      aws_s3_bucket.my_bucket.arn,
      "${aws_s3_bucket.my_bucket.arn}/*",
    ]
  }
```

To provide read-only access to a specific IAM user or role, the code creates an S3 bucket policy resource using the "aws\_s3\_bucket\_policy" resource type. The resource is associated with the S3 bucket resource "aws\_s3\_bucket.my\_bucket" using the "bucket" parameter. The "policy" parameter is set to the Terraform data source "[data.aws](http://data.aws)\_iam\_policy\_document.allow\_read\_only\_access.json", which defines the policy document.

The policy document is created using the "data" block, which creates a Terraform data source.

The data source "aws\_iam\_policy\_document.allow\_read\_only\_access" defines a policy document that allows read-only access to the S3 bucket for a specific IAM user or role. The policy document is specified using JSON syntax.

The policy document has a single "statement" block, which defines the permissions to grant. The statement grants the "s3:GetObject" and "s3:ListBucket" permissions for the specified bucket and bucket objects. The "principals" block specifies the AWS user or role to which the permissions are granted. In this case, the "identifiers" field specifies the AWS account ID of the user or role to which read-only access is granted.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697993302169/608c5844-9cf0-4bb2-bed6-d075265bc961.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697993342094/60967b9c-0705-4c73-b3e7-9b819ca3a033.png align="center")

S3 bucket policy is created that allows read-only access to a specific IAM user.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697993444733/bd3a24a7-1b90-40c9-b388-2487c9b7a6cc.png align="center")

***Happy Learning!***