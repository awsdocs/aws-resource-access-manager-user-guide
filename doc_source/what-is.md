# What is AWS Resource Access Manager?<a name="what-is"></a>

AWS Resource Access Manager \(AWS RAM\) helps you securely share the AWS resources that you create in one AWS account with all of the roles and users in that same account, or with other AWS accounts\. If you have multiple AWS accounts, you can create a resource once and use AWS RAM to make that resource usable by those other accounts\. If your account is managed by AWS Organizations, then you can share resources with all the other accounts in the organization, or only those accounts contained by one or more specified organizational units \(OUs\)\. You can also share with specific AWS accounts by account ID, regardless of whether the account is part of an organization\. [Some supported resource types](shareable.md) also let you share them with specified IAM roles and users\.

**Topics**
+ [Video overviews](#video-intros)
+ [Benefits](#what-is-features)
+ [How resource sharing works](#what-is-how)
+ [Service quotas](#what-is-limits)
+ [Accessing AWS RAM](#what-is-accessing)
+ [Pricing](#what-is-pricing)
+ [Compliance and international standards](#certification)

## Video overviews<a name="video-intros"></a>

The following video provides a brief introduction to AWS RAM and describes how to create a resource share\.



The following video demonstrates how AWS RAM managed permissions let you apply the best practice of least privilege access to your AWS resources\.



## Benefits<a name="what-is-features"></a>

Why use AWS RAM? It offers the following benefits:
+ **Reduces your operational overhead** – Create a resource once, and then use AWS RAM to share that resource with other accounts\. This eliminates the need to provision duplicate resources in every account, which reduces operational overhead\. Within the account that owns the resource, it simplifies granting access to every role and user in that account without having to use identity\-based permission policies\.
+ **Provides security and consistency** – Simplify security management for your shared resources by using a single set of policies and permissions\. If you were to instead create duplicate resources in all your separate accounts, you would have the task of implementing identical policies and permissions, and then have to keep them identical across all those accounts\. Instead, all users of an AWS RAM resource share are managed by a single set of policies and permissions\. AWS RAM offers a consistent experience for sharing different types of AWS resources\.
+ **Provides visibility and auditability** – View the usage details for your shared resources through the integration of AWS RAM with Amazon CloudWatch and AWS CloudTrail\. AWS RAM provides comprehensive visibility into shared resources and accounts\.

### What about cross\-account access with resource\-based policies?<a name="what-is-about-res-pol-sharing"></a>

You can share some types of AWS resources with other AWS accounts by attaching a [resource\-based permission policy](getting-started-terms-and-concepts.md#term-resource-based-policy) that identifies principals outside of your AWS account\. However, sharing a resource by attaching a policy doesn't take advantage of the additional benefits that AWS RAM provides\. By using AWS RAM you get the following features:
+ You can share with an [organization or an organizational unit \(OU\)](https://docs.aws.amazon.com/ram/latest/userguide/getting-started-sharing.html#getting-started-sharing-orgs) without having to enumerate every one of the AWS account IDs\. All principals in the relevant AWS accounts automatically get access to the resources in such a resource share\.
+ Users can see the resources shared with them directly in the originating AWS service console and API operations as if those resources were directly in the user's account\. For example, if you use AWS RAM to share an Amazon VPC subnet with another account, users in that account can see the subnet in the Amazon VPC console and in the results of Amazon VPC API operations performed in that account\. Resources shared by attaching a resource\-based policy aren't visible this way; instead, you have to discover and explicitly refer to the resource by its ARN\.
+ The owners of a resource can see which principals have access to each individual resource that they have shared\.
+ If you share resources with an account that isn't part of your organization, then AWS RAM initiates an invitation process\. The recipient must accept the invitation before that principal can access the shared resources\. [After you turn on the ability to share within your organization,](getting-started-sharing.md#getting-started-sharing-orgs) sharing with accounts in the organization doesn't require invitations\.

If you have resources that you have shared by using a resource\-based permission policy, you can "promote" those resources to fully AWS RAM\-managed resources by using the `[PromoteResourceShareCreatedFromPolicy](https://docs.aws.amazon.com/ram/latest/APIReference/API_PromoteResourceShareCreatedFromPolicy.html)` API operation, or its CLI equivalent, `[promote\-resource\-share\-created\-from\-policy](https://docs.aws.amazon.com/cli/latest/reference/ram/promote-resource-share-created-from-policy.html)`\.

## How resource sharing works<a name="what-is-how"></a>

When you share a resource in the *owning account* with another AWS account, the *consuming account*, you are granting access for principals in the consuming account to the shared resource\. Any policies and permissions that apply to roles and users in the consuming account also apply to the shared resource\. The resources in the share look like they're native resources in the AWS accounts you shared them with\.

You can share both global and Regional resources\. For more information, see [Sharing Regional resources compared to global resources](working-with-regional-vs-global.md)\.

### Sharing your resources<a name="what-is-how-sharing"></a>

With AWS RAM, you share resources that you own by creating a *resource share*\. To create a resource share, you specify the following:
+ The AWS Region in which you want to create the resource share\. In the console, you choose from the **Region** drop\-down menu in the upper\-right corner of the console\. In the AWS CLI, you use the `--region` parameter\.
  + A resource share can contain only Regional resources that are in the same AWS Region as the resource share\.
  + A resource share can contain global resources only if the resource share is in the designated home Region for global resources, US East \(N\. Virginia\), `us-east-1`\.
+ A name for the resource share\.
+ The list of resources that you want to grant access to as part of this resource share\.
+ The principals to which you grant access to the resource share\. Principals can be individual AWS accounts, the accounts in an organization or an organizational unit \(OU\) in AWS Organizations, or individual AWS Identity and Access Management \(IAM\) roles or users\.
**Note**  
Not all resource types can be shared with IAM roles and users\. For information about resources that you can share with these principals, see [Shareable AWS resources](shareable.md)\.
+ The AWS RAM permission to associate with each resource type\. This is an AWS managed permission policy that determines what the principals in the other accounts can do with the resources in the resource share\.

  The behavior of the permission depends on the type of principal:
  + If the principal is in a different account from the one that owns the resource then the permissions attached to the resource share are the maximum permissions available to be granted to roles and users in those accounts\. The administrator of those accounts must then grant individual roles and users access to the shared resource with IAM identity\-based policies\. The permissions granted in those policies can't exceed those defined in permissions attached to the resource share\.
  + If the principal is the account that owns the resource, then the resource\-based policy in the permission is sufficient, and all roles and users in the same account automatically receive the access defined in the permissions attached to the resource share\.

The sharing account retains full ownership of the resources that it shares\.

### Using shared resources<a name="what-is-how-shared"></a>

When the owner of a resource shares it with your account, you can access the shared resource just as you would if your account owned it\. You can access the resource by using the relevant service's console, AWS Command Line Interface \(AWS CLI\) commands, and API operations\. The API operations that principals in your account are allowed to perform vary depending on the resource type and are specified by the AWS RAM permission attached to the resource share\. All IAM policies and service control policies configured in your account also continue to apply, which enables you to make use of your existing investments in security and governance controls\.

When you access a shared resource using that resource's service, you have the same abilities and limitations as the AWS account that owns the resource\.
+ If the resource is Regional, then you can access it from only the AWS Region in which it exists in the owning account\.
+ If the resource is global, then you can access it from any AWS Region that the resource's service console and tools support\. Note that you can view and manage the resource share and its global resources in the AWS RAM console and tools only in the designated home Region, US East \(N\. Virginia\), `us-east-1`\.

## Service quotas<a name="what-is-limits"></a>

Your AWS account has the following limits related to AWS RAM\. You can request an increase for some of these limits\. To request a limit increase, contact [AWS Support](https://console.aws.amazon.com/support/home#/)\.


| Resource | Default limit | 
| --- | --- | 
|  Maximum number of resource shares per AWS Region in an account  |  5,000  | 
|  Maximum number of shared principals per AWS Region in an account  |  5,000  | 
|  Maximum number of shared resources per AWS Region in an account  |  5,000  | 
|  Maximum number of pending invitations per sharing account  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/what-is.html)  |  20  | 
| Maximum number of versions of a permission | 5 | 

## Accessing AWS RAM<a name="what-is-accessing"></a>

You can work with AWS RAM in any of the following ways:

**AWS RAM console**  
AWS RAM provides a web\-based user interface, the AWS RAM console\. If you've signed up for an AWS account, you can access the AWS RAM console by signing into the [AWS Management Console](https://console.aws.amazon.com/) and choosing AWS RAM from the console home page\.  
You can also navigate in your browser directly to the [AWS RAM console](https://console.aws.amazon.com/ram/home)\. If you aren't already signed in, then you're asked to do so before the console appears\.

**AWS CLI and Tools for Windows PowerShell**  
The AWS CLI and Tools for PowerShell provide direct access to the AWS RAM public API operations\. AWS supports these tools on Windows, macOS, and Linux\. For more information about getting started, see the [AWS Command Line Interface User Guide](https://docs.aws.amazon.com/cli/latest/userguide/), or the [AWS Tools for Windows PowerShell User Guide](https://docs.aws.amazon.com/powershell/latest/userguide/)\. For more information about the commands for AWS RAM, see the [AWS CLI Command Reference](https://docs.aws.amazon.com/cli/latest/reference/) or the [AWS Tools for Windows PowerShell Cmdlet Reference](https://docs.aws.amazon.com/powershell/latest/reference/)\.

**AWS SDKs**  
AWS provides API commands for a broad set of programming languages\. For more information about getting started, see *[AWS SDKs and Tools Reference Guide](https://docs.aws.amazon.com/sdkref/latest/guide/)*\.

**Query API**  
If you don't use one of the supported programming languages, then the AWS RAM HTTPS Query API gives you programmatic access to AWS RAM and AWS\. With the AWS RAM API, you can issue HTTPS requests directly to the service\. When you use the AWS RAM API, you must include code to digitally sign requests using your credentials\. For more information, see the [AWS RAM API Reference](https://docs.aws.amazon.com/ram/latest/APIReference/Welcome.html)\.

## Pricing<a name="what-is-pricing"></a>

There are no additional charges for using AWS RAM or for creating resource shares and sharing your resources across accounts\. Resource usage charges vary depending on the resource type\. For more information about how AWS bills shareable resources, refer to the documentation for the resource's owning service\.

## Compliance and international standards<a name="certification"></a>

### PCI DSS<a name="certification-pci-dss"></a>

AWS Resource Access Manager \(AWS RAM\) supports the processing, storage, and transmission of credit card data by a merchant or service provider, and has been validated as being compliant with Payment Card Industry \(PCI\) Data Security Standard \(DSS\)\. 

For more information about PCI DSS, including how to request a copy of the AWS PCI Compliance Package, see [PCI DSS Level 1](http://aws.amazon.com/compliance/pci-dss-level-1-faqs/)\.

### FedRAMP<a name="certification-fedramp"></a>

AWS Resource Access Manager is authorized as FedRAMP Moderate in the following AWS Regions: US East \(N\. Virginia\), US East \(Ohio\), US West \(N\. California\), and US West \(Oregon\)\.

AWS RAM is authorized as FedRAMP High in the following AWS Regions: AWS GovCloud \(US\-West\) and AWS GovCloud \(US\-East\)\.

The Federal Risk and Authorization Management Program \(FedRAMP\) is a US government\-wide program that delivers a standard approach to the security assessment, authorization, and continuous monitoring for cloud products and services\.

For more information about FedRAMP compliance, see [FedRAMP](http://aws.amazon.com/compliance/fedramp-faqs/)\.

### SOC and ISO<a name="certification-soc"></a>

AWS Resource Access Manager can be used for workloads subject to Service Organization Control \(SOC\) compliance and International Organization for Standardization \(ISO\) ISO 9001, ISO 27001, ISO 27017, ISO 27018 and ISO 27701 standards\. Customers in finance, healthcare, and other regulated sectors can get insights into the security processes and controls that protect customer data which can be found in the SOC reports, AWS ISO and CSA STAR certificates in [AWS Artifact](http://aws.amazon.com/artifact)\. 

For more information about SOC compliance, see [SOC](http://aws.amazon.com/compliance/soc-faqs/)\. 

For more information about ISO compliance, see [ISO 9001](http://aws.amazon.com/compliance/iso-9001-faqs/), [ISO 27001](http://aws.amazon.com/compliance/iso-27001-faqs/), [ISO 27017](http://aws.amazon.com/compliance/iso-27017-faqs/), [ISO 27018 ](http://aws.amazon.com/compliance/iso-27018-faqs/) and [ISO 27701](http://aws.amazon.com/compliance/iso-27701-faqs/)\.