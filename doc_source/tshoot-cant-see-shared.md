# Can't see shared resources in the destination account<a name="tshoot-cant-see-shared"></a>

## Scenario<a name="tshoot-cant-see-shared-scenario"></a>

Users can't see the resources that they believe are shared with them from other AWS accounts\.

## Possible causes and solutions<a name="tshoot-cant-see-shared-causes-and-solutions"></a>

### Sharing with AWS Organizations was turned on by using Organizations instead of AWS RAM<a name="tshoot-cant-see-shared-1"></a>

If AWS Organizations was turned on by using Organizations instead of AWS RAM, then sharing within the organization fails\. To check if this is the cause of the problem, navigate to the [Settings page in the AWS RAM console](https://console.aws.amazon.com/ram/home#Settings:) and verify that the **Enable sharing with AWS Organizations** check box is selected\. 
+ If the check box is selected, then this is not the cause\.
+ If the check box is not selected, then this might be the cause\. *Don't select the check box yet*\. Perform the following steps to correct the situation\.

1. Sign in to your the management account of your organization using an IAM role or user with administrative permissions\.

1. Navigate to the [Services page in the AWS Organizations console](https://console.aws.amazon.com/organizations/v2/home/services)\.

1. Choose **RAM**\.

1. Choose **Disable trusted access**\.

1. Navigate to the [Settings page in the AWS RAM console](https://console.aws.amazon.com/ram/home#Settings:)\.

1. Select the box **Enable sharing with AWS Organizations**, and then choose **Save settings**\.

You might need to [update the share and specify the accounts or organizational units](working-with-sharing-update.md) within the organization to share with\.

### The resource share doesn't specify this account as a principal<a name="tshoot-cant-see-shared-2"></a>

In the AWS account that created the resource share, [view the resource share](working-with-sharing-view-sr.md) in the [AWS RAM console](https://console.aws.amazon.com/ram/home)\. Verify that the account that can't access the resources is listed as a **Principal**\. If it isn't, then [update the share to add the account as a principal](working-with-sharing-update.md)\.

### The role or user in the account doesn't have required minimum permissions<a name="tshoot-cant-see-shared-3"></a>

When you share a resource in account A to another account B, roles and users in account B don't automatically get access to the resources in the share\. The administrator of account B must first grant permission to the IAM roles and users in account B who need to access the resource\. As an example, the following policy shows how you might grant read\-only access to roles and users in account B for a resource from account A\. The policy specifies the resource by its [Amazon Resource Name \(ARN\)](https://docs.aws.amazon.com/general/latest/gr/aws-arns-and-namespaces.html)\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Action": [
                "ram:Get*",
                "ram:List*"
            ],
            "Effect": "Allow",
            "Resource": "arn:aws:<service>:<Region-code>:<Account-A-ID>:<resource-id>"
        }
    ]
}
```

### The resource is in a different AWS Region than the current console setting<a name="tshoot-cant-see-shared-4"></a>

AWS RAM is a Regional service\. Resources exist in a specific AWS Region, and to see them, the AWS Management Console must be configured to view the resources in that Region\.

The AWS Region that the console is currently accessing is displayed in the upper\-right corner of the console\. To change it, choose the current Region name and from the dropdown menu, choose the Region whose resources you want to see\.