# Viewing resource shares shared with you<a name="working-with-shared-view-rs"></a>

You can view the resource shares to which you have access\. You can see which principals are sharing resources with you and which resources they're sharing\.

------
#### [ Console ]

**To view the resource shares**

1. Navigate to the [https://console.aws.amazon.com/ram/home#SharedResourceShares:](https://console.aws.amazon.com/ram/home#SharedResourceShares:) page in the AWS RAM console\.

1. Because AWS RAM resource shares exist in specific AWS Regions, choose the appropriate AWS Region from the dropdown list in the upper\-right corner of the console\. To see resource shares that contain global resources, you must set the AWS Region to US East \(N\. Virginia\), \(`us-east-1`\)\. For more information about sharing global resources, see [Sharing Regional resources compared to global resources](working-with-regional-vs-global.md)\.

1. \(Optional\) Apply a filter to find specific resource shares\. You can apply multiple filters to narrow your search\. You can type a keyword, such as part of a resource share name to list only those resource shares that include that text in the name\. Choose the text box to see a dropdown list of suggested attribute fields\. After you choose one, you can choose from the list of available values for that field\. You can add other attributes or keywords until you find the resource you want\.

1. The AWS RAM console displays the following information:
   + **Name** – The name of the resource share\.
   + **ID** – The ID of the resource share\. Choose the ID to view the details page for the resource share\.
   + **Owner** – The ID of the AWS account that created the resource share\.
   + **Status** – The current status of the resource share\. Possible values include:
     + `Active` – The resource share is active and available for use\.
     + `Deleted` – The resource share is deleted and is no longer available for use\.
     + `Pending` – An invitation to accept the resource share is waiting for a response\.

------
#### [ AWS CLI ]

**To view the resource shares**  
Use the [get\-resource\-shares](https://docs.aws.amazon.com/cli/latest/reference/ram/get-resource-shares.html) command with the `--resource-owner` parameter set to `OTHER-ACCOUNTS`\.

The following example shows the list of resource shares shared in the specified AWS Region with the calling account by other AWS accounts\.

```
$ aws ram get-resource-shares \
    --region us-east-1 \
    --resource-owner OTHER-ACCOUNTS
{
    "resourceShares": [
        {
            "resourceShareArn": "arn:aws:ram:us-east-1:111111111111:resource-share/8b831ba0-63df-4608-be3c-19096b1ee16e",
            "name": "Prod Env Shared Licenses",
            "owningAccountId": "111111111111",
            "allowExternalPrincipals": true,
            "status": "ACTIVE",
            "creationTime": "2021-09-21T08:50:41.308000-07:00",
            "lastUpdatedTime": "2021-09-21T08:50:41.308000-07:00",
            "featureSet": "STANDARD"
        },
        {
            "resourceShareArn": "arn:aws:ram:us-east-1:222222222222:resource-share/c4506c70-df75-4e6c-ac30-42ca03295a37",
            "name": "Prod Env Shared Subnets",
            "owningAccountId": "222222222222",
            "allowExternalPrincipals": true,
            "status": "ACTIVE",
            "creationTime": "2021-09-21T08:56:24.737000-07:00",
            "lastUpdatedTime": "2021-09-21T08:56:24.737000-07:00",
            "featureSet": "STANDARD"
        }
    ]
}
```

------