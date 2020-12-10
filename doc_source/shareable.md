# Shareable AWS resources<a name="shareable"></a>

AWS RAM enables you to share resources that are provisioned and managed in other AWS services\. AWS RAM does not let you manage resources, but it does provide the features that let you make resources available across AWS accounts\.

The following sections list the services that integrate with AWS RAM, and the resources that support sharing\.

**Topics**
+ [AWS App Mesh](#shareable-appmesh)
+ [Amazon Aurora](#shareable-aur)
+ [AWS Certificate Manager Private Certificate Authority](#shareable-pca)
+ [AWS CodeBuild](#shareable-codebuild)
+ [Amazon EC2](#shareable-ec2)
+ [EC2 Image Builder](#shareable-imagebuilder)
+ [AWS Glue](#shareable-glue)
+ [AWS License Manager](#shareable-byol)
+ [AWS Network Firewall](#shareable-network-firewall)
+ [AWS Outposts](#shareable-out)
+ [AWS Resource Groups](#shareable-arg)
+ [Amazon Route 53](#shareable-r53)
+ [Amazon VPC](#shareable-vpc)

## AWS App Mesh<a name="shareable-appmesh"></a>

You can share the following AWS App Mesh resources using AWS RAM\.


| Resource | Use case | 
| --- | --- | 
|  Mesh  |  Create and manage a mesh centrally, and share it with other AWS accounts\. A shared mesh allows resources created by different AWS accounts to communicate with each other in the same mesh\. For more information, see [ Working with shared meshes](https://docs.aws.amazon.com/app-mesh/latest/userguide/sharing.html) in the *AWS App Mesh User Guide*\.  | 

## Amazon Aurora<a name="shareable-aur"></a>

You can share the following Amazon Aurora resources using AWS RAM\.


| Resource | Use case | 
| --- | --- | 
|  DB clusters  |  Create and manage a DB cluster centrally, and share it with other AWS accounts\. This lets multiple AWS accounts clone a shared, centrally\-managed DB cluster\. For more information, see [ Cross\-Account Aurora DB Cluster Cloning](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/Aurora.Managing.Clone.html#Aurora.Managing.Clone.Cross-Account) in the *Amazon Aurora User Guide*\.  | 

## AWS Certificate Manager Private Certificate Authority<a name="shareable-pca"></a>

You can share the following ACM Private CA resources using AWS RAM\.


| Resource | Use case | 
| --- | --- | 
|  Private certificate authority \(CA\)  |  Create and manage private certificate authorities \(CAs\) for your organization’s internal PKI, and share them with other AWS accounts\. This lets AWS Certificate Manager users in other accounts issue X\.509 certificates signed by your shared CA\. For more information, see [Enabling access to a private CA](https://docs.aws.amazon.com/acm-pca/latest/userguide/granting-ca-access.html) in the *AWS Certificate Manager Private Certificate Authority User Guide*\.  | 

## AWS CodeBuild<a name="shareable-codebuild"></a>

You can share the following AWS CodeBuild resources using AWS RAM\.


| Resource | Use case | 
| --- | --- | 
|  Projects  |  Create a project and use it to run builds\. Share the project with other AWS accounts or users\. This lets multiple AWS accounts and users view information about a project and analyze its builds\. For more information, see [Working with shared projects](https://docs.aws.amazon.com/codebuild/latest/userguide/project-sharing.html) in the * AWS CodeBuild User Guide*\.  | 
|  Report groups  |  Create a report group and use it to create reports when you build a project\. Share the report group with other AWS accounts or users\. This lets multiple AWS accounts and users view the report group and its reports, and the test case results for each report\. A report can be viewed for 30 days after it is created, and then it expires and is no longer available to view\. For more information, see [Working with shared report groups](https://docs.aws.amazon.com/codebuild/latest/userguide/project-sharing.html) in the *AWS CodeBuild User Guide*\.  | 

## Amazon EC2<a name="shareable-ec2"></a>

You can share the following Amazon EC2 resources using AWS RAM\.


| Resource | Use case | 
| --- | --- | 
|  Capacity Reservations  |  Create and manage Capacity Reservations centrally, and share the reserved capacity with other AWS accounts\. This lets multiple AWS accounts launch their Amazon EC2 instances into centrally\-managed reserved capacity\. For more information, see [Working with shared Capacity Reservations](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/capacity-reservation-sharing.html) in the *Amazon EC2 User Guide for Linux Instances*\.  | 
|  Dedicated Hosts  |  Allocate and manage Amazon EC2 Dedicated Hosts centrally, and share the host's instance capacity with other AWS accounts\. This lets multiple AWS accounts launch their Amazon EC2 instances onto centrally\-managed Dedicated Hosts\. For more information, see [ Working with shared Dedicated Hosts](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/dh-sharing.html) in the *Amazon EC2 User Guide for Linux Instances*\.  | 

## EC2 Image Builder<a name="shareable-imagebuilder"></a>

You can share the following EC2 Image Builder resources using AWS RAM\.


| Resource | Use case | 
| --- | --- | 
|  Components  |  Create and manage components centrally, and share them with other AWS accounts or your organization\. Manage who can use predefined build and test components in their image recipes\. For more information, see [ Resource Sharing in EC2 Image Builder](https://docs.aws.amazon.com/imagebuilder/latest/userguide/image-builder-resource-sharing.html) in the *EC2 Image Builder User Guide*\.  | 
|  Images  |  Create and manage your golden images centrally, and share them with other AWS accounts and your organization\. Manage who can use images created with EC2 Image Builder across your organization\.\. For more information, see [ Resource Sharing in EC2 Image Builder](https://docs.aws.amazon.com/imagebuilder/latest/userguide/image-builder-resource-sharing.html) in the *EC2 Image Builder User Guide*\.  | 
|  Image recipes  |  Create and manage your image recipes centrally, and share them with other AWS accounts and your organization\. This allows you to manage who can use predefined documents to automate repeatable image pipelines for a desired configuration\. For more information, see [ Resource Sharing in EC2 Image Builder](https://docs.aws.amazon.com/imagebuilder/latest/userguide/image-builder-resource-sharing.html) in the *EC2 Image Builder User Guide*\.  | 

## AWS Glue<a name="shareable-glue"></a>

You can share the following AWS Glue resources using AWS RAM\.


| Resource | Use case | 
| --- | --- | 
|  Data catalogs  |  Manage a central data catalog and share metadata about databases and tables with AWS accounts and organizations within your enterprise\. This enables users to run queries on data across multiple accounts\. For more information, see [Sharing Data Catalog Tables and Databases Across AWS Accounts](https://docs.aws.amazon.com/lake-formation/latest/dg/sharing-catalog-resources.html) in the *AWS Lake Formation Guide*\.  | 
|  Databases  |  Create and manage data catalog databases centrally and share them with AWS accounts and organizations within your enterprise\. Databases are collections of data catalog tables\. This enables users to run queries and extract, transform, and load \(ETL\) jobs that can join and query data across multiple accounts\. For more information, see [ Sharing Data Catalog Tables and Databases Across AWS Accounts](https://docs.aws.amazon.com/lake-formation/latest/dg/sharing-catalog-resources.html) in the *AWS Lake Formation Guide*\.  | 
|  Tables  |  Create and manage data catalog tables centrally and share them with AWS accounts and organizations within your enterprise\. Data catalog tables contain metadata about data tables in Amazon S3, JDBC data sources, Amazon Redshift, streaming sources, and other data stores\. This enables users to run queries and ETL jobs that can join and query data data across multiple accounts\. For more information, see [Sharing Data Catalog Tables and Databases Across AWS Accounts](https://docs.aws.amazon.com/lake-formation/latest/dg/sharing-catalog-resources.html) in the *AWS Lake Formation Guide*\.  | 

## AWS License Manager<a name="shareable-byol"></a>

You can share the following AWS License Manager resources using AWS RAM\.


| Resource | Use case | 
| --- | --- | 
|  License configurations  |  Create and manage license configurations centrally, and share them with other AWS accounts\. This lets you enforce centrally\-managed licensing rules that are based on the terms of your enterprise agreements across multiple AWS accounts\. For more information, see [Using license configurations](https://docs.aws.amazon.com/license-manager/latest/userguide/license-configurations.html) in the *License Manager User Guide*\.  | 

## AWS Network Firewall<a name="shareable-network-firewall"></a>

You can share the following AWS Network Firewall resources using AWS RAM\.


| Resource | Use case | 
| --- | --- | 
|  Firewall policies  |  Create and manage firewall policies centrally, and share them within your AWS organization\. This enables multiple accounts in an AWS organization to share a common set of network monitoring, protection, and filtering behaviors\. For more information, see [Working with shared firewall policies and rule groups](https://docs.aws.amazon.com/network-firewall/latest/developerguide/sharing.html) in the *AWS Network Firewall Developer Guide*\.  | 
|  Rule groups  |  Create and manage stateless and stateful rule groups centrally, and share them within your AWS organization\. This enables multiple accounts in an AWS organization to share a set of criteria for inspecting and handling network traffic\. For more information, see [Working with shared firewall policies and rule groups](https://docs.aws.amazon.com/network-firewall/latest/developerguide/sharing.html) in the *AWS Network Firewall Developer Guide*\.  | 

## AWS Outposts<a name="shareable-out"></a>

You can share the following AWS Outposts resources using AWS RAM\.


| Resource | Use case | 
| --- | --- | 
|  Outposts  |  Create and manage Outposts centrally, and share them within your AWS organization\. This enables multiple accounts to create subnets and EBS volumes on your shared, centrally \-managed Outposts\. For more information, see [ Working with shared AWS Outposts resources](https://docs.aws.amazon.com/outposts/latest/userguide/sharing-outposts.html) in the *AWS Outposts User Guide*\.   | 
|  Local gateway route tables  |  Create and manage local gateway route tables on Outpost centrally, and share them within your AWS organization\. This enables multiple accounts to create VPC associations to a local gateway, and view configurations of local gateway route tables and virtual interfaces on your Outpost\. For more information, see [Working with shared AWS Outposts resources](https://docs.aws.amazon.com/outposts/latest/userguide/sharing-outposts.html) in the *AWS Outposts User Guide*\.  | 
|  Subnets  |  Create and manage subnets on Outpost centrally, and share them within your AWS organization\. This enables multiple accounts to launch and run EC2 instances in shared subnets on your Outpost\. For more information, see [ Working with shared AWS Outposts resources](https://docs.aws.amazon.com/outposts/latest/userguide/sharing-outposts.html) in the *AWS Outposts User Guide*\.   | 

## AWS Resource Groups<a name="shareable-arg"></a>

You can share the following AWS Resource Groups resources using AWS RAM\.


| Resource | Use case | 
| --- | --- | 
|  Resource groups  |  Create and manage a host resource group centrally, and share it with other AWS accounts\. This lets multiple AWS accounts share a group of Amazon EC2 Dedicated Hosts created using AWS License Manager\. For more information, see [ Host resource groups in AWS License Manager](https://docs.aws.amazon.com/license-manager/latest/userguide/host-resource-groups.html) in the *AWS License Manager User Guide*\.   | 

## Amazon Route 53<a name="shareable-r53"></a>

You can share the following Amazon Route 53 resources using AWS RAM\.


| Resource | Use case | 
| --- | --- | 
|  Forwarding rules  |  Create and manage forwarding rules centrally, and share them with other AWS accounts\. This lets multiple AWS accounts forward DNS queries from their VPCs to the target IP addresses defined in shared, centrally\-managed resolver rules\. For more information, see [ Sharing forwarding rules with other AWS accounts and using shared rules](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/resolver-rules-managing.html#resolver-rules-managing-sharing) in the *Amazon Route 53 Developer Guide*\.  | 
|  Query logs  |  Create and manage query logs centrally, and share them with other AWS accounts\. This enables multiple AWS accounts to log DNS queries that originate in their VPCs to a centrally\-managed query log\. For more information, see [ Sharing Resolver query logging configurations with other AWS accounts](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/query-logging-configurations-managing-sharing.html) in the *Amazon Route 53 Developer Guide*\.  | 

## Amazon VPC<a name="shareable-vpc"></a>

You can share the following Amazon VPC resources using AWS RAM\.


| Resource | Use case | 
| --- | --- | 
| Customer\-owned IPv4 addresses |  During the AWS Outposts installation process, AWS creates an address pool, known as a *customer\-owned IP address pool*, based on information that you provide about your on\-premises network\. Customer\-owned IP addresses provide local, or external connectivity to resources in your Outpost subnets through your on\-premises network\. You can assign these addresses to resources on your Outpost, such as EC2 instances, using Elastic IP addresses\.  | 
|  Prefix lists  |  Create and manage prefix lists centrally, and share them with other AWS accounts\. This lets multiple AWS accounts reference prefix lists in their resources, such as VPC security groups and subnet route tables\. For more information, see [ Working with Shared Prefix Lists](https://docs.aws.amazon.com/vpc/latest/userguide/sharing-managed-prefix-lists.html) in the *Amazon VPC User Guide*\.  | 
|  Subnets  |  Create and manage subnets centrally, and share them with other accounts or organizational units that are in the same organization from AWS Organizations\. This lets multiple AWS accounts launch their application resources into centrally\-managed VPCs\. These resources include Amazon EC2 instances, Amazon Relational Database Service \(RDS\) databases, Amazon Redshift clusters, and AWS Lambda functions\. For more information, see [ Working with VPC sharing](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-sharing.html) in the *Amazon VPC User Guide*\.  | 
|  Traffic mirror targets  |  Create and manage traffic mirror targets centrally, and share them with other AWS accounts\. This lets multiple AWS accounts send mirrored network traffic from traffic mirror sources in their accounts to a shared, centrally\-managed traffic mirror target\. For more information, see [ Cross\-Account Traffic Mirroring Targets](https://docs.aws.amazon.com/vpc/latest/mirroring/cross-account-traffic-mirroring-targets.html) in the *Traffic Mirroring Guide*\.  | 
|  Transit gateways  |  Create and manage transit gateways centrally, and share them with other AWS accounts\. This lets multiple AWS accounts route traffic between their VPCs and on\-premises networks through a shared, centrally\-managed transit gateway\. For more information, see [Sharing a transit gateway](https://docs.aws.amazon.com/vpc/latest/tgw/tgw-transit-gateways.html#tgw-sharing) in the *Amazon VPC Transit Gateways*\.  | 