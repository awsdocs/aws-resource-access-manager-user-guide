# Shareable AWS resources<a name="shareable"></a><a name="permissions-rbp-supported-resource-types"></a>

With AWS Resource Access Manager \(AWS RAM\), you can share resources that are created and managed by other AWS services\. You can share resources with individual AWS accounts\. You can also share resources with the accounts in an organization or organizational units \(OUs\) in AWS Organizations\. Some supported resource types also let you share resources with individual AWS Identity and Access Management \(IAM\) roles and users\. 

The following sections list the services that work with AWS RAM, and the resources that support sharing\. Also identified are which resource types can be shared with individual IAM users and roles\.

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
+ [Amazon S3 on Outposts](#shareable-s3outposts)
+ [AWS Resource Groups](#shareable-arg)
+ [Amazon Route 53](#shareable-r53)
+ [AWS Systems Manager Incident Manager](#shareable-incidentmgr)
+ [Amazon VPC](#shareable-vpc)

## AWS App Mesh<a name="shareable-appmesh"></a>

You can share the following AWS App Mesh resources by using AWS RAM\.


| Resource type and code | Use case | Share with IAM users and roles | 
| --- | --- | --- | 
|  Mesh `appmesh:Mesh`  |  Create and manage a mesh centrally, and share it with other AWS accounts or your organization\. A shared mesh allows resources created by different AWS accounts to communicate with each other in the same mesh\. For more information, see [ Working with shared meshes](https://docs.aws.amazon.com/app-mesh/latest/userguide/sharing.html) in the *AWS App Mesh User Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  | 

## Amazon Aurora<a name="shareable-aur"></a>

You can share the following Amazon Aurora resources by using AWS RAM\.


| Resource type and code | Use case | Share with IAM users and roles | 
| --- | --- | --- | 
|  DB clusters `rds:Cluster`  |  Create and manage a DB cluster centrally, and share it with other AWS accounts or your organization\. This lets multiple AWS accounts clone a shared, centrally managed DB cluster\. For more information, see [ Cross\-account cloning with AWS RAM and Amazon Aurora](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/Aurora.Managing.Clone.html#Aurora.Managing.Clone.Cross-Account) in the *Amazon Aurora User Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  | 

## AWS Certificate Manager Private Certificate Authority<a name="shareable-pca"></a>

You can share the following ACM Private CA resources by using AWS RAM\.


| Resource type and code | Use case | Share with IAM users and roles | 
| --- | --- | --- | 
|  Private certificate authority \(CA\) `acm-pca:CertificateAuthority`  |  Create and manage private certificate authorities \(CAs\) for your organization’s internal public key infrastructure \(PKI\), and share those CAs with other AWS accounts or your organization\. This lets AWS Certificate Manager users in other accounts issue X\.509 certificates signed by your shared CA\. For more information, see [Controlling access to a private CA](https://docs.aws.amazon.com/acm-pca/latest/userguide/granting-ca-access.html) in the *AWS Certificate Manager Private Certificate Authority User Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  | 

## AWS CodeBuild<a name="shareable-codebuild"></a>

You can share the following AWS CodeBuild resources by using AWS RAM\.


| Resource type and code | Use case | Share with IAM users and roles | 
| --- | --- | --- | 
|  Project `codebuild:Project`  |  Create a project, and use it to run builds\. Share the project with other AWS accounts or your organization\. This lets multiple AWS accounts and users view information about a project and analyze its builds\. For more information, see [Working with shared projects](https://docs.aws.amazon.com/codebuild/latest/userguide/project-sharing.html) in the * AWS CodeBuild User Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  | 
|  Report group `codebuild:ReportGroup`  |  Create a report group, and use it to create reports when you build a project\. Share the report group with other AWS accounts or your organization\. This lets multiple AWS accounts and users view the report group and its reports, and the test case results for each report\. A report can be viewed for 30 days after it's created, and then it expires and is no longer available to view\. For more information, see [Working with shared projects](https://docs.aws.amazon.com/codebuild/latest/userguide/project-sharing.html) in the *AWS CodeBuild User Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  | 

## Amazon EC2<a name="shareable-ec2"></a>

You can share the following Amazon EC2 resources by using AWS RAM\.


| Resource type and code | Use case | Share with IAM users and roles | 
| --- | --- | --- | 
|  Capacity reservations `ec2:CapacityReservation`  |  Create and manage capacity reservations centrally, and share the reserved capacity with other AWS accounts or your organization\. This lets multiple AWS accounts launch their Amazon EC2 instances into centrally managed reserved capacity\. For more information, see [Working with shared Capacity Reservations](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/capacity-reservation-sharing.html) in the *Amazon EC2 User Guide for Linux Instances*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  | 
|  Dedicated hosts `ec2:DedicatedHost`  |  Allocate and manage Amazon EC2 dedicated hosts centrally, and share the host's instance capacity with other AWS accounts or your organization\. This lets multiple AWS accounts launch their Amazon EC2 instances on to centrally managed dedicated hosts\. For more information, see [ Working with shared Dedicated Hosts](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/dh-sharing.html) in the *Amazon EC2 User Guide for Linux Instances*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  | 

## EC2 Image Builder<a name="shareable-imagebuilder"></a>

You can share the following EC2 Image Builder resources by using AWS RAM\.


| Resource type and code | Use case | Share with IAM users and roles | 
| --- | --- | --- | 
|  Components `imagebuilder:Component`  |  Create and manage components centrally, and share them with other AWS accounts or your organization\. Manage who can use predefined build and test components in their image recipes\. For more information, see [ Share EC2 Image Builder resources](https://docs.aws.amazon.com/imagebuilder/latest/userguide/manage-shared-resources.html) in the *EC2 Image Builder User Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  | 
|  Container recipes `imagebuilder:ContainerRecipe`  |  Create and manage your container recipes centrally, and share them with other AWS accounts or your organization\. This allows you to manage who can use predefined documents to duplicate container image builds\. For more information, see [ Share EC2 Image Builder resources](https://docs.aws.amazon.com/imagebuilder/latest/userguide/manage-shared-resources.html) in the *EC2 Image Builder User Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  | 
|  Images `imagebuilder:Image`  |  Create and manage your golden images centrally, and share them with other AWS accounts or your organization\. Manage who can use images created with EC2 Image Builder across your organization\. For more information, see [ Share EC2 Image Builder resources](https://docs.aws.amazon.com/imagebuilder/latest/userguide/manage-shared-resources.html) in the *EC2 Image Builder User Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  | 
|  Image recipes `imagebuilder:ImageRecipe`  |  Create and manage your image recipes centrally, and share them with other AWS accounts or your organization\. This allows you to manage who can use predefined documents to duplicate AMI builds\. For more information, see [ Share EC2 Image Builder resources](https://docs.aws.amazon.com/imagebuilder/latest/userguide/manage-shared-resources.html) in the *EC2 Image Builder User Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  | 

## AWS Glue<a name="shareable-glue"></a>

You can share the following AWS Glue resources by using AWS RAM\.


| Resource type and code | Use case | Share with IAM users and roles | 
| --- | --- | --- | 
|  Data catalogs `glue:Catalog`  |  Manage a central data catalog, and share metadata about databases and tables with AWS accounts or your organization\. This enables users to run queries on data across multiple accounts\. For more information, see [Sharing Data Catalog Tables and Databases Across AWS Accounts](https://docs.aws.amazon.com/lake-formation/latest/dg/sharing-catalog-resources.html) in the *AWS Lake Formation Developer Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  | 
|  Databases `glue:Database`  |  Create and manage data catalog databases centrally, and share them with AWS accounts or your organization\. Databases are collections of data catalog tables\. This enables users to run queries and extract, transform, and load \(ETL\) jobs that can join and query data across multiple accounts\. For more information, see [ Sharing Data Catalog Tables and Databases Across AWS Accounts](https://docs.aws.amazon.com/lake-formation/latest/dg/sharing-catalog-resources.html) in the *AWS Lake Formation Developer Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  | 
|  Tables `glue:Table`  |  Create and manage data catalog tables centrally, and share them with AWS accounts or your organization\. Data catalog tables contain metadata about data tables in Amazon S3, JDBC data sources, Amazon Redshift, streaming sources, and other data stores\. This enables users to run queries and ETL jobs that can join and query data across multiple accounts\. For more information, see [Sharing Data Catalog Tables and Databases Across AWS Accounts](https://docs.aws.amazon.com/lake-formation/latest/dg/sharing-catalog-resources.html) in the *AWS Lake Formation Developer Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  | 

## AWS License Manager<a name="shareable-byol"></a>

You can share the following AWS License Manager resources by using AWS RAM\.


| Resource type and code | Use case | Share with IAM users and roles | 
| --- | --- | --- | 
|  License configurations `license-manager:LicenseConfiguration`  |  Create and manage license configurations centrally, and share them with other AWS accounts or your organization\. This lets you enforce centrally managed licensing rules that are based on the terms of your enterprise agreements across multiple AWS accounts\. For more information, see [License configurations in License Manager](https://docs.aws.amazon.com/license-manager/latest/userguide/license-configurations.html) in the *License Manager User Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  | 

## AWS Network Firewall<a name="shareable-network-firewall"></a>

You can share the following AWS Network Firewall resources by using AWS RAM\.


| Resource type and code | Use case | Share with IAM users and roles | 
| --- | --- | --- | 
|  Firewall policies `network-firewall:FirewallPolicy`  |  Create and manage firewall policies centrally, and share them with other AWS accounts or your organization\. This enables multiple accounts in an organization to share a common set of network monitoring, protection, and filtering behaviors\. For more information, see [Sharing firewall policies and rule groups](https://docs.aws.amazon.com/network-firewall/latest/developerguide/sharing.html) in the *AWS Network Firewall Developer Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  | 
|  Rule groups `network-firewall:StatefulRuleGroup` `network-firewall:StatelessRuleGroup`  |  Create and manage stateless and stateful rule groups centrally, and share them with other AWS accounts or your organization\. This enables multiple accounts in an organization in AWS Organizations to share a set of criteria for inspecting and handling network traffic\. For more information, see [Sharing firewall policies and rule groups](https://docs.aws.amazon.com/network-firewall/latest/developerguide/sharing.html) in the *AWS Network Firewall Developer Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  | 

## AWS Outposts<a name="shareable-out"></a>

You can share the following AWS Outposts resources by using AWS RAM\.


| Resource type and code | Use case | Share with IAM users and roles | 
| --- | --- | --- | 
|  Outposts `outposts:Outpost`  |  Create and manage Outposts centrally, and share them with other AWS accounts in your organization\. This lets multiple accounts create subnets and EBS volumes on your shared, centrally managed Outposts\. For more information, see [ Working with shared AWS Outposts resources](https://docs.aws.amazon.com/outposts/latest/userguide/sharing-outposts.html) in the *AWS Outposts User Guide*\.   |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  | 
|  Local gateway route table `ec2:LocalGatewayRouteTable`  |  Create and manage VPC associations to a local gateway centrally, and share them with other AWS accounts in your organization\. This lets multiple accounts create VPC associations to a local gateway, and view route table and virtual interface configuration\. For more information, see [Shareable Outpost resources](https://docs.aws.amazon.com/outposts/latest/userguide/sharing-outposts.html#sharing-resources) in the *AWS Outposts User Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  | 
|  Sites `outposts:Site`  |  Create and manage Outpost sites and share them with other AWS accounts in your organization\. This lets multiple accounts create and manage Outposts at the shared site and supports split control between the Outpost resources and the site\. For more information, see [ Working with shared AWS Outposts resources](https://docs.aws.amazon.com/outposts/latest/userguide/sharing-outposts.html) in the *AWS Outposts User Guide*\.   |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  | 

## Amazon S3 on Outposts<a name="shareable-s3outposts"></a>

You can share the following Amazon S3 on Outposts resource by using AWS RAM\.


| Resource type and code | Use case | Share with IAM users and roles | 
| --- | --- | --- | 
|  S3 on Outpost `s3-outposts:Outpost`  |  Create and manage Amazon S3 buckets, access points, and endpoints on the Outpost\. This lets multiple accounts create and manage Outposts at the shared site and supports split control between the Outpost resources and the site\. For more information, see [ Working with shared AWS Outposts resources](https://docs.aws.amazon.com/outposts/latest/userguide/sharing-outposts.html) in the *AWS Outposts User Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  | 

## AWS Resource Groups<a name="shareable-arg"></a>

You can share the following AWS Resource Groups resources by using AWS RAM\.


| Resource type and code | Use case | Share with IAM users and roles | 
| --- | --- | --- | 
|  Resource groups `resource-groups:Group`  |  Create and manage a host resource group centrally, and share it with other AWS accounts in your organization\. This lets multiple AWS accounts share a group of Amazon EC2 Dedicated Hosts created using AWS License Manager\. For more information, see [ Host resource groups in AWS License Manager](https://docs.aws.amazon.com/license-manager/latest/userguide/host-resource-groups.html) in the *AWS License Manager User Guide*\.   |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  | 

## Amazon Route 53<a name="shareable-r53"></a>

You can share the following Amazon Route 53 resources by using AWS RAM\.


| Resource type and code | Use case | Share with IAM users and roles | 
| --- | --- | --- | 
|  Route 53 Resolver DNS Firewall rule groups `route53resolver:FirewallRuleGroup`  |  Create and manage Route 53 Resolver DNS Firewall rule groups centrally, and share them with other AWS accounts or your organization\. This enables multiple accounts to share a set of criteria for inspecting and handling outbound DNS queries that go through Route 53 Resolver\. For more information, see [Sharing Route 53 Resolver DNS Firewall rule groups between AWS accounts](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/resolver-dns-firewall-rule-group-sharing.html) in the *Amazon Route 53 Developer Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  | 
|  Forwarding rules `route53resolver:ResolverRule`  |  Create and manage forwarding rules centrally, and share them with other AWS accounts or your organization\. This lets multiple accounts forward DNS queries from their virtual private clouds \(VPCs\) to the target IP addresses defined in shared, centrally managed resolver rules\. For more information, see [ Sharing forwarding rules with other AWS accounts and using shared rules](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/resolver-rules-managing.html#resolver-rules-managing-sharing) in the *Amazon Route 53 Developer Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  | 
|  Query logs `route53resolver:ResolverQueryLogConfig`  |  Create and manage query logs centrally, and share them with other AWS accounts or your organization\. This enables multiple AWS accounts to log DNS queries that originate in their VPCs to a centrally managed query log\. For more information, see [ Sharing Resolver query logging configurations with other AWS accounts](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/query-logging-configurations-managing-sharing.html) in the *Amazon Route 53 Developer Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  | 

## AWS Systems Manager Incident Manager<a name="shareable-incidentmgr"></a>

You can share the following AWS Systems Manager Incident Manager resources by using AWS RAM\.


| Resource type and code | Use case | Share with IAM users and roles | 
| --- | --- | --- | 
|  Contacts `ssm-contacts:Contact`  |  Create and manage contacts and escalation plans centrally, and share the contact details with other AWS accounts or your organization\. This lets many AWS accounts view engagements occurring during an incident\. For more information, see [Working with shared contacts and response plans](https://docs.aws.amazon.com/incident-manager/latest/userguide/sharing.html) in the *AWS Systems Manager Incident Manager User Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  | 
|  Response plans `ssm-incidents:ResponsePlan`  |  Create and manage response plans centrally, and share them with other AWS accounts or your organization\. This lets those AWS accounts connect Amazon CloudWatch alarms and Amazon EventBridge event rules to response plans, automatically creating an incident when it’s detected\. The incident also has access to the metrics of these other AWS accounts\. For more information, see [Working with shared contacts and response plans](https://docs.aws.amazon.com/incident-manager/latest/userguide/sharing.html) in the *AWS Systems Manager Incident Manager User Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  | 

## Amazon VPC<a name="shareable-vpc"></a>

You can share the following Amazon Virtual Private Cloud \(Amazon VPC\) resources by using AWS RAM\.


| Resource type and code | Use case | Share with IAM users and roles | 
| --- | --- | --- | 
|  Customer\-owned IPv4 addresses `ec2:CoipPool`  |  During the AWS Outposts installation process, AWS creates an address pool, known as a *customer\-owned IP address pool*, based on information that you provide about your on\-premises network\. Customer\-owned IP addresses provide local, or external connectivity to resources in your Outposts subnets through your on\-premises network\. You can assign these addresses to resources on your Outpost, such as EC2 instances, using Elastic IP addresses or using the subnet setting that automatically assigns customer\-owned IP addresses\. For more information, see [Customer\-owned IP addresses](https://docs.aws.amazon.com/outposts/latest/userguide/outposts-networking-components.html#ip-addressing) in the *AWS Outposts User Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  | 
|  Prefix lists `ec2:PrefixList`  |  Create and manage prefix lists centrally, and share them with other AWS accounts or your organization\. This lets multiple AWS accounts reference prefix lists in their resources, such as VPC security groups and subnet route tables\. For more information, see [ Working with shared prefix lists](https://docs.aws.amazon.com/vpc/latest/userguide/sharing-managed-prefix-lists.html) in the *Amazon VPC User Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  | 
|  Subnets `ec2:Subnet`  |  Create and manage subnets centrally, and share them with other AWS accounts or your organization\. This lets multiple AWS accounts launch their application resources into centrally managed VPCs\. These resources include Amazon EC2 instances, Amazon Relational Database Service \(RDS\) databases, Amazon Redshift clusters, and AWS Lambda functions\. For more information, see [ Working with VPC sharing](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-sharing.html) in the *Amazon VPC User Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  | 
|  Traffic mirror targets `ec2:TrafficMirrorTarget`  |  Create and manage traffic mirror targets centrally, and share them with other AWS accounts or your organization\. This lets multiple AWS accounts send mirrored network traffic from traffic mirror sources in their accounts to a shared, centrally managed traffic mirror target\. For more information, see [ Cross\-account traffic mirroring targets](https://docs.aws.amazon.com/vpc/latest/mirroring/cross-account-traffic-mirroring-targets.html) in the *Traffic Mirroring Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  | 
|  Transit gateways `ec2:TransitGateway`  |  Create and manage transit gateways centrally, and share them with other AWS accounts or your organization\. This lets multiple AWS accounts route traffic between their VPCs and on\-premises networks through a shared, centrally managed transit gateway\. For more information, see [Sharing a transit gateway](https://docs.aws.amazon.com/vpc/latest/tgw/tgw-transit-gateways.html#tgw-sharing) in the *Amazon VPC Transit Gateways*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  | 
|  Transit gateway multicast domains `ec2:TransitGatewayMulticastDomain`  | Create and manage transit gateway multicast domains centrally, and share them with other AWS accounts or your organization\. This lets multiple AWS accounts register and deregister group members or group sources in the multicast domain\. For more information, see [Working with shared multicast domains](https://docs.aws.amazon.com/vpc/latest/tgw/tgw-transit-gateways.html#multicast-sharing.html) in the Transit Gateways Guide\. |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  | 