# View principals sharing with you<a name="working-with-shared-view-principals"></a>

You can view a list of all the principals that are sharing resources with you\. You can see which resources and resource shares they're sharing with you\.

------
#### [ Console ]

**To view the principals that are sharing resources with you**

1. Open the AWS RAM console at [https://console\.aws\.amazon\.com/ram](https://console.aws.amazon.com/ram/)\.

1. In the navigation pane, choose **Shared with me**, **Principals**\.

1. \(Optional\) You can apply a filter to find specific principals\. You can apply multiple filters to narrow your search\.

1. The console displays the following information:
   + **Principal ID** – The ID of the principal who is sharing with you\.
   + **Resource shares** – The number of resource shares to which the principal has added you\. Choose the number to view the list of resource shares\.
   + **Resources** – The number of resources the principal is sharing with you\. Choose the value to view the list of resources\.

------
#### [ AWS CLI ]

**To view the principals that are sharing resources with you**  
You can use the [list\-principals](https://docs.aws.amazon.com/cli/latest/reference/ram/list-principals.html) command to retrieve the list of principals that are sharing resources with your AWS account\.

The following example command displays details about the AWS account that shared a resource share with the account used to call the operation in the current AWS Region\. 

```
$  aws ram list-principals \
    --resource-owner OTHER-ACCOUNTS
{
    "principals": [
        {
            "id": "111111111111",
            "resourceShareArn": "arn:aws:ram:us-east-1:111111111111:resource-share/8b831ba0-63df-4608-be3c-19096b1ee16e",
            "creationTime": "2021-09-21T08:50:41.308000-07:00",
            "lastUpdatedTime": "2021-09-21T09:06:25.545000-07:00",
            "external": true
        }
    ]
}
```

------