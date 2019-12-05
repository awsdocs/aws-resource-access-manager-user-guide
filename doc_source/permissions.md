# AWS RAM Permissions<a name="permissions"></a>

AWS RAM permissions are policy fragments used by AWS RAM\. They control which actions that principals are allowed to perform on resources that are shared with them\. AWS RAM permissions are used to generate the resource\-based policies that are attached to shared resources\.

The permissions use a similar policy structure to that of IAM policies, and include the following elements: `effect`, `action`, and `condition`\.

AWS RAM includes default AWS\-managed permissions for each supported shareable resource type\. These managed permissions are created and managed by AWS, and they define the allowed actions for each resource type\. For more information about the default AWS\-managed permissions, see [AWS\-Managed Permissions](#permissions-managed)\.

**Topics**
+ [How AWS RAM Permissions Work](#permissions-work)
+ [AWS\-Managed Permissions](#permissions-managed)

## How AWS RAM Permissions Work<a name="permissions-work"></a>

When you create a resource share, AWS RAM automatically attaches the default permission for each associated resource type to the resource share\. For example, if you create a resource share and associate a subnet and a Capacity Reservation, AWS RAM automatically attaches the subnet and Capacity Reservation permissions to the resource share\. 

After the resource share has been created, the permissions are provided to the resource\-owning services\. The resource\-owning service uses the provided permissions to create resource\-based policies for each of the resources included in the resource share\. The resulting resource\-based policies created by the resource\-owning service include the following elements:
+ `Resource`—The resource included in the resource share\.
+ `Effect`—The effect of the AWS RAM permission\. Always `allow`\.
+ `Principal`—The ARNs of the principals associated with the resource share\.
+ `Action`—The standard actions defined in the AWS RAM permission\.

The resource\-based policies are attached to the shared resources\. They allow the specified prinicipals to perform the allowed actions on the resource\.

## AWS\-Managed Permissions<a name="permissions-managed"></a>

AWS RAM provides the following default AWS\-managed permissions:


| Permission name | ARN | Resource type | Effect | Actions | 
| --- | --- | --- | --- | --- | 
|  AWSRAMDefaultPermissionRDSCluster  |  arn:aws:ram::aws:permission/AWSRAMDefaultPermissionRDSCluster  |  rds:Cluster  |  Allow  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 
|  AWSRAMDefaultPermissionCapacityReservation  |  arn:aws:ram::aws:permission/AWSRAMDefaultPermissionCapacityReservation  |  ec2:CapacityReservation  |  Allow  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 
|  AWSRAMDefaultPermissionDedicatedHost  |  arn:aws:ram::aws:permission/AWSRAMDefaultPermissionDedicatedHost  |  ec2:DedicatedHost  |  Allow  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 
|  AWSRAMDefaultPermissionSubnet  |  arn:aws:ram::aws:permission/AWSRAMDefaultPermissionSubnet  |  ec2:Subnet  |  Allow  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 
|  AWSRAMDefaultPermissionTrafficMirror  |  arn:aws:ram::aws:permission/AWSRAMDefaultPermissionTrafficMirror  |  ec2:TrafficMirrorTarget  |  Allow  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 
|  AWSRAMDefaultPermissionTransitGateway  |  arn:aws:ram::aws:permission/AWSRAMDefaultPermissionTransitGateway  |  ec2:TransitGateway  |  Allow  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 
|  AWSRAMDefaultPermissionImageBuilderComponent  |  arn:aws:ram::aws:permission/AWSRAMDefaultPermissionImageBuilderComponent  |  imagebuilder:Component  |  Allow  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 
|  AWSRAMDefaultPermissionImageBuilderImage  |  arn:aws:ram::aws:permission/AWSRAMDefaultPermissionImageBuilderImage  |  imagebuilder:Image  |  Allow  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 
|  AWSRAMDefaultPermissionImageBuilderImageRecipe  |  arn:aws:ram::aws:permission/imagebuilder:AWSRAMDefaultPermissionImageBuilderImageRecipe  |  imagebuilder:ImageRecipe  |  Allow  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 
|  AWSRAMDefaultPermissionLicenseConfiguration  |  arn:aws:ram::aws:permission/AWSRAMDefaultPermissionLicenseConfiguration  |  license\-manager:LicenseConfiguration  |  Allow  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 
|  AWSRAMDefaultPermissionResourceGroup  |  arn:aws:ram::aws:permission/AWSRAMDefaultPermissionResourceGroup  |  resource\-groups:Group  |  Allow  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 
|  AWSRAMDefaultPermissionResolverRule  |  arn:aws:ram::aws:permission/AWSRAMDefaultPermissionResolverRule  |  route53resolver:ResolverRule  |  Allow  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/permissions.html)  | 