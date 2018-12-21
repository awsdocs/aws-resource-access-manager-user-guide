# Using Service\-Linked Roles for AWS RAM<a name="using-service-linked-roles"></a>

When you share resources within an organization in AWS Organizations, AWS Resource Access Manager requires a [ service\-linked role](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_terms-and-concepts.html#iam-term-service-linked-role) to enable trusted access with AWS Organizations\. A service\-linked role is a unique type of IAM role that is linked directly to AWS RAM\. You use AWS RAM to create a service\-linked role that includes all the permissions that the service requires to call other AWS services on your behalf\.

The service\-linked role for AWS RAM makes setting up resource sharing within your organization easier because you don't have to manually add the necessary permissions\. AWS RAM defines the permissions of its service\-linked role, and only AWS RAM can assume the service\-linked role\. The defined permissions include the trust policy and the permissions policy, and that permissions policy cannot be attached to any other IAM entity\.

For information about other services that support service\-linked roles, see [AWS Services That Work with IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_aws-services-that-work-with-iam.html)\. Look for the services that have **Yes** in the **Service\-Linked Role** column\. To view the service\-linked role documentation for a service, choose **Yes** for that service\.

## Service\-Linked Role Permissions for AWS RAM<a name="slr-permissions"></a>

AWS RAM uses the service\-linked role named **AWSServiceRoleForResourceAccessManager** to call the following actions on your behalf when you share resources within your organization:
+ `organizations:DescribeAccount`
+ `organizations:DescribeOrganization`
+ `organizations:DescribeOrganizationalUnit`
+ `organizations:ListAccounts`
+ `organizations:ListAccountsForParent`
+ `organizations:ListChildren`
+ `organizations:ListOrganizationalUnitsForParent`
+ `organizations:ListParents`
+ `organizations:ListRoots`

It also provides permission to delete the service\-linked role named **AWSServiceRoleForResourceAccessManager**\.

The **AWSServiceRoleForResourceAccessManager** service\-linked role trusts the ram\.amazonaws\.com service to assume the role\.

You must configure permissions to allow an IAM entity \(such as a user, group, or role\) to create, edit, or delete a service\-linked role\. For more information, see [Service\-Linked Role Permissions](https://docs.aws.amazon.com/IAM/latest/UserGuide/using-service-linked-roles.html#service-linked-role-permissions) in the *IAM User Guide*\.

## Creating a Service\-Linked Role for AWS RAM<a name="create-slr"></a>

You can create the service\-linked role using the AWS RAM console or the AWS CLI\.

**To create the service\-linked role \(console\)**

1. Open the AWS RAM console at [https://console\.aws\.amazon\.com/ram](https://console.aws.amazon.com/ram/)\.

1. In the navigation pane, choose **Settings**\.

1. Select **Enable resource sharing with AWS Organizations**\.

1. Choose **Save settings**\.

**To create the service\-linked role \(AWS CLI\)**  
Use the [ enable\-sharing\-with\-aws\-organization](https://docs.aws.amazon.com/cli/latest/reference/ram/enable-sharing-with-aws-organization.html) AWS CLI command\.

Alternatively, you can use the IAM [create\-service\-linked\-role](https://docs.aws.amazon.com/cli/latest/reference/iam/create-service-linked-role.html) CLI command and specify the ram\.amazonaws\.com service name\. For more information, see [Creating a Service\-Linked Role](https://docs.aws.amazon.com/IAM/latest/UserGuide/using-service-linked-roles.html#create-service-linked-role) in the *IAM User Guide*\.

 If you delete the service\-linked role, you can use these same processes to create the role again\.

## Editing a Service\-Linked Role for AWS RAM<a name="edit-slr"></a>

AWS RAM does not allow you to edit the **AWSServiceRoleForResourceAccessManager** service\-linked role\. After you create a service\-linked role, you cannot change the name of the role because various entities might reference the role\. However, you can edit the description of the role using IAM\. For more information, see [Editing a Service\-Linked Role](https://docs.aws.amazon.com/IAM/latest/UserGuide/using-service-linked-roles.html#edit-service-linked-role) in the *IAM User Guide*\.

## Deleting a Service\-Linked Role for AWS RAM<a name="delete-slr"></a>

If you no longer need to use a feature or service that requires a service\-linked role, we recommend that you delete that role\.

You can delete a service\-linked role only after first deleting their related resources\. This ensures that you can't inadvertently remove permission to access the resources\.

**To manually delete the service\-linked role for AWS RAM**

1. Disable trusted access to AWS Organizations using the AWS Organizations [disable\-aws\-service\-access](https://docs.aws.amazon.com/cli/latest/reference/organizations/disable-aws-service-access.html) CLI command\.

   ```
   $  aws organizations disable-aws-service-access --service-principal ram.amazonaws.com
   ```
**Important**  
When you disable trusted access to AWS Organizations, principals within your organizations are removed from all resource shares and lose access to those shared resources\.

1. Use the IAM console, the IAM CLI, or the IAM API to delete the **AWSServiceRoleForResourceAccessManager** service\-linked role\. For more information, see [Deleting a Service\-Linked Role](https://docs.aws.amazon.com/IAM/latest/UserGuide/using-service-linked-roles.html#delete-service-linked-role) in the *IAM User Guide*\.