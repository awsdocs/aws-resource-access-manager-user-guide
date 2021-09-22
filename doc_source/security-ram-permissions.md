# AWS RAM managed permissions<a name="security-ram-permissions"></a>

For each shareable resource type, there is at least one AWS RAM managed permission that defines the actions that principals with access to the resources in a resource share are allowed to perform on those resources\. Some resource types have only one AWS RAM managed permission and it is used automatically by default, with no action required by you\. Some resource types define more than one, and you can choose which one to use in a resource share\.

**Topics**
+ [How AWS RAM managed permissions work](#permissions-work)
+ [Types of AWS RAM managed permissions](#permissions-types)
+ [AWS RAM managed permissions reference for default permissions](#permissions-managed)

## How AWS RAM managed permissions work<a name="permissions-work"></a>

AWS RAM managed permissions are similar to [IAM resource\-based policies\.](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies.html#policies_resource-based) When you create a resource share, you associate a AWS RAM managed permission with each resource type that you want to share\.

After you create the resource share, AWS RAM provides the managed permission that you associate with each resource type to the respective resource\-owning service, such as AWS Certificate Manager Private Certificate Authority\. The permissions are then attached to each of the resources in the resource share\.

AWS RAM managed permissions specify the following:

**[Effect](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_effect.html)**  
Indicates whether to `Allow` or `Deny` the principal permission to perform an operation on a shared resource\. For an AWS RAM managed permission, the effect is always `Allow`\.

**[Principal](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_principal.html)**  
The ID number of an AWS account, or the [Amazon Resource Name \(ARN\)](https://docs.aws.amazon.com/general/latest/gr/aws-arns-and-namespaces.html) of an organization or organizational unit \(OU\) in AWS Organizations, or the ARN of an IAM role or user to whom you want to grant access the shared resource\.  
Not all resource types can be shared with IAM roles and users\. For information about resources that you can share with these principals, see [Shareable AWS resources](shareable.md)\.

**[Action](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_action.html)**  
The operation that the principal is granted permission to perform\. This can be an action in the AWS Management Console or an operation in the AWS CLI or AWS API\. The actions are defined by the AWS RAM permission\.

## Types of AWS RAM managed permissions<a name="permissions-types"></a>

When you create a resource share, you choose the AWS RAM permission to associate with each resource type that you include in the resource share\. Managed permissions are defined by the resource\-owning service and managed by AWS RAM\.
+ **Default managed permission** – There is one default manged permission available for each resource type that AWS RAM supports\. The default managed permission allows principals to perform specific actions that are defined by the service for the resource type\. For example, for the Amazon VPC `ec2:Subnet` resource type, the default managed permission allows principals to perform the following actions:
  + `ec2:RunInstances`
  + `ec2:CreateNetworkInterface`
  + `ec2:DescribeSubnets`

  The names of default managed permissions use the following format: `AWSRAMDefaultPermissionShareableResourceType`\. For example, for the `ec2:Subnet` resource type, the name of the default AWS RAM managed permission is `AWSRAMDefaultPermissionSubnet`\.
+ **Additional managed permissions** – Some resource types support additional choices for the permission you can attach to a resource type in a resource share\. Examples include read\-only access or full access \(`Read` and `Write` access\)\. These additional managed permissions provide you with more flexibility to choose the permissions to grant to specific principals for supported resource types\. For example, when you share a resource type that supports both a full access \(`Read` and `Write`\) managed permission and a read\-only managed permission, you can share the resources with the full access managed permission granted to an administrator\. You can then share the resources with other team members using the read\-only managed permission to follow the [security best practice of granting least privilege](https://wikipedia.org/wiki/Principle_of_least_privilege)\.
**Note**  
Currently, only some AWS services that work with AWS RAM support additional managed permissions beyond the default\. You can view the available permissions for each AWS service on the [https://console.aws.amazon.com/ram/home#Permissions:](https://console.aws.amazon.com/ram/home#Permissions:) page\. This page provides details about each available managed permission, including any resource shares that are currently associated with the permission and whether sharing with external principals is allowed, if applicable\. For more information, see [Viewing AWS RAM managed permissions](working-with-sharing-view-permissions.md)\.   
For services that don’t support additional managed permissions, when you create a resource share, AWS RAM automatically applies the default permission defined for the resource type that you choose\.

## AWS RAM managed permissions reference for default permissions<a name="permissions-managed"></a>

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
+ [Amazon S3 on Outposts](#ram-perm-s3outposts)
+ [AWS Resource Groups](#ram-perm-rgs)
+ [Amazon Route 53](#ram-perm-r53)
+ [AWS Systems Manager Incident Manager](#ram-perm-incidentmgr)
+ [Amazon VPC](#ram-perm-vpc)

### AWS App Mesh<a name="ram-perm-mesh"></a>

Following are the default AWS RAM managed permissions for shareable AWS App Mesh resources\.


| Resource type | Permission name and ARN | Allowed actions | 
| --- | --- | --- | 
| appmesh:Mesh |  ** AWSRAMDefaultPermissionAppMesh** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionAppMesh  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/security-ram-permissions.html)  | 

### Amazon Aurora<a name="ram-perm-aur"></a>

Following are the default AWS RAM managed permissions for shareable Amazon Aurora resources\.


| Resource type | Permission name and ARN | Allowed actions | 
| --- | --- | --- | 
| rds:Cluster |  ** AWSRAMDefaultPermissionRDSCluster** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionRDSCluster  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/security-ram-permissions.html)  | 

### AWS Certificate Manager Private Certificate Authority<a name="ram-perm-pca"></a>

Following are the default AWS RAM managed permissions for shareable ACM Private CA resources\.


| Resource type | Permission name and ARN | Allowed actions | 
| --- | --- | --- | 
| acm\-pca:CertificateAuthority |  ** AWSRAMDefaultPermissionCertificateAuthority**  arn:aws:ram::aws:permission/AWSRAMDefaultPermissionCertificateAuthority  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/security-ram-permissions.html)  | 

### AWS CodeBuild<a name="ram-perm-code"></a>

Following are the default AWS RAM managed permissions for shareable AWS CodeBuild resources\.


| Resource type | Permission name and ARN | Allowed actions | 
| --- | --- | --- | 
| codebuild:Project |  ** AWSRAMDefaultPermissionCodeBuildProject**  arn:aws:ram::aws:permission/AWSRAMDefaultPermissionCodeBuildProject  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/security-ram-permissions.html)  | 
| codebuild:ReportGroup |  ** AWSRAMDefaultPermissionCodeBuildReportGroup**  arn:aws:ram::aws:permission/AWSRAMDefaultPermissionCodeBuildReportGroup  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/security-ram-permissions.html)  | 

### Amazon EC2<a name="ram-perm-ec2"></a>

Following are the default AWS RAM managed permissions for shareable Amazon EC2 resources\.


| Resource type | Permission name and ARN | Allowed actions | 
| --- | --- | --- | 
| ec2:CapacityReservation |  ** AWSRAMDefaultPermissionCapacityReservation**  arn:aws:ram::aws:permission/AWSRAMDefaultPermissionCapacityReservation  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/security-ram-permissions.html)  | 
| ec2:DedicatedHost |  ** AWSRAMDefaultPermissionDedicatedHost**  arn:aws:ram::aws:permission/AWSRAMDefaultPermissionDedicatedHost  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/security-ram-permissions.html)  | 

### Amazon EC2 Image Builder<a name="ram-perm-image"></a>

Following are the default AWS RAM managed permissions for shareable Amazon EC2 Image Builder resources\.


| Resource type | Permission name and ARN | Allowed actions | 
| --- | --- | --- | 
| imagebuilder:Component |  ** AWSRAMDefaultPermissionImageBuilderComponent**  arn:aws:ram::aws:permission/AWSRAMDefaultPermissionImageBuilderComponent  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/security-ram-permissions.html)  | 
| imagebuilder:Image |  ** AWSRAMDefaultPermissionImageBuilderImage**  arn:aws:ram::aws:permission/AWSRAMDefaultPermissionImageBuilderImage  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/security-ram-permissions.html)  | 
| imagebuilder:ImageRecipe |  ** AWSRAMDefaultPermissionImageBuilderImageRecipe**  arn:aws:ram::aws:permission/imagebuilder:AWSRAMDefaultPermissionImageBuilderImageRecipe  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/security-ram-permissions.html)  | 
| imagebuilder:ContainerRecipe |  ** AWSRAMDefaultPermissionImageBuilderContainerRecipe**  arn:aws:ram::aws:permission/imagebuilder:AWSRAMDefaultPermissionImageBuilderContainerRecipe  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/security-ram-permissions.html)  | 

### AWS Glue<a name="ram-perm-glue"></a>

Following are the default AWS RAM managed permissions for shareable AWS Glue resources\.


| Resource type | Permission name and ARN | Allowed actions | 
| --- | --- | --- | 
| glue:Catalog |  ** AWSRAMDefaultPermissionGlueCatalog**  arn:aws:ram::aws:permission/AWSRAMDefaultPermissionGlueCatalog  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/security-ram-permissions.html)  | 
| glue:Database |  ** AWSRAMDefaultPermissionGlueDatabase**  arn:aws:ram::aws:permission/AWSRAMDefaultPermissionGlueDatabase  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/security-ram-permissions.html)  | 
| glue:Table |  ** AWSRAMDefaultPermissionGlueTable**  arn:aws:ram::aws:permission/AWSRAMDefaultPermissionGlueTable  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/security-ram-permissions.html)  | 

