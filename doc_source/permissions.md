# AWS RAM managed permissions<a name="permissions"></a>

AWS RAM managed permissions define the actions that are allowed for each shareable resource type in a resource share\. For each shareable resource type, managed permissions define the actions that principals who have access to the shared resources are allowed to perform on those resources\.

**Topics**
+ [How AWS RAM managed permissions work](#permissions-work)
+ [Sharing with IAM roles and IAM users](#permissions-rbp-supported-resource-types)
+ [Types of AWS RAM managed permissions](#permissions-types)
+ [AWS RAM managed permissions reference](#permissions-managed)

## How AWS RAM managed permissions work<a name="permissions-work"></a>

When you create a resource share, you can associate a managed permission with each resource type that you want to share\. After you create the resource share, AWS RAM provides the permission that you associate with each resource type to the respective resource\-owning service, such as AWS Certificate Manager Private Certificate Authority\. The permissions are then attached to each of the resources in the resource share\.

AWS RAM managed permissions specify the following:

**Effect**  
Indicates whether to allow or deny a principal permission to perform an action or operation on a shared resource\. For an AWS RAM managed permission, the effect is always `Allow`\.

**Principal**  
The organization or organizational unit \(OU\) in AWS Organizations, an AWS account, IAM role, or IAM user that can access the shared resource\.  
Not all resource types can be shared with IAM roles and IAM users\. For information about resources that you can share with these principals, see the next section\.

**Action**  
The action or operation that the principal is granted permission to perform\. This can be an action in the AWS Management Console or an operation in the AWS CLI or AWS API\. The actions are defined in the AWS RAM permission\.

## Sharing with IAM roles and IAM users<a name="permissions-rbp-supported-resource-types"></a>

AWS RAM lets you share your resources with an organization or organizational units \(OUs\) in AWS Organizations, and AWS accounts\. For supported resource types, you can also share resources with IAM roles and IAM users\. For each shareable resource type, the following table indicates whether you can share resources of that type with IAM roles and IAM users\.


| Service | Resource type | Can be shared with IAM roles and IAM users | 
| --- | --- | --- | 
|  AWS App Mesh  |  appmesh:Mesh  |  Yes  | 
|  Amazon Aurora  |  rds:Cluster  |  No  | 
|  AWS Certificate Manager Private Certificate Authority  |  acm\-pca:CertificateAuthority  |  Yes  | 
|  AWS CodeBuild  |  codebuild:Project codebuild:ReportGroup  |  Yes  | 
|  Amazon EC2  |  ec2:CapacityReservation ec2:DedicatedHost  |  No  | 
|  Amazon EC2 Image Builder  |  imagebuilder:Component imagebuilder:ContainerRecipe imagebuilder:Image imagebuilder:ImageRecipe  |  Yes  | 
|  AWS Glue  |  glue:Catalog glue:Database glue:Table  |  No  | 
|  AWS License Manager  |  license\-manager:LicenseConfiguration  |  No  | 
|  AWS Network Firewall  |  network\-firewall:FirewallPolicy network\-firewall:StatefulRuleGroup network\-firewall:StatelessRuleGroup  |  Yes  | 
|  AWS Outposts  |  outposts:Outpost  |  No  | 
|  AWS Resource Groups  |  resource\-groups:Group  |  No  | 
|  Amazon Route 53   |  route53resolver:FirewallRuleGroup route53resolver:ResolverQueryLogConfig  |  Yes  | 
|  Amazon Route 53   |  route53resolver:ResolverRule  |  No  | 
|  AWS Systems Manager Incident Manager  |  ssm\-contacts:Contact ssm\-incidents:ResponsePlan  |  Yes  | 
|  Amazon VPC  |  ec2:PrefixList ec2:Subnet ec2:TrafficMirrorTarget ec2:TransitGateway ec2:LocalGatewayRouteTable  |  No  | 

## Types of AWS RAM managed permissions<a name="permissions-types"></a>

When you create a resource share, you choose a permission to associate with each resource type that you want to share\. Managed permissions are defined by the resource\-owning service but are managed by AWS RAM\.
+ **Default managed permissions** – These permissions are available for every resource type that AWS RAM supports\. For each resource type, the default AWS RAM managed permission allows principals to perform specific actions that are defined by the service for the resource type\. For example, for the Amazon VPC `ec2:Subnet` resource type, the default managed permission allows principals to perform the following actions:
  + `ec2:RunInstances`
  + `ec2:CreateNetworkInterface`
  + `ec2:DescribeSubnets`

  The names of default managed permissions use the following format: `AWSRAMDefaultPermissionShareableResource`\. For example, for the `ec2:Subnet` resource type, the name of the default AWS RAM managed permission is `AWSRAMDefaultPermissionSubnet`\.
+ **Additional managed permissions** – Examples include read\-only access or full access \(`Read` and `Write` access\)\. These permissions provide you with more flexibility to choose which permissions to grant to specific principals for supported resource types\. For example, when you share a resource type that supports full access \(`Read` and `Write` permissions\) and read\-only managed permissions, you can share the resources with the full access managed permission with an administrator\. You can then share the resources with other team members with the read\-only managed permission to follow the security best practice of granting least privilege\. Least privilege means the minimum permissions required for access to shared resources\.
**Note**  
Currently, only some AWS services that work with AWS RAM support these permissions\. For services that don’t support additional managed permissions, when you create a resource share, AWS RAM automatically applies the default permission defined for the resource type that you choose\.

## AWS RAM managed permissions reference<a name="permissions-managed"></a>

For services that work with AWS RAM, the following sections list the default managed permissions for shareable resources\.

**Topics**
+ [AWS App Mesh](#ram-perm-mesh)
+ [Amazon Aurora](#ram-perm-aur)
+ [AWS Certificate Manager Private Certificate Authority](#ram-perm-pca)
+ [AWS CodeBuild](#ram-perm-code)
+ [Amazon EC2](#ram-perm-ec2)
+ [Amazon EC2 Image Builder](#ram-perm-image)
+ [AWS Glue](#ram-perm-glue)
+ [AWS License Manager](#ram-perm-lic)
+ [AWS Network Firewall](#ram-perm-network-firewall)
+ [AWS Outposts](#ram-perm-out)
+ [AWS Resource Groups](#ram-perm-rgs)
+ [Amazon Route 53](#ram-perm-r53)
+ [AWS Systems Manager Incident Manager](#ram-perm-incidentmgr)
+ [Amazon VPC](#ram-perm-vpc)

### AWS App Mesh<a name="ram-perm-mesh"></a>

Following are the default AWS RAM managed permissions for shareable AWS App Mesh resources\.


| Resource type | Permission name and ARN | Allowed actions | 
| --- | --- | --- | 
| appmesh:Mesh |  **Name:** AWSRAMDefaultPermissionAppMesh **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionAppMesh  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 

### Amazon Aurora<a name="ram-perm-aur"></a>

Following are the default AWS RAM managed permissions for shareable Amazon Aurora resources\.


| Resource type | Permission name and ARN | Allowed actions | 
| --- | --- | --- | 
| rds:Cluster |  **Name:** AWSRAMDefaultPermissionRDSCluster **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionRDSCluster  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 

### AWS Certificate Manager Private Certificate Authority<a name="ram-perm-pca"></a>

Following are the default AWS RAM managed permissions for shareable ACM Private CA resources\.


| Resource type | Permission name and ARN | Allowed actions | 
| --- | --- | --- | 
| acm\-pca:CertificateAuthority |  **Name:** AWSRAMDefaultPermissionCertificateAuthority **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionCertificateAuthority  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 

### AWS CodeBuild<a name="ram-perm-code"></a>

Following are the default AWS RAM managed permissions for shareable AWS CodeBuild resources\.


| Resource type | Permission name and ARN | Allowed actions | 
| --- | --- | --- | 
| codebuild:Project |  **Name:** AWSRAMDefaultPermissionCodeBuildProject **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionCodeBuildProject  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 
| codebuild:ReportGroup |  **Name:** AWSRAMDefaultPermissionCodeBuildReportGroup **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionCodeBuildReportGroup  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 

### Amazon EC2<a name="ram-perm-ec2"></a>

Following are the default AWS RAM managed permissions for shareable Amazon EC2 resources\.


| Resource type | Permission name and ARN | Allowed actions | 
| --- | --- | --- | 
| ec2:CapacityReservation |  **Name:** AWSRAMDefaultPermissionCapacityReservation **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionCapacityReservation  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 
| ec2:DedicatedHost |  **Name:** AWSRAMDefaultPermissionDedicatedHost **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionDedicatedHost  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 

### Amazon EC2 Image Builder<a name="ram-perm-image"></a>

Following are the default AWS RAM managed permissions for shareable Amazon EC2 Image Builder resources\.


| Resource type | Permission name and ARN | Allowed actions | 
| --- | --- | --- | 
| imagebuilder:Component | **Name:** AWSRAMDefaultPermissionImageBuilderComponent **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionImageBuilderComponent |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 
| imagebuilder:Image |  **Name:** AWSRAMDefaultPermissionImageBuilderImage **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionImageBuilderImage  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 
| imagebuilder:ImageRecipe |  **Name:** AWSRAMDefaultPermissionImageBuilderImageRecipe **ARN:** arn:aws:ram::aws:permission/imagebuilder:AWSRAMDefaultPermissionImageBuilderImageRecipe  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 
| imagebuilder:ContainerRecipe |  **Name:** AWSRAMDefaultPermissionImageBuilderContainerRecipe **ARN:** arn:aws:ram::aws:permission/imagebuilder:AWSRAMDefaultPermissionImageBuilderContainerRecipe  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 

### AWS Glue<a name="ram-perm-glue"></a>

Following are the default AWS RAM managed permissions for shareable AWS Glue resources\.


| Resource type | Permission name and ARN | Allowed actions | 
| --- | --- | --- | 
| glue:Catalog | **Name:** AWSRAMDefaultPermissionGlueCatalog **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionGlueCatalog |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 
| glue:Database | **Name:** AWSRAMDefaultPermissionGlueDatabase **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionGlueDatabase |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 
| glue:Table | **Name:** AWSRAMDefaultPermissionGlueTable **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionGlueTable |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 

### AWS License Manager<a name="ram-perm-lic"></a>

Following are the default AWS RAM managed permissions for shareable AWS License Manager resources\.


| Resource type | Permission name and ARN | Allowed actions | 
| --- | --- | --- | 
| license\-manager:LicenseConfiguration |  **Name:** AWSRAMDefaultPermissionLicenseConfiguration **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionLicenseConfiguration  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 

### AWS Network Firewall<a name="ram-perm-network-firewall"></a>

Following are the default AWS RAM managed permissions for shareable AWS Network Firewall resources\.


| Resource type | Permission name and ARN | Allowed actions | 
| --- | --- | --- | 
| network\-firewall:FirewallPolicy |  **Name:** AWSRAMDefaultPermissionNetworkFirewallPolicy **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionNetworkFirewallPolicy  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 
| network\-firewall:StatefulRuleGroup |  **Name:** AWSRAMDefaultPermissionNetworkFirewallStatefulRuleGroup **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionNetworkFirewallStatefulRuleGroup  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 
| network\-firewall:StatelessRuleGroup |  **Name:** AWSRAMDefaultPermissionNetworkFirewallStatelessRuleGroup **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionNetworkFirewallStatelessRuleGroup  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 

### AWS Outposts<a name="ram-perm-out"></a>

Following are the default AWS RAM managed permissions for shareable AWS Outposts resources\.

**Note**  
For the default AWS RAM managed permissions for shared subnets and local gateway route tables on Outposts, see [Subnets](#subnet) and [local gateway route tables](#lgw)\.


| Resource type | Permission name and ARN | Allowed actions | 
| --- | --- | --- | 
| outposts:Outpost |  **Name:** AWSRAMDefaultPermissionOutpostsOutpost **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionOutpostsOutpost  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 

### AWS Resource Groups<a name="ram-perm-rgs"></a>

Following are the default AWS RAM managed permissions for shareable AWS Resource Groups resources\.


| Resource type | Permission name and ARN | Allowed actions | 
| --- | --- | --- | 
| resource\-groups:Group |  **Name:** AWSRAMDefaultPermissionResourceGroup **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionResourceGroup  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 

### Amazon Route 53<a name="ram-perm-r53"></a>

Following are the default AWS RAM managed permissions for shareable Amazon Route 53 resources\.


| Resource type | Permission name and ARN | Allowed actions | 
| --- | --- | --- | 
| route53resolver:FirewallRuleGroup |  **Name:** AWSRAMDefaultPermissionResolverFirewallRuleGroup **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionResolverFirewallRuleGroup  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 
| route53resolver:ResolverRule |  **Name:** AWSRAMDefaultPermissionResolverRule **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionResolverRule  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 
| route53resolver:ResolverQueryLogConfig |  **Name:** AWSRAMDefaultPermissionResolverQueryLogConfig **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionResolverQueryLogConfig  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 

### AWS Systems Manager Incident Manager<a name="ram-perm-incidentmgr"></a>

Following are the default AWS RAM managed permissions for shareable AWS Systems Manager Incident Manager resources\.


| Resource type | Permission name and ARN | Allowed actions | 
| --- | --- | --- | 
| ssm\-contacts:Contact |  **Name:** AWSRAMDefaultPermissionSSMContactsContact **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionSSMContactsContact  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 
| ssm\-incidents:ResponsePlan |  **Name:** AWSRAMDefaultPermissionSSMIncidentsResponsePlan **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionSSMIncidentsResponsePlan  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 

### Amazon VPC<a name="ram-perm-vpc"></a>

Following are the default AWS RAM managed permissions for shareable Amazon VPC resources\.


| Resource type | Permission name and ARN | Allowed actions | 
| --- | --- | --- | 
| ec2:PrefixList |  **Name:** AWSRAMDefaultPermissionPrefixList **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionPrefixList  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 
| <a name="subnet"></a>ec2:Subnet |  **Name:** AWSRAMDefaultPermissionSubnet **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionSubnet  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 
| ec2:TrafficMirrorTarget |  **Name:** AWSRAMDefaultPermissionTrafficMirror **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionTrafficMirror  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 
| ec2:TransitGateway |  **Name:** AWSRAMDefaultPermissionTransitGateway **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionTransitGateway  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 
| <a name="lgw"></a>ec2:LocalGatewayRouteTable |  **Name:** AWSRAMDefaultPermissionLocalGateway **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionLocalGateway  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html) [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html) [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html) [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html) [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html) [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html) [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html) [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html) [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 