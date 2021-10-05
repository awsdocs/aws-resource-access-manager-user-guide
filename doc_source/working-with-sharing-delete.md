# Deleting a resource share in AWS RAM<a name="working-with-sharing-delete"></a>

You can delete a resource share at any time\. When you delete a resource share, all principals that were associated with the resource share lose access to the shared resources\. Deleting a resource share doesn't delete the shared resources\.

The deleted resource share remains visible in the AWS RAM console for a short period after deletion, but its status changes to `Deleted`\.

------
#### [ Console ]

**To delete a resource share**

1. Open the [https://console.aws.amazon.com/ram/home#OwnedResourceShares:](https://console.aws.amazon.com/ram/home#OwnedResourceShares:) page in the AWS RAM console\.

1. Because AWS RAM resource shares exist in specific AWS Regions, choose the appropriate AWS Region from the dropdown list in the upper\-right corner of the console\.

1. Select the resource share you want to delete\. Be sure to select the correct resource share\. 
**Warning**  
You can't recover a resource share after you delete it\.

1. Choose **Delete**, then in the confirmation message, choose **Delete**\.

------
#### [ AWS CLI ]

**To delete a resource share**  
You can use the [delete\-resource\-share](https://docs.aws.amazon.com/cli/latest/reference/ram/delete-resource-share.html) command to delete a resource share that you no longer need\.

The following example first uses the [get\-resource\-shares](https://docs.aws.amazon.com/cli/latest/reference/ram/get-resource-shares.html) command to get the Amazon Resource Name \(ARN\) of the resource share that you want to delete\. Then it uses [delete\-resource\-share](https://docs.aws.amazon.com/cli/latest/reference/ram/delete-resource-share.html) to delete the specified resource share\.

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
        }
    ]
}
$ aws ram delete-resource-share \
    --resource-share-arn arn:aws:ram:us-east-1:123456789012:resource-share/2ebe77d7-4156-4a93-87a4-228568d04425
{
    "returnValue": true
}
```

------