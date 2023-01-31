# Service quotas for AWS RAM<a name="service-quotas"></a>

Your AWS account has the following limits related to AWS Resource Access Manager \(AWS RAM\)\. You can request an increase for some of these limits\. To request a limit increase, contact [AWS Support](https://console.aws.amazon.com/support/home#/)\.

**Note**  
The following definitions apply to the description In the quotas below:  
**Resource share** – An AWS RAM created container you can use to share multiple resources\. Each resource share, regardless of how many resources it contains, counts as one against your quota\.
**Shared principal** – An identifier you've associated with a resource share\. This can be an IAM role or user, an AWS account identifier, an organizational unit, or an entire organization\. Each shared principal that you reference in a resource share counts adds one to your quota use\. If you share with an entire organization by referencing its ID, it counts as only one against this quota\.
**Resource** – An individual AWS service\-created element that you want to share, such as an Amazon S3 bucket, or an Amazon EC2 instance\. Each resource referenced in a resource share counts as one against this quota\. Note that If you share the same resource in three different resource shares, it increases your count for this quota by three\.


| Resource | Default limit | 
| --- | --- | 
|  Maximum number of resource shares per AWS Region in an account  |  5,000  | 
|  Maximum number of shared principals per AWS Region in an account  |  5,000  | 
|  Maximum number of shared resources per AWS Region in an account  |  5,000  | 
|  Maximum number of pending invitations per sharing account  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ram/latest/userguide/service-quotas.html)  |  20  | 