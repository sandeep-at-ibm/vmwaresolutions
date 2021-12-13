---

copyright:

  years:  2020, 2021

lastupdated: "2021-10-26"

keywords: veeam, veeam install, tech specs veeam

subcollection: vmwaresolutions

---

{{site.data.keyword.attribute-definition-list}}

# Managing Veeam for VMware Solutions Shared
{: #shared_veeam}

The Veeam Availability Suite™ and Veeam® Cloud Connect Replication services are available and ready-to-use in all virtual data centers. These services seamlessly integrate as a managed solution to help your enterprise achieve high availability. They provide recovery points for your applications and data. By using these services, you control both the backup and restore of all virtual machines (VMs) for your infrastructure directly from the Veeam console.

Service charges are incurred only if you choose to use the service.
{: note}

## Veeam Availability Suite
{: #shared_veeam-portal}

The Veeam Availability Suite has visibility to back up VMs from any virtual data center in the organization. It is available at the VMware® vCloud Director organization level for any vCloud Director user with the **Organization Administrator** role.

When you use the Veeam self-service portal to create backup jobs, you can choose vApp and VM instances from any virtual data center in the organization.

You can access the Veeam portal on the virtual data center details page when the virtual data center is in the **Ready to use** state. For more information, see [Procedure to view the virtual data center summary](/docs/vmwaresolutions?topic=vmwaresolutions-shared_viewing-vdc-summary#shared_viewing-vdc-summary-procedure) or [Procedure to view virtual data center details](/docs/vmwaresolutions?topic=vmwaresolutions-shared_viewing-vdc-details#shared_viewing-vdc-details-procedure).

You must contact {{site.data.keyword.IBM}} Support to restore a backup of your data. For more information, see [Contacting IBM Support](/docs/vmwaresolutions?topic=vmwaresolutions-trbl_support).
{: note}

### Procedure to access the Veeam self-service portal from the virtual data center
{: #shared_veeam-portal-proc-access}

1. Under **Recommended services** on the virtual data center details page, click **Veeam Backups**.
2. Use a user with the Organization Administrator role to log in to the Veeam self-service portal. A newly provisioned virtual data center's **admin** user has the role by default.

For more information about generating the vCloud Director console credentials, see [Procedure to access the vCloud Director Management console](/docs/vmwaresolutions?topic=vmwaresolutions-shared_accessing-vcd-console#shared_accessing-vcd-console-procedure).

Alternatively, click the menu under the user in the upper right of the vCloud Director tenant portal and select **Veeam Backup**.
{: note}

### Limitations for Veeam Availability Suite
{: #shared_veeam-portal-limitations}

* For the Veeam **application aware image processing** and **guest file system indexing** options to work for Windows® VMs, the most recent VMware® Tools must be installed on the VMs. Linux® VMs do not support application awareness or guest file system indexing.
* If you are using **application aware image processing** for MS SQL or Oracle DB backups, the options **application aware** and **Item** restore are not supported. The restore operation needs to complete a full VM restore, which requires a downtime window for any consumers of the database.

### Licenses and fees for Veeam Availability Suite
{: #shared_veeam-portal-fees}

Veeam usage incurs on-demand charges. For more information, see [VMware Solutions Shared pricing](/docs/vmwaresolutions?topic=vmwaresolutions-shared_pricing).

### Backup data storage and encryption
{: #shared_veeam-storage}

For more information about how Veeam Availability Suite stores backups, see [How is your data stored and encrypted in the VMware Solutions Shared Veeam Availability Suite service](/docs/vmwaresolutions?topic=vmwaresolutions-data-security-mng-data#data-security-data-veeamshared).

## Veeam Cloud Connect Replication
{: #shared_veeam-cloud-connect}

Veeam Cloud Connect Replication provides seamless replication of your workloads from on-premises to {{site.data.keyword.cloud_notm}}. Use Veeam Cloud Connect as disaster recovery for failover during on-premises outages or to permanently move workloads directly to {{site.data.keyword.cloud_notm}}.

Starting with the 4.2 release, VMware Solutions Shared virtual data centers provide Veeam Backup and Replication V11 for the Veeam Cloud Connect Replication ready-to-use service. For more informaiton about compatibility requirements between Veeam service providers and tenants, see [Product Versions in Veeam Cloud Connect Infrastructure](https://helpcenter.veeam.com/docs/backup/cloud/cloud_connect_versions.html?ver=110).
{: note}

When you access Veeam Cloud Connect, **DNS name** and **Port** details are specific to the region where your virtual data center exists.

| {{site.data.keyword.cloud_notm}} data center location | DNS name   | Port |
|:-------------------------------|:----------|:------|
| Dallas | ``dalvccgw.vmware-solutions.cloud.ibm.com`` | ``6180``|
| Frankfurt | ``fravccgw.vmware-solutions.cloud.ibm.com`` | ``6180`` |
{: caption="Table 1. Virtual data center region details" caption-side="top"}

### Procedure to connect to Veeam Cloud Connect for replication
{: #shared_veeam-cloud-connect-proc-access}

1. Add your service provider to your Veeam Backup and Replication Server: [Connecting to Service Providers](https://helpcenter.veeam.com/docs/backup/cloud/cloud_connect_sp.html?ver=100){: external}
   * For **Step 2: Specify Cloud Gateway Settings**, use the **DNS name** and **Port** details that are specific to your virtual data center region. You can locate your **DNS name** and **Port** details on the virtual data center details page. Scroll down to the **Recommended services** pane and locate **Connection Details** for Veeam Cloud Connect.  
   * For **Step 3: Verify TLS Certificate and Specify User Account Settings**, use the following credentials:  
    *Organization\Username* or *Username@Organization*  
    For example: `OrganizationName\admin` Or `admin@OrganizationName`  
    An on-premises Veeam Backup and Replication Server connecting to {{site.data.keyword.cloud_notm}} must validate the revocation status of the {{site.data.keyword.vmwaresolutions_short}} SSL certificate that is provided by DigiCert. You must have **admin** privileges.  
2. From your on-premises Veeam Backup and Replication Server, view Veeam Cloud Connect failover plans, perform failovers, or undo failovers from {{site.data.keyword.cloud_notm}}.

### Procedure to access the Veeam Cloud Connect self-service portal from the virtual data center
{: #shared_veeam-cloud-connect-self-service-proc-access}

If you don't have access to your on-premises Veeam Backup and Replication Server, connect to the Veeam Cloud Connect self-service portal. From the portal you can view failover plans, perform failovers, or undo failovers from {{site.data.keyword.cloud_notm}}.

1. Under **Recommended services** on the virtual data center details page, click **Veeam Cloud Connect**. The Veeam Cloud Connect self-service portal login is displayed.
2. Log in to the Veeam Cloud Connect portal.

You must add your organization name as a prefix to your **User** credential to log in to the Veeam Cloud Connect self-service portal. You can locate your organization name under the self-service portal access information under **Veeam Cloud Connect Replication**. For example, `8823e1828b208ef9380b3\admin`.
{: important}

For more information about using Veeam Cloud Connect, see the [Veeam Cloud Connect User Guide](https://helpcenter.veeam.com/docs/backup/cloud/cloud_connect_user_guide.html?ver=100){: external}.

## Deleting Veeam backups
{: #shared_veeam-delete}

Restore points are automatically removed from the Veeam self-service portal when you delete a virtual data center. For more information, see [Deleting virtual data centers](/docs/vmwaresolutions?topic=vmwaresolutions-shared_deletinginstance).

If you remove a vCloud Director virtual data center from your account, all backups and restore points that are associated with the virtual data center are deleted and cannot be recovered. If you remove all vCloud Director virtual data centers in your account, all backup operations are stopped.
{: important}

## Related links
{: #shared_veeam-related}

* [VMware Solutions Shared overview](/docs/vmwaresolutions?topic=vmwaresolutions-shared_overview)
* [Ordering virtual data centers](/docs/vmwaresolutions?topic=vmwaresolutions-shared_ordering)
* [Using Veeam Cloud Connect Portal](https://helpcenter.veeam.com/docs/backup/cloud/cloud_connect_portal_use.html?ver=100){: external}
* [Veeam website](https://www.veeam.com/){: external}
* [Veeam Help Center](https://www.veeam.com/documentation-guides-datasheets.html){: external}
