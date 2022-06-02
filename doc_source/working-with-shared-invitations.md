# Accepting and rejecting resource share invitations<a name="working-with-shared-invitations"></a>

To access shared resources, the owner of the resource share must add you as a principal\.

If you're added to the resource share through an AWS account that is in an organization in AWS Organizations, and sharing within the organization is enabled, then you automatically get access to the shared resources without having to accept an invitation\.

If you're added to a resource share by one of the following, you receive an invitation to join the resource share:
+ An account outside of your organization in AWS Organizations
+ An account inside your organization when sharing with AWS Organizations is not enabled

If you receive an invitation to join a resource share, you must accept it to access its shared resources\. If you decline the invitation, you can't access the shared resources\.

You have seven days to accept an invitation to join a resource share\. If you don't accept the invitation within seven days, the invitation expires and is automatically declined\.

------
#### [ Console ]

**To respond to an invitation to a resource share**

1. Navigate to the **[Shared with me : Resource shares](https://console.aws.amazon.com/ram/home#SharedResourceShares:)** page in the AWS RAM console\.

1. Because AWS RAM resource shares exist in specific AWS Regions, choose the appropriate AWS Region from the dropdown list in the upper\-right corner of the console\. To see resource shares that contain global resources, you must set the AWS Region to US East \(N\. Virginia\), \(`us-east-1`\)\. For more information about sharing global resources, see [Sharing Regional resources compared to global resources](working-with-regional-vs-global.md)\.

1. Review the list of resource shares to which you have been added\.

   The **Status** column indicates your current participation status for the resource share\. The `Pending` status indicates that you have been added to a resource share, but you have not yet accepted or rejected the invitation\.

1. To respond to the resource share invitation, select the resource share ID and choose **Accept resource share** to accept the invitation, or **Reject resource share** to decline the invitation\. If you reject the invitation, you don't get access to the resources\. If you accept the invitation, you gain access to the resources\.

------
#### [ AWS CLI ]

**To respond to an invitation to a resource share**  
You can use the following commands to accept or reject invitations to a resource share:
+ [get\-resource\-share\-invitations](https://docs.aws.amazon.com/cli/latest/reference/ram/get-resource-share-invitations.html)
+ [accept\-resource\-share\-invitation](https://docs.aws.amazon.com/cli/latest/reference/ram/accept-resource-share-invitation.html)
+ [reject\-resource\-share\-invitation](https://docs.aws.amazon.com/cli/latest/reference/ram/reject-resource-share-invitation.html)

1. The following example starts by using the [get\-resource\-share\-invitations](https://docs.aws.amazon.com/cli/latest/reference/ram/get-resource-share-invitations.html) command to retrieve a list of all of the invitations available to the user's AWS account\. The AWS CLI `query` parameter lets you restrict the output to only those invitations with its `status` set to `PENDING`\. This example shows one invitation from account 111111111111 is currently `PENDING` for the current account `123456789012` in the specified AWS Region\.

   ```
   $ aws ram get-resource-share-invitations \
       --region us-east-1 \
       --query 'resourceShareInvitations[?status==`PENDING`]'
   {
       "resourceShareInvitations": [
           {
               "resourceShareInvitationArn": "arn:aws:ram:us-east-1:111111111111:resource-share-invitation/3b3bc051-fbf6-4336-8377-06c559dfee49",
               "resourceShareName": "Test TrngAcct Resource Share",
               "resourceShareArn": "arn:aws:ram:us-east-1:111111111111:resource-share/c4506c70-df75-4e6c-ac30-42ca03295a37",
               "senderAccountId": "111111111111",
               "receiverAccountId": "123456789012",
               "invitationTimestamp": "2021-09-21T08:56:24.977000-07:00",
               "status": "PENDING"
           }
       ]
   }
   ```

1. After you find the invitation that you want to accept, make note of the `resourceShareInvitationArn` in the output to use in the next command to accept the invitation\.

   ```
   $ aws ram accept-resource-share-invitation \
       --region us-east-1 \
       --resource-share-invitation-arn arn:aws:ram:us-east-1:111111111111:resource-share-invitation/3b3bc051-fbf6-4336-8377-06c559dfee49
   {
       "resourceShareInvitation": {
           "resourceShareInvitationArn": "arn:aws:ram:us-east-1:111111111111:resource-share-invitation/3b3bc051-fbf6-4336-8377-06c559dfee49",
           "resourceShareName": "Test TrngAcct Resource Share",
           "resourceShareArn": "arn:aws:ram:us-east-1:111111111111:resource-share/c4506c70-df75-4e6c-ac30-42ca03295a37",
           "senderAccountId": "111111111111",
           "receiverAccountId": "123456789012",
           "invitationTimestamp": "2021-09-21T09:18:24.545000-07:00",
           "status": "ACCEPTED"
       }
   }
   ```

   If successful, note that the response shows that the `status` has changed from `PENDING` to `ACCEPTED`\.

If you instead wanted to reject the invitation, run the [reject\-resource\-share\-invitation](https://docs.aws.amazon.com/cli/latest/reference/ram/reject-resource-share-invitation.html) command, with the same parameters\.

```
$ aws ram reject-resource-share-invitation \
    --region us-east-1 \
    --resource-share-invitation-arn arn:aws:ram:us-east-1:111111111111:resource-share-invitation/3b3bc051-fbf6-4336-8377-06c559dfee49
{
    "resourceShareInvitation": {
        "resourceShareInvitationArn": "arn:aws:ram:us-east-1:111111111111:resource-share-invitation/3b3bc051-fbf6-4336-8377-06c559dfee49",
        "resourceShareName": "Test TrngAcct Resource Share",
        "resourceShareArn": "arn:aws:ram:us-east-1:111111111111:resource-share/c4506c70-df75-4e6c-ac30-42ca03295a37",
        "senderAccountId": "111111111111",
        "receiverAccountId": "123456789012",
        "invitationTimestamp": "2021-09-21T09:18:24.545000-07:00",
        "status": "REJECTED"
    }
}
```

------