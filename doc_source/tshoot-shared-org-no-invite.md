# The other account in my organization never receives an invitation<a name="tshoot-shared-org-no-invite"></a>

## Scenario<a name="tshoot-shared-org-no-invite-scenario"></a>

When you share resources with another account in the same organization managed by AWS Organizations, they don't receive invitations\.

## Cause<a name="tshoot-shared-org-no-invite-cause"></a>

This is **expected behavior** if your account has [sharing within the AWS organization](getting-started-sharing.md#getting-started-sharing-orgs) turned on\.

When this option is turned on and you share with another account in your organization, no invitations are sent and no acceptance is required\. All organization accounts that you reference as principals in the resource share can immediately begin accessing the resources in the share\.

If your account has *not* turned on sharing within the AWS organization, then when you share with other accounts, even if they are in the same AWS organization, they are treated as standalone accounts\. Invitations are sent and must be accepted before users can access the resources in the shares\.