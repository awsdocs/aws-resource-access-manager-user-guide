# Updating AWS RAM managed permissions to a newer version<a name="working-with-sharing-update-permissions"></a>

From time to time, AWS updates the managed permissions you can attach to a resource share for a specific resource type\. When AWS does this, it creates a new version of the managed permission\. Resource shares that include the specified resource type don't automatically use the latest version of the managed permission\. You must explicitly update the managed permission for each resource share yourself\. This helps ensure you can evaluate the changes before you apply them to your resource shares\.

------
#### [ Console ]

At this time, you can perform this task only by using the AWS CLI operations for AWS RAM, or their AWS SDK equivalents\.

------
#### [ AWS CLI ]

 **To update the version of an AWS RAM managed permission** 

1. Run the command [get\-resource\-shares](https://docs.aws.amazon.com/cli/latest/reference/ram/get-resource-shares.html) with the `--permission-arn` parameter to specify the [Amazon Resource Name \(ARN\)](https://docs.aws.amazon.com/general/latest/gr/aws-arns-and-namespaces.html) of the managed permission that you want to update\. This results in the command returning only those resource shares that use that managed permission\.

   For example, the following sample command returns details for every resource share that uses the default AWS RAM managed permission for Amazon EC2 capacity reservations\.

   ```
   $ aws ram get-resource-shares \
       --resource-owner SELF \
       --permission-arn arn:aws:ram::aws:permission/AWSRAMDefaultPermissionCapacityReservation
   ```

   The output includes the ARN of every resource share with at least one resource whose access is controlled by that managed permission\.

1. For each resource share specified in the previous command, run the command [associate\-resource\-share\-permission](https://docs.aws.amazon.com/cli/latest/reference/ram/associate-resource-share-permission.html)\. Include the `--resource-share-arn` to specify the resource share to update, the `--permission-arn` to specify which AWS RAM managed permission you're updating, and the `--replace` parameter to specify that you want to update the share to use the latest version of that managed permission\.

   ```
   $ aws ram associate-resource-share-permission \
       --resource-share-arn < ARN of one of the shares from the output of the previous command > \
       --permission-arn arn:aws:ram::aws:permission/AWSRAMDefaultPermissionCapacityReservation \
       --replace
   ```

1. Repeat the command in step 2 for each `ResourceShareArn` you received in the results from the command in step 1\.

------