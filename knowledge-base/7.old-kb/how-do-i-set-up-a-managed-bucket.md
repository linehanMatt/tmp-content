---
title: 'How do I set up a managed bucket?'
description: 'Use Dataset Manager to create a managed S3 bucket to push data to your datasets.'
lastUpdated: '2023-11-05T20:59:38.235Z'
tags: ['Selling Data', 'Ingesting Data']
---
### Overview

Once you've [created your dataset](https://kb.narrative.io/create-a-dataset) you can either use the UI to upload data to the bucket, or for larger datasets or regular dataset deliveries, you can create an AWS S3 bucket inside Narrative's account and use it as a destination for dataset ingestion deliveries. Creating an AWS S3 bucket managed by Narrative allows Narrative to read from the bucket and pull your data into our platform. 

Narrative offers two methods to permission yourself to write data to the bucket: **Bucket Policy** and **Narrative-generated IAM role**.  This article will guide you on how to select your access type, and how to create and access your bucket using each method.

### Overview of Synchronization Process

Using Dataset Manager you can to create your own managed S3 bucket by following these steps:

1.  Set up an AWS Account if you don't already have one.
2.  Generate an S3 Bucket using the Narrative UI.
3.  Set up bucket access using your AWS Account administrative console. 

#### Step 1: Set up an AWS Account

