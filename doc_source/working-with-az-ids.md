# Availability Zone IDs for your AWS resources<a name="working-with-az-ids"></a>

AWS maps the physical Availability Zones *randomly* to the available zone names for each AWS account\. This approach helps to distribute resources across the Availability Zones in an AWS Region, instead of resources likely being concentrated in Availability Zone "a" for each Region\. As a result, the Availability Zone `us-east-1a` for *your* AWS account might not represent the same physical location as `us-east-1a` for a different AWS account\. For more information, see [Regions and Availability Zones](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-regions-availability-zones.html) in the *Amazon EC2 User Guide*\.

The following illustration shows how the AZ IDs are the same for every account even though the Availability Zone names can map differently for each account\.

![\[\]](http://docs.aws.amazon.com/ram/latest/userguide/images/az_ids_example.png)

For some resources, you must identify not only the AWS Region, but also the Availability Zone\. For example, an Amazon VPC subnet\. Within a single account, the mapping of an Availability Zone to a specific name isn't important\. But, when you use AWS RAM to share such a resource with other AWS accounts, the mapping *is* important\. This random mapping complicates the ability of the account accessing the shared resource to know which Availability Zone to reference\. To help with this, such resources also allow you to identify the actual location of your resources relative to your accounts by using the *AZ ID*\. An AZ ID is a unique and consistent identifier for an Availability Zone across all AWS accounts\. For example, `use1-az1` is an AZ ID for an Availability Zone in the `us-east-1` Region and it represents the same physical location in every AWS account\.

You can use AZ IDs to determine the location of resources in one account relative to the resources in another account\. For example, if you share a subnet in the Availability Zone with the AZ ID `use1-az2` with another account, this subnet is available to that account in the Availability Zone whose AZ ID is also `use1-az2`\. The AZ ID for each subnet is displayed in the Amazon VPC console, and can be queried using the AWS CLI\.

------
#### [ Console ]

**To view the AZ IDs for the Availability Zones in your account**

1. Navigate to the [AWS RAM console home](https://console.aws.amazon.com/ram/home) page in the AWS RAM console\.

1. You can view the AZ IDs for the current AWS Region under **Your AZ ID**\.

------
#### [ AWS CLI ]

**To view the AZ IDs for the Availability Zones in your account**  
The following example command shows the AZ IDs for the Availability Zones in the us\-west\-2 Region and how they are mapped for the calling AWS account\.

```
$ aws ec2 describe-availability-zones \
    --region us-west-2
{
    "AvailabilityZones": [
        {
            "State": "available",
            "OptInStatus": "opt-in-not-required",
            "Messages": [],
            "RegionName": "us-west-2",
            "ZoneName": "us-west-2a",
            "ZoneId": "usw2-az2",
            "GroupName": "us-west-2",
            "NetworkBorderGroup": "us-west-2",
            "ZoneType": "availability-zone"
        },
        {
            "State": "available",
            "OptInStatus": "opt-in-not-required",
            "Messages": [],
            "RegionName": "us-west-2",
            "ZoneName": "us-west-2b",
            "ZoneId": "usw2-az1",
            "GroupName": "us-west-2",
            "NetworkBorderGroup": "us-west-2",
            "ZoneType": "availability-zone"
        },
        {
            "State": "available",
            "OptInStatus": "opt-in-not-required",
            "Messages": [],
            "RegionName": "us-west-2",
            "ZoneName": "us-west-2c",
            "ZoneId": "usw2-az3",
            "GroupName": "us-west-2",
            "NetworkBorderGroup": "us-west-2",
            "ZoneType": "availability-zone"
        },
        {
            "State": "available",
            "OptInStatus": "opt-in-not-required",
            "Messages": [],
            "RegionName": "us-west-2",
            "ZoneName": "us-west-2d",
            "ZoneId": "usw2-az4",
            "GroupName": "us-west-2",
            "NetworkBorderGroup": "us-west-2",
            "ZoneType": "availability-zone"
        }
    ]
}
```

------