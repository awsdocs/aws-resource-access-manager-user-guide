# Considerations for using customer managed permissions in AWS RAM<a name="managed-permission-considerations"></a>

Customer managed permissions are only available in the AWS Region that you create them in\. Not all resource types support customer managed permissions\. For a list of supported resource types in AWS Resource Access Manager, see [Shareable AWS resources](shareable.md)\.

Customer managed permissions with multiple statements aren't supported\. You can only use single non\-negating operators in customer managed permissions\.

The following conditions aren't supported in customer managed permissions:
+ Principal in the organization related:
  + `aws:PrincipalOrgId`
  + `aws:PrincipalOrgPaths`
  + `aws:PrincipalAccount`
+ Principal for a specified service related:
  + `aws:SourceArn`
  + `aws:SourceAccount`
+ System tags:
  + `aws:PrincipalTag/aws:`
  + `aws:ResourceTag/aws:`
  + `aws:RequestTag/aws:`