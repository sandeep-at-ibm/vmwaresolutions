---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-19"

---

# VCSA update and SSO-linked vCenters

## VCSA update

VUM does not update the VCSA. The following information describes the process of updating this appliance. The VCSA deployed in a VMware vCenter Server on {{site.data.keyword.cloud}} instance has no internet access, so the update bundle must be downloaded to a jump-server first.

The VCSA is updated via appliance management console, not the vSphere Web Client. The VCSA appliance management console is accessed by using a browser, the VCSA IP address, and port 5480.

You must initiate a snapshot of the appliance or a backup of the VCSA before you update. Ensure that everything works as expected, then remove the snapshot within a few days, to avoid performance degradation. Additionally, review the release notes before you attempt any upgrade.

To update the VCSA, follow these steps:
1. You can download updates by going to the VMware Patch [Download Center](https://my.vmware.com/group/vmware/patch#search), logging in and choosing VC from the **Search by Product** menu. Select the appropriate patch and click **Download**.
2. Using the vSphere Web Client, upload the ISO file to the vCenter datastore repository.
3. Mount the update ISO file to the vCenter server.
4. Take a snapshot of your vCenter server.
5. Log in to vCenter appliance management console at: `https://vcenterip:5480`
6. Go to the **Update** section and select **Check Updates** and then **Check CDROM**. The update is listed.
7. Select **Install Updates** and **Accept** the EULA. The update installs.
8. After the update is complete, you must go back to the appliance management console and select to restart the console.
9. Log back into the vSphere Web Client and check for any errors. Complete a manual scan of VUM, **Home** > **Hosts and Cluster**, then select a datacenter or cluster and select **Update Manager tab** and then click **Scan for Updates**. If the manual scan results in an error, see [Resetting VMware Update Manager database on a vCenter Server appliance 6.5 (2147284)](https://kb.vmware.com/s/article/2147284).
10. After testing, if you need to back out, revert to snapshot or restore the vCenter with a previous backup.

## SSO-linked vCenters

If you have primary and secondary vCenter Server instances, then your VCSAs are configured to be in a single vCenter Single Sign-On (SSO) domain. Each VCSA has a deployed VUM instance. The configuration properties that you modify are applied only to the VUM instance that you specify and are not propagated to the other instances in the group.

You can specify a VUM instance by selecting the name of the VCSA with which the VUM instance is registered from the navigation bar. You can also manage baselines, baseline groups, scan, and remediate only the inventory objects that are managed by the VCSA with which the VUM instance is registered.

### Related links

* [VMware HCX on {{site.data.keyword.cloud_notm}} Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (demonstrations)
