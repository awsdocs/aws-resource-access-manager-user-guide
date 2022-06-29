# How AWS RAM works with IAM<a name="security-iam-policies"></a>

By default, IAM users don't have permission to create or modify AWS RAM resources\. To allow IAM users to create or modify resources and perform tasks, you must either attach an AWS managed policy or create and attach new IAM policies that grant permission to use specific resources and API actions\. You then attach those policies to the IAM users or groups that require those permissions\.

AWS RAM provides several AWS managed policies that you can use that will address the needs of many users\. For more information about these, see [AWS managed policies for AWS RAM](security-iam-managed-policies.md)\.

If you need finer control over the permissions you grant to your users, you can construct your own policies in the IAM console\. For information about creating policies and attaching them to your IAM users and roles, see [Policies and permissions in IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies.html) in the *AWS Identity and Access Management User Guide*\.

The following sections provide the AWS RAM specific details for building an IAM permission policy\.

**Contents**
+ [Policy structure](#structure)
  + [Effect](#iam-policies-effect)
  + [Action](#iam-policies-action)
  + [Resource](#iam-policies-resource)
  + [Condition](#iam-policies-condition)

## Policy structure<a name="structure"></a>

An IAM policy is a JSON document that includes the following statements: Effect, Action, Resource, and Condition\. An IAM policy typically takes the following form\.

```
{
    "Statement":[{
        "Effect":"<effect>",
        "Action":"<action>",
        "Resource":"<arn>",
        "Condition":{
            "<comparison-operator>":{
                "<key>":"<value>"
            }
        }
    }]
}
```

### Effect<a name="iam-policies-effect"></a>

The *Effect* statement indicates whether the policy allows or denies a user permission to perform an action\. The possible values include: `Allow` and `Deny`\.

### Action<a name="iam-policies-action"></a>

The *Action* statement specifies the AWS RAM API actions for which the policy is allowing or denying permission\. For a complete list of the allowed actions, see [ Actions defined by AWS Resource Access Manager](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_awsresourceaccessmanager.html#awsresourceaccessmanager-actions-as-permissions) in the *IAM User Guide*\.

### Resource<a name="iam-policies-resource"></a>

The *Resource* statement specifies the AWS RAM resources that are affected by the policy\. To specify a resource in the statement, you need to use its unique Amazon Resource Name \(ARN\)\. For a complete list of the allowed resources, see [ Resources defined by AWS Resource Access Manager](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_awsresourceaccessmanager.html#awsresourceaccessmanager-resources-for-iam-policies) in the *IAM User Guide*\.

### Condition<a name="iam-policies-condition"></a>

*Condition* statements are optional\. They can be used to further refine the conditions under which the policy applies\. AWS RAM supports the following condition keys:
+ `aws:RequestTag/${TagKey}` – Tests whether the service request includes a tag with the specified tag key exists and has the specified value\.
+ `aws:ResourceTag/${TagKey}` – Tests whether the resource acted on by the service request has an attached tag with a tag key that you specify in the policy\.

  The following example condition checks that the resource referenced in the service request has an attached tag with the key name "Owner" and a value of "Dev Team"\.

  ```
  "Condition" : { 
      "StringEquals" : {
          "aws:ResourceTag/Owner" : "Dev Team" 
      } 
  }
  ```
+ `aws:TagKeys` – Specifies the tag keys that must be used to create or tag a resource share\.
+ `ram:AllowsExternalPrincipals` – Tests whether the resource share in the service request allows sharing with external principals\. An external principal is an AWS account outside of your organization in AWS Organizations\. If this evaluates to `False`, then you can share this resource share with accounts only in the same organization\.
+ `ram:PermissionArn` – Tests whether the permission ARN specified in the service request matches an ARN string that you specify in the policy\.
+ `ram:PermissionResourceType` – Tests whether the permission specified in the service request is valid for the resource type that you specify in the policy\. Specify resource types using the format shown in the list of [shareable resource types](shareable.md)\.
+ `ram:Principal` – Tests whether the identity of the role or user that is performing the service request matches an ARN string that you specify in the policy\.
+ `ram:RequestedAllowsExternalPrincipals` – Tests whether the service request includes the `allowExternalPrincipals` parameter and whether its argument matches the value you specify in the policy\.
+ `ram:RequestedResourceType` – Tests whether the resource type of the resource being acted on matches a resource type string that you specify in the policy\. Specify resource types using the format shown in the list of [shareable resource types](shareable.md)\.
+ `ram:ResourceArn` – Tests whether the ARN of the resource being acted upon by the service request matches an ARN that you specify in the policy\.
+ `ram:ResourceShareName` – Tests whether the name of the resource share being acted upon by the service request matches a string that you specify in the policy\.
+ `ram:ShareOwnerAccountId` – Tests the account ID number of the resource share being acted upon by the service request matches a string that you specify in the policy\. 