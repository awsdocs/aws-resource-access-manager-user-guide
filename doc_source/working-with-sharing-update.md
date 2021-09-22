# Update a resource share in AWS Resource Access Manager<a name="working-with-sharing-update"></a>

You can update a resource share at any time in the following ways:
+ You can add principals, resources, or tags to a resource share that you created\.
+ For resource types that support more than the default AWS RAM managed permission, you can choose a different permission\.
+ You can revoke access to shared resources by removing principals or resources from a resource share\. If you revoke access, principals no longer have access to the shared resources\.

**Note**  
Principals with whom you share resources can leave your resource share if the share is empty or contains only resource types that support leaving a resource share\. If the resource share contains resource types that do not support leaving, a message might appear to inform principals that they must contact the share owner\. In this case, you must remove the principals from your resource share\. For a list of resource types that do not support this action, see [Prerequisites for leaving a resource share](working-with-shared-leave.md#working-with-shared-leave-prerequisites)\.

------
#### [ Console ]

**To update a resource share**

1. Navigate to the [https://console.aws.amazon.com/ram/home#OwnedResourceShares:](https://console.aws.amazon.com/ram/home#OwnedResourceShares:) page in the AWS RAM console\.

1. Because AWS RAM resource shares exist in specific AWS Regions, choose the appropriate AWS Region from the drop\-down list in the upper\-right corner of the console\.

1. Select the resource share and then choose **Modify**\.

1. In **Step 1: Specify resource share details**, review the resource share details, and if required, update any of the following:

   1. \(Optional\) To change the name of the resource share, edit **Name**\.

   1. \(Optional\) To add a resource to the resource share, under **Resources**, choose the type of resource and then select the check box next to the resource to add to the resource share\.

   1. \(Optional\) To remove a resource from the resource share, locate the resource under **Selected resources**, and then choose the **X** next to the resource's ID\.

   1. \(Optional\) To add a tag to the resource share, under **Tags**, enter a tag key and value in the empty text boxes\. To add a new empty text box pair for an addition tag, choose **Add new tag**\. You can add up to 50 tags\. pair\.

   1. To remove a tag from the resource share, under **Tags**, locate the tag and choose **Remove** next to it\.

1. Choose **Next**\.

1. \(Optional\) In **Step 2: Associate a permission with each resource type**, if more than the default AWS RAM managed permission is available, you can choose the permission to associate with the resource type\. For more information, see [Types of AWS RAM managed permissions](security-ram-permissions.md#permissions-types)\. If only the default AWS RAM managed permission is available, then you can't alter anything for this resource type\.

   To display the actions that the AWS RAM managed permission allows, choose **View the actions that are allowed by this permission** to expand it and display the list\.

1. Choose **Next**\.

1. In **Step 3: Choose principals that are allowed to access**, review the selected principals, and if required, update any of the following:

   1. \(Optional\) To change whether sharing is enabled with principals inside or outside your organization, choose one of the following options:
      + To share resources with AWS accounts, IAM users, and IAM roles that are outside of your organization, choose **Allow sharing with external principals**\.
      + To restrict resource sharing to only principals in your organization in AWS Organizations, choose **Allow sharing with principals in your organization only**\.

   1. For **Principals**, do the following:
      + \(Optional\) To add an organization, organizational unit \(OU\), or AWS account inside your organization, turn on **Display organizational structure** to display a "tree" view of your organization\. Then select the check box next to each principal that you want to add\.
**Note**  
The **Display organizational structure **toggle appears only if sharing with AWS Organizations is enabled and you are signed in as a principal in the organization's management account\.  
You can't use this method to specify an AWS account outside your organization, or an IAM role or IAM user\. Instead, you must add these principals by typing their identifiers in from the text box below the **Display organizational structure** switch\. See the next bullet\.
      + \(Optional\) To add a principal by its identifier, choose the principal type from the drop\-down list, and then enter the ID or ARN for the principal\. Finally, choose **Add**\.

        The addition immediately appears in the **Selected principals** list\.

        You can then add additional accounts, OUs, or your organization by repeating this step\.
      + \(Optional\) To remove a principal, locate it under **Selected principals**, select its checkbox, and then choose **Deselect**\. 

1. Choose **Next**\.

1. In **Step 4: Review and update**, review the configuration details for your resource share\. To change the configuration for any step, choose the link that corresponds to the step you want to go back to, and make the required changes\.

1. Choose **Update resource share** when you are done making changes\.

------
#### [ AWS CLI ]

**To update a resource share \(AWS CLI\)**  
You can use the following AWS CLI commands to modify a resource share:
+ To rename a resource share, or to change whether external principals are allowed, use the command `[update\-resource\-share](https://docs.aws.amazon.com/cli/latest/reference/ram/update-resource-share.html)`\. The following example renames the specified resource share and sets it to allow only principals from its organization\.

  ```
  $ aws ram update-resource-share \
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
+ To add a resource to a resource share, use the command `[associate\-resource\-share](https://docs.aws.amazon.com/cli/latest/reference/ram/associate-resource-share.html)`\. The following example adds a subnet to the specified resource share\.

  ```
  $ aws ram associate-resource-share \
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
+ To add or replace a AWS RAM managed permission for a resource type in a resource share, use the commands `[list\-permissions](https://docs.aws.amazon.com/cli/latest/reference/ram/list-permissions.html)` and `[associate\-resource\-share\-permission](https://docs.aws.amazon.com/cli/latest/reference/ram/associate-resource-share-permission.html)`\. Note that you can assign only one permission per resource type in a resource share\. If you attempt to add one to a resource type that already has a permission, you must include the `--replace` option or the command fails with an error\.

  The following example commands lists the ARNs for the permissions available for an Amazon EC2 Subnet, and then uses one of them to replace the currently assigned permission for that resource type in the specified resource share\. 

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
      --resource-share-arn arn:aws:ram:us-east-1:123456789012:resource-share/f1d72a60-da19-4765-b4f9-e27b658b15b8 \
      --permission-arn arn:aws:ram::aws:permission/AWSRAMDefaultPermissionSubnet
  {
      "returnValue": true
  }
  ```
+ To remove a resource from a resource share, use the command [disassociate\-resource\-share](https://docs.aws.amazon.com/cli/latest/reference/ram/disassociate-resource-share.html)\. The followi example removes the Amazon EC2 subnet with the specified AN from the specified resource share\.

  ```
  $ aws ram disassociate-resource-share \
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
+ To modify the tags attached to a resource share, use the commands [tag\-resource](https://docs.aws.amazon.com/cli/latest/reference/ram/tag-resource.html) and [untag\-resource](https://docs.aws.amazon.com/cli/latest/reference/ram/untag-resource.html)\. The following example adds the tag `project=lima` to the specified resource share\.

  ```
  $ aws ram tag-resource \
      --resource-share-arn arn:aws:ram:us-east-1:123456789012:resource-share/f1d72a60-da19-4765-b4f9-e27b658b15b8 \
      --tags key=project,value=lima
  ```

  The following example removes the tag with a key of `project` from the specified resource share\.

  ```
  $ aws ram untag-resource \
      --resource-share-arn arn:aws:ram:us-east-1:123456789012:resource-share/f1d72a60-da19-4765-b4f9-e27b658b15b8 \
      --tag-keys=project
  ```

  The tagging commands produce no output when successful\.

------