# Errors when trying to share with accounts outside of my organization<a name="tshoot-sharing-outside-org"></a>

## Scenario<a name="tshoot-sharing-outside-org-scenario"></a>

You get one of the following errors when you try to share resources with accounts that are outside of your organization:
+ "You cannot share the resource outside your organization\."
+ "The resource you are attempting to share can only be shared within your AWS Organization\."
+ "InvalidParameterException: Principal Account\-ID is not in your AWS organization\. You do not have permission to add external AWS accounts to a resource share\."
+ "OperationNotPermittedException: The resource you are attempting to share can only be shared within your AWS Organization\."

## Possible causes and solutions<a name="tshoot-sharing-outside-org-causes-and-solutions"></a>

### Some resource types can be shared only with accounts in the same organization<a name="tshoot-sharing-outside-org-1"></a>

Some resource types can’t be shared with any account that isn't a member of that organization\. An example resource type with this restriction is virtual private connections \(VPCs\) that are part of Amazon Elastic Compute Cloud \(Amazon EC2\)\.

To verify if you can share a particular resource type with accounts and principals outside of your organization, see [Shareable AWS resources](https://docs.aws.amazon.com/ram/latest/userguide/shareable.html)\.

### The service\-linked role wasn't successfully created<a name="tshoot-sharing-outside-org-2"></a>

This issue can occur if the service\-linked role `AWSServiceRoleForResourceAccessManager` wasn't successfully created when you turned on integration between AWS RAM and AWS Organizations\.

If you receive one of these errors when attempting to share a resource with an account that ***is*** part of your organization, perform the following steps to delete and re\-create the service\-linked role\.

1. Sign in to your the management account of your organization using an IAM role or user with administrative permissions\.

1. Navigate to the [Services page in the AWS Organizations console](https://console.aws.amazon.com/organizations/v2/home/services)\.

1. Choose **RAM**\.

1. Choose **Disable trusted access**\.

1. Navigate to the [Settings page in the AWS RAM console](https://console.aws.amazon.com/ram/home#Settings:)\.

1. Select the box **Enable sharing with AWS Organizations**, and then choose **Save settings**\.