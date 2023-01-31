# Shareable AWS resources<a name="shareable"></a><a name="permissions-rbp-supported-resource-types"></a>

With AWS Resource Access Manager \(AWS RAM\), you can share resources that are created and managed by other AWS services\. You can share resources with individual AWS accounts\. You can also share resources with the accounts in an organization or organizational units \(OUs\) in AWS Organizations\. Some supported resource types also let you share resources with individual AWS Identity and Access Management \(IAM\) roles and users\. 

The following sections list the resource types, grouped by AWS service, that you can share by using AWS RAM\. The columns in the tables specify which features each resource type supports:


|  |  | 
| --- |--- |
|  **Can share with IAM users and roles**  |   ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  – you can share resources of this type with individual AWS Identity and Access Management \(IAM\) roles and users, in addition to accounts \.  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  – you can share resources of this type with only accounts\.   | 
|  **Can share with accounts outside its organization**  |   ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  – you can share resources of this type with any individual account, inside or outside of its organization\.  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  – you can share resources of this type with only accounts that are members of the same organization\.  | 

## AWS App Mesh<a name="shareable-appmesh"></a>

You can share the following AWS App Mesh resources by using AWS RAM\.


| Resource type and code | Use case | Can share with IAM users and roles | Can share with accounts outside its organization | 
| --- | --- | --- | --- | 
|  Mesh `appmesh:Mesh`  |  Create and manage a mesh centrally, and share it with other AWS accounts or your organization\. A shared mesh allows resources created by different AWS accounts to communicate with each other in the same mesh\. For more information, see [ Working with shared meshes](https://docs.aws.amazon.com/app-mesh/latest/userguide/sharing.html) in the *AWS App Mesh User Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  Can share with **any** AWS account\. | 

## Amazon Aurora<a name="shareable-aur"></a>

You can share the following Amazon Aurora resources by using AWS RAM\.


| Resource type and code | Use case | Can share with IAM users and roles | Can share with accounts outside its organization | 
| --- | --- | --- | --- | 
|  DB clusters `rds:Cluster`  |  Create and manage a DB cluster centrally, and share it with other AWS accounts or your organization\. This lets multiple AWS accounts clone a shared, centrally managed DB cluster\. For more information, see [ Cross\-account cloning with AWS RAM and Amazon Aurora](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/Aurora.Managing.Clone.html#Aurora.Managing.Clone.Cross-Account) in the *Amazon Aurora User Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  Can share with **any** AWS account\. | 

## AWS Private Certificate Authority<a name="shareable-pca"></a>

You can share the following AWS Private CA resources by using AWS RAM\.


| Resource type and code | Use case | Can share with IAM users and roles | Can share with accounts outside its organization | 
| --- | --- | --- | --- | 
|  Private certificate authority \(CA\) `acm-pca:CertificateAuthority`  |  Create and manage private certificate authorities \(CAs\) for your organization’s internal public key infrastructure \(PKI\), and share those CAs with other AWS accounts or your organization\. This lets AWS Certificate Manager users in other accounts issue X\.509 certificates signed by your shared CA\. For more information, see [Controlling access to a private CA](https://docs.aws.amazon.com/acm-pca/latest/userguide/granting-ca-access.html) in the *AWS Private Certificate Authority User Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  Can share with **any** AWS account\. | 

## AWS CodeBuild<a name="shareable-codebuild"></a>

You can share the following AWS CodeBuild resources by using AWS RAM\.


| Resource type and code | Use case | Can share with IAM users and roles | Can share with accounts outside its organization | 
| --- | --- | --- | --- | 
|  Project `codebuild:Project`  |  Create a project, and use it to run builds\. Share the project with other AWS accounts or your organization\. This lets multiple AWS accounts and users view information about a project and analyze its builds\. For more information, see [Working with shared projects](https://docs.aws.amazon.com/codebuild/latest/userguide/project-sharing.html) in the * AWS CodeBuild User Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  Can share with **any** AWS account\. | 
|  Report group `codebuild:ReportGroup`  |  Create a report group, and use it to create reports when you build a project\. Share the report group with other AWS accounts or your organization\. This lets multiple AWS accounts and users view the report group and its reports, and the test case results for each report\. A report can be viewed for 30 days after it's created, and then it expires and is no longer available to view\. For more information, see [Working with shared projects](https://docs.aws.amazon.com/codebuild/latest/userguide/project-sharing.html) in the *AWS CodeBuild User Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  Can share with **any** AWS account\. | 

## Amazon EC2<a name="shareable-ec2"></a>

You can share the following Amazon EC2 resources by using AWS RAM\.


| Resource type and code | Use case | Can share with IAM users and roles | Can share with accounts outside its organization | 
| --- | --- | --- | --- | 
|  Capacity reservations `ec2:CapacityReservation`  |  Create and manage capacity reservations centrally, and share the reserved capacity with other AWS accounts or your organization\. This lets multiple AWS accounts launch their Amazon EC2 instances into centrally managed reserved capacity\. For more information, see [Working with shared Capacity Reservations](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/capacity-reservation-sharing.html) in the *Amazon EC2 User Guide for Linux Instances*\.  If you don't meet all of the [prerequisites for sharing a capacity reservation](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/capacity-reservation-sharing.html#sharing-cr-prereq), then the sharing operation can fail\. If this happens and a user attempts to launch an Amazon EC2 instance into that capacity reservation, it launches as an on\-demand instance that can accrue higher costs\. We recommend that you verify that you can access the shared capacity reservation by attempting to [view it in the Amazon EC2 console](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/capacity-reservation-sharing.html#identifying-shared-cr)\. You can also monitor for failed resource shares so that you can take corrective action before users launch instances in ways that raise your costs\. For more information, see [Example: Alerting on resource share failures](using-cloudwatch-events.md#using-cloudwatch-events-example-sharing)\.   |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  Can share with **any** AWS account\. | 
|  Dedicated hosts `ec2:DedicatedHost`  |  Allocate and manage Amazon EC2 dedicated hosts centrally, and share the host's instance capacity with other AWS accounts or your organization\. This lets multiple AWS accounts launch their Amazon EC2 instances on to centrally managed dedicated hosts\. For more information, see [ Working with shared Dedicated Hosts](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/dh-sharing.html) in the *Amazon EC2 User Guide for Linux Instances*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  Can share with **any** AWS account\. | 
|  Placement groups `ec2:PlacementGroup`  | Share the placement groups you own across your AWS accounts, both within and outside your organization\. You can launch Amazon EC2 instances from any of the accounts you share with into a shared placement group\. For more information, see, [Share a placement group](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/share-placement-group.html) in the Amazon EC2 User Guide for Linux Instances\. |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  Can share with **any** AWS account\. | 

## EC2 Image Builder<a name="shareable-imagebuilder"></a>

You can share the following EC2 Image Builder resources by using AWS RAM\.


| Resource type and code | Use case | Can share with IAM users and roles | Can share with accounts outside its organization | 
| --- | --- | --- | --- | 
|  Components `imagebuilder:Component`  |  Create and manage components centrally, and share them with other AWS accounts or your organization\. Manage who can use predefined build and test components in their image recipes\. For more information, see [ Share EC2 Image Builder resources](https://docs.aws.amazon.com/imagebuilder/latest/userguide/manage-shared-resources.html) in the *EC2 Image Builder User Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  Can share with **any** AWS account\. | 
|  Container recipes `imagebuilder:ContainerRecipe`  |  Create and manage your container recipes centrally, and share them with other AWS accounts or your organization\. This allows you to manage who can use predefined documents to duplicate container image builds\. For more information, see [ Share EC2 Image Builder resources](https://docs.aws.amazon.com/imagebuilder/latest/userguide/manage-shared-resources.html) in the *EC2 Image Builder User Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  Can share with **any** AWS account\. | 
|  Images `imagebuilder:Image`  |  Create and manage your golden images centrally, and share them with other AWS accounts or your organization\. Manage who can use images created with EC2 Image Builder across your organization\. For more information, see [ Share EC2 Image Builder resources](https://docs.aws.amazon.com/imagebuilder/latest/userguide/manage-shared-resources.html) in the *EC2 Image Builder User Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  Can share with **any** AWS account\. | 
|  Image recipes `imagebuilder:ImageRecipe`  |  Create and manage your image recipes centrally, and share them with other AWS accounts or your organization\. This allows you to manage who can use predefined documents to duplicate AMI builds\. For more information, see [ Share EC2 Image Builder resources](https://docs.aws.amazon.com/imagebuilder/latest/userguide/manage-shared-resources.html) in the *EC2 Image Builder User Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  Can share with **any** AWS account\. | 

## AWS Glue<a name="shareable-glue"></a>

You can share the following AWS Glue resources by using AWS RAM\.


| Resource type and code | Use case | Can share with IAM users and roles | Can share with accounts outside its organization | 
| --- | --- | --- | --- | 
|  Data catalogs `glue:Catalog`  |  Manage a central data catalog, and share metadata about databases and tables with AWS accounts or your organization\. This enables users to run queries on data across multiple accounts\. For more information, see [Sharing Data Catalog Tables and Databases Across AWS Accounts](https://docs.aws.amazon.com/lake-formation/latest/dg/sharing-catalog-resources.html) in the *AWS Lake Formation Developer Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  Can share with **any** AWS account\. | 
|  Databases `glue:Database`  |  Create and manage data catalog databases centrally, and share them with AWS accounts or your organization\. Databases are collections of data catalog tables\. This enables users to run queries and extract, transform, and load \(ETL\) jobs that can join and query data across multiple accounts\. For more information, see [ Sharing Data Catalog Tables and Databases Across AWS Accounts](https://docs.aws.amazon.com/lake-formation/latest/dg/sharing-catalog-resources.html) in the *AWS Lake Formation Developer Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  Can share with **any** AWS account\. | 
|  Tables `glue:Table`  |  Create and manage data catalog tables centrally, and share them with AWS accounts or your organization\. Data catalog tables contain metadata about data tables in Amazon S3, JDBC data sources, Amazon Redshift, streaming sources, and other data stores\. This enables users to run queries and ETL jobs that can join and query data across multiple accounts\. For more information, see [Sharing Data Catalog Tables and Databases Across AWS Accounts](https://docs.aws.amazon.com/lake-formation/latest/dg/sharing-catalog-resources.html) in the *AWS Lake Formation Developer Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  Can share with **any** AWS account\. | 

## AWS License Manager<a name="shareable-byol"></a>

You can share the following AWS License Manager resources by using AWS RAM\.


| Resource type and code | Use case | Can share with IAM users and roles | Can share with accounts outside its organization | 
| --- | --- | --- | --- | 
|  License configurations `license-manager:LicenseConfiguration`  |  Create and manage license configurations centrally, and share them with other AWS accounts or your organization\. This lets you enforce centrally managed licensing rules that are based on the terms of your enterprise agreements across multiple AWS accounts\. For more information, see [License configurations in License Manager](https://docs.aws.amazon.com/license-manager/latest/userguide/license-configurations.html) in the *License Manager User Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  Can share with **any** AWS account\. | 

## AWS Migration Hub Refactor Spaces<a name="shareable-mhb"></a>

You can share the following AWS Migration Hub Refactor Spaces resources by using AWS RAM\.


| Resource type and code | Use case | Can share with IAM users and roles | Can share with accounts outside its organization | 
| --- | --- | --- | --- | 
|  Refactor Spaces Environment `refactor-spaces:Environment`  |  Create a Refactor Spaces environment, and use it to contain your Refactor Spaces applications\. Share the environment with other AWS accounts or all of the accounts in your organization\. This lets multiple AWS accounts and users view information about the environment and the applications in it\. For more information, see [Sharing Refactor Spaces environments using AWS RAM](https://docs.aws.amazon.com/migrationhub-refactor-spaces/latest/userguide/sharing.html) in the *AWS Migration Hub Refactor Spaces User Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  Can share with **any** AWS account\. | 

## AWS Network Firewall<a name="shareable-network-firewall"></a>

You can share the following AWS Network Firewall resources by using AWS RAM\.


| Resource type and code | Use case | Can share with IAM users and roles | Can share with accounts outside its organization | 
| --- | --- | --- | --- | 
|  Firewall policies `network-firewall:FirewallPolicy`  |  Create and manage firewall policies centrally, and share them with other AWS accounts or your organization\. This enables multiple accounts in an organization to share a common set of network monitoring, protection, and filtering behaviors\. For more information, see [Sharing firewall policies and rule groups](https://docs.aws.amazon.com/network-firewall/latest/developerguide/sharing.html) in the *AWS Network Firewall Developer Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  Can share with **any** AWS account\. | 
|  Rule groups `network-firewall:StatefulRuleGroup` `network-firewall:StatelessRuleGroup`  |  Create and manage stateless and stateful rule groups centrally, and share them with other AWS accounts or your organization\. This enables multiple accounts in an organization in AWS Organizations to share a set of criteria for inspecting and handling network traffic\. For more information, see [Sharing firewall policies and rule groups](https://docs.aws.amazon.com/network-firewall/latest/developerguide/sharing.html) in the *AWS Network Firewall Developer Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  Can share with **any** AWS account\. | 

## AWS Outposts<a name="shareable-out"></a>

You can share the following AWS Outposts resources by using AWS RAM\.


| Resource type and code | Use case | Can share with IAM users and roles | Can share with accounts outside its organization | 
| --- | --- | --- | --- | 
|  Outposts `outposts:Outpost`  |  Create and manage Outposts centrally, and share them with other AWS accounts in your organization\. This lets multiple accounts create subnets and EBS volumes on your shared, centrally managed Outposts\. For more information, see [ Working with shared AWS Outposts resources](https://docs.aws.amazon.com/outposts/latest/userguide/sharing-outposts.html) in the *AWS Outposts User Guide*\.   |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  Can share with **only** AWS accounts in its own organization\. | 
|  Local gateway route table `ec2:LocalGatewayRouteTable`  |  Create and manage VPC associations to a local gateway centrally, and share them with other AWS accounts in your organization\. This lets multiple accounts create VPC associations to a local gateway, and view route table and virtual interface configuration\. For more information, see [Shareable Outpost resources](https://docs.aws.amazon.com/outposts/latest/userguide/sharing-outposts.html#sharing-resources) in the *AWS Outposts User Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  Can share with **only** AWS accounts in its own organization\. | 
|  Sites `outposts:Site`  |  Create and manage Outpost sites and share them with other AWS accounts in your organization\. This lets multiple accounts create and manage Outposts at the shared site and supports split control between the Outpost resources and the site\. For more information, see [ Working with shared AWS Outposts resources](https://docs.aws.amazon.com/outposts/latest/userguide/sharing-outposts.html) in the *AWS Outposts User Guide*\.   |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  Can share with **any** AWS account\. | 

## Amazon S3 on Outposts<a name="shareable-s3outposts"></a>

You can share the following Amazon S3 on Outposts resource by using AWS RAM\.


| Resource type and code | Use case | Can share with IAM users and roles | Can share with accounts outside its organization | 
| --- | --- | --- | --- | 
|  S3 on Outpost `s3-outposts:Outpost`  |  Create and manage Amazon S3 buckets, access points, and endpoints on the Outpost\. This lets multiple accounts create and manage Outposts at the shared site and supports split control between the Outpost resources and the site\. For more information, see [ Working with shared AWS Outposts resources](https://docs.aws.amazon.com/outposts/latest/userguide/sharing-outposts.html) in the *AWS Outposts User Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  Can share with **only** AWS accounts in its own organization\. | 

## AWS Resource Explorer<a name="shareable-arex"></a>

You can share the following AWS Resource Explorer resources by using AWS RAM\.


| Resource type and code | Use case | Can share with IAM users and roles | Can share with accounts outside its organization | 
| --- | --- | --- | --- | 
|  Views `resource-explorer-2:View`  |  Create and configure Resource Explorer views centrally, and share them with other AWS accounts in your organization\. This lets roles and users in multiple AWS accounts search for and discover the resources accessible through the view\. For more information, see [About Resource Explorer views](https://docs.aws.amazon.com/resource-explorer/latest/userguide/manage-views-about.html) in the *AWS Resource Explorer User Guide*\.   |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  Can share with **any** AWS account\. | 

## AWS Resource Groups<a name="shareable-arg"></a>

You can share the following AWS Resource Groups resources by using AWS RAM\.


| Resource type and code | Use case | Can share with IAM users and roles | Can share with accounts outside its organization | 
| --- | --- | --- | --- | 
|  Resource groups `resource-groups:Group`  |  Create and manage a host resource group centrally, and share it with other AWS accounts in your organization\. This lets multiple AWS accounts share a group of Amazon EC2 Dedicated Hosts created using AWS License Manager\. For more information, see [ Host resource groups in AWS License Manager](https://docs.aws.amazon.com/license-manager/latest/userguide/host-resource-groups.html) in the *AWS License Manager User Guide*\.   |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  Can share with **any** AWS account\. | 

## Amazon Route 53<a name="shareable-r53"></a>

You can share the following Amazon Route 53 resources by using AWS RAM\.


| Resource type and code | Use case | Can share with IAM users and roles | Can share with accounts outside its organization | 
| --- | --- | --- | --- | 
|  Route 53 Resolver DNS Firewall rule groups `route53resolver:FirewallRuleGroup`  |  Create and manage Route 53 Resolver DNS Firewall rule groups centrally, and share them with other AWS accounts or your organization\. This enables multiple accounts to share a set of criteria for inspecting and handling outbound DNS queries that go through Route 53 Resolver\. For more information, see [Sharing Route 53 Resolver DNS Firewall rule groups between AWS accounts](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/resolver-dns-firewall-rule-group-sharing.html) in the *Amazon Route 53 Developer Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  Can share with **any** AWS account\. | 
|  Forwarding rules `route53resolver:ResolverRule`  |  Create and manage forwarding rules centrally, and share them with other AWS accounts or your organization\. This lets multiple accounts forward DNS queries from their virtual private clouds \(VPCs\) to the target IP addresses defined in shared, centrally managed resolver rules\. For more information, see [ Sharing forwarding rules with other AWS accounts and using shared rules](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/resolver-rules-managing.html#resolver-rules-managing-sharing) in the *Amazon Route 53 Developer Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  Can share with **any** AWS account\. | 
|  Query logs `route53resolver:ResolverQueryLogConfig`  |  Create and manage query logs centrally, and share them with other AWS accounts or your organization\. This enables multiple AWS accounts to log DNS queries that originate in their VPCs to a centrally managed query log\. For more information, see [ Sharing Resolver query logging configurations with other AWS accounts](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/query-logging-configurations-managing-sharing.html) in the *Amazon Route 53 Developer Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  Can share with **any** AWS account\. | 

## Amazon SageMaker<a name="shareable-sagemaker"></a>

You can share the following Amazon SageMaker resources by using AWS RAM\.


| Resource type and code | Use case | Can share with IAM users and roles | Can share with accounts outside its organization | 
| --- | --- | --- | --- | 
|  Lineage group `sagemaker:LineageGroup`  |  Amazon SageMaker lets you create lineage groups of your pipeline metadata to get a deeper understanding of its history and relationships\. Share the lineage group with other AWS accounts or the accounts in your organization\. This lets multiple AWS accounts and users view information about the lineage group and query the tracking entities within it\. For more information, see [Cross\-Account Lineage Tracking](https://docs.aws.amazon.com/sagemaker/latest/dg/xaccount-lineage-tracking.html) in the *Amazon SageMaker Developer Guide*\.   |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  Can share with **any** AWS account\. | 
|  SageMaker pipeline `sagemaker:Pipeline`  |  With Amazon SageMaker Model Building Pipelines, you can create, automate, and manage end\-to\-end machine learning workflows at scale\. Share your pipelines with other AWS accounts or the accounts in your organization to achieve a multi\-account strategy for your machine learning operations\. This lets multiple AWS accounts and users view information about a pipeline and its executions with optional access to start, stop, and retry pipelines from other accounts\. For more information, see [Cross\-Account Support for SageMaker Pipelines](https://docs.aws.amazon.com/sagemaker/latest/dg/build-and-manage-xaccount.html) in the *Amazon SageMaker Developer Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  Can share with **any** AWS account\. | 

## AWS Service Catalog AppRegistry<a name="shareable-sc-appregistry"></a>

You can share the following AWS Service Catalog AppRegistry resources by using AWS RAM\.


| Resource type and code | Use case | Can share with IAM users and roles | Can share with accounts outside its organization | 
| --- | --- | --- | --- | 
|  Application `servicecatalog:Application`  |  Create an application, and use it to track the resources belonging to that application throughout your AWS environment\. Share the application with other AWS accounts or your organization\. This lets multiple AWS accounts and users view information about the application and associated resources with it locally\. For more information, see [Creating applications](https://docs.aws.amazon.com/servicecatalog/latest/arguide/create-apps.html) in the *Service Catalog User Guide*\. \.   |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  Can share with **only** AWS accounts in its own organization\. | 
|  Attribute Group `servicecatalog:AttributeGroup`  |  Create an attribute group, and use it to store meta\-data relating to your applications\. Share the attribute groups with other AWS accounts or your organization\. This lets multiple AWS accounts and users view information about the attribute groups\. For more information, see [Creating attribute groups](https://docs.aws.amazon.com/servicecatalog/latest/arguide/associate-attributes.html) in the *Service Catalog User Guide*\. \.   |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  Can share with **only** AWS accounts in its own organization\. | 

## AWS Systems Manager Incident Manager<a name="shareable-incidentmgr"></a>

You can share the following AWS Systems Manager Incident Manager resources by using AWS RAM\.


| Resource type and code | Use case | Can share with IAM users and roles | Can share with accounts outside its organization | 
| --- | --- | --- | --- | 
|  Contacts `ssm-contacts:Contact`  |  Create and manage contacts and escalation plans centrally, and share the contact details with other AWS accounts or your organization\. This lets many AWS accounts view engagements occurring during an incident\. For more information, see [Working with shared contacts and response plans](https://docs.aws.amazon.com/incident-manager/latest/userguide/sharing.html) in the *AWS Systems Manager Incident Manager User Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  Can share with **any** AWS account\. | 
|  Response plans `ssm-incidents:ResponsePlan`  |  Create and manage response plans centrally, and share them with other AWS accounts or your organization\. This lets those AWS accounts connect Amazon CloudWatch alarms and Amazon EventBridge event rules to response plans, automatically creating an incident when it’s detected\. The incident also has access to the metrics of these other AWS accounts\. For more information, see [Working with shared contacts and response plans](https://docs.aws.amazon.com/incident-manager/latest/userguide/sharing.html) in the *AWS Systems Manager Incident Manager User Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  Can share with **any** AWS account\. | 

## Amazon VPC<a name="shareable-vpc"></a>

You can share the following Amazon Virtual Private Cloud \(Amazon VPC\) resources by using AWS RAM\.


| Resource type and code | Use case | Can share with IAM users and roles | Can share with accounts outside its organization | 
| --- | --- | --- | --- | 
|  Customer\-owned IPv4 addresses `ec2:CoipPool`  |  During the AWS Outposts installation process, AWS creates an address pool, known as a *customer\-owned IP address pool*, based on information that you provide about your on\-premises network\. Customer\-owned IP addresses provide local, or external connectivity to resources in your Outposts subnets through your on\-premises network\. You can assign these addresses to resources on your Outpost, such as EC2 instances, using Elastic IP addresses or using the subnet setting that automatically assigns customer\-owned IP addresses\. For more information, see [Customer\-owned IP addresses](https://docs.aws.amazon.com/outposts/latest/userguide/outposts-networking-components.html#ip-addressing) in the *AWS Outposts User Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  Can share with **only** AWS accounts in its own organization\. | 
|  IP Address Manager \(IPAM\) pools `ec2:IpamPool`  |  Share Amazon VPC IPAM pools centrally with other AWS accounts, IAM roles or users, or an entire organization or organizational unit \(OU\) in AWS Organizations\. This lets those principals allocate CIDRs from the pool to AWS resources, such as VPCs, in their respective accounts\. For more information, see [Share an IPAM pool using AWS RAM](https://docs.aws.amazon.com/vpc/latest/ipam/managing.html#shared-resource-pools) in the *Amazon VPC IP Address Manager User Guide*\.   |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  Can share with **any** AWS account\. | 
|  IP Address Manager \(IPAM\) resource discoveries `ec2:IpamResourceDiscovery`  |  Share resource discoveries with other AWS accounts\. A resource discovery is an Amazon VPC IPAM component that enables IPAM to manage and monitor resources that belong to the owning account\. For more information, see [Work with resource discoveries](https://docs.aws.amazon.com/vpc/latest/ipam/res-disc-ipam.html) in the *Amazon VPC IPAM User Guide*\.   |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  Can share with **any** AWS account\. | 
|  Prefix lists `ec2:PrefixList`  |  Create and manage prefix lists centrally, and share them with other AWS accounts or your organization\. This lets multiple AWS accounts reference prefix lists in their resources, such as VPC security groups and subnet route tables\. For more information, see [ Working with shared prefix lists](https://docs.aws.amazon.com/vpc/latest/userguide/sharing-managed-prefix-lists.html) in the *Amazon VPC User Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  Can share with **any** AWS account\. | 
|  Subnets `ec2:Subnet`  |  Create and manage subnets centrally, and share them with AWS accounts within your organization\. This lets multiple AWS accounts launch their application resources into centrally managed VPCs\. These resources include Amazon EC2 instances, Amazon Relational Database Service \(RDS\) databases, Amazon Redshift clusters, and AWS Lambda functions\. For more information, see [ Working with VPC sharing](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-sharing.html) in the *Amazon VPC User Guide*\.  To include a subnet when you create a resource share, you must have the `ec2:DescribeSubnets` and `ec2:DescribeVpcs` permissions, in addition to `ram:CreateResourceShare`\.   |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  Can share with **only** AWS accounts in its own organization\. | 
|  Traffic mirror targets `ec2:TrafficMirrorTarget`  |  Create and manage traffic mirror targets centrally, and share them with other AWS accounts or your organization\. This lets multiple AWS accounts send mirrored network traffic from traffic mirror sources in their accounts to a shared, centrally managed traffic mirror target\. For more information, see [ Cross\-account traffic mirroring targets](https://docs.aws.amazon.com/vpc/latest/mirroring/cross-account-traffic-mirroring-targets.html) in the *Traffic Mirroring Guide*\.  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  Can share with **any** AWS account\. | 
|  Transit gateways `ec2:TransitGateway`  |  Create and manage transit gateways centrally, and share them with other AWS accounts or your organization\. This lets multiple AWS accounts route traffic between their VPCs and on\-premises networks through a shared, centrally managed transit gateway\. For more information, see [Sharing a transit gateway](https://docs.aws.amazon.com/vpc/latest/tgw/tgw-transit-gateways.html#tgw-sharing) in the *Amazon VPC Transit Gateways*\.  To include a transit gateway when you create a resource share, you must have the `ec2:DescribeTransitGateway` permission in addition to `ram:CreateResourceShare`\.   |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  Can share with **any** AWS account\. | 
|  Transit gateway multicast domains `ec2:TransitGatewayMulticastDomain`  | Create and manage transit gateway multicast domains centrally, and share them with other AWS accounts or your organization\. This lets multiple AWS accounts register and deregister group members or group sources in the multicast domain\. For more information, see [Working with shared multicast domains](https://docs.aws.amazon.com/vpc/latest/tgw/tgw-transit-gateways.html#multicast-sharing.html) in the Transit Gateways Guide\. |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-no.png) No  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  Can share with **any** AWS account\. | 

## AWS Cloud WAN<a name="shareable-globalwan"></a>

You can share the following AWS Cloud WAN resources by using AWS RAM\.


| Resource type and code | Use case | Can share with IAM users and roles | Can share with accounts outside its organization | 
| --- | --- | --- | --- | 
|  Cloud WAN core network `networkmanager:CoreNetwork`  |  Create and manage a Cloud WAN core network centrally, and share it with other AWS accounts\. This lets multiple AWS accounts access and provision hosts on a single Cloud WAN core network\. For more information, see [Share a core network](https://docs.aws.amazon.com/vpc/latest/cloudwan/cloudwan-share-network.html) in the *AWS Cloud WAN User Guide*\.   |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  |  ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ram/latest/userguide/images/icon-yes.png) Yes  Can share with **any** AWS account\. | 