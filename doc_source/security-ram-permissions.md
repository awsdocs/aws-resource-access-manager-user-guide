# Managing permissions in AWS RAM<a name="security-ram-permissions"></a>

In AWS RAM, there are [two types of managed permissions](getting-started-terms-and-concepts.md#term-managed-permission-version), AWS managed permissions and customer managed permissions\.

Managed permissions define how a consumer can act on the resources in a resource share\. When you create a resource share, you must specify which managed permission to use for each resource type that is included in the resource share\. The policy template in the managed permission contains everything needed for a resource\-based policy except for the principal and the resource\. The resource's Amazon Resource Name \(ARN\) and the ARN of the principals associated with the resource share complete the elements of a resource\-based policy\. AWS RAM then authors the resource\-based policy that it attaches to all resources in that resource share\.

Each managed permission can have one or more versions\. One version is designated as the *default* version for that managed permission\. Occasionally, AWS updates an AWS managed permission for a resource type by creating a new version and designating that new version as the default\. You can also update your customer managed permissions by creating new versions\. Managed permissions that are already attached to a resource share are ***not*** automatically updated\. The AWS RAM console does indicate when a new default version is available, and you can review the changes in the new default version compared to the previous one\.

**Note**  
We recommend that you update to the new version of the AWS managed permission as soon as possible\. These updates typically add support for new or updated AWS services that can share additional resource types using AWS RAM\. A new default version can also address and correct security vulnerabilities\.

**Important**  
You can only attach the default version of the managed permission to a new resource share\. 

You can retrieve the list of the available managed permissions at any time\. For more information, see [Viewing managed permissions](working-with-sharing-view-permissions.md)\.

**Topics**
+ [Viewing managed permissions](working-with-sharing-view-permissions.md)
+ [Creating and using customer managed permissions in AWS RAM](create-customer-managed-permissions.md)
+ [Updating AWS managed permissions to a newer version](working-with-sharing-update-permissions.md)
+ [Considerations for using customer managed permissions in AWS RAM](managed-permission-considerations.md)
+ [How managed permissions work](#permissions-work)
+ [Types of managed permissions](#permissions-types)

## How managed permissions work<a name="permissions-work"></a>

For a quick overview, watch the following video that demonstrates how managed permissions let you apply the best practice of least privilege access to your AWS resources\.



When you create a resource share, you associate an AWS managed permission with each resource type that you want to share\. If the managed permission has more than one version, the new resource share always uses the version designated as the default\.

After you create the resource share, AWS RAM uses the managed permission to generate a resource\-based policy that is attached to each shared resource\.

The policy template in a managed permission specifies the following:

**Effect**  
Indicates whether to `Allow` or `Deny` the principal permission to perform an operation on a shared resource\. For a managed permission, the effect is always `Allow`\. For more information, see [Effect](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_effect.html) in the *IAM User Guide*\.

**Action**  
The list of operations that the principal is granted permission to perform\. This can be an action in the AWS Management Console or an operation in the AWS Command Line Interface \(AWS CLI\) or AWS API\. The actions are defined by the AWS permission\. For more information, see [Action](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_action.html) in the *IAM User Guide*\.

**Condition**  
When and how a principal can interact with a resource in a resource share\. Conditions add an extra layer of security to your shared resources\. Use them to limit access for sensitive actions to your shared resources\. For example, you can include conditions requiring the actions to originate from a specific corporate IP address range, or that the actions must be performed by users authenticated with multi\-factor authentication\. For more information about conditions, see [AWS global condition context keys](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html) in the *IAM User Guide*\. For more information about service\-specific conditions, see [ Actions, resources, and condition keys for AWS services](https://docs.aws.amazon.com/service-authorization/latest/reference/reference_policies_actions-resources-contextkeys.html) in the *Service Authorization Reference*\.  
Conditions are available for customer managed permissions and supported resource types for AWS managed permissions\.  
For information about conditions that are excluded from use with customer managed permissions, see [Considerations for using customer managed permissions in AWS RAM](managed-permission-considerations.md)\.

## Types of managed permissions<a name="permissions-types"></a>

When you create a resource share, you choose a managed permission to associate with each resource type that you include in the resource share\. AWS managed permissions are defined by the AWS resource\-owning service and managed by AWS RAM\. You author and maintain your own customer managed permissions\.
+ **AWS managed permission** – There is one default managed permission available for every resource type that AWS RAM supports\. The default managed permission is the one used for a resource type unless you explicitly choose one of the additional managed permissions\. The default managed permission is intended to support the most common customer scenarios for sharing resources of the specified type\. The default managed permission allows principals to perform specific actions that are defined by the service for the resource type\. For example, for the Amazon VPC `ec2:Subnet` resource type, the default managed permission allows principals to perform the following actions:
  + `ec2:RunInstances`
  + `ec2:CreateNetworkInterface`
  + `ec2:DescribeSubnets`

  The names of default AWS managed permissions use the following format: `AWSRAMDefaultPermissionShareableResourceType`\. For example, for the `ec2:Subnet` resource type, the name of the default AWS managed permission is `AWSRAMDefaultPermissionSubnet`\.
**Note**  
The default managed permission is separate from the default [*version*](getting-started-terms-and-concepts.md#term-managed-permission-version) of a managed permission\. All managed permissions, whether default or one of the additional managed permissions supported by some resource types, are separate, complete permissions with different effects and actions that support different sharing scenarios, such as read\-write versus read\-only access\. Any managed permission, whether AWS or customer managed can have multiple versions, one of which is the default version for that permission\.

  For example, when you share a resource type that supports both a full access \(`Read` and `Write`\) managed permission and a read\-only managed permission, you can create one resource share for the administrator with the full access managed permission\. You can then create a separate resource share for other developers using the read\-only managed permission to follow the [practice of granting least privilege](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html#grant-least-privilege)\.
**Note**  
All AWS services that work with AWS RAM support at least one default managed permission\. You can view the available permissions for each AWS service on the **[Managed permissions library](https://console.aws.amazon.com/ram/home#Permissions:)** page\. This page provides details about each available managed permission, including any resource shares that are currently associated with the permission and whether sharing with external principals is allowed, if applicable\. For more information, see [Viewing managed permissions](working-with-sharing-view-permissions.md)\.   
For services that don’t support additional managed permissions, when you create a resource share, AWS RAM automatically applies the default permission defined for the resource type that you choose\. If supported, you will also have the option to choose **Create customer managed permission** on the **Associate managed permissions** page\. 
+ **Customer managed permission** – Customer managed permissions are managed permissions that you author and maintain by precisely specifying which actions can be performed under which conditions with resources shared using AWS RAM\. For example, you want to limit read access for your Amazon VPC IP Address Manager \(IPAM\) pools, which help you manage your IP addresses at scale\. You can create customer managed permissions for your developers to assign IP addresses, but not view the range of IP addresses other developer accounts assign\. You can follow the best practice of least privilege, granting only the permissions required to perform tasks on shared resources\.