# Authentication and Access Control<a name="control-access"></a>

You can use IAM policies to control access to certain AWS RAM features and resource sharing capabilities\. For more information about IAM policies, see [Permissions and Policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies.html) in the *IAM User Guide*\. For more information about managing and creating custom IAM policies, see [Managing IAM Policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_manage.html)\.

**Topics**
+ [IAM Policies for AWS RAM](iam-policies.md)
+ [Example IAM Policies](#iam-examples)
+ [AWS RAM Permissions](permissions.md)
+ [Disabling Sharing with AWS Organizations](disable-sharing.md)

## Example IAM Policies<a name="iam-examples"></a>

**Topics**
+ [Allow Sharing of Specific Resources](#owner-share-specific-resources)
+ [Allow Sharing of Specific Resource Types](#owner-share-resource-types)
+ [Restrict Sharing with External AWS Accounts](#control-access-owner-external)

### Example 1: Allow Sharing of Specific Resources<a name="owner-share-specific-resources"></a>

You can use an IAM policy to restrict principals to associating only specific resources with resource shares\.

For example, the following policy limits principals to sharing only the resolver rule with the specified Amazon Resource Name \(ARN\)\.

```
{
    "Version": "2012-10-17",
    "Statement": [{
        "Effect": "Allow",
        "Action": ["ram:CreateResourceShare", "ram:AssociateResourceShare"],
        "Resource": "*",
        "Condition": {
            "StringEquals": {
                "ram:ResourceArn": "arn:aws:route53resolver:us-west-2:123456789012:resolver-rule/rslvr-rr-5328a0899aexample"
            }
        }
    }]
}
```

### Example 2: Allow Sharing of Specific Resource Types<a name="owner-share-resource-types"></a>

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

### Example 3: Restrict Sharing with External AWS Accounts<a name="control-access-owner-external"></a>

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