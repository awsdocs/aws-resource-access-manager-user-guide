# Creating a resource share in AWS Resource Access Manager<a name="working-with-sharing-create"></a>

To share resources that you own, create a resource share\. When you create a resource share, you do the following:

1. Add the resources to share\.

1. If more than the default AWS RAM managed permission is available, choose a permission to associate with each resource type\. If only the default permission is available, AWS RAM automatically associates this permission with the resource type\. 

1. Specify the principals that you want to have access to the resources\.

**Considerations**
+ You can share a resource only if you own it\. You can't share a resource that is shared with you\.
+ AWS RAM is a Regional service\. When you share a resource with principals in other AWS accounts, they must access it from the same AWS Region that it was created in\. 
+ If you are part of an organization in AWS Organizations and sharing within your organization is enabled, principals in the organization are automatically granted access to the shared resources without the use of invitations\. A principal in an account with whom you share outside of the context of an organization receive an invitation to join the resource share and are granted access to the shared resources only after they accept the invitation\.
+ After you add an organization to a resource share, changes to the accounts that are in an OU or accounts that join or leave an organization dynamically affect the resource share\. For example, if you add a new account to an OU that has access to a resource share, then the new account automatically has access to the shared resources\.
+ You can add only the organization your account is a member of, and OUs from that organization to your resource shares\. You can't add OUs or organizations from outside your own organization to a resource share as principals\. However, you can add individual AWS accounts, IAM users, and IAM roles from outside your organization as principals to a resource share\.
**Note**  
Not all resource types can be shared with IAM roles and users\. For information about resources that you can share with these principals, see [Shareable AWS resources](shareable.md)\.

------
#### [ Console ]

**To create a resource share**

