# Example IAM policies for AWS RAM<a name="iam-examples"></a>

**Topics**
+ [Allow sharing of specific resources](#owner-share-specific-resources)
+ [Allow sharing of specific resource types](#owner-share-resource-types)
+ [Restrict sharing with external AWS accounts](#control-access-owner-external)

## Example 1: Allow sharing of specific resources<a name="owner-share-specific-resources"></a>

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

## Example 2: Allow sharing of specific resource types<a name="owner-share-resource-types"></a>

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

## Example 3: Restrict sharing with external AWS accounts<a name="control-access-owner-external"></a>

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
                "ram:RequestedAllowsExternalPrincipals": "false"
            }
        }
    }]
}
```