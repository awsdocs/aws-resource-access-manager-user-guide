# Viewing AWS RAM managed permissions<a name="working-with-sharing-view-permissions"></a>

You can view details about AWS RAM managed permissions that are available to assign to resource types in your resource shares\. You can identify which managed permissions are by which resource shares\. To see these details, use the **Permissions library** in the AWS RAM console\.

------
#### [ Console ]

**To view details about AWS RAM managed permissions**

1. Navigate to the **[https://console.aws.amazon.com/ram/home#Permissions:](https://console.aws.amazon.com/ram/home#Permissions:)** page in the AWS RAM console\.

1. Because AWS RAM resource shares exist in specific AWS Regions, choose the appropriate AWS Region from the drop\-down list in the upper\-right corner of the console\.

1. In the **Permissions **list, choose the managed permission for which you want to view details\. You can use the search box to filter the list of permissions by entering part of a name or a resource type\.

1. \(Optional\) To change the display preferences, choose the gear icon in the upper right of the **Permissions **panel\. You can change the following preferences:
   + **Page size** – The number of resources displayed on each page\.
   + **Wrap lines** – Whether to wrap lines in table rows\.
   + **Columns** – Whether to display or hide information about the resource type and associated shares\.

   After you finish setting display preferences, choose **Confirm**\.

1. For each permission, the list displays the following information:
   + **Permission name** – The name of the AWS managed permission\. 
   + **Resource type** – The resource type that is associated with the managed permission\.
   + **Associated shares** – The number of resource shares that are associated with the managed permission\. If a number appears, then you can choose the number to display a table of resource shares with the following information:
     + **Resource share name** – The name of the resource share that is associated with the managed permission\.
     + **Owner** – The AWS account number of the resource share owner\.
     + **Allow external principals** – Whether that resource share allows sharing with principals outside the organization in AWS Organizations\.
     + **Status** – The current status of the association between the resource share and the managed permission\. 

   You can choose the managed permission's name to display more information about that permission\. The details page for a permission displays the following information:
   + **Resource type** – The type of AWS resource to which this managed permission applies\.
   + **Last updated time** – The date and time when the managed permission was last updated\.
   + **Creation time** – The date and time when the managed permission was created\.
   + **ARN **– The [Amazon Resource Name \(ARN\)](https://docs.aws.amazon.com/general/latest/gr/aws-arns-and-namespaces.html) of the managed permission\. The ARNs for managed permissions follow this format:

     

     `arn:aws:ram::aws:permission/AWSRAM[DefaultPermission]ShareableResourceType`

     The substring `[DefaultPermission]` is present in the name of only the one managed permission for that resource type that is designated the default\.
   + **Allowed actions** – The list of AWS service actions that principals are allowed to perform on the associated resource type\.

------
#### [ AWS CLI ]

**To view the principals you're sharing resources with**  
You can use the [list\-permissions](https://docs.aws.amazon.com/cli/latest/reference/ram/list-permissions.html) command to get a list of the permissions available to use on resource shares in the current AWS Region for the calling account\.

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
            "creationTime": "2021-06-09T09:22:57.427000-07:00",
            "lastUpdatedTime": "2021-06-09T09:22:57.427000-07:00"
        },
        {
            "arn": "arn:aws:ram::aws:permission/AWSRAMDefaultPermissionAppMesh",
            "version": "1",
            "defaultVersion": true,
            "name": "AWSRAMDefaultPermissionAppMesh",
            "resourceType": "appmesh:Mesh",
            "creationTime": "2020-05-12T11:12:54.068000-07:00",
            "lastUpdatedTime": "2020-05-12T11:12:54.068000-07:00"
        },

        ... TRUNCATED FOR BREVITY ... RUN COMMAND TO SEE COMPLETE LIST OF PERMISSIONS ...

        {
            "arn": "arn:aws:ram::aws:permission/AWSRAMRevokeCertificateCertificateAuthority",
            "version": "1",
            "defaultVersion": true,
            "name": "AWSRAMRevokeCertificateCertificateAuthority",
            "resourceType": "acm-pca:CertificateAuthority",
            "creationTime": "2021-06-09T09:23:16.668000-07:00",
            "lastUpdatedTime": "2021-06-09T09:23:16.668000-07:00"
        },
        {
            "arn": "arn:aws:ram::aws:permission/AWSRAMSubordinateCACertificatePathLen0IssuanceCertificateAuthority",
            "version": "1",
            "defaultVersion": true,
            "name": "AWSRAMSubordinateCACertificatePathLen0IssuanceCertificateAuthority",
            "resourceType": "acm-pca:CertificateAuthority",
            "creationTime": "2021-06-09T09:23:11.462000-07:00",
            "lastUpdatedTime": "2021-06-09T09:23:11.462000-07:00"
        }
    ]
}
```

------