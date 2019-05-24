# Authentication and Access Control<a name="control-access"></a>

You can use IAM policies to control access to certain AWS RAM features and resource sharing capabilities\. For more information about IAM policies, see [Permissions and Policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies.html) in the *IAM User Guide*\. For more information about managing and creating custom IAM policies, see [Managing IAM Policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_manage.html)\.

**Topics**
+ [IAM Policies for AWS RAM](#iam-policies)
+ [Example IAM Policies](#iam-examples)
+ [Disabling Sharing with AWS Organizations](disable-sharing.md)

## IAM Policies for AWS RAM<a name="iam-policies"></a>

By default, IAM users don't have permission to create or modify AWS RAM resources\. To allow IAM users to create or modify resources and perform tasks, you must create IAM policies that grant permission to use specific resources and API actions\. You then attach those policies to the IAM users or groups that require those permissions\.

An IAM policy is a JSON document that includes the following statements: Effect, Action, Resource, and Condition\. An IAM policy typically takes the following form:

```
			{
  "Statement":[{
    "Effect":"effect",
    "Action":"action",
    "Resource":"arn",
    "Condition":{
      "condition":{
        "key":"value"
        }
      }
    }
  ]
}
```

### Effect<a name="iam-policies-effect"></a>

The *Effect* statement indicates whether the policy allows or denies a user permission to perform an action\. The possible values include: `Allow` and `Deny`\.

### Action<a name="iam-policies-action"></a>

The *Action* statement specifies the AWS RAM API actions for which the policy is allowing or denying permission\. For a complete list of the allowed actions, see [ Actions Defined by AWS Resource Access Manager](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_awsresourceaccessmanager.html#awsresourceaccessmanager-actions-as-permissions) in the *IAM User Guide*\.

### Resource<a name="iam-policies-resource"></a>

The *Resource* statement specifies the AWS RAM resources that are affected by the policy\. To specify a resource in the statement, you need to use its unique Amazon Resource Name \(ARN\)\. For a complete list of the allowed resources, see [ Resources Defined by AWS Resource Access Manager](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_awsresourceaccessmanager.html#awsresourceaccessmanager-resources-for-iam-policies) in the *IAM User Guide*\.

### Condition<a name="iam-policies-condition"></a>

*Condition* statements are optional\. They can be used to further refine the conditions under which the policy applies\. AWS RAM supports the following condition keys:
+ `aws:RequestTag/${TagKey}` — Specifies a tag key and value pair that must be used when creating or tagging a resource share\. 
+ a`ws:ResourceTag/${TagKey}` — Indicates that the action can be performed only on resources that have the specified tag key and value pair\.
+ `aws:TagKeys` — Specifies the tag keys that can be used when creating or tagging a resource share\.
+ `ram:AllowsExternalPrincipals` — Indicates that the action can be performed only on resource shares that allow or deny sharing with external principals\. An external principal is an AWS account outside of your AWS organization
+ `ram:Principal` — Indicates that the action can be performed only on the specified principal\.
+ `ram:RequestedResourceType` — Indicates that the action can be performed only on the specified resource type\. Resource types must be specified in the following format: 
  + `route53resolver:ResolverRule`
  + `ec2:TransitGateway`
  + `ec2:Subnet`
  + `license-manager:LicenseConfiguration`
+ `ram:ResourceArn` — Indicates that the action can be performed only on a resource with the specified ARN\.
+ `ram:ResourceShareName` — Indicates that the action can be performed only on a resource share with the specified name\.
+ `ram:ShareOwnerAccountId` — Indicates that the action can be performed only on resource shares owned by a specific account\.

## Example IAM Policies<a name="iam-examples"></a>

### Allow Sharing of Specific Resource Types<a name="owner-share-resource-types"></a>

You can use an IAM policy to limit principals to associating only specific resource types with resource shares\.

For example, the following policy limits principals to sharing only resolver rules\.

```
{
	  "Version": "2012-10-17",
	  "Statement": [{
	     "Effect": "Allow",
	     "Action": ["ram:CreateResourceShare", "ram:AssociateResourceShare"],
	     "Resource": "*",
	     "Condition": {
	        "StringEquals": {
	           "ram:RequestedResourceType": "route53resolver:ResolverRule"
	        }
	     }
	  }]
	}
```

### Restrict Sharing with External AWS Accounts<a name="control-access-owner-external"></a>

You can use an IAM policy to prevent principals from sharing resources with AWS accounts that are outside of its AWS organization\.

For example, the following IAM policy prevents principals from adding external AWS accounts to resource shares\.

```
{
	  "Version": "2012-10-17",
	  "Statement": [{
	     "Effect": "Allow",
	     "Action": "ram:CreateResourceShare",
	     "Resource": "*",
	     "Condition": {
	        "Bool": {
	           "ram:AllowsExternalPrincipals": "false"
	        }
	     }
	  }]
	}
```