### AWS License Manager<a name="ram-perm-lic"></a>

Following are the default AWS RAM managed permissions for shareable AWS License Manager resources\.


| Resource type | Permission name and ARN | Allowed actions | 
| --- | --- | --- | 
| license\-manager:LicenseConfiguration |  ** AWSRAMDefaultPermissionLicenseConfiguration**  arn:aws:ram::aws:permission/AWSRAMDefaultPermissionLicenseConfiguration  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/security-ram-permissions.html)  | 

### AWS Network Firewall<a name="ram-perm-network-firewall"></a>

Following are the default AWS RAM managed permissions for shareable AWS Network Firewall resources\.


| Resource type | Permission name and ARN | Allowed actions | 
| --- | --- | --- | 
| network\-firewall:FirewallPolicy |  ** AWSRAMDefaultPermissionNetworkFirewallPolicy**  arn:aws:ram::aws:permission/AWSRAMDefaultPermissionNetworkFirewallPolicy  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/security-ram-permissions.html)  | 
| network\-firewall:StatefulRuleGroup |  ** AWSRAMDefaultPermissionNetworkFirewallStatefulRuleGroup**  arn:aws:ram::aws:permission/AWSRAMDefaultPermissionNetworkFirewallStatefulRuleGroup  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/security-ram-permissions.html)  | 
| network\-firewall:StatelessRuleGroup |  ** AWSRAMDefaultPermissionNetworkFirewallStatelessRuleGroup**  arn:aws:ram::aws:permission/AWSRAMDefaultPermissionNetworkFirewallStatelessRuleGroup  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/security-ram-permissions.html)  | 

