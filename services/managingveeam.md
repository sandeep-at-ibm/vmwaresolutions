---

copyright:

  years:  2016, 2020

lastupdated: "2020-04-17"

keywords: Veeam console, Veeam backup restore, update Veeam license

subcollection: vmwaresolutions


---

{:external: target="_blank" .external}

# Managing Veeam
{: #managingveeam}

After the service is deployed into your instance, you can access the Veeam console by using Remote Desktop Protocol. With Remote Desktop Protocol, you can manage the backup and restore of all the virtual machines in your environment, including the management components. You can also upgrade the service by downloading and installing the Veeam updates from the Veeam website.

## Accessing the Veeam console by using Remote Desktop Protocol
{: #managingveeam-accessing}

To manage the Veeam service, access the Veeam console by completing the following steps:
1. Use Remote Desktop Protocol to connect to the Windows IP address.
2. Log in to the Windows console by using the Administrator credentials.
3. Access the Veeam console from the Windows console by using the Administrator credentials.

You can find the Windows IP address and the Administrator credentials on the Veeam service details page.

For more information, see [Ordering, viewing, and removing services for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservices).

## Backing up and restoring management components for instances with Veeam installations
{: #managing-veeam-backup-and-replication}

The Veeam service can be configured to back up the management components by using the Veeam console. For more information, see [Backing up components](/docs/vmwaresolutions?topic=vmwaresolutions-solution_backingup).

For instances deployed in (or upgraded to) V1.8 or later releases, the configuration changes to your environment are not automatically backed up. Therefore, before you change the configuration of your environment, it is recommended that you back up the management components manually by running the management backup job in the Veeam console. For more information about backing up manually, see the [Veeam technical instructions](https://helpcenter.veeam.com/backup/vsphere/scheduing_manual.html){:external}.

When failures occur on the management components, you can restore the management components to a previous backup by using the Veeam console. For more information about restoring manually, see the [Veeam technical instructions]( https://helpcenter.veeam.com/backup/vsphere/performing_full_recovery.html){:external}.

## Applying updates to Veeam
{: #managingveeam-updates}

You are responsible for maintaining the Veeam software to keep it updated to the most recent version.

### Applying updates to instances deployed with public and private network
{: #managingveeam-updates-public-private}

If the Veeam service is installed on an instance with public and private network, you can check for and download the updates by using the Veeam software itself.

### Applying updates to instances deployed with private network only
{: #managingveeam-updates-private}

If the Veeam service is installed on an instance with private network only, because the Veeam VSI is configured with no public network access, you cannot check for or download updates by using the Veeam software itself. Instead, you must download updates from the Veeam website, transfer them to the Veeam VM, and then install them.

## Updating Veeam licenses
{: #managingveeam-update-license}

### Updating Veeam licenses for instances deployed with public and private network
{: #managingveeam-update-license-public-private}

If the Veeam service is installed on an instance with public and private network, you can update your Veeam license either automatically or manually by following the Veeam instructions at [Updating license]( https://helpcenter.veeam.com/docs/backup/vsphere/license_update.html){:external}.

### Updating Veeam licenses for instances deployed with private network only
{: #managingveeam-update-license-private}

If the Veeam service is installed on an instance with private network only, you must take note of the expiration date for your license and [contact {{site.data.keyword.IBM}} Support](/docs/vmwaresolutions?topic=vmwaresolutions-trbl_support) to get assistance with updating the license key when the renewal is needed.

## Related links
{: #managingveeam-related}

* [Veeam overview](/docs/vmwaresolutions?topic=vmwaresolutions-veeam_considerations)
* [Managed Backup Services](/docs/vmwaresolutions?topic=vmwaresolutions-managing_veeam_services)
* [VMware Solutions FAQ](/docs/vmwaresolutions?topic=vmwaresolutions-faq-vmwaresolutions)
* [Veeam backup and replication FAQ](/docs/virtualization?topic=Virtualization-faqs-veeam-backup-and-replication)
* [Veeam.com website](https://www.veeam.com/){:external}
* [Veeam technical documentation](https://www.veeam.com/documentation-guides-datasheets.html){:external}
