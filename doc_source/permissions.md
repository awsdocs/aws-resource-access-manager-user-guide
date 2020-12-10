# AWS RAM permissions<a name="permissions"></a>

AWS RAM permissions are policy fragments used by AWS RAM\. They control which actions principals are allowed to perform on resources that are shared with them\. AWS RAM permissions are used to generate the resource\-based policies that are attached to shared resources\.

AWS RAM includes default AWS\-managed permissions for each supported shareable resource type\. These managed permissions are created and managed by AWS, and they define the allowed actions for each shareable resource type\. For more information about the default AWS\-managed permissions, see [AWS\-managed permissions](#permissions-managed)\.

**Topics**
+ [How AWS RAM permissions work](#permissions-work)
+ [AWS\-managed permissions](#permissions-managed)

## How AWS RAM permissions work<a name="permissions-work"></a>

When you create a resource share, AWS RAM automatically attaches the default permission for each associated resource type to the resource share\. For example, if you create a resource share and associate a subnet and a Capacity Reservation, AWS RAM automatically attaches the subnet and Capacity Reservation permissions to the resource share\. 

After the resource share has been created, the permissions are provided to the respective resource\-owning services\. The resource\-owning service uses the provided permissions to create resource\-based policies for each of the resources included in the resource share\. The resulting resource\-based policies created by the resource\-owning service include the following elements:
+ `Resource`—The resource included in the resource share\.
+ `Effect`—The effect of the AWS RAM permission\. Always `allow`\.
+ `Principal`—The ARNs of the principals associated with the resource share\.
+ `Action`—The standard actions defined in the AWS RAM permission\.

The resource\-based policies are attached to the shared resources\. They allow the specified principals to perform the allowed actions on the resource\.

## AWS\-managed permissions<a name="permissions-managed"></a>

AWS RAM provides the following default AWS\-managed permissions:

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
+ [Amazon Route 53](#ram-perm-r53)
+ [Amazon VPC](#ram-perm-vpc)

### AWS App Mesh<a name="ram-perm-mesh"></a>

AWS RAM provides the following default AWS\-managed permissions for shareable AWS App Mesh resources\.


| Resource type | Permission name and ARN | Effect | Actions | 
| --- | --- | --- | --- | 
| appmesh:Mesh |  **Name:** AWSRAMDefaultPermissionAppMesh **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionAppMesh  | Allow |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 

### Amazon Aurora<a name="ram-perm-aur"></a>

AWS RAM provides the following default AWS\-managed permissions for shareable Amazon Aurora resources\.


| Resource type | Permission name and ARN | Effect | Actions | 
| --- | --- | --- | --- | 
| rds:Cluster |  **Name:** AWSRAMDefaultPermissionRDSCluster **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionRDSCluster  | Allow |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 

### AWS Certificate Manager Private Certificate Authority<a name="ram-perm-pca"></a>

AWS RAM provides the following default AWS\-managed permissions for shareable ACM Private CA resources\.


| Resource type | Permission name and ARN | Effect | Actions | 
| --- | --- | --- | --- | 
| acm\-pca:CertificateAuthority |  **Name:** AWSRAMDefaultPermissionCertificateAuthority **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionCertificateAuthority  | Allow |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 

### AWS CodeBuild<a name="ram-perm-code"></a>

AWS RAM provides the following default AWS\-managed permissions for shareable AWS CodeBuild resources\.


| Resource type | Permission name and ARN | Effect | Actions | 
| --- | --- | --- | --- | 
| codebuild:Project |  **Name:** AWSRAMDefaultPermissionCodeBuildProject **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionCodeBuildProject  | Allow |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 
| codebuild:ReportGroup |  **Name:** AWSRAMDefaultPermissionCodeBuildReportGroup **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionCodeBuildReportGroup  | Allow |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 

### Amazon EC2<a name="ram-perm-ec2"></a>

AWS RAM provides the following default AWS\-managed permissions for shareable Amazon EC2 resources\.


| Resource type | Permission name and ARN | Effect | Actions | 
| --- | --- | --- | --- | 
| ec2:CapacityReservation |  **Name:** AWSRAMDefaultPermissionCapacityReservation **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionCapacityReservation  | Allow |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 
| ec2:DedicatedHost |  **Name:** AWSRAMDefaultPermissionDedicatedHost **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionDedicatedHost  | Allow |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 

### Amazon EC2 Image Builder<a name="ram-perm-image"></a>

AWS RAM provides the following default AWS\-managed permissions for shareable Amazon EC2 Image Builder resources\.


| Resource type | Permission name and ARN | Effect | Actions | 
| --- | --- | --- | --- | 
| imagebuilder:Component | **Name:** AWSRAMDefaultPermissionImageBuilderComponent **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionImageBuilderComponent | Allow |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 
| imagebuilder:Image |  **Name:** AWSRAMDefaultPermissionImageBuilderImage **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionImageBuilderImage  | Allow |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 
| imagebuilder:ImageRecipe |  **Name:** AWSRAMDefaultPermissionImageBuilderImageRecipe **ARN:** arn:aws:ram::aws:permission/imagebuilder:AWSRAMDefaultPermissionImageBuilderImageRecipe  | Allow |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 

### AWS Glue<a name="ram-perm-glue"></a>

AWS RAM provides the following default AWS\-managed permissions for shareable AWS Glue resources\.


| Resource type | Permission name and ARN | Effect | Actions | 
| --- | --- | --- | --- | 
| glue:Catalog | **Name:** AWSRAMDefaultPermissionGlueCatalog **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionGlueCatalog | Allow |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 
| glue:Database | **Name:** AWSRAMDefaultPermissionGlueDatabase **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionGlueDatabase | Allow |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 
| glue:Table | **Name:** AWSRAMDefaultPermissionGlueTable **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionGlueTable | Allow |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 

### AWS License Manager<a name="ram-perm-lic"></a>

AWS RAM provides the following default AWS\-managed permissions for shareable AWS License Manager resources\.


| Resource type | Permission name and ARN | Effect | Actions | 
| --- | --- | --- | --- | 
| license\-manager:LicenseConfiguration |  **Name:** AWSRAMDefaultPermissionLicenseConfiguration **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionLicenseConfiguration  | Allow |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 

### AWS Network Firewall<a name="ram-perm-network-firewall"></a>

AWS RAM provides the following default AWS\-managed permissions for shareable AWS Network Firewall resources\.


| Resource type | Permission name and ARN | Effect | Actions | 
| --- | --- | --- | --- | 
| network\-firewall:FirewallPolicy |  **Name:** AWSRAMDefaultPermissionNetworkFirewallPolicy **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionNetworkFirewallPolicy  | Allow |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 
| network\-firewall:StatefulRuleGroup |  **Name:** AWSRAMDefaultPermissionNetworkFirewallStatefulRuleGroup **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionNetworkFirewallStatefulRuleGroup  | Allow |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 
| network\-firewall:StatelessRuleGroup |  **Name:** AWSRAMDefaultPermissionNetworkFirewallStatelessRuleGroup **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionNetworkFirewallStatelessRuleGroup  | Allow |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 

### AWS Outposts<a name="ram-perm-out"></a>

AWS RAM provides the following default AWS\-managed permissions for shareable AWS Outposts resources\.

**Note**  
For the default AWS\-managed permissions for shared subnets and local gateway route tables on Outposts, see [Subnets](#subnet) and [local gateway route tables](#lgw)\.


| Resource type | Permission name and ARN | Effect | Actions | 
| --- | --- | --- | --- | 
| outposts:Outpost |  **Name:** AWSRAMDefaultPermissionOutpostsOutpost **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionOutpostsOutpost  | Allow |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 

### AWS Resource Groups<a name="ram-perm-rgs"></a>

AWS RAM provides the following default AWS\-managed permissions for shareable AWS Resource Groups resources\.


| Resource type | Permission name and ARN | Effect | Actions | 
| --- | --- | --- | --- | 
| resource\-groups:Group |  **Name:** AWSRAMDefaultPermissionResourceGroup **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionResourceGroup  | Allow |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 

### Amazon Route 53<a name="ram-perm-r53"></a>

AWS RAM provides the following default AWS\-managed permissions for shareable Amazon Route 53 resources\.


| Resource type | Permission name and ARN | Effect | Actions | 
| --- | --- | --- | --- | 
| route53resolver:ResolverRule |  **Name:** AWSRAMDefaultPermissionResolverRule **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionResolverRule  | Allow |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 
| route53resolver:ResolverQueryLogConfig |  **Name:** AWSRAMDefaultPermissionResolverQueryLogConfig **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionResolverQueryLogConfig  | Allow |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 

### Amazon VPC<a name="ram-perm-vpc"></a>

AWS RAM provides the following default AWS\-managed permissions for shareable Amazon VPC resources\.


| Resource type | Permission name and ARN | Effect | Actions | 
| --- | --- | --- | --- | 
| ec2:PrefixList |  **Name:** AWSRAMDefaultPermissionPrefixList **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionPrefixList  |  Allow  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 
| <a name="subnet"></a>ec2:Subnet |  **Name:** AWSRAMDefaultPermissionSubnet **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionSubnet  | Allow |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 
| ec2:TrafficMirrorTarget |  **Name:** AWSRAMDefaultPermissionTrafficMirror **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionTrafficMirror  | Allow |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 
| ec2:TransitGateway |  **Name:** AWSRAMDefaultPermissionTransitGateway **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionTransitGateway  | Allow |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 
| <a name="lgw"></a>ec2:LocalGatewayRouteTable |  **Name:** AWSRAMDefaultPermissionLocalGateway **ARN:** arn:aws:ram::aws:permission/AWSRAMDefaultPermissionLocalGateway  | Allow |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html) [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html) [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html) [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html) [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html) [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html) [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html) [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html) [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 