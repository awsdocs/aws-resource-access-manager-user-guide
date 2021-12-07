# Viewing the principals you share resources with in AWS RAM<a name="working-with-sharing-view-principals"></a>

You can view the principals you share your resources with, across all resource shares\. Viewing this list of principals helps you determine who has access to your shared resources\.

------
#### [ Console ]

**To view the principals you're sharing resources with**

1. Navigate to the [https://console.aws.amazon.com/ram/home#OwnedPrincipals:](https://console.aws.amazon.com/ram/home#OwnedPrincipals:) page in the AWS RAM console\.

1. Because AWS RAM resource shares exist in specific AWS Regions, choose the appropriate AWS Region from the dropdown list in the upper\-right corner of the console\. To see resource shares that contain global resources, you must set the AWS Region to US East \(N\. Virginia\), \(`us-east-1`\)\. For more information about sharing global resources, see [Sharing Regional resources compared to global resources](working-with-regional-vs-global.md)\.

1. Apply a filter to find specific principals\. You can apply multiple filters to narrow your search\. Choose the text box to see a dropdown list of suggested attribute fields\. After you choose one, you can choose from the list of available values for that field\. You can add other attributes or keywords until you find the resource you want\.

1. For each principal in the list, the console displays the following information:
   + **Principal ID** – The ID of the principal\. Choose the ID to open a new browser tab to view the principal in its native console\. 
   + **Resource shares** – The number of resource shares you shared with the specified principal\. Choose the number to view the list of resource shares\.
   + **Resources** – The number of resources you shared with the principal\. Choose the number to view the list of shared resources\.

------
#### [ AWS CLI ]

**To view the principals you're sharing resources with**  
You can use the [list\-principals](https://docs.aws.amazon.com/cli/latest/reference/ram/list-principals.html) command to get a list of the principals you reference in resource shares that you created in the current AWS Region for the calling account\.

The following example lists the principals that have access to shares created in the default Region for the calling account\. In this example, the principals are the calling account's organization and a separate AWS account, as part of two different resource shares\. You must use the service endpoint for the AWS Region that contains the resource share\.

```
$ aws ram list-principals \
    --region us-east-1 \
    --resource-owner SELF
{
    "principals": [
        {
            "id": "arn:aws:organizations::123456789012:organization/o-a1b2c3dr",
            "resourceShareArn": "arn:aws:ram:us-east-1:123456789012:resource-share/a477f3b2-4001-4dcb-bd54-7c8d23b4f07d",
            "creationTime": "2021-09-14T20:40:58.532000-07:00",
            "lastUpdatedTime": "2021-09-14T20:40:59.610000-07:00",
            "external": false
        },
        {
            "id": "111111111111",
            "resourceShareArn": "arn:aws:ram:us-east-1:123456789012:resource-share/6405fa7c-0786-4e15-8c9f-8aec02802f18",
            "creationTime": "2021-09-15T15:00:31.601000-07:00",
            "lastUpdatedTime": "2021-09-15T15:14:13.618000-07:00",
            "external": true
        }
    ]
}
```

------