### AWS Outposts<a name="ram-perm-out"></a>

Following are the default AWS RAM managed permissions for shareable AWS Outposts resources\.

**Note**  
For the default AWS RAM managed permissions for shared subnets and local gateway route tables on Outposts, see the `ec2:Subnet` and `ec2:LocalGatewayRouteTable` resource types in [Amazon VPC](#ram-perm-vpc)\.  
For the default AWS RAM managed permissions for Amazon S3 on Outposts, see the `s3-outposts:Outpost` resource type in [Amazon S3 on Outposts](#ram-perm-s3outposts)\.


| Resource type | Permission name and ARN | Allowed actions | 
| --- | --- | --- | 
| outposts:Outpost |  ** AWSRAMDefaultPermissionOutpostsOutpost**  arn:aws:ram::aws:permission/AWSRAMDefaultPermissionOutpostsOutpost  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/security-ram-permissions.html)  | 

### Amazon S3 on Outposts<a name="ram-perm-s3outposts"></a>

Following is the default AWS RAM managed permission for the `s3-outposts:Outpost` resource type\.


| Resource type | Permission name and ARN | Allowed actions | 
| --- | --- | --- | 
| s3\-outposts:Outpost |  ** AWSRAMDefaultPermissionS3Outposts**  arn:aws:ram::aws:permission/AWSRAMDefaultPermissionS3Outposts  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/security-ram-permissions.html)  | 

