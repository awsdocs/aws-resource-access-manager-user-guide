# Error: "UnknownResourceException"<a name="tshoot-unknown-resource"></a>

## Scenario<a name="tshoot-unknown-resource-scenario"></a>

You get one of the following errors: 
+ "CannotCreateResourceShare: UnknownResourceException: OrganizationalUnit ou\-*xxxx* could not be found"
+ "CannotUpdateResourceShare: UnknownResourceException: OrganizationalUnit ou\-*xxxx* could not be found"\.

## Cause<a name="tshoot-unknown-resource-cause"></a>

These errors can occur if you enable integration between AWS RAM and AWS Organizations by using either the [Organizations console or the Organizations EnableAWSServiceAccess API](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_integrate_services.htm) instead of by [using the AWS RAM console](getting-started-sharing.md#getting-started-sharing-orgs)\. When you enable integration by using the Organizations console or API, the service doesn’t create the `AWSServiceRoleForResourceAccessManager` role in your account\. That role is needed to access information about your organization\. Because the role wasn't created, AWS RAM can’t access details about the accounts or organizational units \(OUs\) in your organization\.

## Solution<a name="tshoot-unknown-resource-fix"></a>

To resolve the issue, turn off integration between AWS RAM and AWS Organizations\. Then turn it on again by calling the AWS RAM [EnableSharingWithAwsOrganization](https://docs.aws.amazon.com/ram/latest/APIReference/API_EnableSharingWithAwsOrganization.html) API operation, or by using the AWS Management Console to perform the following steps\.

1. Sign in to your the management account of your organization using an IAM role or user with administrative permissions\.

1. Navigate to the [Services page in the AWS Organizations console](https://console.aws.amazon.com/organizations/v2/home/services)\.

1. Choose **RAM**\.

1. Choose **Disable trusted access**\.

1. Navigate to the [Settings page in the AWS RAM console](https://console.aws.amazon.com/ram/home#Settings:)\.

1. Select the box **Enable sharing with AWS Organizations**, and then choose **Save settings**\.

You should now be able to use AWS RAM to share your resources with accounts and OUs in the organization\.