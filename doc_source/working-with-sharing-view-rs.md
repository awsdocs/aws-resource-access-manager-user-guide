# Viewing resource shares you created in AWS RAM<a name="working-with-sharing-view-rs"></a>

You can view a list of the resource shares that you have created\. You can see which resources you're sharing and the principals with whom they're shared\.

------
#### [ Console ]

**To view your resource shares**

1. Open the [https://console.aws.amazon.com/ram/home#OwnedResourceShares:](https://console.aws.amazon.com/ram/home#OwnedResourceShares:) page in the AWS RAM console\.

1. Because AWS RAM resource shares exist in specific AWS Regions, choose the appropriate AWS Region from the dropdown list in the upper\-right corner of the console\. To see resource shares that contain global resources, you must set the AWS Region to US East \(N\. Virginia\), \(`us-east-1`\)\. For more information about sharing global resources, see [Sharing Regional resources compared to global resources](working-with-regional-vs-global.md)\.

1. \(Optional\) Apply a filter to find specific resource shares\. You can apply multiple filters to narrow your search\. You can type a keyword, such as part of a resource share name to list only those resource shares that include that text in the name\. Choose the text box to see a dropdown list of suggested attribute fields\. After you choose one, you can choose from the list of available values for that field\. You can add other attributes or keywords until you find the resource you want\.

1. Choose the name of the resource share to review\. The console displays the following information about the resource share:
   + **Summary** – Lists the resource share name, ID, owner, Amazon Resource Name \(ARN\), creation date, whether it allows sharing with external accounts, and its current status\.
   + **Permissions** – Lists the AWS RAM managed permissions that are attached to this resource share\. There can be at most one permission per resource type included in the resource share\. 
   + **Shared resources** – Lists the individual resources that are included in the resource share\. Choose the ID of a resource to open a new browser tab to view the resource in its native service's console\.
   + **Shared principals** – Lists the principals with whom the resources are shared\.
   + **Tags** – Lists the tag key\-value pairs that are attached to the resource share itself; these are not the tags attached to the individual resources included in the resource share\.

------
#### [ AWS CLI ]

**To view your resource shares**  
You can use the [get\-resource\-shares](https://docs.aws.amazon.com/cli/latest/reference/ram/get-resource-shares.html) command with the parameter `--resource-owner` set to `SELF` to display details of the resource shares created in your AWS account\.

The following example shows the resource shares that are shared in the current AWS Region \(`us-east-1`\) for the calling AWS account\. To get the resource shares created in a different Region, use the `--region <region-code>` parameter\. To get resource shares that include global resources, you must specify the Region US East \(N\. Virginia\), `us-east-1`\.

```
$  aws ram get-resource-shares \
    --resource-owner SELF
{
    "resourceShares": [
        {
            "resourceShareArn": "arn:aws:ram:us-east-1:123456789012:resource-share/2ebe77d7-4156-4a93-87a4-228568d04425",
            "name": "MySubnetShare",
            "owningAccountId": "123456789012",
            "allowExternalPrincipals": true,
            "status": "ACTIVE",
            "creationTime": "2021-09-10T15:38:54.449000-07:00",
            "lastUpdatedTime": "2021-09-10T15:38:54.449000-07:00",
            "featureSet": "STANDARD"
        },
        {
            "resourceShareArn": "arn:aws:ram:us-east-1:123456789012:resource-share/818d71dd-7512-4f71-99c6-2ae57aa010bc",
            "name": "MyLicenseConfigShare",
            "owningAccountId": "123456789012",
            "allowExternalPrincipals": true,
            "status": "ACTIVE",
            "creationTime": "2021-09-14T20:42:40.266000-07:00",
            "lastUpdatedTime": "2021-09-14T20:42:40.266000-07:00",
            "featureSet": "STANDARD"
        }
    ]
}
```

------