### AWS Resource Groups<a name="ram-perm-rgs"></a>

Following are the default AWS RAM managed permissions for shareable AWS Resource Groups resources\.


| Resource type | Permission name and ARN | Allowed actions | 
| --- | --- | --- | 
| resource\-groups:Group |  ** AWSRAMDefaultPermissionResourceGroup**  arn:aws:ram::aws:permission/AWSRAMDefaultPermissionResourceGroup  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/security-ram-permissions.html)  | 

### Amazon Route 53<a name="ram-perm-r53"></a>

Following are the default AWS RAM managed permissions for shareable Amazon Route 53 resources\.


| Resource type | Permission name and ARN | Allowed actions | 
| --- | --- | --- | 
| route53resolver:FirewallRuleGroup |  ** AWSRAMDefaultPermissionResolverFirewallRuleGroup**  arn:aws:ram::aws:permission/AWSRAMDefaultPermissionResolverFirewallRuleGroup  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/security-ram-permissions.html)  | 
| route53resolver:ResolverRule |  ** AWSRAMDefaultPermissionResolverRule**  arn:aws:ram::aws:permission/AWSRAMDefaultPermissionResolverRule  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/security-ram-permissions.html)  | 
| route53resolver:ResolverQueryLogConfig |  ** AWSRAMDefaultPermissionResolverQueryLogConfig**  arn:aws:ram::aws:permission/AWSRAMDefaultPermissionResolverQueryLogConfig  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/security-ram-permissions.html)  | 

### AWS Systems Manager Incident Manager<a name="ram-perm-incidentmgr"></a>

Following are the default AWS RAM managed permissions for shareable AWS Systems Manager Incident Manager resources\.


| Resource type | Permission name and ARN | Allowed actions | 
| --- | --- | --- | 
| ssm\-contacts:Contact |  ** AWSRAMDefaultPermissionSSMContactsContact**  arn:aws:ram::aws:permission/AWSRAMDefaultPermissionSSMContactsContact  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/security-ram-permissions.html)  | 
| ssm\-incidents:ResponsePlan |  ** AWSRAMDefaultPermissionSSMIncidentsResponsePlan**  arn:aws:ram::aws:permission/AWSRAMDefaultPermissionSSMIncidentsResponsePlan  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/security-ram-permissions.html)  | 

### Amazon VPC<a name="ram-perm-vpc"></a>

Following are the default AWS RAM managed permissions for shareable Amazon VPC resources\.


| Resource type | Permission name and ARN | Allowed actions | 
| --- | --- | --- | 
| ec2:PrefixList |  ** AWSRAMDefaultPermissionPrefixList**  arn:aws:ram::aws:permission/AWSRAMDefaultPermissionPrefixList  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/security-ram-permissions.html)  | 
| <a name="subnet"></a>ec2:Subnet |  ** AWSRAMDefaultPermissionSubnet**  arn:aws:ram::aws:permission/AWSRAMDefaultPermissionSubnet  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/security-ram-permissions.html)  | 
| ec2:TrafficMirrorTarget |  ** AWSRAMDefaultPermissionTrafficMirror**  arn:aws:ram::aws:permission/AWSRAMDefaultPermissionTrafficMirror  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/security-ram-permissions.html)  | 
| ec2:TransitGateway |  ** AWSRAMDefaultPermissionTransitGateway**  arn:aws:ram::aws:permission/AWSRAMDefaultPermissionTransitGateway  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/security-ram-permissions.html)  | 
| <a name="lgw"></a>ec2:LocalGatewayRouteTable |  ** AWSRAMDefaultPermissionLocalGateway**  arn:aws:ram::aws:permission/AWSRAMDefaultPermissionLocalGateway  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/security-ram-permissions.html) [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/security-ram-permissions.html) [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/security-ram-permissions.html) [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/security-ram-permissions.html) [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/security-ram-permissions.html) [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/security-ram-permissions.html) [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/security-ram-permissions.html) [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/security-ram-permissions.html) [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/security-ram-permissions.html)  | 