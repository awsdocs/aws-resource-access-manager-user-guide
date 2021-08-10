# Share AWS resources owned by you<a name="working-with-sharing"></a>

You can use AWS RAM to share the resources that you specify with the principals that you specify\. At any time, you can modify resource shares that you created and delete them when they are no longer needed\.

**Topics**
+ [Create a resource share](#working-with-sharing-create)
+ [Update a resource share](#working-with-sharing-update)
+ [View a resource share](#working-with-sharing-view-rs)
+ [View your shared resources](#working-with-sharing-view-sr)
+ [View principals](#working-with-sharing-view-accounts)
+ [View AWS RAM managed permissions](#working-with-sharing-view-permissions)
+ [Delete a resource share](#working-with-sharing-delete)
+ [Supported actions on shared resources](#working-with-sharing-view-permissions)

## Create a resource share<a name="working-with-sharing-create"></a>

To share resources that you own, create a resource share\. When you create a resource share, you do the following:

1. Add the resources to share\.

1. If more than the default AWS RAM managed permission is available, choose a permission to associate with each resource type\. If only the default permission is available, AWS RAM automatically associates this permission with the resource type\. 

1. Specify the principals that you want to have access to the resources\.

For information about how to create a resource share, see [Sharing your AWS resources](getting-started-sharing.md)\.

## Update a resource share<a name="working-with-sharing-update"></a>

You can update a resource share at any time in the following ways:
+ You can add principals, resources, or tags to a resource share that you created\.
+ For resource types that support more than the default AWS RAM managed permission, you can choose a different permission\. 
+ You also can revoke access to shared resources by removing principals or resources from a resource share\. If you revoke access, principals no longer have access to the shared resources\.

**Note**  
Principals with whom you share resources can leave your resource share if the share is empty or contains only resource types that support this action\. If the resource share contains resource types that do not support this action, a message might appear to inform principals that they must contact the share owner\. In this case, you must remove the principals from your resource share\. For a list of resource types that do not support this action, see [Prerequisites for leaving a resource share](working-with-shared.md#working-with-shared-leave-prerequisites)\.

**To update a resource share \(console\)**

1. Open the AWS RAM console at [https://console\.aws\.amazon\.com/ram](https://console.aws.amazon.com/ram/)\.

1. In the navigation pane, choose **Shared by me**, **Resource shares**\.

1. Select the resource share and choose **Modify**\.

1. In **Step 1: Specify resource share details**, review the resource share details, and if required, update any of the following:

   1. \(Optional\) To change the name of the resource share, edit **Name**\.

   1. \(Optional\) To add a resource to the resource share, under **Resources**, choose the type of resource and select the check box next to the resource\.

   1. \(Optional\) To remove a resource, locate the resource under **Selected resources**, and choose **X**\.

   1. \(Optional\) To add a tag to the resource share, under **Tags**, choose **Add tag** and enter a tag key and tag value pair\.

   1. To remove a tag from the resource share, locate it and choose **Remove tag**\.

1. Choose **Next**\.

1. \(Optional\) In **Step 2: Associate a permission with each resource type**, if more than the default AWS RAM managed permission is available, choose the permission to associate with the resource type\. For more information, see [Types of AWS RAM managed permissions](permissions.md#permissions-types)\.

   To display the actions that the permission allows, expand **View the actions that are allowed by this permission**\.

1. Choose **Next**\.

1. In **Step 3: Choose principals to grant access**, review the selected principals, and if required, update any of the following:

   1. \(Optional\) To change whether sharing is enabled with principals inside or outside your organization, choose one of the following options:
      + To share resources with AWS accounts, IAM users, and IAM roles that are outside your organization, choose **Allow sharing with external principals**\.
      + To restrict resource sharing to principals in your organization in AWS Organizations, choose **Allow sharing with principals in your organization only**\.

   1. For **Principals**, do the following:
      + \(Optional\) To add an organization, organizational unit \(OU\), or AWS account inside your organization, turn on **Display organizational structure** to display a "tree" view of your organization\. Then select the check box next to each principal that you want to add\.
**Note**  
The **Display organizational structure **toggle appears only if sharing with AWS Organizations is enabled and you are signed in to the management account for the organization\.  
You can't use this method to specify an AWS account outside your organization, or an IAM role or IAM user\. Instead, you must add these principals from the list\.
      + \(Optional\) To add a principal from the list, choose the principal type, enter the ID or ARN for the principal, and choose **Add**\. 
      + \(Optional\) To remove a principal, locate it under **Selected principals**, and choose **Deselect**\. 

1. Choose **Next**\.

1. In **Step 4: Review and update**, review the configuration details for your resource share\. To change the configuration for any step, choose the link that corresponds to the step, and make the required changes\.

1. Choose **Update resource share**\.

**To update a resource share \(AWS CLI\)**

Use the following commands:
+ [associate\-resource\-share](https://docs.aws.amazon.com/cli/latest/reference/ram/associate-resource-share.html)
+ [disassociate\-resource\-share](https://docs.aws.amazon.com/cli/latest/reference/ram/disassociate-resource-share.html)
+ [tag\-resource](https://docs.aws.amazon.com/cli/latest/reference/ram/tag-resource.html)
+ [update\-resource\-share](https://docs.aws.amazon.com/cli/latest/reference/ram/update-resource-share.html)

## View a resource share<a name="working-with-sharing-view-rs"></a>

You can view a list of all the resource shares that you have created\. You can see which resources you are sharing and the principals with whom they are shared\.

**To view your resource shares \(console\)**

1. Open the AWS RAM console at [https://console\.aws\.amazon\.com/ram](https://console.aws.amazon.com/ram/)\.

1. In the navigation pane, choose **Shared by me**, **Resource shares**\. 

1. Apply a filter to find specific resource shares\. You can apply multiple filters to narrow your search\.

1. Choose the resource share to review\. The following information is available:
   + **Summary** – Lists information about the resource share, such as its name, ID, owner, Amazon Resource Name \(ARN\), creation date, and current status\.
   + **Shared resources** – Lists the resources that are included in the resource share\. Choose the ID of a resource to view it in its service console\.
   + **Shared principals** – Lists the principals with whom the resources are shared\.
   + **Tags** – Lists the tag key\-value pairs for the resource share\.

**To view your resource shares \(AWS CLI\)**  
Use the [get\-resource\-shares](https://docs.aws.amazon.com/cli/latest/reference/ram/get-resource-shares.html) command\.

## View your shared resources<a name="working-with-sharing-view-sr"></a>

You can view the resources that are shared by your account, across all resource shares\. This enables you to determine which resources you are currently sharing, the number of resource shares they are included in, and the number of principals that have access to them\.

**To view the resources that you're sharing by using the console**

1. Open the AWS RAM console at [https://console\.aws\.amazon\.com/ram](https://console.aws.amazon.com/ram/)\.

1. In the navigation pane, choose **Shared by me**, **Shared resources**\.

1. For each shared resource, the following information is available:
   + **Resource ID** – The ID of the resource\. Choose the ID of a resource to view it in its service console\.
   + **Resource type** – The type of resource\.
   + **Last share date** – The date on which the resource was last shared\.
   + **Resource shares** – The number of resource shares in which the resource is included\. Choose the value to list the resource shares\.
   + **Principals** – The number of principals with whom the resource is shared\. Choose the value to view the principals\.

**To view the resources that you're sharing by using the AWS CLI**  
Use the [list\-resources](https://docs.aws.amazon.com/cli/latest/reference/ram/list-resources.html) command\.

## View the principals with whom you're sharing<a name="working-with-sharing-view-accounts"></a>

You can view the principals with whom you are sharing your resources, across all resource shares\. Viewing the principals with whom you are sharing enables you to determine who has access to your shared resources\.

**To view the principals with whom you're sharing by using the console**

1. Open the AWS RAM console at [https://console\.aws\.amazon\.com/ram](https://console.aws.amazon.com/ram/)\.

1. In the navigation pane, choose **Shared by me**, **Principals**\.

1. For each principal, the following information is available:
   + **Principal ID** – The ID of the principal\.
   + **Resource shares** – The number of resource shares you shared with the principal\. Choose the value to view the resource shares\.
   + **Resources** – The number of resources you shared with the principal\. Choose the value to view the shared resources\.

**To view the principals with whom you're sharing by using the AWS CLI**  
Use the [list\-principals](https://docs.aws.amazon.com/cli/latest/reference/ram/list-principals.html) command\.

## View details about AWS RAM managed permissions<a name="working-with-sharing-view-permissions"></a>

To view details about AWS RAM managed permissions \(managed permissions\) and identify which permissions are associated with one or more resource shares, use the **Permissions Library** in the AWS RAM console\.

**To view details about AWS RAM managed permissions**

1. Open the AWS RAM console at [https://console\.aws\.amazon\.com/ram](https://console.aws.amazon.com/ram/)\.

1. In the navigation pane, choose **Permissions library**\. 

1. In the **Permissions **list, choose the managed permission for which you want to view details\. You can use the search box to filter the list of permissions\.

1. \(Optional\) To change the display preferences, choose the gear icon in the upper right of the **Permissions **panel\. You can change the following preferences:
   + **Page size** – The number of resources displayed on each page\.
   + **Wrap lines** – Whether to wrap lines in table rows\.
   + **Columns** – Whether to display or hide information about the resource type and associated shares\.

1. After you finish setting display preferences, choose **Confirm**\.

1. For each permission, the list displays the following information:
   + **Permission name** – The name of the managed permission, formatted as a link\. You can select the link to display more information about the permission\. In addition to the resource type that is associated with the permission, the following information is displayed:
     + **Last updated time** – The date and time when the managed permission was last updated\.
     + **Creation time** – The date and time when the managed permission was created\.
     + **ARN **– The ARN of the managed permission\. The ARNs of default managed permissions follow this format:

       `arn:aws:ram::aws:permission/AWSRAMDefaultPermissionShareableResource`

       For example:

       `arn:aws:ram::aws:permission/AWSRAMDefaultPermissionSubnet`
     + **Allowed actions** – The list of actions that principals are allowed to perform on the associated resource type\.
   + **Resource type** – The resource type that is associated with the managed permission\.
   + **Associated shares** – The number of resource shares that are associated with the managed permission\. If one or more resource shares are associated with a permission, you can select the circle icon that contains the number to display the following information:
     + **Resource share name** – The name of the resource share that is associated with the managed permission\.
     + **Owner** – The AWS account number of the resource share owner\.
     + **Allow external principals** – Whether the resource share allows sharing with principals outside the organization in AWS Organizations\.
     + **Status** – The status of the association\. 

## Delete a resource share<a name="working-with-sharing-delete"></a>

You can delete a resource share at any time\. When you delete a resource share, all principals that were associated with the resource share lose access to the shared resources\. Deleting a resource share does not delete the shared resources\.

The deleted resource share remains visible in the console for a short period after deletion, but its status changes to `Deleted`\.

**To delete a resource share by using the console**

1. Open the AWS RAM console at [https://console\.aws\.amazon\.com/ram](https://console.aws.amazon.com/ram/)\.

1. In the navigation pane, choose **Shared by me**, **Resource shares**\.

1. Select the resource share\. Be sure to select the correct resource share\. You can't recover a resource share after you delete it\.

1. Choose **Delete**, type the confirmation message, and choose **Delete**\.

**To delete a resource share by using the AWS CLI**  
Use the [delete\-resource\-share](https://docs.aws.amazon.com/cli/latest/reference/ram/delete-resource-share.html) command\.

## Supported actions on shared resources<a name="working-with-sharing-view-permissions"></a>

You can use the AWS CLI to view the actions that principals can perform on shared resources\. For more information, see the [get\-resource\-policies](https://docs.aws.amazon.com/cli/latest/reference/ram/get-resource-policies.html) command\.