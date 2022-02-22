# Monitoring AWS RAM using CloudWatch Events<a name="using-cloudwatch-events"></a>

Using Amazon CloudWatch Events, you can set up automatic notifications for specific events in AWS RAM\. Events from AWS RAM are delivered to CloudWatch Events in near\-real time\. You can configure CloudWatch Events to monitor events and invoke targets in response to events that indicate changes to your resource shares\. Changes to a resource share trigger events for both the owner of the resource share and the principals that were granted access to the resource share\.

When you create an event pattern, the source is `aws.ram`\.

**Note**  
Take care writing code that depends on these events\. These events are not guaranteed, but are emitted on a best effort basis\. If an error occurs when AWS RAM attempts to emit an event, the service tries several more times\. However, it can time out and result in the loss of that specific event\.

For more information, see the [Amazon CloudWatch Events User Guide](https://docs.aws.amazon.com/AmazonCloudWatch/latest/events/)\.