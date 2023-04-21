# You can't share a VPC subnet<a name="tshoot-subnet-limits"></a>

## Scenario<a name="tshoot-subnet-limits-scenario"></a>

When you attempt to use AWS RAM to share a VPC subnet with another account, the sharing operation succeeds\. However, the consuming account shows `LIMIT EXCEEDED` for that resource in the AWS RAM console\.

## Cause<a name="tshoot-subnet-limits-cause"></a>

Some individual resource types have service\-specific restrictions separate from the restrictions enforced by AWS RAM\. Some of those restrictions can effectively prevent sharing even if you haven't reached one of the restrictions in AWS RAM\. Limits are an example of these restrictions\. Amazon Virtual Private Cloud \(Amazon VPC\) limits the number of subnets that you can share with another individual account\. If you try to share a subnet with a consuming account that already contains the maximum number of subnets, then that consuming accounts displays `LIMIT EXCEEDED` in the console for that resource\. For more information about this limit, see [Amazon VPC Quotas – VPC sharing](https://docs.aws.amazon.com/vpc/latest/userguide/amazon-vpc-limits.html#vpc-share-limits) in the *Amazon Virtual Private Cloud User Guide*\. 

To address this, first check for other resource shares that might be sharing the specified resource with the affected account, and remove those shares that you might no longer require\. You can also request an increase for a limit that supports adjusting\. Use the [Service Quotas console](https://console.aws.amazon.com/servicequotas) to request a limit increase\.

**Note**  
AWS RAM doesn't automatically detect limit increase changes\. You must re\-associate the resource or principal to the resource share for RAM to detect the change\.