If you already have an AWS account you can skip this step, otherwise follow [the official AWS account creation guide](https://aws.amazon.com/premiumsupport/knowledge-center/create-and-activate-aws-account/).

The account will only be used to securely access your managed bucket.

Inside Dataset Manager, click on **Sources** in the navigation menu on the lefthand side of the page then **New Sources**.

#### Step 2: Generate a bucket in the Narrative UI

1.  **Source Type**
    
    The "Managed AWS S3 Bucket" option will be preselected for you.
    
2.  **Configuration**
    
    Configure your managed bucket.
    
    *   **AWS Account ID**: the 12 digit AWS account ID that will have access to your bucket. If you are having trouble finding this number consult [the AWS guide on account identifiers](https://docs.aws.amazon.com/general/latest/gr/acct-identifiers.html).
    *   **Resource ID**: a short identifier that will be a part of your bucket's name. A typical choice would be your company's name, lowercased and spaces replaced with -.
    *   **Access type:**
        *   Select **bucket policy** (default) or **IAM role.** For more about the differences, see below.
    *   **External ID** (Optional, lAM role only): If you are using role-based security, you can increase the security of your bucket by requiring external identifiers. [Learn more.](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_create_for-user_externalid.html?icmpid=docs_iam_console)
3.  **Create**
    
    Review your bucket configuration then click "Create".
    

#### Step 3: Set up Bucket Access

Once your managed bucket has been created you'll need to configure your AWS account to access it. How you do this will depend on whether you have selected **bucket policy** access or **Narrative-generated IAM Role** access. 

Read below for more information about both options and the directions to gain access to the Narrative managed bucket using each methodology. 

### Bucket Policy vs Narrative-Generated IAM Role

Narrative offers two methods to permission yourself to write data to the bucket: **Bucket Policy** and **Narrative-generated IAM role**.

In general, Narrative suggests using bucket access policy, as it is typically easier for you or your AWS administrator to configure and gives you more optionality when writing data to your bucket.

Read more for more about each option below:

**Bucket Policy Access (Default)**

**Role Access**

Customers can define access for any principal in their own AWS S3 account in any way that they want.

Narrative defines an AWS IAM role in Narrative's account, and then you permission that role to a principal in your account

Your team can define exactly how access to the bucket should be assigned and determine with any granularity which permissions should be assigned to which principals for the bucket.

Narrative controls the permissions that the role has, you can only assign that role to a specific principal in your account.

Allows \`aws s3 cp\` command from one bucket to another bucket (assuming your permissions allow it).

Does not allow \`aws s3 cp\` from one S3 bucket to another without additional configuration on your end.

Whenever you write data to the bucket, you MUST include a bucket ACL of \`bucket-owner-full-control\` on the object that is added (so Narrative can access the object you have written).

 

### Setting up Bucket Access: Bucket Policy Access

This is the recommended method to access your bucket, allowing you to maintain full control over which AWS principals have access to the bucket.

If you have selected “Bucket Policy Access”, your next step is to grant programmatic access or AWS Management Console access to Amazon S3 resources.

You can see AWS instructions for performing both of these actions here: [https://aws.amazon.com/blogs/security/writing-iam-policies-how-to-grant-access-to-an-amazon-s3-bucket/](https://aws.amazon.com/blogs/security/writing-iam-policies-how-to-grant-access-to-an-amazon-s3-bucket/).

Now, you or the specified principal in your AWS account can access the managed S3 bucket and write data to it.

#### Writing Data to an S3 Bucket with Bucket Policy Access

If you are using Bucket Policy Access, all files must be written to the Narrative bucket utilizing the following Access Control List (ACL):

\--acl bucket-owner-full-control

Any attempt to write data to the bucket without this ACL will result in a "permission denied" error. 

Here is an example of using the AWS "copy" command to add data to a bucket:

aws s3 cp --profile my-user file.csv s3://my-narratie-managed-bucket-rbmvd38/my\_directory/ --acl bucket-owner-full-control

#### Next Steps

Now that your managed bucket is set up and you can access it you are ready to start ingesting data into your datasets.

See our [guide for ingesting data using your managed bucket](https://kb.narrative.io/how-do-i-ingest-data-using-my-managed-bucket)

### Setting up Bucket Access: Narrative-Generated IAM Role Access

#### Narrative-Generated IAM Role Access

The example below gives an [IAM user](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users.html) access to a managed bucket but the same can be done for any group, role, etc. inside your AWS account: Narrative does not restrict who can use the role inside your account, giving you complete control over access management. The steps to follow are:

1.  Grant a user access to the role.
2.  Configure your tools to use the role. Examples for the following systems will be given:
    1.  AWS CLI
    2.  AWS Console

#### Prerequisite: Grant User Access

No matter which tool you plan to use to access your bucket the first step is to grant a user inside your account permission to use the role. Narrative does not restrict who can use the role inside your account so the same steps could be followed for any group, role, etc. inside your account.

**This step may require the assistance of an administrator of your AWS account** as it requires AWS IAM permissions.

*   Open the AWS IAM console at [](https://console.aws.amazon.com/iam/home#)[https://console.aws.amazon.com/iam](https://console.aws.amazon.com/iam)
*   Select the user that you want to be able to access your managed bucket.
*   Under the **Permissions** tab, click **Add inline policy**
*   On the **Create Policy** page, select the **JSON** tab and use the following policy definition:

{  
  "Version": "2012-10-17",  
  "Statement": \[  
    {  
      "Sid": "AssumeNarrativeBucketAccessRole",  
      "Effect": "Allow",  
      "Action": "sts:AssumeRole",  
      "Resource": \[  
        "BUCKET\_ROLE\_ARN"  
      \]  
    }  
  \]  
}

*   Substitute **BUCKET\_ROLE\_ARN** with the role ARN under your managed bucket on the Sources page in Dataset Manager.
*   Click **Review Policy**. On the following page give the role a name, e.g. "narrative-managed-bucket-access", and click **Create Policy**.

Now your user will be able access the role. Next we'll walk through configuring different tools to use the role.

### Example: Access via **the AWS CLI**

The AWS CLI can be used to access your managed bucket. If you've never used the AWS CLI before you'll need to:

*   Follow the installation instructions: [](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html)[https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html)
*   Perform initial configuration: [](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html)[https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html)

You can access your role by setting up a profile to automatically use the role when using the AWS CLI. This can be done by updating your configuration file (typically ~/.aws.config ) as follows:

\[profile SOURCE\_PROFILE\]  
aws\_access\_key\_id = ...  
aws\_secret\_access\_key = ...  
  
\[profile BUCKET\_PROFILE\_NAME\]  
role\_arn = BUCKET\_ROLE\_ARN  
external\_id = EXTERNAL\_ID  
source\_profile = SOURCE\_PROFILE

Substitute the following values in the example configuration:

*   **SOURCE\_PROFILE**: replace this with any named profile that contains IAM user credentials with permissions to use the role.
*   **BUCKET\_ROLE\_ARN**: use the role ARN under your managed bucket on the Sources page in Dataset Manager.
*   **EXTERNAL\_ID**: if you specified an external ID when creating your managed bucket then use it here, otherwise remove the line "external\_id = EXTERNAL\_ID" altogether.
*   **BUCKET\_PROFILE\_NAME:** the name you will pass on the command line to access your bucket, this can be anything you choose.

Now you can use the profile you just set up to access your bucket:

aws s3 ls --profile BUCKET\_PROFILE\_NAME s3://BUCKET\_NAME/

Where **BUCKET\_NAME** is the name of your managed bucket.

For a more detailed guide detailing how to configure the AWS CLI to use a role, [reference the official AWS guide](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-role.html).

### Example: Access via the AWS Console

You can use the AWS console to sign in as yourself then "switch roles" to gain access to your bucket. The "switch roles" action temporarily sets aside your original user permissions and instead gives you the permissions assigned to bucket role.

You **cannot** use the AWS console to access your bucket if you specified an external ID: this is a limitation of the AWS console.

#### **Identify Your Role's Name**

The first step is to identify your bucket role name using your role ARN. Your role ARN is of the form:

arn:aws:iam::NARRATIVE\_ACCOUNT\_ID:role/ROLE\_NAME

Where:

*   **NARRATIVE\_ACCOUNT\_ID** is Narrative's AWS account ID
*   **ROLE\_NAME** is the name of the role.

For example, if your role ARN is:

arn:aws:iam::123456789012:role/nio-example-t2pxc2uync7h-access

Then the **ROLE\_NAME** is "nio-example-t2pxc2uync7h-access".

#### **Configure the Console to Switch Roles**

Sign in to your AWS account as a user who access to the role (see **Prerequisite: Grant User Access)**. The next step is to configure the console so that you switch roles.

First, choose your user name on the navigation bar in the upper right and select **Switch Roles**.![](https://solutions.narrative.io/hubfs/undefined-Jun-13-2022-08-32-08-11-PM.png)

You'll be presented with the following form:

![](https://solutions.narrative.io/hubfs/undefined-Jun-13-2022-08-32-07-86-PM.png)  
Use the following values:

*   **Account**: use the value "narrative-io"
*   **Role**: use your **ROLE\_NAME**, found in the previous step.
*   **Display Name**: enter text that you want to appear on the navigation bar in place of your user name when this role is active.

Click **Switch Role**. You'll see your chosen **Display Name** on the navigation bar in the upper right indicating you successfully switched to the bucket access role.

#### **Access Your Bucket**

To access your bucket in the S3 console, you'll have to follow a link directly to your bucket and will be unable to access it from the S3 console home page. Your direct link looks like the following:

https://s3.console.aws.amazon.com/s3/buckets/BUCKET\_NAME/

Where **BUCKET\_NAME** is substituted with the name of your managed bucket. We suggest bookmarking this link for your convenience.

The requirement to follow a direct link is a limitation of console when accessing S3 buckets in third party accounts.

For official guidance on assuming a role and information on how to _stop_ using a role inside the AWS console, reference [the official guide](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_use_switch-role-console.html).

#### Next Steps

Now that your managed bucket is set up and you can access it you are ready to start ingesting data into your datasets.

See our [guide for ingesting data using your managed bucket](https://kb.narrative.io/how-do-i-ingest-data-using-my-managed-bucket)
