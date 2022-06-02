# Using shared AWS resources<a name="getting-started-shared"></a>

To start using resources that were shared with your account using AWS Resource Access Manager, complete the following tasks\.

**Topics**
+ [Respond to the resource share invitation](#getting-started-shared-respond-invitation)
+ [Use the resources that are shared with you](#getting-started-shared-use-resources)

## Respond to the resource share invitation<a name="getting-started-shared-respond-invitation"></a>

If you receive an invitation to join a resource share, you must accept it to gain access to the shared resources\. If you're part of an organization in AWS Organizations and sharing in your organization is enabled, principals in your organization are automatically granted access to the shared resources\. Those principals don't receive invitations\.

------
#### [ Console ]

**To respond to invitations**

1. Open the **[Shared with me : Resource shares](https://console.aws.amazon.com/ram/home#SharedResourceShares:)** page in the AWS RAM console\.
**Note**  
A resource share is visible in only the AWS Region in which it was created\. If an expected resource share doesn't appear in the console, you might need to switch to a different AWS Region using the drop\-down control in the upper\-right corner\.

1. Review the list of resource shares to which you have been granted access\.

   The **Status** column indicates your current participation status for the resource share\. The `Pending` status indicates that you have been added to a resource share, but you have not yet accepted or rejected the invitation\.

1. To respond to the resource share invitation, select the resource share ID and choose **Accept resource share** to accept the invitation, or **Reject resource share** to decline the invitation\. If you reject the invitation, you don't get access to the resources\. If you accept the invitation, you gain access to the resources\.

------
#### [ AWS CLI ]

To start, get a list of the resource share invitations that are available to you\. The following example command was run in the `us-west-2` Region, and shows one resource share is available in the `PENDING` state\.

```
$ aws ram get-resource-share-invitations
{
    "resourceShareInvitations": [
        {
            "resourceShareInvitationArn": "arn:aws:ram:us-west-2:111122223333:resource-share-invitation/1234abcd-ef12-9876-5432-aaaaaa111111",
            "resourceShareName": "MyNewResourceShare",
            "resourceShareArn": "arn:aws:ram:us-west-2:111122223333:resource-share/1234abcd-ef12-9876-5432-bbbbbb222222",
            "senderAccountId": "111122223333",
            "receiverAccountId": "444455556666",
            "invitationTimestamp": "2021-09-15T15:00:32.568000-07:00",
            "status": "PENDING"
        }
    ]
}
```

You can use the Amazon Resource Name \(ARN\) of the invitation from the previous command as a parameter in the next command to accept that invitation\.

```
$ aws ram accept-resource-share-invitation \
    --resource-share-invitation-arn arn:aws:ram:us-west-2:111122223333:resource-share-invitation/1234abcd-ef12-9876-5432-aaaaaa111111
{
    "resourceShareInvitation": {
        "resourceShareInvitationArn": "arn:aws:ram:us-west-2:111122223333:resource-share-invitation/1234abcd-ef12-9876-5432-aaaaaa111111",
        "resourceShareName": "MyNewResourceShare",
        "resourceShareArn": "arn:aws:ram:us-west-2:111122223333:resource-share/1234abcd-ef12-9876-5432-bbbbbb222222",
        "senderAccountId": "111122223333",
        "receiverAccountId": "444455556666",
        "invitationTimestamp": "2021-09-15T15:14:12.580000-07:00",
        "status": "ACCEPTED"
    }
}
```

The output shows that the `status` has changed to `ACCEPTED`\. The resources that are included in that resource share are now available to principals in the accepting account\.

------

## Use the resources that are shared with you<a name="getting-started-shared-use-resources"></a>

After you accept the invitation to join a resource share, you can perform specific actions on the shared resources\. These actions vary by resource type\. For more information, see [Shareable AWS resources](shareable.md)\. The resources are available directly in each resource's service console and API/CLI operations\. If the resource is regional, then you must use the correct AWS Region in the service console or API/CLI command\. If the resource is global, then you must use the designated home Region, US East \(N\. Virginia\), `us-east-1` To view the resource in AWS RAM, you must open the AWS RAM console to the AWS Region that the resource share was created in\.