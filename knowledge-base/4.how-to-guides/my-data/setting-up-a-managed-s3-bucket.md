---
title: 'Setting Up a Managed S3 Bucket in Narrative'
description: 'Guide on creating and configuring a managed AWS S3 bucket for data ingestion into Narrative’s platform.'
lastUpdated: '2024-01-31'
tags: ['Selling Data', 'Ingesting Data']
---

### Introduction

After creating your dataset in Narrative, you might want to upload data directly or automate dataset deliveries for larger datasets or regular updates. This guide explains how to create a managed AWS S3 bucket within Narrative’s account for seamless data ingestion.

### Creating Your Managed S3 Bucket

#### **Step 1: AWS Account Setup**

Ensure you have an AWS account. If not, create one following [AWS’s account creation guide](https://aws.amazon.com/premiumsupport/knowledge-center/create-and-activate-aws-account/).

#### **Step 2: Generate a Bucket in Narrative**

1. **Source Type:** Select "Managed AWS S3 Bucket."
2. **Configuration:** Provide your 12-digit AWS Account ID, a Resource ID (e.g., your company name in lowercase), and choose your Access Type: **Bucket Policy** (default) or **Narrative-generated IAM role**. Optionally, for IAM role access, add an External ID for enhanced security. Review and click "Create."

#### **Step 3: Configure Bucket Access**

Configure access in your AWS console based on the selected Access Type:

- **Bucket Policy Access:** Directly grant access to specific AWS principals. Preferred for easier setup and granular access control.
- **Narrative-Generated IAM Role:** Narrative defines an IAM role for bucket access, which you then assign to a principal in your account.

### Access Types Explained

- **Bucket Policy:** Offers flexibility in defining access permissions. Ideal for direct object copying between buckets.
- **IAM Role:** Controlled by Narrative, requiring you to assign the role to your account’s principals. Does not allow direct `aws s3 cp` commands without additional setup.

#### Setting Up Bucket Policy Access

1. **Grant Access:** Follow AWS’s guide to [grant access to an Amazon S3 bucket](https://aws.amazon.com/blogs/security/writing-iam-policies-how-to-grant-access-to-an-amazon-s3-bucket/).
2. **Writing Data:** Ensure all uploads include the `--acl bucket-owner-full-control` flag to grant Narrative access.

Example AWS CLI command:

```shell
aws s3 cp file.csv s3://your-managed-bucket-name/your_directory/ --acl bucket-owner-full-control
```

### Setting Up IAM Role Access

**Grant User Access**
Assign the Narrative-provided IAM role to your AWS user or principal to enable access to the managed bucket.

**Configure Tools**
Update your AWS CLI configuration or AWS Console to utilize the assigned IAM role. For the AWS CLI, this involves adding a profile for the role in `~/.aws/config`.

#### **Example AWS CLI Configuration:**

```plaintext
[profile your-source-profile]
aws_access_key_id = YOUR_ACCESS_KEY
aws_secret_access_key = YOUR_SECRET_KEY

[profile your-bucket-profile-name]
role_arn = your-bucket-role-arn
source_profile = your-source-profile
```

To list the contents of your bucket using the configured profile, execute the following command:

```shell
aws s3 ls --profile your-bucket-profile-name s3://your-bucket-name/
```

### Next Steps

With your managed bucket successfully set up and accessible, you're poised to start the data ingestion process into Narrative.
