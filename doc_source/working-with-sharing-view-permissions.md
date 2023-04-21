# Viewing managed permissions<a name="working-with-sharing-view-permissions"></a>

You can view details about managed permissions that are available to assign to resource types in your resource shares\. You can identify the managed permissions that are assigned to resource shares\. To see these details, use the **Managed permissions library** in the AWS RAM console\.

------
#### [ Console ]

**To view details about managed permissions available in AWS RAM**

1. Navigate to the ****[Managed permissions library](https://console.aws.amazon.com/ram/home#Permissions:)**** page in the AWS RAM console\.

1. Because AWS RAM resource shares exist in specific AWS Regions, choose the appropriate AWS Region from the dropdown list in the upper\-right corner of the console\. To see resource shares that contain global resources, you must set the AWS Region to US East \(N\. Virginia\), \(`us-east-1`\)\. For more information about sharing global resources, see [Sharing Regional resources compared to global resources](working-with-regional-vs-global.md)\. Although all Regions share the same available AWS managed permissions, this affects the number of associated resource shares displayed for each managed permission in [Step 5](#step-5)\. Customer managed permissions are only available in the Region that they were created in\.

1. In the **Managed permissions **list, choose the managed permission for which you want to view details\. You can use the search box to filter the list of managed permissions by entering part of a name or a resource type, or choosing a managed permission type from the dropdown list\.

1. \(Optional\) To change the display preferences, choose the gear icon in the upper right of the **Managed permissions** panel\. You can change the following preferences:
   + **Page size** – The number of resources displayed on each page\.
   + **Wrap lines** – Whether to wrap lines in table rows\.
   + **Columns** – Whether to display or hide information about the resource type and associated shares\.

   After you finish setting display preferences, choose **Confirm**\.

1. <a name="step-5"></a>For each managed permission, the list displays the following information:
   + **Managed permission name** – The name of the managed permission\. 
   + **Resource type** – The resource type that is associated with the managed permission\.
   + **Managed permission type** – Whether the managed permission is an AWS managed permission or a customer managed permission\.
   + **Associated shares** – The number of resource shares that are associated with the managed permission\. If a number appears, then you can choose the number to display a table of resource shares with the following information:
     + **Resource share name** – The name of the resource share that is associated with the managed permission\.
     + **Managed permission version** – The version of the managed permission that is attached to this resource share\.
     + **Owner** – The AWS account number of the resource share owner\.
     + **Allow external principals** – Whether that resource share allows sharing with principals outside the organization in AWS Organizations\.
     + **Status** – The current status of the association between the resource share and the managed permission\.
   + **Status** – Describes whether the managed permission is:
     + **Attachable** – You can attach the managed permission to your resource shares\.
     + **Unattachable** – You can't attach the managed permission to your resource shares\.
     + **Deleting** – The managed permission is no longer active and will soon be deleted\.
     + **Deleted** – The managed permission has been deleted\. It remains visible for two hours before it disappears from the **Managed permission library**\.

   You can choose the managed permission's name to display more information about that managed permission\. The details page for a managed permission displays the following information:
   + **Resource type** – The type of AWS resource to which this managed permission applies\.
   + **Number of versions** – You can have up to five versions of a customer managed permission\. 
   + **Default version** – Specifies which version is the default and therefore assigned automatically to all new resource shares that use this managed permission\. Any existing resource shares that use different versions display a prompt for you to update the resource share to the default version\.
   + **ARN **– The [Amazon Resource Name \(ARN\)](https://docs.aws.amazon.com/general/latest/gr/aws-arns-and-namespaces.html) of the managed permission\. The ARNs for AWS managed permissions use the following format:

     `arn:aws:ram::aws:permission/AWSRAM[DefaultPermission]ShareableResourceType`

     The substring `[DefaultPermission]` \(without the brackets in an actual ARN\) is present in the name of only the one managed permission for that resource type that is designated the default\.
   + **Managed permission versions** – You can choose which version's information to display in the tabs below this dropdown list\.
     + **Details** tab:
       + **Creation time** – The date and time when this version of the managed permission was created\.
       + **Last updated time** – The date and time when this version of the managed permission was last updated\.
     + **Policy template** tab – The list of service actions and conditions, if applicable, that this version of the managed permission allows principals to perform on the associated resource type\.
     + **Associated resource shares** – The list of resource shares that use this version of the managed permission\.

------
#### [ AWS CLI ]

**To view details about managed permissions available in AWS RAM**  
You can use the [https://docs.aws.amazon.com/cli/latest/reference/ram/list-permissions.html](https://docs.aws.amazon.com/cli/latest/reference/ram/list-permissions.html) command to get a list of the managed permissions available to use on resource shares in the current AWS Region for the calling account\.

```
$ aws ram list-permissions
{
    "permissions": [
        {
            "arn": "arn:aws:ram::aws:permission/AWSRAMBlankEndEntityCertificateAPICSRPassthroughIssuanceCertificateAuthority",
            "version": "1",
            "defaultVersion": true,
            "name": "AWSRAMBlankEndEntityCertificateAPICSRPassthroughIssuanceCertificateAuthority",
            "resourceType": "acm-pca:CertificateAuthority",
            "status": "ATTACHABLE",
            "creationTime": "2022-06-30T13:03:31.732000-07:00",
            "lastUpdatedTime": "2022-06-30T13:03:31.732000-07:00",
            "isResourceTypeDefault": false,
            "permissionType": "AWS_MANAGED"
        },
        {
            "arn": "arn:aws:ram::aws:permission/AWSRAMBlankEndEntityCertificateAPIPassthroughIssuanceCertificateAuthority",
            "version": "1",
            "defaultVersion": true,
            "name": "AWSRAMBlankEndEntityCertificateAPIPassthroughIssuanceCertificateAuthority",
            "resourceType": "acm-pca:CertificateAuthority",
            "status": "ATTACHABLE",
            "creationTime": "2022-11-18T07:05:46.976000-08:00",
            "lastUpdatedTime": "2022-11-18T07:05:46.976000-08:00",
            "isResourceTypeDefault": false,
            "permissionType": "AWS_MANAGED"
        },

        ... TRUNCATED FOR BREVITY ... RUN COMMAND TO SEE COMPLETE LIST OF PERMISSIONS ...

        {
            "arn": "arn:aws:ram::aws:permission/AWSRAMVPCPermissionsNetworkManagerCoreNetwork",
            "version": "1",
            "defaultVersion": true,
            "name": "AWSRAMVPCPermissionsNetworkManagerCoreNetwork",
            "resourceType": "networkmanager:CoreNetwork",
            "status": "ATTACHABLE",
            "creationTime": "2022-06-30T13:03:46.557000-07:00",
            "lastUpdatedTime": "2022-06-30T13:03:46.557000-07:00",
            "isResourceTypeDefault": false,
            "permissionType": "AWS_MANAGED"
        },        {
            "arn": "arn:aws:ram:us-east-1:123456789012:permission/My-Test-CMP",
            "version": "1",
            "defaultVersion": true,
            "name": "My-Test-CMP",
            "resourceType": "ec2:IpamPool",
            "status": "ATTACHABLE",
            "creationTime": "2023-03-08T06:54:10.038000-08:00",
            "lastUpdatedTime": "2023-03-08T06:54:10.038000-08:00",
            "isResourceTypeDefault": false,
            "permissionType": "CUSTOMER_MANAGED"
        }
    ]
}
```

You can also find the ARN of a specific managed permission by its name in the `--query` parameter of the `list-permissions` AWS CLI command\. The following example filters the output to include only elements in the `permissions` array results that match the specified name\. We also specify that we want to see only the ARN field in the results, and in plain text format instead of the default JSON\.

```
$ aws ram list-permissions \
    --query "permissions[?name == 'My-Test-CMP'].arn \
    --output text
arn:aws:ram:us-east-1:123456789012:permission/My-Test-CMP
```

After you find the ARN of the specific managed permission you're interested in, you can retrieve its details, including its JSON policy text, by running the command [https://docs.aws.amazon.com/cli/latest/reference/ram/get-permission.html](https://docs.aws.amazon.com/cli/latest/reference/ram/get-permission.html)\.

```
$ aws ram get-permission \
    --permission-arn arn:aws:ram:us-east-1:123456789012:permission/My-Test-CMP
{
    "permission": {
        "arn": "arn:aws:ram:us-east-1:123456789012:permission/My-Test-CMP",
        "version": "1",
        "defaultVersion": true,
        "name": "My-Test-CMP",
        "resourceType": "ec2:IpamPool",
        "permission": "{\n\t\"Effect\": \"Allow\",\n\t\"Action\": [\n\t\t\"ec2:GetIpamPoolAllocations\",\n\t\t\"ec2:GetIpamPoolCidrs\",\n\t\t\"ec2:AllocateIpamPoolCidr\",\n\t\t\"ec2:AssociateVpcCidrBlock\",\n\t\t\"ec2:CreateVpc\",\n\t\t\"ec2:ProvisionPublicIpv4PoolCidr\",\n\t\t\"ec2:ReleaseIpamPoolAllocation\"\n\t]\n}",
        "creationTime": "2023-03-08T06:54:10.038000-08:00",
        "lastUpdatedTime": "2023-03-08T06:54:10.038000-08:00",
        "isResourceTypeDefault": false,
        "permissionType": "CUSTOMER_MANAGED",
        "featureSet": "STANDARD",
        "status": "ATTACHABLE"
    }
}
```

------