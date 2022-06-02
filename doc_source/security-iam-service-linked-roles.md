# Using Service\-Linked Roles for AWS RAM<a name="security-iam-service-linked-roles"></a>

AWS Resource Access Manager uses AWS Identity and Access Management \(IAM\)[ service\-linked roles](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_terms-and-concepts.html#iam-term-service-linked-role)\. A service\-linked role is a unique type of IAM role that is linked directly to the AWS RAM service\. Service\-linked roles are predefined by AWS and include all the permissions that AWS RAM needs to call other AWS services on your behalf\.

A service\-linked role makes configuring AWS RAM easier because you don’t have to manually add the necessary permissions\. AWS RAM defines the permissions of its service\-linked roles, and unless defined otherwise, only AWS RAM can assume its service\-linked roles\. The defined permissions include both a trust policy and a permissions policy, and that permissions policy cannot be attached to any other IAM entity\.

For information about other services that support service\-linked roles, see [AWS Services That Work with IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_aws-services-that-work-with-iam.html) and look for the services that have **Yes **in the **Service\-Linked Role** column\. Choose a **Yes** with a link to view the service\-linked role documentation for that service\.

## Service\-Linked Role Permissions for AWS RAM<a name="slr-permissions"></a>

AWS RAM uses the service\-linked role named `AWSServiceRoleForResourceAccessManager` when you enable sharing with AWS Organizations\. This role grants permissions to the AWS RAM service to view organization details, such as the list of member accounts and which organizational units each account is in\.

This service\-linked role trusts the following service to assume the role:
+ `ram.amazonaws.com`

The role permissions policy named AWSResourceAccessManagerServiceRolePolicy is attached to this service\-linked role, and allows AWS RAM to complete the following actions on the specified resources:
+ Actions: read\-only actions that retrieve details about your organization's structure\. For the complete list of actions, you can view the policy in the IAM console: [AWSResourceAccessManagerServiceRolePolicy](https://console.aws.amazon.com/iam/home#/policies/arn:aws:iam::aws:policy/aws-service-role/AWSResourceAccessManagerServiceRolePolicy$jsonEditor)\.

For a principal to turn on AWS RAM sharing within your organization, that principal \(an IAM entity such as a user, group, or role\), must have permission to create a service\-linked role\. For more information, see [Service\-Linked Role Permissions](https://docs.aws.amazon.com/IAM/latest/UserGuide/using-service-linked-roles.html#service-linked-role-permissions) in the *IAM User Guide*\.

## Creating a Service\-Linked Role for AWS RAM<a name="create-slr"></a>

You don't need to manually create a service\-linked role\. When you turn on AWS RAM sharing within your organization in the AWS Management Console, or run the [EnableSharingWithAwsOrganization](https://docs.aws.amazon.com/ram/latest/APIReference/API_EnableSharingWithAwsOrganization.html) in your account using the AWS CLI or an AWS API, AWS RAM creates the service\-linked role for you\. 

If you delete this service\-linked role, then AWS RAM no longer has permissions to view the details of your organization's structure\.

## Editing a service\-linked role for AWS RAM<a name="edit-slr"></a>

AWS RAM does not allow you to edit the AWSResourceAccessManagerServiceRolePolicy service\-linked role\. After you create a service\-linked role, you cannot change the name of the role because various entities might reference the role\. However, you can edit the description of the role using IAM\. For more information, see [Editing a Service\-Linked Role](https://docs.aws.amazon.com/IAM/latest/UserGuide/using-service-linked-roles.html#edit-service-linked-role) in the *IAM User Guide*\.

## Deleting a Service\-Linked Role for AWS RAM<a name="delete-slr"></a>

You can use the IAM console, the AWS CLI or the AWS API to manually delete the service\-linked role\.

**To manually delete the service\-linked role using IAM**

Use the IAM console, the AWS CLI, or the AWS API to delete the `AWSResourceAccessManagerServiceRolePolicy` service\-linked role\. For more information, see [Deleting a Service\-Linked Role](https://docs.aws.amazon.com/IAM/latest/UserGuide/using-service-linked-roles.html#delete-service-linked-role) in the *IAM User Guide*\.

## Supported Regions for AWS RAM Service\-Linked Roles<a name="slr-regions"></a>

AWS RAM supports using service\-linked roles in all of the Regions where the service is available\. For more information, see [AWS Regions and Endpoints](https://docs.aws.amazon.com/general/latest/gr/rande.html) in the *Amazon Web Services General Reference*\.