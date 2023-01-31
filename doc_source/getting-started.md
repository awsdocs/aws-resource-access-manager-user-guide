# Getting started with AWS RAM<a name="getting-started"></a>

With AWS Resource Access Manager, you can share resources that you own with other individual AWS accounts\. If your account is managed by AWS Organizations, you can also share resources with the other accounts in your organization\. You can also use resources that were shared with you by other AWS accounts\. 

If you don't enable sharing within AWS Organizations, you can't share resources with your organization or with the organizational units \(OU\) in your organization\. However, you can still share resources with individual AWS accounts in your organization\. For [supported resource types](shareable.md), you can also share resources with individual AWS Identity and Access Management \(IAM\) roles or users in your organization\. In this case, these principals are treated as if they were external accounts, rather than as part of your organization\. They receive an invitation to join the resource share, and they must accept the invitation to gain access to the shared resources\.

**Topics**
+ [Terms and concepts](getting-started-terms-and-concepts.md)
+ [Sharing your resources](getting-started-sharing.md)
+ [Using shared resources](getting-started-shared.md)