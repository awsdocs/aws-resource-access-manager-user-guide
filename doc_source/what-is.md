# What is AWS Resource Access Manager \(AWS RAM\)?<a name="what-is"></a>

AWS Resource Access Manager \(AWS RAM\) helps you securely share the AWS resources that you create in one AWS account to other AWS accounts\. If you have multiple AWS accounts, you can create a resource once and use AWS RAM to make that resource accessible to those other accounts\. If your account is managed by AWS Organizations then you can share resources with all of the other accounts in the organization, or only those contained by one or more specified organizational units \(OUs\)\. You can also share with specific AWS accounts by account ID, whether the account is part of an organization or not\. [Some supported resource types](shareable.md) also let you share them with specified IAM roles and users\.

**Topics**
+ [Benefits](#what-is-features)
+ [How resource sharing works](#what-is-how)
+ [Service quotas](#what-is-limits)
+ [Accessing AWS RAM](#what-is-accessing)
+ [Pricing](#what-is-pricing)

## Benefits<a name="what-is-features"></a>

Why use AWS RAM? It offers the following benefits:
+ **Reduces your operational overhead**—Create a resource once, and then use AWS RAM to share that resource with other accounts\. This eliminates the need to provision duplicate resources in every account, which reduces operational overhead\.
+ **Provides security and consistency**—Simplify security management for your shared resources by using a single set of policies and permissions\. If you were to instead create duplicate resources in all of your separate accounts, you'd have the task of implementing identical policies and permissions, and then have to keep them identical across all of those accounts\. Instead, all users of a AWS RAM resource share are managed by a single set of policies and permissions\. AWS RAM offers a consistent experience for sharing different types of AWS resources\.
+ **Provides visibility and auditability**—View the usage details for your shared resources through the integration of AWS RAM with Amazon CloudWatch and AWS CloudTrail\. AWS RAM provides comprehensive visibility into shared resources and accounts\.

## How resource sharing works<a name="what-is-how"></a>

When you share a resource with another AWS account, you are granting access to principals in that account to the shared resource\. Any policies and permissions that apply to the account you shared the resource with also apply to the shared resource\. The resources in the share look like they are native resources in the AWS accounts you shared them with\.

### Sharing your resources<a name="what-is-how-sharing"></a>

With AWS RAM, you share resources that you own by creating a resource share\. When you create a resource share, you specify the following:
+ A name for the resource share\.
+ The resources that you want to grant access as part of this resource share\.
+ The principals to which you grant access to the resource share\. Principals can be individual AWS accounts, the accounts in an organization or an organizational unit \(OU\) in AWS Organizations, or individual IAM roles or users\.
**Note**  
Not all resource types can be shared with IAM roles and users\. For information about resources that you can share with these principals, see [Shareable AWS resources](shareable.md)\.
+ The AWS RAM permission to associate with each resource type\. This is an AWS managed permission policy that determines what the principals in the other accounts can do with the resources in the resource share\.

Your account retains full ownership of the resources that you share\.

### Using shared resources<a name="what-is-how-shared"></a>

When the owner of a resource shares it with your account, you can access the shared resource just as you would if it was owned by your account\. You can access the resource by using the relevant service's console, AWS CLI commands, and API actions\. The actions that principals in your account are allowed to perform vary depending on the resource type and are specified by the AWS RAM permission attached to the resource share\. All IAM policies and service control policies configured in your account also continue to apply, which enables you to leverage your existing investments in security and governance controls\.

## Service quotas<a name="what-is-limits"></a>

Your AWS account has the following limits related to AWS RAM\. You can request an increase for some of these limits\. To request a limit increase, contact [AWS Support](https://console.aws.amazon.com/support/home#/)\.


| Resource | Default limit | 
| --- | --- | 
|  Maximum number of resource shares per account  |  5,000  | 
|  Maximum number of shared principals per account  |  5,000  | 
|  Maximum number of shared resources per account  |  5,000  | 
|  Maximum number of pending invitations per account  |  20  | 

## Accessing AWS RAM<a name="what-is-accessing"></a>

You can work with AWS RAM in any of the following ways:

**AWS RAM console**  
AWS RAM provides a web\-based user interface, the AWS RAM console\. If you've signed up for an AWS account, you can access the AWS RAM console by signing into the [AWS Management Console](https://console.aws.amazon.com/) and choosing AWS RAM from the console home page\.  
You can also navigate in your browser directly to the [AWS RAM console](https://console.aws.amazon.com/ram/home)\. If you aren't already signed in, then you're asked to do so before the console appears\.

**AWS Command Line Interface \(AWS CLI\) and Tools for Windows PowerShell**  
The AWS CLI and Tools for PowerShell provide direct access to the AWS RAM public API operations\. They are supported on Windows, macOS, and Linux\. For more information about getting started, see the [AWS Command Line Interface User Guide](https://docs.aws.amazon.com/cli/latest/userguide/), or the [AWS Tools for Windows PowerShell User Guide](https://docs.aws.amazon.com/powershell/latest/userguide/)\. For more information about the commands for AWS RAM, see the [AWS CLI Command Reference](https://docs.aws.amazon.com/cli/latest/reference/) or the [AWS Tools for Windows PowerShell Cmdlet Reference](https://docs.aws.amazon.com/powershell/latest/reference/)\.

**AWS SDKs**  
AWS provides API commands for a broad set of programming languages\. For more information about getting started, see *[AWS SDKs and Tools Reference Guide](https://docs.aws.amazon.com/sdkref/latest/guide/)*\.

**Query API**  
If you don't use one of the supported programming languages, then the AWS RAM HTTPS Query API gives you programmatic access to AWS RAM and AWS\. The AWS RAM API lets you issue HTTPS requests directly to the service\. When you use the AWS RAM API, you must include code to digitally sign requests using your credentials\. For more information, see the [AWS RAM API Reference](https://docs.aws.amazon.com/ram/latest/APIReference/Welcome.html)\.

## Pricing<a name="what-is-pricing"></a>

There are no additional charges for using AWS RAM or for creating resource shares and sharing your resources across accounts\. Resource usage charges vary depending on the resource type\. For more information about how shareable resources are billed, refer to the documentation for the resource's owning service\.