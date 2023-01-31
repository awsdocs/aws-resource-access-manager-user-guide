# AWS managed policies for AWS RAM<a name="security-iam-managed-policies"></a>

AWS Resource Access Manager currently provides several AWS RAM managed policies, which are described in this topic\.

**Topics**
+ [AWSResourceAccessManagerReadOnlyAccess](#security-iam-managed-policies-AWSResourceAccessManagerReadOnlyAccess)
+ [AWSResourceAccessManagerFullAccess](#security-iam-managed-policies-AWSResourceAccessManagerFullAccess)
+ [AWSResourceAccessManagerResourceShareParticipantAccess](#security-iam-managed-policies-AWSResourceAccessManagerResourceShareParticipantAccess)
+ [AWSResourceAccessManagerServiceRolePolicy](#security-iam-managed-policies-AWSResourceAccessManagerServiceRolePolicy)
+ [Policy updates](#security-iam-awsmanpol-updates)

In the preceding list, you can attach the first three policies to your IAM roles, groups, and users to grant permissions\. The last policy in the list is reserved for the AWS RAM service's service\-linked role\.

To add permissions to users, groups, and roles, it is easier to use AWS managed policies than to write policies yourself\. It takes time and expertise to [create IAM customer managed policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_create-console.html) that provide your team with only the permissions they need\. To get started quickly, you can use our AWS managed policies\. These policies cover common use cases and are available in your AWS account\. For more information about AWS managed policies, see [AWS managed policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-vs-inline.html#aws-managed-policies) in the *IAM User Guide*\.

AWS services maintain and update AWS managed policies\. You can't change the permissions in AWS managed policies\. Services occasionally add additional permissions to an AWS managed policy to support new features\. This type of update affects all identities \(users, groups, and roles\) where the policy is attached\. Services are most likely to update an AWS managed policy when a new feature is launched or when new operations become available\. Services do not remove permissions from an AWS managed policy, so policy updates won't break your existing permissions\.

Additionally, AWS supports managed policies for job functions that span multiple services\. For example, the `ViewOnlyAccess` AWS managed policy provides read\-only access to many AWS services and resources\. When a service launches a new feature, AWS adds read\-only permissions for new operations and resources\. For a list and descriptions of job function policies, see [AWS managed policies for job functions](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_job-functions.html) in the *IAM User Guide*\.

## AWS managed policy: AWSResourceAccessManagerReadOnlyAccess<a name="security-iam-managed-policies-AWSResourceAccessManagerReadOnlyAccess"></a>

You can attach the `AWSResourceAccessManagerReadOnlyAccess` policy to your IAM identities\.

This policy provides read\-only permissions to the resource shares that are owned by your AWS account\.

It does this by granting permission to run any of the `Get*` or `List*` operations\. It doesn't provide any ability to modify any resource share\.

**Permissions details**  
This policy includes the following permissions\.
+ `ram` – Allows principals to view details about resource shares owned by the account\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Action": [
                "ram:Get*",
                "ram:List*"
            ],
            "Effect": "Allow",
            "Resource": "*"
        }
    ]
}
```

## AWS managed policy: AWSResourceAccessManagerFullAccess<a name="security-iam-managed-policies-AWSResourceAccessManagerFullAccess"></a>

You can attach the `AWSResourceAccessManagerFullAccess` policy to your IAM identities\.

This policy provides full administrative access to view or modify the resource shares that are owned by your AWS account\.

It does this by granting permission to run any `ram` operations\.

**Permissions details**  
This policy includes the following permissions\.
+ `ram` – Allows principals to view or modify any information about the resource shares that are owned by the AWS account\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Action": [
                "ram:*"
            ],
            "Effect": "Allow",
            "Resource": "*"
        }
    ]
}
```

## AWS managed policy: AWSResourceAccessManagerResourceShareParticipantAccess<a name="security-iam-managed-policies-AWSResourceAccessManagerResourceShareParticipantAccess"></a>

You can attach the `AWSResourceAccessManagerResourceShareParticipantAccess` policy to your IAM identities\.

This policy provides principals the ability to accept or reject resource shares that are shared with this AWS account, and to view details about these resource shares\. It doesn't provide any ability to modify those resource shares\.

It does this by granting permission to run some `ram` operations\.

**Permissions details**  
This policy includes the following permissions\.
+ `ram` – Allows principals to accept or reject resource share invitations and to view details about the resource shares that are shared with the account\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Action": [
                "ram:AcceptResourceShareInvitation",
                "ram:GetResourcePolicies",
                "ram:GetResourceShareInvitations",
                "ram:GetResourceShares",
                "ram:ListPendingInvitationResources",
                "ram:ListPrincipals",
                "ram:ListResources",
                "ram:RejectResourceShareInvitation"
            ],
            "Effect": "Allow",
            "Resource": "*"
        }
    ]
}
```

## AWS managed policy: AWSResourceAccessManagerServiceRolePolicy<a name="security-iam-managed-policies-AWSResourceAccessManagerServiceRolePolicy"></a>

The AWS managed policy `AWSResourceAccessManagerServiceRolePolicy`can be used only with the service\-linked role for AWS RAM\. You can't attach, detach, modify, or delete this policy\.

This policy provides AWS RAM with read\-only access to your organization's structure\. When you enable integration between AWS RAM and AWS Organizations, AWS RAM automatically creates a service\-linked role named [AWSServiceRoleForResourceAccessManager](https://console.aws.amazon.com/iam/home#/roles/AWSServiceRoleForResourceAccessManager) that the service assumes when it needs to look up information about your organization and its accounts, for example, when you view the organization's structure in the AWS RAM console\.

It does this by granting read\-only permission to run the `organizations:Describe` and `organizations:List` operations that provide details of the organization's structure and accounts\.

**Permissions details**  
This policy includes the following permissions\.
+ `organizations` – Allows principals to view information about the organization's structure, including the organizational units, and the AWS accounts they contain\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "organizations:DescribeAccount",
                "organizations:DescribeOrganization",
                "organizations:DescribeOrganizationalUnit",
                "organizations:ListAccounts",
                "organizations:ListAccountsForParent",
                "organizations:ListChildren",
                "organizations:ListOrganizationalUnitsForParent",
                "organizations:ListParents",
                "organizations:ListRoots"
            ],
            "Resource": "*"
        },
        {
            "Sid": "AllowDeletionOfServiceLinkedRoleForResourceAccessManager",
            "Effect": "Allow",
            "Action": [
                "iam:DeleteRole"
            ],
            "Resource": [
                "arn:aws:iam::*:role/aws-service-role/ram.amazonaws.com/*"
            ]
        }
    ]
}
```

## AWS RAM updates to AWS managed policies<a name="security-iam-awsmanpol-updates"></a>

View details about updates to AWS managed policies for AWS RAM since this service began tracking these changes\. For automatic alerts about changes to this page, subscribe to the RSS feed on the AWS RAM Document history page\.


| Change | Description | Date | 
| --- | --- | --- | 
|  AWS Resource Access Manager started tracking changes  |  AWS RAM documented its existing managed policies and started tracking changes\.  | September 16, 2021 | 