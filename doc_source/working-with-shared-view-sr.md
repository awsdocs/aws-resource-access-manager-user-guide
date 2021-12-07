# Viewing resources shared with you<a name="working-with-shared-view-sr"></a>

You can view the shared resources that you can access\. You can see which principals shared the resources with you and which resource shares include the resources\.

------
#### [ Console ]

**To view resources shared with you**

1. Navigate to the [https://console.aws.amazon.com/ram/home#SharedResources:](https://console.aws.amazon.com/ram/home#SharedResources:) page in the AWS RAM console\.

1. Because AWS RAM resource shares exist in specific AWS Regions, choose the appropriate AWS Region from the dropdown list in the upper\-right corner of the console\. To see resource shares that contain global resources, you must set the AWS Region to US East \(N\. Virginia\), \(`us-east-1`\)\. For more information about sharing global resources, see [Sharing Regional resources compared to global resources](working-with-regional-vs-global.md)\.

1. Apply a filter to find specific shared resources\. You can apply multiple filters to narrow your search\.

1. The following information is available:
   + **Resource ID** – The ID of the resource\. Choose the ID of the resource to view it in its service console\.
   + **Resource type** – The type of resource\.
   + **Last share date** – The date on which the resource was shared with you\.
   + **Resource shares** – The number of resource shares in which the resource is included\. Choose the value to view the resource shares\.
   + **Owner ID** – The ID of the principal who owns the resource\.

------
#### [ AWS CLI ]

**To view resources shared with you**  
You can use the [list\-resources](https://docs.aws.amazon.com/cli/latest/reference/ram/list-resources.html) command to view resources that are shared with you\.

The following example command displays details about the resource accessible through a resource share in the specified AWS Region from another AWS account\.

```
$ aws ram list-resources \
    --region us-east-1 \
    --resource-owner OTHER-ACCOUNTS
{
    "resources": [
        {
            "arn": "arn:aws:license-manager:us-east-1:111111111111:license-configuration:lic-36be0485f5ae379cc74cf8e9242ab143",
            "type": "license-manager:LicenseConfiguration",
            "resourceShareArn": "arn:aws:ram:us-east-1:111111111111:resource-share/8b831ba0-63df-4608-be3c-19096b1ee16e",
            "status": "AVAILABLE",
            "creationTime": "2021-09-21T08:50:41.308000-07:00",
            "lastUpdatedTime": "2021-09-21T08:50:42.517000-07:00"
        }
    ]
}
```

------