# Service quotas for AWS RAM<a name="service-quotas"></a>

Your AWS account has the following limits related to AWS Resource Access Manager \(AWS RAM\)\. You can request an increase for some of these limits\. To request a limit increase, contact [AWS Support](https://console.aws.amazon.com/support/home#/)\.

**Note**  
The following definitions apply to the description in the quotas below:  
**Resource** – An individual AWS service\-created element that you want to share, such as an Amazon S3 bucket or an Amazon EC2 instance\. Each resource referenced in a resource share counts as one against this quota\. If you share the same resource in three different resource shares, it increases your count for this quota by three\.
**Resource share** – An AWS RAM created container that you can use to share resources\. Each resource share, regardless of how many resources it contains, counts as one against your quota\.
**Shared principal** – An identifier that you've associated with a resource share\. This can be an AWS Identity and Access Management \(IAM\) role or user, an AWS account identifier, an organizational unit, or an entire organization\. Each shared principal that you reference in a resource share adds one to your quota use\. If you share with an entire organization by referencing its ID, it counts as only one against this quota\.
**Customer managed permission** – Managed permissions that you create to address specific use cases using least privilege access to manage how your shared resources are used\. 


| Resource | Default limit | 
| --- | --- | 
|  Maximum number of resource shares per AWS Region  |  25,000  | 
|  Maximum number of resource associations per resource share  |  5,000  | 
|  Maximum number of principal associations per resource share  |  5,000  | 
|  Maximum number of customer managed permissions   |  1,500  | 
|  Maximum number of customer managed permissions per resource type  |  10  | 
|  Maximum number of versions per customer managed permission  |  5  | 
|  Maximum number of resource associations across all resource shares in an AWS Region   Each resource included in a resource share counts against this limit\. If a resource is included in 10 different resource shares, that counts 10 against the limit\.   |  25,000  | 
|  Maximum number of principal associations across all resource shares in an AWS Region  Each principal included in a resource share counts against this limit\. If a principal is included in 10 different resource shares, that counts 10 against the limit\.   |  25,000  | 
|  Maximum number of pending invitations per sharing account  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/service-quotas.html)  |  20  | 