# Error: "Your account ID does not exist in an AWS organization"<a name="tshoot-no-slr"></a>

## Scenario<a name="tshoot-no-slr-scenario"></a>

You get the error "Your account ID does not exist in an AWS organization" when trying to share a resource with accounts or organizational units \(OUs\) in your organization\.

## Cause<a name="tshoot-no-slr-cause"></a>

This error can happen if the service\-linked role [AWSServiceRoleForResourceAccessManager](https://console.aws.amazon.com/iam/home#/roles/AWSServiceRoleForResourceAccessManager) isn't successfully created when you turn on integration between AWS Resource Access Manager and AWS Organizations\.

## Solution<a name="tshoot-no-slr-fix"></a>

To re\-create the required service\-linked role, perform the following steps to turn off integration and then turn it on again\. 

1. Sign in to your the management account of your organization using an IAM role or user with administrative permissions\.

1. Navigate to the [Services page in the AWS Organizations console](https://console.aws.amazon.com/organizations/v2/home/services)\.

1. Choose **RAM**\.

1. Choose **Disable trusted access**\.

1. Navigate to the [Settings page in the AWS RAM console](https://console.aws.amazon.com/ram/home#Settings:)\.

1. Select the box **Enable sharing with AWS Organizations**, and then choose **Save settings**\.

You should now be able to use AWS RAM to share your resources with accounts and OUs in the organization\.