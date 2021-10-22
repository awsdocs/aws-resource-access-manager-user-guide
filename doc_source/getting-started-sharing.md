# Sharing your AWS resources<a name="getting-started-sharing"></a>

To share a resource that you own by using AWS RAM, do the following:
+ [Enable resource sharing within AWS Organizations](#getting-started-sharing-orgs) \(optional\)
+ [Create a resource share](#getting-started-sharing-create)

**Notes**  
Sharing a resource makes it available for use by principals outside of the AWS account that created the resource\. Sharing doesn't change any permissions or quotas that apply to the resource in the account that created it\.
AWS RAM is a Regional service\. The principals that you share with can access the resource share in only the AWS Region in which it was created\.
Some resources have special considerations and prerequisites for sharing\. For more information, see [Shareable AWS resources](shareable.md)\.

## Enable resource sharing within AWS Organizations<a name="getting-started-sharing-orgs"></a>

When your account is managed by AWS Organizations, you can take advantage of that to share resources more easily\. With or without Organizations, a user can share with individual accounts\. However, if your account is in an organization, then you can share with individual accounts, or with all accounts in the organization or in an OU without having to enumerate each account\.

To share resources within an organization, you must first use the AWS RAM console or AWS Command Line Interface \(AWS CLI\) to enable sharing with AWS Organizations\. When you share resources in your organization, AWS RAM doesn't send invitations to principals\. Principals in your organization gain access to shared resources without exchanging invitations\.

If you no longer need to share resources with your entire organization or OUs, you can disable resource sharing\. For more information, see [Disabling resource sharing with AWS Organizations](security-disable-sharing-with-orgs.md)\.

**Requirements**
+ Only the management account can enable sharing with AWS Organizations\.
+ The organization must be enabled for all features\. For more information, see [ Enabling all features in your organization](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_org_support-all-features.html) in the *AWS Organizations User Guide*\.

**Important**  
You must enable sharing with AWS Organizations by using the AWS RAM console or the [enable\-sharing\-with\-aws\-organization](https://docs.aws.amazon.com/cli/latest/reference/ram/enable-sharing-with-aws-organization.html) AWS CLI command\. This ensures that the `AWSServiceRoleForResourceAccessManager` service\-linked role is created\. If you enable trusted access with AWS Organizations by using the AWS Organizations console or the [ enable\-aws\-service\-access](https://docs.aws.amazon.com/cli/latest/reference/organizations/enable-aws-service-access.html) AWS CLI command, the `AWSServiceRoleForResourceAccessManager` service\-linked role isn't created, and you can't share resources within your organization\.

------
#### [ Console ]

**To enable resource sharing within AWS Organizations**

1. Open the [https://console.aws.amazon.com/ram/home#Settings:](https://console.aws.amazon.com/ram/home#Settings:) page in the AWS RAM console\.

1. Choose **Enable sharing with AWS Organizations**, and then choose **Save settings**\.

------
#### [ AWS CLI ]

**To enable resource sharing within AWS Organizations**  
Use the [enable\-sharing\-with\-aws\-organization](https://docs.aws.amazon.com/cli/latest/reference/ram/enable-sharing-with-aws-organization.html) command\.

This command can be used in any AWS Region, and it enables sharing with AWS Organizations in all Regions in which AWS RAM is supported\.

```
$ aws ram enable-sharing-with-aws-organization
{
    "returnValue": true
}
```

------

## Create a resource share<a name="getting-started-sharing-create"></a>

To share resources that you own, create a resource share\. When you create a resource share, you do the following:

1. Add the resources that you want to share\.

1. For each resource type that you include in the share, specify the permission to use for that resource type\.
   + If only the *default permission* is available for a resource type, then AWS RAM automatically associates that permission with the resource type and there is no action for you\.
   + If more than the default AWS RAM managed permission is available for a resource type, then you must choose the permission to associate with that resource type\. 

1. Specify the principals that you want to have access to the resources\.

**Considerations**
+ You can share a resource only if you own it\. You can't share a resource that is shared with you\.
+ AWS RAM is a Regional service\. When you share a resource with principals in other AWS accounts, they must access each resource from the same AWS Region that it was created in\. For supported global resources, you can access those resources from any AWS Region that is supported by that resource's service console and tools\. Note that you can view such resource shares and their global resources in the AWS RAM console and tools only in the designated home Region, US East \(N\. Virginia\), `us-east-1`\.
+ If you're part of an organization in AWS Organizations and sharing within your organization is enabled, principals in the organization are automatically granted access to the shared resources without the use of invitations\. A principal in an account with whom you share outside of the context of an organization receives an invitation to join the resource share and is granted access to the shared resources only after they accept the invitation\.
+ After you add an organization or an organization unit \(OU\) to a resource share, changes to the accounts that are in an OU or accounts that join or leave an organization dynamically affect the resource share\. For example, if you add a new account to an OU that has access to a resource share, then the new member account automatically receives access to the shared resources\.
+ You can add only the organization your account is a member of, and OUs from that organization to your resource shares\. You can't add OUs or organizations from outside your own organization to a resource share as principals\. However, you can add individual AWS accounts, IAM users, and IAM roles from outside your organization as principals to a resource share\.
**Note**  
Not all resource types can be shared with IAM roles and users\. For information about resources that you can share with these principals, see [Shareable AWS resources](shareable.md)\.

------
#### [ Console ]

**To create a resource share**

1. Open the [AWS RAM console](https://console.aws.amazon.com/ram/home)\.

1. Because AWS RAM resource shares exist in specific AWS Regions, choose the appropriate AWS Region from the dropdown list in the upper\-right corner of the console\. If you want to include global resources in the resource share, then you must choose the designated home Region, US East \(N\. Virginia\), `us-east-1`\.

1. If you're new to AWS RAM, choose **Create a resource share** from the home page\. Otherwise, choose **Create resource share** from the [https://console.aws.amazon.com/ram/home#OwnedResourceShares:](https://console.aws.amazon.com/ram/home#OwnedResourceShares:) page\.

1. In **Step 1: Specify resource share details**, do the following:

   1. For **Name**, enter a descriptive name for the resource share\.

   1. Under **Resources**, choose resources to add to the resource share as follows:
      + For **Select resource type**, choose the type of resource to share\. This filters the list of shareable resources to only those resources of the selected type\.
      + In the resulting list of resources, select the check boxes next to the individual resources that you want to share\. The selected resources move under **Selected resources**\.

        If you're sharing resources that are associated with a specific availability zone, then using the Availability Zone ID \(AZ ID\) helps you determine the relative location of these resources across accounts\. For more information, see [Availability Zone IDs for your AWS resources](working-with-az-ids.md)\.

   1. \(Optional\) To [attach tags](https://docs.aws.amazon.com/general/latest/gr/aws_tagging.html) to the resource share, under **Tags**, enter a tag key and value\. Add others by choosing **Add new tag**\. Repeat this step as needed\. These tags applied to only the resource share itself, not to the resources in the resource share\.

1. Choose **Next**\.

1. In **Step 2: Associate a permission with each resource type**, if more than the default AWS RAM managed permission is available, then you can choose which permission to associate with the resource type\. If only the default permission is available, then AWS RAM automatically associates this permission with the resource type\. For more information, see [Types of AWS RAM managed permissions](security-ram-permissions.md#permissions-types)\.

   To display the actions that the permission allows, expand **View the actions that are allowed by this permission**\.

1. Choose **Next**\.

1. In **Step 3: Choose principals to grant access**, do the following:

   1. By default, **Allow sharing with external principals** is selected, which means that you can share resources with AWS accounts that are outside of your organization\. For [supported resource types](shareable.md), you can also share resources with IAM roles and users\.

      To restrict resource sharing to only principals in your organization, choose **Allow sharing with principals in your organization only**\.

   1. For **Principals**, do the following:
      + To add the organization, an organizational unit \(OU\), or an AWS account that is part of an organization, turn on **Display organizational structure**\. This displays a tree view of your organization\. Then, select the check box next to each principal that you want to add\.
        + If you select the organization \(the ID begins with `o-`\), then all AWS accounts in the organization can access the resource share\. 
        + If you select an OU \(the ID begins with `ou-`\), then all AWS accounts in that OU and its child OUs can access the resource share\.
        + If you select an individual AWS account, then only that account can access the resource share\.
**Note**  
The **Display organizational structure **toggle appears only if sharing with AWS Organizations is enabled and you're signed in to the management account for the organization\.  
You can't use this method to specify an AWS account outside your organization, or an IAM role or IAM user\. Instead, you must turn off **Display organizational structure** and use the dropdown list and text box to enter the ID or ARN\.
      + To specify a principal by ID or ARN, including principals that are outside of the organization, then for each principal, select the principal type\. Next, enter the ID \(for an AWS account, organization, or OU\) or ARN \(for an IAM user or role\), and then choose **Add**\. The available principal types and ID and ARN formats are as follows:
        + **AWS account** – To add an AWS account, enter the 12\-digit account ID\. For example:

          `123456789012`
        + **Organization** – To add all of the AWS accounts in your organization, enter the ID of the organization\. For example:

          `o-abcd1234`
        + **Organizational unit \(OU\)** – To add an OU, enter the ID of the OU\. For example:

          `ou-abcd-1234efgh`
        + **IAM role** – To add an IAM role, enter the ARN of the role\. Use the following syntax\.

          `arn:partition:iam::account:role/role-name`

          For example:

          `arn:aws:iam::123456789012:role/MyS3AccessRole`
**Note**  
To obtain the unique ARN for an IAM role, [view the list of roles in the IAM console](https://console.aws.amazon.com/iamv2/home?#/roles), use the [get\-role](https://docs.aws.amazon.com/cli/latest/reference/iam/get-role.html) AWS CLI command or the [GetRole](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetRole.html) API action\.
        + **IAM user** – To add an IAM user, enter the ARN of the user\. Use the following syntax\.

          `arn:partition:iam::account:user/user-name`

          For example:

          `arn:aws:iam::123456789012:user/JohnDoe`
**Note**  
To obtain the unique ARN for an IAM user, [view the list of users in the IAM console](https://console.aws.amazon.com/iamv2/home?#/users), use the [get\-user](https://docs.aws.amazon.com/cli/latest/reference/iam/get-user.html) AWS CLI command or the [GetUser](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetUser.html) API action\.

   1. For **Selected principals**, verify that the principals you specified appear in the list\.

1. Choose **Next**\.

1. In **Step 4: Review and create**, review the configuration details for your resource share\. To change the configuration for any step, choose the link that corresponds to the step you want to go back to and make the required changes\.

1. After you finish reviewing the resource share, choose **Create resource share**\.

   It can take a few minutes for the resource and principal associations to complete\. Allow this process to complete before you try to use the resource share\.

1. You can add and remove resources and principals or apply custom tags to your resource share at any time\. You can change permission for resource types that are included in your resource share, for those types that support more than the default permission\. You can delete your resource share when you no longer want to share the resources\. For more information, see [Share AWS resources owned by you](working-with-sharing.md)\.

------
#### [ AWS CLI ]

**To create a resource share**  
Use the [create\-resource\-share](https://docs.aws.amazon.com/cli/latest/reference/ram/create-resource-share.html) command\. The following command creates a resource share that is shared with all of the AWS accounts in the organization\. The share contains an AWS License Manager license configuration, and it grants the default permissions for that resource type\.

```
$ aws ram create-resource-share \
    --region us-east-1 \
    --name MyLicenseConfigShare \
    --permission-arns arn:aws:ram::aws:permission/AWSRAMDefaultPermissionLicenseConfiguration \
    --resource-arns arn:aws:license-manager:us-east-1:123456789012:license-configuration:lic-abc123 \
    --principals arn:aws:organizations::123456789012:organization/o-1234abcd
{
    "resourceShare": {
        "resourceShareArn": "arn:aws:ram:us-east-1:123456789012:resource-share/12345678-abcd-09876543",
        "name": "MyLicenseConfigShare",
        "owningAccountId": "123456789012",
        "allowExternalPrincipals": true,
        "status": "ACTIVE",
        "creationTime": "2021-09-14T20:42:40.266000-07:00",
        "lastUpdatedTime": "2021-09-14T20:42:40.266000-07:00"
    }
}
```

------