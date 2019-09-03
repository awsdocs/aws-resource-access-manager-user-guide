# Shareable Resources<a name="shareable"></a>

AWS RAM lets you share resources that are provisioned and managed in other AWS services\. AWS RAM does not let you manage resources, but it does provide the features that let you make resources available across AWS accounts\.

The following sections list the services that integrate with AWS RAM, and the resources that support sharing\.

**Topics**
+ [Amazon EC2](#shareable-ec2)
+ [AWS License Manager](#shareable-byol)
+ [Amazon Aurora](#shareable-aur)
+ [Amazon Route 53](#shareable-r53)

## Amazon EC2<a name="shareable-ec2"></a>

You can share the following Amazon EC2 resources using AWS RAM\.


| Resource | Use case | 
| --- | --- | 
|  Capacity Reservations  |  Create and manage Capacity Reservations centrally, and share the reserved capacity with other AWS accounts\. This lets multiple AWS accounts launch their Amazon EC2 instances into centrally\-managed reserved capacity\. For more information, see [Working with Shared Capacity Reservations](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/capacity-reservation-sharing.html) in the *Amazon EC2 User Guide for Linux Instances*\.  | 
|  Subnets  |  Create and manage subnets centrally, and share them with other AWS accounts\. This lets multiple AWS accounts launch their application resources into centrally\-managed VPCs\. These resources include Amazon EC2 instances, Amazon Relational Database Service \(RDS\) databases, Amazon Redshift clusters, and AWS Lambda functions\. For more information, see [ Working with VPC Sharing](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-sharing.html) in the *Amazon VPC User Guide*\.  | 
|  Traffic mirror targets  |  Create and manage traffic mirror targets centrally, and share them with other AWS accounts\. This lets multiple AWS accounts send mirrored network traffic from traffic mirror sources in their accounts to a shared, centrally\-managed traffic mirror target\. For more information, see [ Cross\-Account Traffic Mirroring Targets](https://docs.aws.amazon.com/vpc/latest/mirroring/cross-account-traffic-mirroring-targets.html) in the *Traffic Mirroring Guide*\.  | 
|  Transit gateways  |  Create and manage transit gateways centrally, and share them with other AWS accounts\. This lets multiple AWS accounts route traffic between their VPCs and on\-premises networks through a shared, centrally\-managed transit gateway\. For more information, see [Sharing a Transit Gateway](https://docs.aws.amazon.com/vpc/latest/tgw/tgw-transit-gateways.html#tgw-sharing) in the *Transit Gateways Guide*\.  | 

## AWS License Manager<a name="shareable-byol"></a>

You can share the following AWS License Manager resources using AWS RAM\.


| Resource | Use case | 
| --- | --- | 
|  License configurations  |  Create and manage license configurations centrally, and share them with other AWS accounts\. This lets you enforce centrally\-managed licensing rules that are based on the terms of your enterprise agreements across multiple AWS accounts\. For more information, see [Using License Configurations](https://docs.aws.amazon.com/license-manager/latest/userguide/license-configurations.html) in the *AWS License Manager User Guide*\.  | 

## Amazon Aurora<a name="shareable-aur"></a>

You can share the following Amazon Aurora resources using AWS RAM\.


| Resource | Use case | 
| --- | --- | 
|  DB clusters  |  Create and manage a DB cluster centrally, and share it with other AWS accounts\. This lets multiple AWS accounts clone a shared, centrally\-managed DB cluster\. For more information, see [ Cross\-Account Aurora DB Cluster Cloning](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/Aurora.Managing.Clone.html#Aurora.Managing.Clone.Cross-Account) in the *Amazon Aurora User Guide*\.  | 

## Amazon Route 53<a name="shareable-r53"></a>

You can share the following Amazon Route 53 resources using AWS RAM\.


| Resource | Use case | 
| --- | --- | 
|  Forwarding rules  |  Create and manage forwarding rules centrally, and share them with other AWS accounts\. This lets multiple AWS accounts forward DNS queries from their VPCs to the target IP addresses defined in shared, centrally\-managed resolver rules\. For more information, see [ Sharing Forwarding Rules with Other AWS Accounts and Using Shared Rules](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/resolver-rules-managing.html#resolver-rules-managing-sharing) in the *Amazon Route 53 Developer Guide*\.  | 