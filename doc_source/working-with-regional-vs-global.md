# Sharing regional resources versus global resources<a name="working-with-regional-vs-global"></a>

This topic discusses the differences in how AWS Resource Access Manager \(AWS RAM\) works with regional and global resources\.

## What is the difference between regional and global resources?<a name="regional-resources"></a>

**Regional resources**  
Most resources that you can share with AWS RAM are *regional* in nature\. You create them in a specified AWS Region, and they then exist in that Region\. You must direct your operations to that AWS Region to see or interact with those resources\. For example, to create an Amazon Elastic Compute Cloud \(Amazon EC2\) instance with the AWS Management Console, you [point the console to the AWS Region](https://docs.aws.amazon.com/awsconsolehelpdocs/latest/gsg/select-region.html) that you want to create the instance in\. If you use the AWS Command Line Interface \(AWS CLI\) to create the instance, then you include the `--region` parameter\. The AWS SDKs each have their own equivalent mechanism to specify the AWS Region the operation uses\.  
There are several reasons for using regional resources\. One good reason is to ensure that the resources, and the service endpoints that you use to access them are as close to the customer as possible\. This improves performance by minimizing latency\. Another is to provide an isolation boundary\. This lets you create independent copies of resources in multiple Regions to distribute the load and improve scalability\. At the same time, it isolates the resources from each other to improve availability\.  
If you specify a different AWS Region in the AWS Management Console or in a AWS CLI command then you can't see or interact with the resources you could see in the previous Region\.  
When you look at the [Amazon Resource Name \(ARN\)](https://docs.aws.amazon.com/general/latest/gr/aws-arns-and-namespaces.html) for a regional resource, the AWS Region that contains the resource is specified as the fourth field in the ARN\. For example, an Amazon EC2 instance is a regional resource\. Such resources have ARNs that looks similar to the following sample for a VPC that exists in the `us-east-1` Region\.  

```
arn:aws:ec2:us-east-1:123456789012:instance/i-0a6f30921424d3eee
```

**Global resources**  
Some AWS services support resources that are accessible *globally*\. This means that you can use the resource from ***anywhere***\. You don't specify a Region in a global service's console or specify a `--region` parameter when using the service's AWS CLI and AWS SDK operations to access a global resource\.  
Global resources support cases where it is critical that only one instance of a particular resource can exist at a time\. In such scenarios, replication or synchronization between copies in different Regions is not adequate\. The price of having to access a single global endpoint, with the possible increase in latency, is considered acceptable to ensure that any changes are instantaneously visible to consumers of the resource\. For example, when you create a AWS CloudWAN core network as a global resource, it is consistent to all users, appearing as a single, contiguous global network across all regions\.  
The [Amazon Resource Name \(ARN\)](https://docs.aws.amazon.com/general/latest/gr/aws-arns-and-namespaces.html) for a global resource doesn't include an AWS Region\. The fourth field of such an ARN is empty, such as the following sample ARN for a CloudWAN core network:  

```
arn:aws:networkmanager::123456789012:core-network/core-network-0514d38fa6f796cea
```

## Resource shares and their Regions<a name="shares-with-regional-only"></a>

AWS RAM is a regional service, and a resource share is regional\. A resource share can therefore contain resources from the same AWS Region as the resource share, and any supported global resources\. This AWS Region in which you create the resource share is the resource share's *home Region*\.

**Important**  
At this time, you can create resource shares with global resources **only in the designated home Region **US East \(N\. Virginia\) Region, `us-east-1`\. Although you can create the resource share only in that single home Region, any shared global resource continues to appear as a standard global resource when viewed in that service's console or CLI/SDK operations\. The restriction to the home Region applies only to the resource share, not the resources it contains\.

If you want to share a regional resource that you created in the `us-west-2` Region, then you must configure the AWS RAM console to use `us-west-2` and create the resource share there\. You can't create a resource share that includes regional resources from different AWS Regions\. This means that to share resources from both `us-west-2` and `eu-north-1`, you must create two different resource shares\. You can't combine resources from two different Regions into a single resource share\.

If you want to share a global resource, then in the AWS RAM console you must use the designated home Region, US East \(N\. Virginia\) `us-east-1`, and create the resource share there\. This means that you can mix global resources in a resource share only with resources from the `us-east-1` Region\.

Even though the global resource is viewable in a AWS RAM resource share in only the designated home Region, it is still a global resource when share it\. It can be accessed in the shared AWS accounts from any AWS Region from which it is accessible in the original AWS account\.

**Considerations**
+ To create a resource share in the AWS RAM console, you must use the AWS Region that contains the resources that you want to share\. If you want to include a global resource, then you must use the designated home Region to create the share\. For example, to share a AWS CloudWAN core network, you must create the resource share in the `us-east-1` Region\.
+ To view or modify a resource share in the AWS RAM console, you must use the AWS Region that contains the resource share\. Similarly, the AWS RAM AWS CLI/SDK operations let you interact with only resource shares that are in AWS Region that you specify in your operation\. To view or modify resource shares that contain global resources, you must use `us-east-1`\.
+ To view a regional resource in the AWS RAM console to include it in a resource share, you must use the AWS Region that contains the regional resource\.
+ To view a global resource in the AWS RAM console to include it in a resource share, you must use the designated home Region, US East \(N\. Virginia\),`us-east-1`\.
+ You can create a resource share with ***both*** regional and global resources in only the designated home Region, US East \(N\. Virginia\),`us-east-1`\. 