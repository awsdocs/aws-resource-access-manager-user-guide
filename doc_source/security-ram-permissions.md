# AWS RAM managed permissions<a name="security-ram-permissions"></a>

For each shareable resource type, there is at least one AWS Resource Access Manager \(AWS RAM\) managed permission that defines the actions that principals with access to the resources in a resource share are allowed to perform on those resources\. Some resource types have only one AWS RAM managed permission, and it's used automatically by default, with no action required by you\. Some resource types define more than one managed permission, and you can choose which one to use in a resource share\.

You can retrieve the list of the available managed permissions at any time\. For more information, see [Viewing AWS RAM managed permissions](working-with-sharing-view-permissions.md)\.

**Topics**
+ [How AWS RAM managed permissions work](#permissions-work)
+ [Types of AWS RAM managed permissions](#permissions-types)

## How AWS RAM managed permissions work<a name="permissions-work"></a>

AWS RAM managed permissions are similar to [IAM resource\-based policies\.](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies.html#policies_resource-based) When you create a resource share, you associate a AWS RAM managed permission with each resource type that you want to share\.

After you create the resource share, AWS RAM provides the managed permission that you associate with each resource type to the respective resource\-owning service, such as AWS Certificate Manager Private Certificate Authority\. The permissions are then attached to each of the resources in the resource share\.

AWS RAM managed permissions specify the following:

**Effect**  
Indicates whether to `Allow` or `Deny` the principal permission to perform an operation on a shared resource\. For an AWS RAM managed permission, the effect is always `Allow`\. For more information, see [Effect](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_effect.html) in the *IAM User Guide*\.

**Principal**  
The ID number of an AWS account, or the [Amazon Resource Name \(ARN\)](https://docs.aws.amazon.com/general/latest/gr/aws-arns-and-namespaces.html) of an organization or organizational unit \(OU\) in AWS Organizations, or the Amazon Resource Name \(ARN\) of an AWS Identity and Access Management \(IAM\) role or user to whom you want to grant access the shared resource\. For more information, see [Principal](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_principal.html) in the *IAM User Guide*\.  
Not all resource types can be shared with IAM roles and users\. For information about resources that you can share with these principals, see [Shareable AWS resources](shareable.md)\.

**Action**  
The operation that the principal is granted permission to perform\. This can be an action in the AWS Management Console or an operation in the AWS Command Line Interface \(AWS CLI\) or AWS API\. The actions are defined by the AWS RAM permission\. For more information, see [Action](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_action.html) in the *IAM User Guide*\.

## Types of AWS RAM managed permissions<a name="permissions-types"></a>

When you create a resource share, you choose the AWS RAM permission to associate with each resource type that you include in the resource share\. Managed permissions are defined by the resource\-owning service and managed by AWS RAM\.
+ **Default managed permission** – There is one default managed permission available for each resource type that AWS RAM supports\. The default managed permission allows principals to perform specific actions that are defined by the service for the resource type\. For example, for the Amazon VPC `ec2:Subnet` resource type, the default managed permission allows principals to perform the following actions:
  + `ec2:RunInstances`
  + `ec2:CreateNetworkInterface`
  + `ec2:DescribeSubnets`

  The names of default managed permissions use the following format: `AWSRAMDefaultPermissionShareableResourceType`\. For example, for the `ec2:Subnet` resource type, the name of the default AWS RAM managed permission is `AWSRAMDefaultPermissionSubnet`\.
+ **Additional managed permissions** – Some resource types support additional choices for the permission you can attach to a resource type in a resource share\. Examples include read\-only access or full access \(`Read` and `Write` access\)\. These additional managed permissions provide you with more flexibility to choose the permissions to grant to specific principals for supported resource types\. For example, when you share a resource type that supports both a full access \(`Read` and `Write`\) managed permission and a read\-only managed permission, you can share the resources with the full access managed permission granted to an administrator\. You can then share the resources with other team members using the read\-only managed permission to follow the [security best practice of granting least privilege](https://wikipedia.org/wiki/Principle_of_least_privilege)\.
**Note**  
Currently, only some AWS services that work with AWS RAM support additional managed permissions beyond the default\. You can view the available permissions for each AWS service on the [https://console.aws.amazon.com/ram/home#Permissions:](https://console.aws.amazon.com/ram/home#Permissions:) page\. This page provides details about each available managed permission, including any resource shares that are currently associated with the permission and whether sharing with external principals is allowed, if applicable\. For more information, see [Viewing AWS RAM managed permissions](working-with-sharing-view-permissions.md)\.   
For services that don’t support additional managed permissions, when you create a resource share, AWS RAM automatically applies the default permission defined for the resource type that you choose\.