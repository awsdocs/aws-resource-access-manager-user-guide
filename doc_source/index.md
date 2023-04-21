# AWS Resource Access Manager User Guide

-----
*****Copyright &copy; Amazon Web Services, Inc. and/or its affiliates. All rights reserved.*****

-----
Amazon's trademarks and trade dress may not be used in
connection with any product or service that is not Amazon's,
in any manner that is likely to cause confusion among customers,
or in any manner that disparages or discredits Amazon. All other
trademarks not owned by Amazon are the property of their respective
owners, who may or may not be affiliated with, connected to, or
sponsored by Amazon.

-----
## Contents
+ [What is AWS Resource Access Manager?](what-is.md)
+ [Getting started with AWS RAM](getting-started.md)
   + [Terms and concepts for AWS RAM](getting-started-terms-and-concepts.md)
   + [Sharing your AWS resources](getting-started-sharing.md)
   + [Using shared AWS resources](getting-started-shared.md)
+ [Working with shared AWS resources](working-with.md)
   + [Sharing Regional resources compared to global resources](working-with-regional-vs-global.md)
   + [Share AWS resources owned by you](working-with-sharing.md)
      + [Viewing resource shares you created in AWS RAM](working-with-sharing-view-rs.md)
      + [Creating a resource share in AWS RAM](working-with-sharing-create.md)
      + [Update a resource share in AWS RAM](working-with-sharing-update.md)
      + [Viewing your shared resources in AWS RAM](working-with-sharing-view-sr.md)
      + [Viewing the principals you share resources with in AWS RAM](working-with-sharing-view-principals.md)
      + [Deleting a resource share in AWS RAM](working-with-sharing-delete.md)
   + [Access AWS resources shared with you](working-with-shared.md)
      + [Accepting and rejecting resource share invitations](working-with-shared-invitations.md)
      + [Viewing resource shares shared with you](working-with-shared-view-rs.md)
      + [Viewing resources shared with you](working-with-shared-view-sr.md)
      + [View principals sharing with you](working-with-shared-view-principals.md)
      + [Leaving a resource share](working-with-shared-leave.md)
   + [Availability Zone IDs for your AWS resources](working-with-az-ids.md)
+ [Shareable AWS resources](shareable.md)
+ [Managing permissions in AWS RAM](security-ram-permissions.md)
   + [Viewing managed permissions](working-with-sharing-view-permissions.md)
   + [Creating and using customer managed permissions in AWS RAM](create-customer-managed-permissions.md)
   + [Updating AWS managed permissions to a newer version](working-with-sharing-update-permissions.md)
   + [Considerations for using customer managed permissions in AWS RAM](managed-permission-considerations.md)
+ [Security in AWS RAM](security.md)
   + [Data protection in AWS RAM](security-data-protection.md)
   + [Identity and access management for AWS RAM](security-iam.md)
      + [How AWS RAM works with IAM](security-iam-policies.md)
      + [AWS managed policies for AWS RAM](security-iam-managed-policies.md)
      + [Using Service-Linked Roles for AWS RAM](security-iam-service-linked-roles.md)
      + [Example IAM policies for AWS RAM](security-iam-policies-examples.md)
      + [Example service control policies for AWS Organizations and AWS RAM](scp.md)
      + [Disabling resource sharing with AWS Organizations](security-disable-sharing-with-orgs.md)
   + [Logging and monitoring in AWS RAM](security-monitoring.md)
      + [Monitoring AWS RAM using CloudWatch Events](using-cloudwatch-events.md)
      + [Logging AWS RAM API calls with AWS CloudTrail](cloudtrail-logging.md)
   + [Resilience in AWS RAM](security-disaster-recovery-resiliency.md)
   + [Infrastructure security in AWS RAM](security-infrastructure.md)
+ [Troubleshooting issues with AWS RAM](troubleshooting.md)
   + [Error: "Your account ID does not exist in an AWS organization"](tshoot-no-slr.md)
   + [Error: "AccessDeniedException"](tshoot-access-denied.md)
   + [Error: "UnknownResourceException"](tshoot-unknown-resource.md)
   + [Errors when trying to share with accounts outside of my organization](tshoot-sharing-outside-org.md)
   + [Can't see shared resources in the destination account](tshoot-cant-see-shared.md)
   + [Error: Limit exceeded](tshoot-limits-exceeded.md)
   + [The other account in my organization never receives an invitation](tshoot-shared-org-no-invite.md)
   + [You can't share a VPC subnet](tshoot-subnet-limits.md)
+ [Service quotas for AWS RAM](service-quotas.md)
+ [Using AWS RAM with an AWS SDK](sdk-general-info.md)
+ [Document history for the AWS RAM User Guide](doc-history.md)