# Sharing your AWS resources<a name="getting-started-sharing"></a>

To share a resource that you own by using AWS RAM, do the following:
+ [Enable resource sharing with AWS Organizations](#getting-started-sharing-orgs) \(optional\)
+ [Create a resource share](#getting-started-sharing-create)

**Note**  
Some resources have special considerations and prerequisites for sharing\. For more information, see [Shareable AWS resources](shareable.md)\.

## Enable resource sharing with AWS Organizations<a name="getting-started-sharing-orgs"></a>

To share resources with your organization or organizational units in AWS Organizations, you must use the AWS RAM console or AWS CLI to enable sharing with AWS Organizations\. When you share resources in your organization, AWS RAM does not send invitations to principals\. Principals in your organization gain access to shared resources without exchanging invitations\.

If you no longer need to share resources with your entire organization or organizational units, you can disable resource sharing\. For more information, see [Disabling resource sharing with AWS Organizations](disable-sharing.md)\.

**Requirements**
+ Only the management account can enable sharing with AWS Organizations\.
+ The organization must be enabled for all features\. For more information, see [ Enabling All Features in Your Organization](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_org_support-all-features.html) in the *AWS Organizations User Guide*\.

**Important**  
If you don't enable sharing with AWS Organizations, you can't share resources with your organization or organizational units in your organization\. However, you can still share resources with individual AWS accounts in your organization\. For [supported resource types](permissions.md#permissions-rbp-supported-resource-types), you can also share resources with IAM roles or IAM users in your organization\. In this case, these principals are treated as external principals\. They receive an invitation to join the resource share, and they must accept the invitation to gain access to the shared resources\.
You must enable sharing with AWS Organizations by using the AWS RAM console or the [enable\-sharing\-with\-aws\-organization](https://docs.aws.amazon.com/cli/latest/reference/ram/enable-sharing-with-aws-organization.html) AWS CLI command\. This ensures that the `AWSServiceRoleForResourceAccessManager` service\-linked role is created\. If you enable trusted access with AWS Organizations by using the AWS Organizations console or the [ enable\-aws\-service\-access](https://docs.aws.amazon.com/cli/latest/reference/organizations/enable-aws-service-access.html) AWS CLI command, the `AWSServiceRoleForResourceAccessManager` service\-linked role is not created, and you can't share resources within your organization\.

**To enable resource sharing with AWS Organizations \(console\)**

1. Open the **Settings** page of AWS RAM console at [https://console\.aws\.amazon\.com/ram/home\#Settings](https://console.aws.amazon.com/ram/home#Settings)\.

1. Choose **Enable sharing with AWS Organizations**\.

**To enable resource sharing with AWS Organizations \(AWS CLI\)**  
Use the [enable\-sharing\-with\-aws\-organization](https://docs.aws.amazon.com/cli/latest/reference/ram/enable-sharing-with-aws-organization.html) command\.

This command can be used in any AWS Region, and it enables sharing with AWS Organizations in all Regions in which AWS RAM is supported\.

## Create a resource share<a name="getting-started-sharing-create"></a>

To share resources that you own, create a resource share\. When you create a resource share, you add the resources to share, choose a permission to associate with each resource type, and specify the principals that you want to have access to the resources\.

**Considerations**
+ You can share a resource only if you own it\. You can't share a resource that is shared with you\.
+ If you are part of an organization in AWS Organizations and sharing within your organization is enabled, principals in your organization are automatically granted access to the shared resources\. Otherwise, principals receive an invitation to join the resource share and are granted access to the shared resources after accepting the invitation\.
+ After you add an organization to a resource share, changes to the OU or organization affect the resource share\. For example, if you add a new account to the organization, it has access to the shared resources\.
+ You can't add OUs or organizations outside your organization in AWS Organizations to a resource share as principals\. You can add AWS accounts, IAM users, and IAM roles as principals outside your organization\.
**Note**  
Not all resource types can be shared with IAM roles and IAM users\. For information about resources that you can share with these principals, see [Sharing with IAM roles and IAM users](permissions.md#permissions-rbp-supported-resource-types)\.

**To create a resource share \(console\)**

1. Open the AWS RAM console at [https://console\.aws\.amazon\.com/ram](https://console.aws.amazon.com/ram/)\.

1. If you are new to AWS RAM, choose **Create a resource share** from the home page\. Otherwise, choose **Create resource share** from the **Resource shares** page\.

1. In **Step 1: Specify resource share details**, do the following:

   1. For **Name**, enter a descriptive name for the resource share\.

   1. Under **Resources**, choose resources to add to the resource share as follows:
      + For **Select resource type**, choose the type of resource to share\. This filters the list of shareable resources to resources of the selected type\.
      + In the list of resources, select the check boxes next to the resources to share\. The selected resources are moved under **Selected resources**\.

        If you are sharing zonal resources, using the Availability Zone ID \(AZ ID\) helps you determine the relative location of these resources across accounts\. For more information, see [AZ IDs for your AWS resources](working-with-az-ids.md)\.

   1. For **Tags \- *optional***, enter a key and value for the tag\. To add another tag, choose **Add new tag** and enter a tag key and value\. Repeat this step as needed\. These tags are applied to the resource share only, not to resources in the resource share\.

1. Choose **Next**\.

1. In **Step 2: Associate a permission with each resource type**, if more than the default AWS RAM managed permission is available, choose the permission to associate with the resource type\. If only the default permission is available, AWS RAM automatically associates this permission with the resource type\. For more information, see [Types of AWS RAM managed permissions](permissions.md#permissions-types)\.

   To display the actions that the permission allows, expand **View the actions that are allowed by this permission**\.

1. Choose **Next**\.

1. In **Step 3: Choose principals to grant access**, do the following:

   1. By default, **Allow sharing with external principals** is selected, which means that you can share resources with AWS accounts that are outside your organization\. For [supported resource types](permissions.md#permissions-rbp-supported-resource-types), you can also share resources with IAM roles and IAM users\. 

      To restrict resource sharing to principals in your organization in AWS Organizations, choose **Allow sharing with principals in your organization only**\.

   1. For **Principals**, do the following:
      + To add an organization, organizational unit \(OU\), or AWS account inside your organization, turn on **Display organizational structure** to display a "tree" view of your organization\. Then, select the check box next to each principal that you want to add\.
**Note**  
The **Display organizational structure **toggle appears only if sharing with AWS Organizations is enabled and you are signed in to the management account for the organization\.  
You can't use this method to specify an AWS account outside your organization, or an IAM role or IAM user\. Instead, you must add these principals from the list\.
      + To specify a principal from the list, for each principal, select the principal type, enter the ID or ARN, and choose **Add**\. The available principal types and ID and ARN formats are as follows:
        + **AWS account**: To add an AWS account, enter the 12\-digit account ID\. For example:

          `123456789012`
        + **Organization**: To add your entire organization, enter the ID of the organization\. For example:

          `o-abcd1234efgh5678`
        + **Organizational unit \(OU\)**: To add an OU, enter the ID of the OU\. For example:

          `ou-abcd1234-mnop5678qrst9098uv76`
        + **IAM role**: To add an IAM role, enter the ARN of the role\. Use the following syntax:

          `arn:partition:iam::account:role/role-name`

          For example:

          `arn:aws:iam::123456789012:role/S3Access`
**Note**  
To obtain the unique ARN for an IAM role, use the [get\-role](https://docs.aws.amazon.com/cli/latest/reference/iam/get-role.html) AWS CLI command or the [GetRole](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetRole.html) API action\.
        + **IAM user**: To add an IAM user, enter the ARN of the user\. Use the following syntax:

          `arn:partition:iam::account:user/user-name`

          For example:

          `arn:aws:iam::123456789012:user/JohnDoe`
**Note**  
To obtain the unique ARN for an IAM user, use the [get\-user](https://docs.aws.amazon.com/cli/latest/reference/iam/get-user.html) AWS CLI command or the [GetUser](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetUser.html) API action\.

   1. For **Selected principals**, verify that the principals you specified appear in the list\.

1. Choose **Next**\.

1. In **Step 4: Review and create**, review the configuration details for your resource share\. To change the configuration for any step, choose the link that corresponds to the step and make the required changes\.

1. After you finish reviewing the configuration details, choose **Create resource share**\.

   It can take a few minutes for the resource and principal associations to complete\. Allow this process to complete before attempting to use the resource share\.

1. You can add and remove resources and principals or apply custom tags to your resource share at any time\. You can delete your resource share when you no longer want to share the resources\. For more information, see [Share AWS resources owned by you](working-with-sharing.md)\.

**To create a resource share by using the AWS CLI**  
Use the [create\-resource\-share](https://docs.aws.amazon.com/cli/latest/reference/ram/create-resource-share.html) command\.