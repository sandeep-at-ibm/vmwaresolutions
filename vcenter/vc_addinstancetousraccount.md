---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-08"

---

# Migrating pre-V2.5 vCenter Server instances to IBM Cloud accounts

VMware vCenter Server instances that are deployed in V2.5 and later releases in your {{site.data.keyword.cloud}} account are automatically added to your account and are managed by {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM).

For instances that were deployed in V2.4 and earlier releases, you can migrate them to specified {{site.data.keyword.cloud_notm}} accounts for IAM-enabled user management.


## Procedure

1. In the {{site.data.keyword.vmwaresolutions_short}} console, click **Deployed Instances** from the left navigation pane.
2. At the upper-right corner of the console, click your avatar, and then click the **Account** field to select the user account that you want to migrate the instance to.
3. In the **vCenter Server Instances** table, find the pre-V2.5 instance.
4. In the **Actions** column, click the overflow menu icon, and then click **Migrate Instance to Account**.
5. In the **Migrate Instance to Account** window, confirm the account to migrate the instance to, and then click **Migrate**.

## Results

1. You get a console notification that your request to migrate the instance to the specified {{site.data.keyword.cloud_notm}} account is accepted.
2. When the instance migration is completed, the instance is displayed on the **Deployed Instances** page under the account to which it was migrated. The migrated instance is no longer displayed in the original account from which it was migrated.

### Related links

* [Managing user access with IAM](../vmonic/iam.html)
* [Inviting users to access services and resources](../vmonic/iamuserinvite.html)
* [What is IBM Cloud IAM](../../../iam/index.html)
