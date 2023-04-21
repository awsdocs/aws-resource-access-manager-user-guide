# Update a resource share in AWS RAM<a name="working-with-sharing-update"></a>

You can update a resource share in AWS RAM at any time in the following ways:
+ You can add principals, resources, or tags to a resource share that you created\.
+ For resource types that support more than the default AWS managed permission, you can choose which managed permission applies to resources of each type\.
+ When a managed permission attached to the resource share has a new default version, you can update the managed permission to use the new version\.
+ You can revoke access to shared resources by removing principals or resources from a resource share\. If you revoke access, principals no longer have access to the shared resources\.

**Note**  
Principals with whom you share resources can leave your resource share if the share is empty or contains only resource types that support leaving a resource share\. If the resource share contains resource types that don't support leaving, a message appears to inform principals that they must contact the share owner\. In this case, you, as the owner of the resource share, must remove the principals from your resource share\. For a list of resource types that don't support this action, see [Prerequisites for leaving a resource share](working-with-shared-leave.md#working-with-shared-leave-prerequisites)\.

------
#### [ Console ]

**To update a resource share**

1. Navigate to the **[Shared by me : Resource shares](https://console.aws.amazon.com/ram/home#OwnedResourceShares:)** page in the AWS RAM console\.

1. Because AWS RAM resource shares exist in specific AWS Regions, choose the appropriate AWS Region from the dropdown list in the upper\-right corner of the console\. To see resource shares that contain global resources, you must set the AWS Region to US East \(N\. Virginia\), \(`us-east-1`\)\. For more information about sharing global resources, see [Sharing Regional resources compared to global resources](working-with-regional-vs-global.md)\.

1. Select the resource share and then choose **Modify**\.

1. In **Step 1: Specify resource share details**, review the resource share details, and if required, update any of the following:

   1. \(Optional\) To change the name of the resource share, edit **Name**\.

   1. \(Optional\) To add a resource to the resource share, under **Resources**, choose the type of resource and then select the check box next to the resource to add it to the resource share\. Global resources appear only if you set the Region to US East \(N\. Virginia\), \(`us-east-1`\) in the AWS Management Console\.

   1. \(Optional\) To remove a resource from the resource share, locate the resource under **Selected resources**, and then choose the **X** next to the resource's ID\.

   1. \(Optional\) To add a tag to the resource share, under **Tags**, enter a tag key and value in the empty text boxes\. To add more than one tag key and value pair, choose **Add new tag**\. You can add up to 50 tags\. 

   1. To remove a tag from the resource share, under **Tags**, locate the tag and choose **Remove** next to it\.

1. Choose **Next**\.

1. \(Optional\) In **Step 2: Associate a managed permission with each resource type**, you can choose to associate a managed permission created by AWS with the resource type, choose an existing customer managed permission, or you can create your own customer managed permission\. For more information, see [Types of managed permissions](security-ram-permissions.md#permissions-types)\.

   You can also choose **Create customer managed permission** to construct a customer managed permission that meets the requirements of your sharing use case\. For more information, see [Create a customer managed permission](create-customer-managed-permissions.md#create_cmp)\. After completing the process, choose ![\[Refresh icon\]](http://docs.aws.amazon.com/ram/latest/userguide/images/refresh_icon.PNG), and then you can select your new customer managed permission from the **Managed permission** dropdown list\.

   To display the actions that the managed permission allows, expand **View the policy template for this managed permission**\.

1. If the version of the managed permission currently assigned to the resource share isn't the current default version, then you can update to the default version by choosing **Update to default version**\.
**Note**  
Until you save your changes to the resource share after the final step, you can cancel the version update by choosing **Revert to previous version**\. However, for AWS managed permissions, after you save the resource share, the change is final and you can no longer return to the previous version\.

1. Choose **Next**\.

1. In **Step 3: Choose principals that are allowed to access**, review the selected principals, and if required, update any of the following:

   1. \(Optional\) To change whether sharing is enabled with principals inside or outside your organization, choose one of the following options:
      + To share resources with AWS accounts or individual IAM roles or users that are outside of your organization, choose **Allow sharing with external principals**\.
      + To restrict resource sharing to only principals in your organization in AWS Organizations, choose **Allow sharing with principals in your organization only**\.

   1. For **Principals**, do the following:
      + \(Optional\) To add an organization, organizational unit \(OU\), or member AWS account inside your organization, turn on **Display organizational structure** to display a tree view of your organization\. Then select the check box next to each principal that you want to add\.
**Important**  
When you share with an organization or an OU, and that scope includes the account that owns the resource share, all principals in the sharing account automatically get access to the resources in the share\. The access granted is defined by the managed permissions associated with the share\. This is because the resource\-based policy that AWS RAM attaches to each resource in the share uses `"Principal": "*"`\. For more information, see [Implications of using "Principal": "\*" in a resource\-based policy](getting-started-terms-and-concepts.md#term-principal-star)\.  
Principals in the other consuming accounts don't immediately get access to the share's resources\. The other accounts' administrators must first attach identity\-based permission policies to the appropriate principals\. Those policies must grant `Allow` access to the ARNs of individual resources in the resource share\. The permissions in those policies can't exceed those specified in the managed permission associated with the resource share\.
**Note**  
The **Display organizational structure **toggle appears only if sharing with AWS Organizations is enabled and you are signed in as a principal in the organization's management account\.  
You can't use this method to specify an AWS account outside your organization, or an IAM role or user\. Instead, you must add these principals by entering their identifiers, which are shown in the text box below the **Display organizational structure** switch\. See the next bullet point\.
      + \(Optional\) To add a principal by its identifier, choose the principal type from the dropdown list, and then enter the ID or ARN for the principal\. Finally, choose **Add**\.

        If you select an individual AWS account, then only that account can access the resource share\. You can choose either of the following options\.
        + **Another AWS account \(other than the resource owner\)** – Makes the resource available to the other account\. The administrator of that account must complete the process by granting access to the shared resource using identity\-based permission policies to individual roles and users\. Those permissions can't exceed those defined in the managed permissions attached to the resource share\.
        + **This AWS account \(resource owner\)** – All roles and users in the resource owning account automatically receive the access defined by the managed permissions attached to the resource share\.
      + The addition immediately appears in the **Selected principals** list\.

        You can then add additional accounts, OUs, or your organization by repeating this step\.
      + \(Optional\) To remove a principal, locate it under **Selected principals**, select its check box, and then choose **Deselect**\. 

1. Choose **Next**\.

1. In **Step 4: Review and update**, review the configuration details for your resource share\. 

1. To change the configuration for any step, choose the link that corresponds to the step you want to go back to, and then make the required changes\.

   If any managed permissions are still using versions other than the default, you have another opportunity to address that by choosing **Update to default version**\.

1. Choose **Update resource share** when you're done making changes\.

------
#### [ AWS CLI ]

**To update a resource share**  
You can use the following AWS CLI commands to modify a resource share:
+ To rename a resource share, or to change whether external principals are allowed, use the command [https://docs.aws.amazon.com/cli/latest/reference/ram/update-resource-share.html](https://docs.aws.amazon.com/cli/latest/reference/ram/update-resource-share.html)\. The following example renames the specified resource share and sets it to allow only principals from its organization\. You must use the service endpoint for the AWS Region that contains the resource share\. 

  ```
  $ aws ram update-resource-share \
      --region us-east-1 \
      --resource-share-arn arn:aws:ram:us-east-1:123456789012:resource-share/7ab63972-b505-7e2a-420d-6f5d3EXAMPLE \
      --name "my-renamed-resource-share" \
      --no-allow-external-principals
  {
      "resourceShare": {
          "resourceShareArn": "arn:aws:ram:us-east-1:123456789012:resource-share/7ab63972-b505-7e2a-420d-6f5d3EXAMPLE",
          "name": "my-renamed-resource-share",
          "owningAccountId": "123456789012",
          "allowExternalPrincipals": false,
          "status": "ACTIVE",
          "creationTime": 1565295733.282,
          "lastUpdatedTime": 1565303080.023
      }
  }
  ```
+ To add a resource to a resource share, use the command [https://docs.aws.amazon.com/cli/latest/reference/ram/associate-resource-share.html](https://docs.aws.amazon.com/cli/latest/reference/ram/associate-resource-share.html)\. The following example adds a subnet to the specified resource share\.

  ```
  $ aws ram associate-resource-share \
      --region us-east-1 \
      --resource-arns arn:aws:ec2:us-east-1:123456789012:subnet/subnet-0250c25a1f4e15235 \
      --resource-share-arn arn:aws:ram:us-east-1:123456789012:resource-share/7ab63972-b505-7e2a-420d-6f5d3EXAMPLE
  {
      "resourceShareAssociations": [
          "resourceShareArn": "arn:aws:ram:us-east-1:123456789012:resource-share/7ab63972-b505-7e2a-420d-6f5d3EXAMPLE",
          "associatedEntity": "arn:aws:ec2:us-east-1:123456789012:subnet/subnet-0250c25a1f4e15235",
          "associationType": "RESOURCE",
          "status": "ASSOCIATING",
          "external": false
      ]
  }
  ```
+ To add or replace a managed permission for a resource type in a resource share, use the commands [https://docs.aws.amazon.com/cli/latest/reference/ram/list-permissions.html](https://docs.aws.amazon.com/cli/latest/reference/ram/list-permissions.html) and [https://docs.aws.amazon.com/cli/latest/reference/ram/associate-resource-share-permission.html](https://docs.aws.amazon.com/cli/latest/reference/ram/associate-resource-share-permission.html)\. You can assign only one managed permission per resource type in a resource share\. If you try to add a managed permission to a resource type that already has a managed permission, you must include the `--replace` option or the command fails with an error\.

  The following example command lists the ARNs for the managed permissions available for an Amazon Elastic Compute Cloud \(Amazon EC2\) subnet, and then uses one of those ARNs to replace the currently assigned AWS managed permission for that resource type in the specified resource share\. 

  ```
  $ aws ram list-permissions \
      --resource-type ec2:Subnet
  {
      "permissions": [
          {
              "arn": "arn:aws:ram::aws:permission/AWSRAMDefaultPermissionSubnet",
              "version": "1",
              "defaultVersion": true,
              "name": "AWSRAMDefaultPermissionSubnet",
              "resourceType": "ec2:Subnet",
              "creationTime": "2020-02-27T11:38:26.727000-08:00",
              "lastUpdatedTime": "2020-02-27T11:38:26.727000-08:00"
          }
      ]
  }
  $ aws ram associate-resource-share-permission \
      --region us-east-1 \
      --resource-share-arn arn:aws:ram:us-east-1:123456789012:resource-share/f1d72a60-da19-4765-b4f9-e27b658b15b8 \
      --permission-arn arn:aws:ram::aws:permission/AWSRAMDefaultPermissionSubnet
  {
      "returnValue": true
  }
  ```
+ To remove a resource from a resource share, use the command [https://docs.aws.amazon.com/cli/latest/reference/ram/disassociate-resource-share.html](https://docs.aws.amazon.com/cli/latest/reference/ram/disassociate-resource-share.html)\. The following example removes the Amazon EC2 subnet with the specified ARN from the specified resource share\.

  ```
  $ aws ram disassociate-resource-share \
      --region us-east-1 \
      --resource-arns arn:aws:ec2:us-east-1:123456789012:subnet/subnet-0250c25a1f4e15235 \
      --resource-share-arn arn:aws:ram:us-east-1:123456789012:resource-share/7ab63972-b505-7e2a-420d-6f5d3EXAMPLE
  {
      "resourceShareAssociations": [
          "resourceShareArn": "arn:aws:ram:us-east-1:123456789012:resource-share/7ab63972-b505-7e2a-420d-6f5d3EXAMPLE",
          "associatedEntity": "arn:aws:ec2:us-east-1:ubnet/subnet-0250c25a1f4e15235",
          "associationType": "RESOURCE",
          "status": "DISASSOCIATING",
          "external": false
      ]
  }
  ```
+ To modify the tags attached to a resource share, use the commands [https://docs.aws.amazon.com/cli/latest/reference/ram/tag-resource.html](https://docs.aws.amazon.com/cli/latest/reference/ram/tag-resource.html) and [https://docs.aws.amazon.com/cli/latest/reference/ram/untag-resource.html](https://docs.aws.amazon.com/cli/latest/reference/ram/untag-resource.html)\. The following example adds the tag `project=lima` to the specified resource share\.

  ```
  $ aws ram tag-resource \
      --region us-east-1 \
      --resource-share-arn arn:aws:ram:us-east-1:123456789012:resource-share/f1d72a60-da19-4765-b4f9-e27b658b15b8 \
      --tags key=project,value=lima
  ```

  The following example removes the tag with a key of `project` from the specified resource share\.

  ```
  $ aws ram untag-resource \
      --region us-east-1 \
      --resource-share-arn arn:aws:ram:us-east-1:123456789012:resource-share/f1d72a60-da19-4765-b4f9-e27b658b15b8 \
      --tag-keys=project
  ```

  The tagging commands produce no output when successful\.

------