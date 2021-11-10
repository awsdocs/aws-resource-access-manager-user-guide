# Example service control policies for AWS Organizations and AWS RAM<a name="scp"></a>

AWS RAM supports service control policies \(SCPs\)\. SCPs are policies that you attach to elements in an organization to manage permissions within that organization\. An SCP applies to all AWS accounts [under the element to which you attach the SCP](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_inheritance_auth.html)\. SCPs offer central control over the maximum available permissions for all accounts in your organization\. They can help you to ensure your AWS accounts stay within your organization’s access control guidelines\. For more information, see [ Service control policies](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_type-auth.html) in the *AWS Organizations User Guide*\.

## Prerequisites<a name="scp-prereqs"></a>

To use SCPs, you must first do the following:
+ Enable all features in your organization\. For more information, see [Enabling all features in your organization](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_org_support-all-features.html) in the *AWS Organizations User Guide*
+ Enable SCPs for use within your organization\. For more information, see [Enabling and disabling policy types](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_enable-disable.html) in the *AWS Organizations User Guide*
+ Create the SCPs that you need\. For more information about creating SCPs, see [ Creating and updating SCPs](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_scp-create.html) in the *AWS Organizations User Guide*\.

## Example Service Control Policies<a name="scp-examples"></a>

**Contents**
+ [Example 1: Prevent external sharing](#example-one)
+ [Example 2: Allow specific accounts to share specific resource types](#example-two)
+ [Example 3: Prevent sharing with the entire organization or with organizational units](#example-three)
+ [Example 4: Allow sharing with only specific principals](#example-four)

The following examples show how you can control various aspects of resource sharing in an organization\.

### Example 1: Prevent external sharing<a name="example-one"></a>

The following SCP prevents users from creating resource shares that allow sharing with principals that are outside of the sharing user's organization\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Deny",
            "Action": [
                "ram:CreateResourceShare",
                "ram:UpdateResourceShare"
            ],
            "Resource": "*",
            "Condition": {
                "Bool": {
                    "ram:RequestedAllowsExternalPrincipals": "true"
                }
            }
        }
    ]
}
```

### Example 2: Allow specific accounts to share specific resource types<a name="example-two"></a>

The following SCP allows *only* accounts `111111111111` and `222222222222` to create new resource shares that share Amazon EC2 prefix lists or to associate prefix lists with existing resource shares\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Deny",
            "Action": [
                "ram:AssociateResourceShare",
                "ram:CreateResourceShare"
            ],
            "Resource": "*",
            "Condition": {
                "StringNotEquals": {
                    "aws:PrincipalAccount": [
                        "111111111111",
                        "222222222222"
                    ]
                },
                "StringEquals": {
                    "ram:RequestedResourceType": "ec2:PrefixList"
                }
            }
        }
    ]
}
```

### Example 3: Prevent sharing with the entire organization or with organizational units<a name="example-three"></a>

The following SCP prevents users from creating resource shares that share resources with an entire organization or with any organizational units\. Users *can* share with individual AWS accounts in the organization, or with IAM roles or users\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Deny",
            "Action": [
                "ram:CreateResourceShare",
                "ram:AssociateResourceShare"
            ],
            "Resource": "*",
            "Condition": {
                "ForAnyValue:StringLike": {
                    "ram:Principal": [
                        "arn:aws:organizations::*:organization/*",
                        "arn:aws:organizations::*:ou/*"
                    ]
                }
            }
        }
    ]
}
```

### Example 4: Allow sharing with only specific principals<a name="example-four"></a>

The following example SCP allows users to share resources with *only* organization `o-12345abcdef,` organizational unit `ou-98765fedcba`, and AWS account `111111111111`\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Deny",
            "Action": [
                "ram:AssociateResourceShare",
                "ram:CreateResourceShare"
            ],
            "Resource": "*",
            "Condition": {
                "ForAnyValue:StringNotEquals": {
                    "ram:Principal": [
                        "arn:aws:organizations::123456789012:organization/o-12345abcdef",
                        "arn:aws:organizations::123456789012:ou/o-12345abcdef/ou-98765fedcba",
                        "111111111111"
                    ]
                }
            }
        }
    ]
}
```