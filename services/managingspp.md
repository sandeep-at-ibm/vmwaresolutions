---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-15"

---

# Managing IBM Spectrum Protect Plus on IBM Cloud

## Accessing the IBM Spectrum Protect Plus management console

To manage the IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud}} service, you must access the IBM Spectrum Protect Plus management console by completing the following steps:
1. Use the {{site.data.keyword.cloud_notm}} infrastructure VPN or a jump server to allow access to the IP address of the IBM Spectrum Protect Plus virtual machine. You can find the IP address on the service details page for IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} in the {{site.data.keyword.vmwaresolutions_short}} console.
2. To access the IBM Spectrum Protect Plus management console, click **View IBM Spectrum Protect Plus Console** on the service details page for IBM Spectrum Protect Plus on {{site.data.keyword.cloud}}, and then log in by using the credentials listed on the same service details page.

## Applying fixes for IBM Spectrum Protect Plus on IBM Cloud

You are responsible for maintaining the IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} service to the most recent version. You can download the required updates from the [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} Support](https://www.ibm.com/mysupport/s/topic/0TO50000000IQWtGAO/spectrum-protect-plus) page.

For more information, see the following topics:
* [Ordering and removing services for Cloud Foundation instances](../sddc/sd_addingremovingservices.html)
* [Ordering and removing services for vCenter Server instances](../vcenter/vc_addingremovingservices.html)

## Updating the operating system of the IBM Spectrum Protect Plus virtual machine

To update the operating system of the IBM Spectrum Protect Plus virtual machine, you must log in as the **root** user. The **root** user password is the same as the password that you can find on the service details page for IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}.

## Backing up and restoring management components for instances that have IBM Spectrum Protect Plus on IBM Cloud installed

 **Note**: The following information applies to IBM Spectrum Protect Plus installations on instances deployed in (or upgraded to) V2.3 or later. For V2.2 instances, this service provides data protection for the workload virtual machines only.

The IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} service is preconfigured with a management backup job that automatically runs to back up the following management components daily with up to seven points of restoration:
* VMware vCenter Server
* Platform Services Controller (PSC)
* IBM CloudDriver
* **Cloud Foundation instances only**: VMware SDDC Manager
* **vCenter Server instances with HA AD/DNS only**: High-availability pair of AD/DNS

If failures occur on the management components, you can open a ticket by [contacting IBM Support](../vmonic/trbl_support.html) to request the management components to be restored to a previous backup.

## Related links

* [Components and considerations for IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](spp_considerations.html)
* [How to increase vsnap storage for IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} post deployment](https://developer.ibm.com/recipes/tutorials/how-to-increase-vsnap-storage-for-ibm-spectrum-protect-plus-on-ibm-cloud-post-deployment/)
* [Ordering Cloud Foundation instances](../sddc/sd_orderinginstance.html)
* [Ordering vCenter Server instances](../vcenter/vc_orderinginstance.html)
* [IBM Spectrum Protect Plus documentation](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html)
