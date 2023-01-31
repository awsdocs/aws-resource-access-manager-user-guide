# Terms and concepts for AWS RAM<a name="getting-started-terms-and-concepts"></a>

The following concepts help explain how you can use AWS Resource Access Manager \(AWS RAM\) to share your resources\.

## Resource share<a name="term-resource-share"></a>

You share resources using AWS RAM by creating a *resource share*\. A resource share has the following three elements:
+ A list of one or more AWS resources to be shared\.
+ A list of one or more [principals](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_principal.html#Principal_specifying) to whom access to the resources is granted\.
+ A [managed permission](#term-managed-permission) for each type of resource that you include in the share\. Each managed permission applies to all resources of that type in that resource share\.

After you use AWS RAM to create a resource share, the principals specified in the resource share can be granted access to the share's resources\.
+ If you turn on AWS RAM sharing with AWS Organizations, and your principals you share with are in the same organization as the sharing account then those principals can receive access as soon as their account administrator grants them permissions to use the resources using an AWS Identity and Access Management \(IAM\) permission policy\.
+ If you don't turn on AWS RAM sharing with Organizations, you can still share resources with individual AWS accounts that are in your organization\. The administrator in the consuming account receives an invitation to join the resource share, and they must accept the invitation before the principals specified in the resource share can access the shared resources\.
+ You can also share with accounts outside of your organization, if the resource type supports it\. The administrator in the consuming account receives an invitation to join the resource share, and they must accept the invitation before the principals specified in the resource share can access the shared resources\. For information about which resource types support this type of sharing, see [Shareable AWS resources](shareable.md) and view the **Can share with accounts outside its organization** column\.

## Sharing account<a name="term-sharing-account"></a>

The *sharing account* contains the resource that is shared and in which the AWS RAM administrator creates the AWS resource share by using AWS RAM\. 

An AWS RAM administrator is an IAM principal who has permissions to create and configure resource shares in the AWS account\. Because AWS RAM works by attaching a resource\-based policy to the resources in a resource share, the AWS RAM administrator also must have permissions to call the `PutResourcePolicy` operation in the AWS service for each resource type included in a resource share\.

## Consuming account<a name="term-consuming-account"></a>

The *consuming account* is the AWS account to which a resource is shared\. The resource share can specify an entire account as the principal, or for some resource types, individual roles or users in the account \. For information about which resource types support this type of sharing, see [Shareable AWS resources](shareable.md) and view the **Can share with IAM roles & users** column\.

 The principals in the consuming account can perform only those actions allowed by ***both*** of the following permissions:
+ The AWS RAM managed permissions attached to the resource share\. These specify the *maximum* permissions that can be granted to the principals in the consuming account\.
+ The IAM identity\-based policies attached to individual roles or users by the IAM administrator in the consuming account\. Those policies must grant `Allow` access to specified actions and to the [Amazon Resource Name \(ARN\)](https://docs.aws.amazon.com/general/latest/gr/aws-arns-and-namespaces.html) of a resource in the sharing account\.

AWS RAM supports the following IAM principal types as consumers of resource shares:
+ **Another AWS account\.** The resource share makes the included resources in the sharing account available to the consuming account\. 
+ **Individual IAM roles or users in another account**\. Some resource types support sharing directly with individual IAM roles or users\. Specify this principal type by its ARN\.
  + **IAM role**: `arn:aws:iam::123456789012:role/rolename`
  + **IAM user**: `arn:aws:iam::123456789012:user/username`
+ **Accounts in an organization**\. If the sharing account is managed by AWS Organizations, then the resource share can specify the organization’s ID to share with all of the accounts in the organization\. The resource share can alternatively specify an organizational unit \(OU\) ID to share with all of the accounts in that OU\. A sharing account can share only with its own organization or OU IDs within its own organization\. Specify accounts in an organization by the ARN of the organization or the OU\.
  + **All accounts in an organization**\. Example ARN of an organization in AWS Organizations:

    `arn:aws:organizations::123456789012:organization/o-<orgid>`
  + **All accounts in an organizational unit**\. Example ARN of an OU ID:

    `arn:aws:organizations::123456789012:organization/o-<orgid>/ou-<rootid>-<ouid>`
**Important**  
When you share with an organization or an OU, and that scope includes the account that owns the resource share, all principals in the sharing account automatically get access to the resources in the share\. The access granted is defined by the managed permissions associated with the share\. This is because the resource\-based policy that AWS RAM attaches to each resource in the share uses `"Principal": "*"`\. For more information, see [Implications of using "Principal": "\*" in a resource\-based policy](#term-principal-star)\.  
Principals in the other consuming accounts don't immediately get access to the share's resources\. The other accounts' administrators must first attach identity\-based permission policies to the appropriate principals\. Those policies must grant `Allow` access to the ARNs of individual resources in the resource share\. The permissions in those policies can't exceed those specified in the AWS RAM managed permission associated with the resource share\.

## Resource\-based policy<a name="term-resource-based-policy"></a>

Resource\-based policies are JSON text documents that implement the IAM policy language\. Unlike identity\-based policies that you attach to the principal, such as an IAM role or user, you attach resource\-based policies to the resource\. You must specify a `Principal` policy element that determines who can access the resource\. For more information, see [Identity\-based policies and resource\-based policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_identity-vs-resource.html) in the *IAM User Guide*\.

AWS RAM provides a simple and secure resource sharing experience by providing an easy\-to\-use abstraction resource\-based policies\. 

For those resource types that support resource\-based policies, AWS RAM automatically constructs and manages the resource\-based policies for you\. For a given resource, AWS RAM builds the resource\-based policy by combining the information from all of the resource shares that include that resource\. For example, consider an Amazon SageMaker pipeline that you share by using AWS RAM and include in two different resource shares\. You could use one resource share to provide read\-only access to your entire organization\. You could then use the other resource share to grant only SageMaker execution permissions to a single account\. AWS RAM automatically combines those two different sets of permissions into a single resource policy with multiple statements\. It then attaches the combined resource\-based policy to the pipeline resource\. You can view this underlying resource policy by calling the [GetResourcePolicy](https://docs.aws.amazon.com/ram/latest/APIReference/API_GetResourcePolicies.html) operation\. AWS services then use that resource\-based policy to authorize any principal who attempts to perform an action on the shared resource\. 

Although you can manually create the resource\-based policies and attach them to your resources by calling `PutResourcePolicy`, we recommend that you use AWS RAM because it provides the following advantages
+ **Discoverability for share consumers:** If you share resources by using AWS RAM, users can see all of the resources shared with them directly in the resource owning service's console and API operations as if those resources were directly in the user's account\. For example, if you share an AWS CodeBuild project with another account, users in the consuming account can see the project in the CodeBuild console and in the results of CodeBuild API operations performed\. Resources shared by directly attaching a resource\-based policy aren't visible this way\. Instead, you must discover and explicitly refer to the resource by its ARN\.
+ **Manageability for share owners:** If you share resources by using AWS RAM, resource owners in the sharing account can centrally see which other accounts have access to their resources\. If you share a resource using a resource\-based policy, you can see the consuming accounts only by examining the policy for individual resources in the relevant service console or API\.
+ **Efficiency:** If you share resources by using AWS RAM, you can share multiple resources and manage them as a unit\. Resources shared by using only resource\-based policies require individual policies attached to every resource that you share\.
+ **Simple:** AWS RAM abstracts you from needing to understand the JSON\-based IAM policy language\. AWS RAM provides ready\-to\-use managed permissions that you can choose from to attach to your resource shares\.

By using AWS RAM, you can even share some resource types that don’t support resource\-based policies yet\. For such resource types, AWS RAM automatically generates a resource\-based policy as a representation of the actual permissions\. Users can view this representation by calling [GetResourcePolicy](https://docs.aws.amazon.com/ram/latest/APIReference/API_GetResourcePolicies.html)\. This includes the following resource types:
+ Amazon Aurora – DB clusters
+ Amazon EC2 – capacity reservations and dedicated hosts
+ AWS License Manager – License configurations
+ AWS Outposts – Local gateway route tables, outposts, and sites
+ Amazon Route 53 – Forwarding rules
+ Amazon Virtual Private Cloud – Customer\-owned IPv4 addresses, prefix lists, subnets, traffic mirror targets, transit gateways, transit gateway multicast domains

### Examples of AWS RAM generated resource\-based policies<a name="rbp-examples"></a>

If you share an EC2 Image Builder image resource with an individual ***account***, AWS RAM generates a policy that looks like the following example and attaches it to any image resources that are included in the resource share\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": {"AWS": "arn:aws:iam::123456789012:root"},
            "Action": [
                "imagebuilder:GetImage",
                "imagebuilder:ListImages",
            ],
            "Resource": "arn:aws:imagebuilder:us-east-1:123456789012:image/testimage/1.0.0/44"
        }
    ]
}
```

If you share an EC2 Image Builder image resource with an ***IAM role or user*** in a different AWS account, AWS RAM generates a policy that looks like the following example and attaches it to any image resources that are included in the resource share\.

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {
        "AWS": "arn:aws:iam::123456789012:role/MySampleRole"
      },
      "Action": [
          "imagebuilder:GetImage",
          "imagebuilder:ListImages",
      ],
      "Resource": "arn:aws:imagebuilder:us-east-1:123456789012:image/testimage/1.0.0/44"
    }
  ]
}
```

If you share an EC2 Image Builder image resource with all of the accounts in an organization or with the accounts an OU, AWS RAM generates a policy that looks like the following example and attaches it to any image resources that are included in the resource share\.

**Note**  
This policy uses `"Principal": "*"` and then uses the `"Condition"` element to restrict permissions to identities that match the specified `PrincipalOrgID`\. For more information, see [Implications of using "Principal": "\*" in a resource\-based policy](#term-principal-star)\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": "*",
            "Action": [
                "imagebuilder:GetImage",
                "imagebuilder:ListImages",
            ],
            "Resource": "arn:aws:imagebuilder:us-east-1:123456789012:image/testimage/1.0.0/44"
            "Condition": {
                "StringEquals": {
                    "aws:PrincipalOrgID": "o-123456789"
                }
            }
        }
    ]
}
```

### Implications of using "Principal": "\*" in a resource\-based policy<a name="term-principal-star"></a>

When you include `"Principal": "*"` in a resource\-based policy, the policy grants access to all IAM principals in the account that contains the resource, subject to any restrictions imposed by a `Condition` element, if it exists\. Explicit `Deny` statements in any policy that applies to the calling principal overrides the permissions granted by this policy\. However, an ***implicit*** `Deny` \(meaning the lack of an *explicit * `Allow`\) in any applicable identity policies, permissions boundary policies, or session policies does ***not*** result in a `Deny` to the principals granted access to an action by such a resource\-based policy\.

If this behavior isn’t desirable for your scenario, then you can limit this behavior by adding an ***explicit*** `Deny` statement to an identity policy, permissions boundary, or session policy that affects the relevant roles and users\. 

## Managed permission<a name="term-managed-permission"></a>

Managed permissions define how a consumer can act on the resources with a resource share\. When you create a resource share, you must specify which managed permission to use for each resource type that is included in the resource share\. A managed permission lists the *conditions* under which the users of the shared resource can perform the specified `actions` on the resources\.

AWS RAM defines at least one AWS managed permission for every supported resource type\. Some resource types support more than one AWS managed permission, with one designated as the default\. The default managed permission is used unless you specify otherwise\. You can attach only one managed permission for each resource type in a resource share\. You can't create a resource share in which some resources of a certain type use one managed permission and other resources of the same type use a different managed permission\. To do that you'd need to create two different resource shares and split the resources among them, giving each share's set a different managed permission\.

AWS RAM uses [resource\-based policies](#term-resource-based-policy) to provide most of the core functionality of a managed permission\. Managed permissions are evaluated along with all other IAM policy types that apply to the access scenario\. This includes any IAM identity\-based permission policies attached to the principals who are attempting to access the resource, and service control policies \(SCPs\) for AWS Organizations that might apply to the AWS account\. Resource\-based policies generated by RAM participate in the same policy evaluation logic as all other IAM policies\. For complete details of policy evaluation and how to determine the resulting permissions, see [Policy evaluation logic](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_evaluation-logic.html) in the *IAM User Guide*\.

## Permission version<a name="term-managed-permission-version"></a>

A managed permission can be updated over time to address new functionality or to address discovered shortcomings\. Any change to a managed permission is represented as a new version of that managed permission\. One of the versions is always designated as the default version\.

When you create or update a resource share, you can attach only the default version of the specified managed permission\. For more information, see [Updating AWS RAM managed permissions to a newer version](working-with-sharing-update-permissions.md)\.