1. Open the [AWS RAM console](https://console.aws.amazon.com/ram/home)\.

1. Because AWS RAM resource shares exist in specific AWS Regions, choose the appropriate AWS Region from the drop\-down list in the upper\-right corner of the console\.

1. If you are new to AWS RAM, choose **Create a resource share** from the home page\. Otherwise, choose **Create resource share** from the [https://console.aws.amazon.com/ram/home#OwnedResourceShares:](https://console.aws.amazon.com/ram/home#OwnedResourceShares:) page\.

1. In **Step 1: Specify resource share details**, do the following:

   1. For **Name**, enter a descriptive name for the resource share\.

   1. Under **Resources**, choose resources to add to the resource share as follows:
      + For **Select resource type**, choose the type of resource to share\. This filters the list of shareable resources to only those resources of the selected type\.
      + In the resulting list of resources, select the check boxes next to the individual resources that you want to share\. The selected resources move under **Selected resources**\.

        If you are sharing zonal resources, using the Availability Zone ID \(AZ ID\) helps you determine the relative location of these resources across accounts\. For more information, see [AZ IDs for your AWS resources](working-with-az-ids.md)\.

   1. If you want to [attach tags](https://docs.aws.amazon.com/general/latest/gr/aws_tagging.html) to the resource share then under **Tags**, enter a tag key and value\. Add others by choosing **Add new tag**\. Repeat this step as needed\. These tags are applied to the resource share only, not to the resources in the resource share\.

1. Choose **Next**\.

1. In **Step 2: Associate a permission with each resource type**, if more than the default AWS RAM managed permission is available then you can choose which permission to associate with the resource type\. If only the default permission is available then AWS RAM automatically associates this permission with the resource type\. For more information, see [Types of AWS RAM managed permissions](security-ram-permissions.md#permissions-types)\.

   To display the actions that the permission allows, expand **View the actions that are allowed by this permission**\.

1. Choose **Next**\.

1. In **Step 3: Choose principals to grant access**, do the following:

   1. By default, **Allow sharing with external principals** is selected, which means that you can share resources with AWS accounts that are outside of your organization\. For [supported resource types](shareable.md), you can also share resources with IAM roles and users\.

      To restrict resource sharing to only principals in your organization, choose **Allow sharing with principals in your organization only**\.

   1. For **Principals**, do the following:
      + To add the organization, an organizational unit \(OU\), or an AWS account that is part of an organization, turn on **Display organizational structure**\. This displays a tree view of your organization\. Then, select the check box next to each principal that you want to add\.
        + If you select the organization \(the ID begins with `o-`\), then all AWS accounts in the organization can access the resource share\. 
        + If you select an OU \(the ID begins with `ou-`\) then all AWS accounts in that OU and its child OUs can access the resource share\.
        + If you select and individual AWS account then only that account can access the resource share\.
**Note**  
The **Display organizational structure **toggle appears only if sharing with AWS Organizations is enabled and you are signed in to the management account for the organization\.  
You can't use this method to specify an AWS account outside your organization, or an IAM role or IAM user\. Instead, you must turn off **Display organizational structure** and use the drop\-down list and text box to enter the ID or ARN\.
      + To specify a principal by ID or ARN, including principals that are outside of the organization, then for each principal, select the principal type\. Next, enter the ID \(for an AWS account, organization, or OU\) or ARN \(for an IAM user or role\), and then choose **Add**\. The available principal types and ID and ARN formats are as follows:
        + **AWS account**: To add an AWS account, enter the 12\-digit account ID\. For example:

          `123456789012`
        + **Organization**: To add all of the AWS accounts in your organization, enter the ID of the organization\. For example:

          `o-abcd1234`
        + **Organizational unit \(OU\)**: To add an OU, enter the ID of the OU\. For example:

          `ou-abcd-1234efgh`
        + **IAM role**: To add an IAM role, enter the ARN of the role\. Use the following syntax:

          `arn:partition:iam::account:role/role-name`

          For example:

          `arn:aws:iam::123456789012:role/MyS3AccessRole`
**Note**  
To obtain the unique ARN for an IAM role, [view the list of roles in the IAM console](https://console.aws.amazon.com/iamv2/home?#/roles), use the [get\-role](https://docs.aws.amazon.com/cli/latest/reference/iam/get-role.html) AWS CLI command or the [GetRole](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetRole.html) API action\.
        + **IAM user**: To add an IAM user, enter the ARN of the user\. Use the following syntax:

          `arn:partition:iam::account:user/user-name`

          For example:

          `arn:aws:iam::ExampleAWSAccountNo3;:user/JohnDoe`
**Note**  
To obtain the unique ARN for an IAM user, [view the list of users in the IAM console](https://console.aws.amazon.com/iamv2/home?#/users), use the [get\-user](https://docs.aws.amazon.com/cli/latest/reference/iam/get-user.html) AWS CLI command or the [GetUser](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetUser.html) API action\.

   1. For **Selected principals**, verify that the principals you specified appear in the list\.

1. Choose **Next**\.

1. In **Step 4: Review and create**, review the configuration details for your resource share\. To change the configuration for any step, choose the link that corresponds to the step you want to go back to and make the required changes\.

1. After you finish reviewing the resource share, choose **Create resource share**\.

   It can take a few minutes for the resource and principal associations to complete\. Allow this process to complete before attempting to use the resource share\.

1. You can add and remove resources and principals or apply custom tags to your resource share at any time\. You can change permission for resource types that are included in your resource share, for those types that support more than the default permission\. You can delete your resource share when you no longer want to share the resources\. For more information, see [Share AWS resources owned by you](working-with-sharing.md)\.

------
#### [ AWS CLI ]

**To create a resource share by using the AWS CLI**  
Use the [create\-resource\-share](https://docs.aws.amazon.com/cli/latest/reference/ram/create-resource-share.html) command\. The following command creates a resource share that is shared with all of the AWS accounts in the organization\. The share contains a AWS License Manager license configuration and it grants the default permissions for that resource type\.

```
$ aws ram create-resource-share \
    --name MyLicenseConfigShare \
    --permission-arns arn:aws:ram::aws:permission/AWSRAMDefaultPermissionLicenseConfiguration \
    --resource-arns arn:aws:license-manager::123456789012:license-configuration:lic-abc123 \
    --principals arn:aws:organizations::ExampleAWSAccountNo3;:organization/o-1234abcd
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