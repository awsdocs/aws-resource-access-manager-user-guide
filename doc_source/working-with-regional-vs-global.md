# Sharing Regional resources compared to global resources<a name="working-with-regional-vs-global"></a>

This topic discusses the differences in how AWS Resource Access Manager \(AWS RAM\) works with Regional and global resources\.

## What are the differences between Regional and global resources?<a name="regional-resources"></a>

**Regional resources**  
Most resources that you can share with AWS RAM are *Regional*\. You create them in a specified AWS Region, and then they exist in that Region\. To see or interact with those resources, you must direct your operations to that Region\. For example, to create an Amazon Elastic Compute Cloud \(Amazon EC2\) instance with the AWS Management Console, you [choose the AWS Region](https://docs.aws.amazon.com/awsconsolehelpdocs/latest/gsg/select-region.html) that you want to create the instance in\. If you use the AWS Command Line Interface \(AWS CLI\) to create the instance, then you include the `--region` parameter\. The AWS SDKs each have their own equivalent mechanism to specify the Region that the operation uses\.  
There are several reasons for using Regional resources\. One good reason is to ensure that the resources, and the service endpoints that you use to access them, are as close to the customer as possible\. This improves performance by minimizing latency\. Another reason is to provide an isolation boundary\. This lets you create independent copies of resources in multiple Regions to distribute the load and improve scalability\. At the same time, it isolates the resources from each other to improve availability\.  
If you specify a different AWS Region in the console or in an AWS CLI command, then you can no longer see or interact with the resources you could see in the previous Region\.  
When you look at the [Amazon Resource Name \(ARN\)](https://docs.aws.amazon.com/general/latest/gr/aws-arns-and-namespaces.html) for a Regional resource, the Region that contains the resource is specified as the fourth field in the ARN\. For example, an Amazon EC2 instance is a Regional resource\. Such resources have ARNs that looks similar to the following sample for a VPC that exists in the `us-east-1` Region\.  

```
arn:aws:ec2:us-east-1:123456789012:instance/i-0a6f30921424d3eee
```

**Global resources**  
Some AWS services support resources that you can access *globally*, meaning that you can use the resource from ***anywhere***\. You don't specify an AWS Region in a global service's console\. To access a global resource, you don't specify a `--region` parameter when using the service's AWS CLI and AWS SDK operations\.  
Global resources support cases where it's critical that only one instance of a particular resource can exist at a time\. In such scenarios, replication or synchronization between copies in different Regions isn't adequate\. Having to access a single global endpoint, with the possible increase in latency, is considered acceptable to ensure that any changes are instantaneously visible to consumers of the resource\. For example, when you create an AWS Cloud WAN core network as a global resource, it's consistent to all users\. It appears as a single, contiguous global network across all Regions\.  
The [Amazon Resource Name \(ARN\)](https://docs.aws.amazon.com/general/latest/gr/aws-arns-and-namespaces.html) for a global resource doesn't include a Region\. The fourth field of such an ARN is empty, such as the following sample ARN for a Cloud WAN core network\.  

```
arn:aws:networkmanager::123456789012:core-network/core-network-0514d38fa6f796cea
```

## Resource shares and their Regions<a name="shares-with-regional-only"></a>

AWS RAM is a Regional service, and a resource share is Regional\. Therefore, a resource share can contain resources from the same AWS Region as the resource share, and any supported global resources\. The Region in which you create the resource share is the resource share's *home Region*\.

**Important**  
Currently, you can create resource shares with global resources **only in the designated home Region **US East \(N\. Virginia\) Region, `us-east-1`\. Although you can create the resource share only in that single home Region, any shared global resource appears as a standard global resource when viewed in that service's console or CLI and SDK operations\. The restriction to the home Region applies only to the resource share, not the resources it contains\.

To share a Regional resource that you created in the `us-west-2` Region, you must configure the AWS RAM console to use `us-west-2` and create the resource share there\. You can't create a resource share that includes Regional resources from different AWS Regions\. This means that to share resources from both `us-west-2` and `eu-north-1`, you must create two different resource shares\. You can't combine resources from two different Regions into a single resource share\.

To share a global resource in the AWS RAM console, you must configure the AWS RAM console to use the designated home Region, US East \(N\. Virginia\) `us-east-1`\. Then, create the resource share in the designated home Region\. You can mix global resources in a resource share only with resources from the `us-east-1` Region\.

Even though the global resource is viewable in an AWS RAM resource share in only the designated home Region, it's still a global resource after you share it\. You can access it in the shared AWS accounts from any Region from which you could access it in the original AWS account\.

**Considerations**
+ To create a resource share in the AWS RAM console, you must use the Region that contains the resources that you want to share\. If you want to include a global resource, then you must use the designated home Region to create the share\. For example, to share an AWS Cloud WAN core network, you must create the resource share in the `us-east-1` Region\.
+ To view or modify a resource share in the AWS RAM console, you must use the Region that contains the resource share\. Similarly, the AWS RAM AWS CLI and SDK operations let you interact with only resource shares that are in the Region that you specify in your operation\. To view or modify resource shares that contain global resources, you must use the designated home Region, US East \(N\. Virginia\), `us-east-1`\.
+ To view a Regional resource in the AWS RAM console to include it in a resource share, you must use the Region that contains the Regional resource\.
+ To view a global resource in the AWS RAM console to include it in a resource share, you must use the designated home Region, US East \(N\. Virginia\), `us-east-1`\.
+ You can create a resource share with ***both*** Regional and global resources in only the designated home Region, US East \(N\. Virginia\), `us-east-1`\. 