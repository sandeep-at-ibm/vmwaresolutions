---

copyright:

  years:  2016, 2020

lastupdated: "2020-06-11"

keywords: Veeam console, Veeam backup restore, update Veeam license

subcollection: vmwaresolutions


---

{:external: target="_blank" .external}

# Managing Veeam
{: #managingveeam}

After the service is deployed into your instance, you can access the Veeam console by using Remote Desktop Protocol. With Remote Desktop Protocol, you can manage the backup and restore of all the virtual machines in your environment, including the management components. You can also upgrade the service by downloading and installing the Veeam updates from the Veeam website.

Veeam v10 is installed on newly deployed instances. If you have Veeam v9.5, you can continue to use it. However, you can no longer install Veeam v9.5 on a new instance.

## Tasks you can perform with Veeam v10
{: #managingveeam-fivetasks_v10}

For Veeam v10, there are 5 separate tasks you might perform, depending on what you want to accomplish:
* Order a new vCenter Server instance with Veeam

   A Veeam standalone license is automatically deployed. Veeam service installation only starts after the standalone license was successfully ordered.

   Veeam v10 is installed on either VM or VSI, depending on what you selected.

* Install Veeam on an existing vCenter Server instance

   A Veeam standalone license is automatically deployed. Veeam service installation only starts after the standalone license was successfully ordered.

   Veeam v10 is installed on either VM or VSI depending on what you selected.

* Uninstall Veeam on an existing vCenter Server instance

   If you uninstall an older version of Veeam, for example Veeam v9.5, the license charge for that version is canceled because the license is “attached” to the older version.

   However, if you uninstall Veeam v10, the standalone license instance is not deleted. You must delete the license separately in order to cancel the license charge.

   For more information, see [Managing Veeam licenses](/docs/vmwaresolutions?topic=vmwaresolutions-veeam_managing_licenses).

* Order a new Veeam standalone license

   A SKU in IMS is ordered with the number of VMs to license. A license key is not displayed because no unique keys are generated.

   For more information, see [Managing Veeam licenses](/docs/vmwaresolutions?topic=vmwaresolutions-veeam_managing_licenses).

* Delete a Veeam standalone license

   When you delete a Veeam standalone license, the license charge in IMS is canceled. There is no effect on the Veeam installation.       

   When you want to increase your usage, you should delete your old standalone instance after you order a new instance to avoid unnecessary charges.

   For more information, see [Managing Veeam licenses](/docs/vmwaresolutions?topic=vmwaresolutions-veeam_managing_licenses).

## Considerations for installing and deleting Veeam licenses
{: #managingveeam-install-delete-consid}

This topic provides information about licenses for both Veeam v9.5 and Veeam v10.

The way in which a Veeam license is installed and deleted is different starting with Veeam v10.

Once you place an order for Veeam v10, a Veeam standalone license is automatically deployed for the backend. The Veeam service installation only begins after the standalone license order has successfully completed. After that, the system will install Veeam on either the VM or VSI, depending on what you ordered.

When you uninstall Veeam 10, the standalone license instance is not deleted. You must delete it separately. Otherwise, you will continue to be charged for the license.

You might want to consider this when you plan to upgrade your Veeam usage. You could be charged for licenses for Veeam 9.5, which is deprecated, and for Veeam 10. Therefore, you might decide to order a new license for your Veeam install toward the end of a month, so you aren’t charged for both licenses for most of the month.

If you have an existing Veeam v9.5 install that comes with a license and you want more coverage, you can keep your license that came with the install and order a new license to upgrade usage. Later, if you delete v9.5, you must separately delete any standalone licenses you ordered or you will continue to be charged for them.

Although you can order a new standalone license, we do not recommend "stacking" licenses. For example, if you initially ordered Veeam with 20 VMs and now want coverage for 40 VMs, you should not keep your old license and order a license for 20 VMs. Instead, you should order a license for 40 VMs and delete your original 20 VM license.

When licenses are ordered, the system does not generate a key. We are applying a master key.

## Accessing the Veeam console by using Remote Desktop Protocol
{: #managingveeam-accessing}

To manage the Veeam service, access the Veeam console by completing the following steps:
1. Use Remote Desktop Protocol to connect to the Windows IP address.
2. Log in to the Windows console by using the Administrator credentials.
3. Access the Veeam console from the Windows console by using the Administrator credentials.

You can find the Windows IP address and the Administrator credentials on the Veeam service details page.

For more information, see [Ordering, viewing, and deleting services for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservices).

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

If the Veeam service is installed on an instance with private network only, because the Veeam VSI or VM is configured with no public network access, you cannot check for or download updates by using the Veeam software itself. Instead, you must download updates from the Veeam website, transfer them to the Veeam VM, and then install them.

### Updating Veeam licenses for instances deployed with public and private network
{: #managingveeam-update-license-public-private}

If the Veeam service is installed on an instance with public and private network, you can update your Veeam v9.5 license either automatically or manually. For Veeam v10, you must update your Veeam license automatically. You cannot update it manually. Follow the Veeam instructions at [Updating license]( https://helpcenter.veeam.com/docs/backup/vsphere/license_update.html){:external}.

### Updating Veeam licenses for instances deployed with private network only
{: #managingveeam-update-license-private}

If the Veeam service is installed on an instance with private network only, you must take note of the expiration date for your license and [contact {{site.data.keyword.IBM}} Support](/docs/vmwaresolutions?topic=vmwaresolutions-trbl_support) to get assistance with updating the license key when the renewal is needed.

### Known issue about license key message for automatic updating
{: #managingveeam-known-issue-message}

On the Veeam v10 console, when you’re automatically updating a license before it expires, you might see a "License key is up-to-date" message that looks like an error. There is no error and you can ignore the message.

## Related links
{: #managingveeam-related}

* [Veeam v9.5 overview](/docs/vmwaresolutions?topic=vmwaresolutions-veeam_considerations)
* [Veeam v10 overview](/docs/vmwaresolutions?topic=vmwaresolutions-veeamvm_overview)
* [Ordering Veeam](/docs/vmwaresolutions?topic=vmwaresolutions-veeam_ordering)
* [Ordering Veeam licenses](/docs/vmwaresolutions?topic=vmwaresolutions-veeam_ordering_licenses)
* [Managing Veeam licenses](/docs/vmwaresolutions?topic=vmwaresolutions-veeam_managing_licenses)
* [Ordering and configuring IBM Cloud Object Storage with Veeam](/docs/vmwaresolutions?topic=vmwaresolutions-icos_ordering)
* [VMware Solutions FAQ](/docs/vmwaresolutions?topic=vmwaresolutions-faq-vmwaresolutions)
* [Veeam backup and replication](https://www.ibm.com/cloud/architecture/architectures/virtualization_backup_veeam){:external}
* [Veeam backup and replication FAQ](https://www.veeam.com/availability-suite-faq.html){:external}
* [Veeam.com website](https://www.veeam.com/){:external}
* [Veeam technical documentation](https://www.veeam.com/documentation-guides-datasheets.html){:external}
