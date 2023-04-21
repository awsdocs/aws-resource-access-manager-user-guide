# Updating AWS managed permissions to a newer version<a name="working-with-sharing-update-permissions"></a>

Occasionally, AWS updates the AWS managed permissions available to attach to a resource share for a specific resource type\. When AWS does this, it creates a new version of the AWS managed permission\. Resource shares that include the specified resource type aren't automatically updated to use the latest version of the managed permission\. You must explicitly update the managed permission for each resource share\. This extra step is required so that you can evaluate the changes before you apply them to your resource shares\.

------
#### [ Console ]

 Whenever the console displays a page that lists the permissions associated with a resource share, and one or more of those permissions are using a version other than the default for the permission, the console displays a banner at the top of the console page\. The banner indicates that your resource share is using a version other than the default\.

In addition, individual permissions can display an **Update to default version** button next to the current version number when that version is not the default\.

Choosing that button starts the [**Update resource share**](working-with-sharing-update.md) wizard\. On Step 2 of the wizard you can update the version of any non\-default permissions to use their default versions\.

The changes are not saved until you complete the wizard by choosing **Submit** on the last page of the wizard\. 

**Note**  
You can attach only the default version, and you can't revert to another version\.  
For customer managed permissions, after you update the permissions to the default version, you can't apply another version to a resource share unless you first set that other version as the default\. For example, if you updated a permission to the default version and then found an error that you wanted to roll back, you could designate the previous version as the default\. Alternatively, you could create a different new version and then designate that as the default\. After you performed one of those options, you would then update your resource shares to use what is now the default version\.

------
#### [ AWS CLI ]

 **To update the version of an AWS managed permission**

1. Run the command [https://docs.aws.amazon.com/cli/latest/reference/ram/get-resource-shares.html](https://docs.aws.amazon.com/cli/latest/reference/ram/get-resource-shares.html) with the `--permission-arn` parameter to specify the [Amazon Resource Name \(ARN\)](https://docs.aws.amazon.com/general/latest/gr/aws-arns-and-namespaces.html) of the managed permission that you want to update\. This results in the command returning only those resource shares that use that managed permission\.

   For example, the following sample command returns details for every resource share that uses the default AWS managed permission for Amazon EC2 capacity reservations\.

   ```
   $ aws ram get-resource-shares \
       --resource-owner SELF \
       --permission-arn arn:aws:ram::aws:permission/AWSRAMDefaultPermissionCapacityReservation
   ```

   The output includes the ARN of every resource share with at least one resource whose access is controlled by that managed permission\.

1. For each resource share specified in the previous command, run the command [https://docs.aws.amazon.com/cli/latest/reference/ram/associate-resource-share-permission.html](https://docs.aws.amazon.com/cli/latest/reference/ram/associate-resource-share-permission.html)\. Include the `--resource-share-arn` to specify the resource share to update, the `--permission-arn` to specify which AWS managed permission you're updating, and the `--replace` parameter to specify that you want to update the share to use the latest version of that managed permission\. You don't need to specify the version number; the default version is automatically used\.

   ```
   $ aws ram associate-resource-share-permission \
       --resource-share-arn < ARN of one of the shares from the output of the previous command > \
       --permission-arn arn:aws:ram::aws:permission/AWSRAMDefaultPermissionCapacityReservation \
       --replace
   ```

1. Repeat the command in the previous step for each `ResourceShareArn` that you received in the results from the command in step 1\.

------