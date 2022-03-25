# Monitoring AWS RAM using CloudWatch Events<a name="using-cloudwatch-events"></a>

Using Amazon CloudWatch Events, you can set up automatic notifications for specific events in AWS RAM\. Events from AWS RAM are delivered to CloudWatch Events in near\-real time\. You can configure CloudWatch Events to monitor events and invoke targets in response to events that indicate changes to your resource shares\. Changes to a resource share trigger events for both the owner of the resource share and the principals that were granted access to the resource share\.

When you create an event pattern, the source is `aws.ram`\.

**Note**  
Take care writing code that depends on these events\. These events are not guaranteed, but are emitted on a best effort basis\. If an error occurs when AWS RAM attempts to emit an event, the service tries several more times\. However, it can time out and result in the loss of that specific event\.

For more information, see the [Amazon CloudWatch Events User Guide](https://docs.aws.amazon.com/AmazonCloudWatch/latest/events/)\.

## Example: Alerting on resource share failures<a name="using-cloudwatch-events-example-sharing"></a>

Consider the scenario where you want to share Amazon EC2 capacity reservations with other accounts in your organization\. Doing this is a good way to reduce your costs\.

However, if you don't meet all of the [prerequisites for sharing a capacity reservation](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/capacity-reservation-sharing.html#sharing-cr-prereq), then it can silently fail performing the asynchronous tasks involved in sharing resources\. If the share operation fails, and your users in other accounts attempt to launch instances with one of those capacity reservations, then Amazon EC2 acts as if the capacity reservation was full and launches the instance as an on\-demand instance instead\. This can result in higher than expected costs\.

To monitor for resource share failures, set up an Amazon CloudWatch Events rule that alerts you whenever an AWS RAM resource share fails\. The following tutorial procedure uses an Amazon Simple Notification Service \(SNS\) topic to notify all topic subscribers whenever EventBridge discovers a resource sharing failure\. For more information about Amazon SNS, see the [Amazon Simple Notification Service Developer Guide](https://docs.aws.amazon.com/sns/latest/dg/)\.

**To create a rule that notifies you when resource sharing fails**

1. Open the [Amazon EventBridge console](https://console.aws.amazon.com/events)\.

1. In the navigation pane, choose **Rules**, and then in the **Rules** list, choose **Create rule**\.

1. Enter a name and optional description for your rule, then choose **Next**\.

1. Scroll down to the **Event pattern** box, and choose **Custom patterns \(JSON editor\)**\.

1. Copy and paste the following event pattern:

   ```
   {
     "source": ["aws.ram"],
     "detail-type": ["Resource Sharing State Change"],
     "detail": {
       "event": ["Resource Share Association"],
       "status": ["failed"]
     }
   }
   ```

1. Choose **Next**\.

1. For **Target 1**, under **Target type**, choose **AWS service**\.

1. Under **Select a target**, choose **SNS topic**\.

1. For **Topic**, choose the SNS topic to which you want to publish the notification\. This topic must already exist\.

1. Choose **Next**, and then choose **Next** again to see to review your configuration\.

1. When you're satisfied with your options, choose **Create rule**\.

1. Back on the **Rules** page, ensure that your new rule is marked **Enabled**\. If necessary, choose the radio button next to your rule name, and then choose **Enable**\.

As long as that rule is enabled, any AWS RAM resource share that fails generates an SNS alert to the recipients of the topic you published to\.

You can also confirm that shared capacity reservations are accessible to the accounts you shared them with by attempting to [view them in the Amazon EC2 console from those accounts](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/capacity-reservation-sharing.html#identifying-shared-cr)\.