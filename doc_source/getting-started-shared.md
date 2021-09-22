# Using shared AWS resources<a name="getting-started-shared"></a>

**Topics**
+ [Respond to the resource share invitation](#getting-started-shared-respond-invitation)
+ [Use the resources that are shared with you](#getting-started-shared-use-resources)

## Respond to the resource share invitation<a name="getting-started-shared-respond-invitation"></a>

If you receive an invitation to join a resource share, you must accept it to gain access to the shared resources\. If you are part of an organization in AWS Organizations and sharing in your organization is enabled, principals in your organization are automatically granted access to the shared resources\. Those principals do not receive invitations\.

------
#### [ Console ]

**To respond to invitations**

1. Open the [https://console.aws.amazon.com/ram/home#SharedResourceShares:](https://console.aws.amazon.com/ram/home#SharedResourceShares:) page in the AWS RAM console\.

1. In the navigation pane, choose **Shared with me**, **Resource shares**\.

1. Review the list of resource shares to which you have been added\.

   The **Status** column indicates your current participation status for the resource share\. The `Pending` status indicates that you have been added to a resource share, but you have not yet accepted or rejected the invitation\.

1. To respond to the resource share invitation, select the resource share ID and choose **Accept resource share** to accept the invitation, or **Reject resource share** to decline the invitation\. If you reject the invitation, you do not get access to the resources\. If you accept the invitation, you gain access to the resources\.

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

You can use the ARN of the invitation from the previous command as a parameter to the next command to accept that invitation\.

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

Note that the output now shows that the `status` has changed to `ACCEPTED`\. The resources that are included in that resource share are now available to principals in the accepting account\.

------

## Use the resources that are shared with you<a name="getting-started-shared-use-resources"></a>

After you accept the invitation to join a resource share, you can perform specific actions on the shared resources\. These actions vary by resource type\. For more information, see [Shareable AWS resources](shareable.md)\.