# Leaving a resource share<a name="working-with-shared-leave"></a>

If you no longer need access to resources that are shared with you, you can leave a resource share at any time\. When you leave a resource share, you lose access to the shared resources\.

## Prerequisites for leaving a resource share<a name="working-with-shared-leave-prerequisites"></a>
+ You can leave a resource share only if it was shared with you as an AWS account not in the context of an organization\. You can't leave a resource share if you were added to it by an AWS account inside your organization and sharing with AWS Organizations is enabled\. Access to resource shares within an organization is automatic\.
+ To leave a resource share, verify that the resource share is either empty or that it contains only resource types that support leaving a share\. 

  The following resource types ***do not*** support leaving a resource share\. If the resource share contains one or more of these, ask the owner of the resource share to remove your principal from those with permission to the share\.    
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/working-with-shared-leave.html)

## How to leave a resource share<a name="working-with-shared-leave-how-to-leave"></a>

------
#### [ Console ]

**To leave a resource share**

1. Navigate to the [https://console.aws.amazon.com/ram/home#SharedResourceShares:](https://console.aws.amazon.com/ram/home#SharedResourceShares:) page in the AWS RAM console\.

1. Because AWS RAM resource shares exist in specific AWS Regions, choose the appropriate AWS Region from the dropdown list in the upper\-right corner of the console\. To see resource shares that contain global resources, you must set the AWS Region to US East \(N\. Virginia\), \(`us-east-1`\)\. For more information about sharing global resources, see [Sharing Regional resources compared to global resources](working-with-regional-vs-global.md)\.

1. Select the resource share you want to leave\.

1. Choose **Leave resource share**, and in the confirmation dialog box, choose **Leave**\.

------
#### [ AWS CLI ]

**To leave a resource share**  
You can use the [disassociate\-resource\-share](https://docs.aws.amazon.com/cli/latest/reference/ram/disassociate-resource-share.html) command to leave a resource share\.

The following example commands causes the AWS account that calls the command to lose access to the resources shared by the resource share specified by the ARN\. You must direct the request to the service endpoint in the AWS Region that contains the resource share that you want to leave\.

1. First, retrieve the list of resource shares to retrieve the ARN of the resource share that you want to leave\.

   ```
   $ aws ram get-resource-shares \
       --region us-east-1 \
       --resource-owner OTHER-ACCOUNTS
   {
       "resourceShares": [
           {
               "resourceShareArn": "arn:aws:ram:us-east-1:111111111111:resource-share/8b831ba0-63df-4608-be3c-19096b1ee16e",
               "name": "Prod Environment Shared Licenses",
               "owningAccountId": "111111111111",
               "allowExternalPrincipals": true,
               "status": "ACTIVE",
               "creationTime": "2021-09-21T08:50:41.308000-07:00",
               "lastUpdatedTime": "2021-09-21T08:50:41.308000-07:00",
               "featureSet": "STANDARD"
           }
       ]
   }
   ```

1. Then, you can run the command to leave that resource share\. Note that you must also specify your account ID, `123456789012`, as the principal to disassociate from the specified resource share, which is shared by account `111111111111`\.

   ```
   $ aws ram disassociate-resource-share \
       --region us-east-1 \
       --resource-share-arn arn:aws:ram:us-east-1:111111111111:resource-share/8b831ba0-63df-4608-be3c-19096b1ee16e \
       --principals 123456789012 
                           {
       "resourceShareAssociations": [
           {
               "resourceShareArn": "arn:aws:ram:us-east-1:111111111111:resource-share/8b831ba0-63df-4608-be3c-19096b1ee16e",
               "associatedEntity": "123456789012",
               "associationType": "PRINCIPAL",
               "status": "DISASSOCIATING",
               "external": false
           }
       ]
   }
   ```

------