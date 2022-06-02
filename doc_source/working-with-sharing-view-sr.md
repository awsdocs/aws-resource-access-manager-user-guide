# Viewing your shared resources in AWS RAM<a name="working-with-sharing-view-sr"></a>

You can view the list of individual resources that you've shared, across all resource shares\. The list helps you to determine which resources you're currently sharing, the number of resource shares that they're included in, and the number of principals that have access to them\.

------
#### [ Console ]

**To view the resources that you're currently sharing**

1. Open the **[Shared by me : Shared resources](https://console.aws.amazon.com/ram/home#OwnedResources:)** page in the AWS RAM console\.

1. Because AWS RAM resource shares exist in specific AWS Regions, choose the appropriate AWS Region from the dropdown list in the upper\-right corner of the console\. To see resource shares that contain global resources, you must set the AWS Region to US East \(N\. Virginia\), \(`us-east-1`\)\. For more information about sharing global resources, see [Sharing Regional resources compared to global resources](working-with-regional-vs-global.md)\.

1. For each shared resource, the following information is available:
   + **Resource ID** – The ID of the resource\. Choose the ID of a resource to open a new browser tab to view the resource in its native service console\.
   + **Resource type** – The type of resource\.
   + **Last share date** – The date on which the resource was last shared\.
   + **Resource shares** – The number of resource shares that include the resource\. To see the list of the resource shares, choose the number\.
   + **Principals** – The number of principals who can access the resource\. Choose the value to view the principals\.

------
#### [ AWS CLI ]

**To view the resources that you're currently sharing**  
You can use the [list\-resources](https://docs.aws.amazon.com/cli/latest/reference/ram/list-resources.html) command with the parameter `--resource-owner` set to `SELF` to display details of the resources that you currently share\.

The following example shows the resources that are included in resource shares in the AWS Region \(`us-east-1`\) for the calling AWS account\. To get the resources that you share in a different Region, use the `--region <region-code>` parameter\.

```
$ aws ram list-resources \
    --region us-east-1 \
    --resource-owner SELF
{
    "resources": [
        {
            "arn": "arn:aws:license-manager:us-east-1:123456789012:license-configuration:lic-ecbd5574fd92cb0d312baea260e4cece",
            "type": "license-manager:LicenseConfiguration",
            "resourceShareArn": "arn:aws:ram:us-east-1:123456789012:resource-share/818d71dd-7512-4f71-99c6-2ae57aa010bc",
            "creationTime": "2021-09-14T20:42:40.266000-07:00",
            "lastUpdatedTime": "2021-09-14T20:42:41.081000-07:00"
        },
        {
            "arn": "arn:aws:license-manager:us-east-1:123456789012:license-configuration:lic-ecbd5574fd92cb0d312baea260e4cece",
            "type": "license-manager:LicenseConfiguration",
            "resourceShareArn": "arn:aws:ram:us-east-1:123456789012:resource-share/a477f3b2-4001-4dcb-bd54-7c8d23b4f07d",
            "creationTime": "2021-07-22T11:48:11.104000-07:00",
            "lastUpdatedTime": "2021-07-22T11:48:11.971000-07:00"
        }
    ]
}
```

------