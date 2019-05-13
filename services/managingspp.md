---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-28"

subcollection: vmware-solutions


---

# Managing IBM Spectrum Protect Plus on IBM Cloud
{: #managingspp}

## Accessing the IBM Spectrum Protect Plus management console
{: #managingspp-console}

To manage the {{site.data.keyword.IBM}} Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} service, you must access the IBM Spectrum Protect Plus management console by completing the following steps:
1. Use the {{site.data.keyword.cloud_notm}} infrastructure VPN or a jump server to allow access to the IP address of the IBM Spectrum Protect Plus virtual machine (VM). You can find the IP address on the service details page for IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} in the {{site.data.keyword.vmwaresolutions_short}} console.
2. To access the IBM Spectrum Protect Plus management console, click **View IBM Spectrum Protect Plus Console** on the service details page for IBM Spectrum Protect Plus on {{site.data.keyword.cloud}}, and then log in by using the credentials listed on the same service details page.

## Applying updates to IBM Spectrum Protect Plus on IBM Cloud
{: #managingspp-updates}

You are responsible for maintaining IBM Spectrum Protect Plus to keep it updated to the most recent version. You can download the required updates from the [IBM Spectrum Protect Plus Support](https://www.ibm.com/mysupport/s/topic/0TO50000000IQWtGAO/spectrum-protect-plus){:new_window} page.

For more information, see [Ordering, viewing, and removing services for vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices).

## Updating the operating system of the IBM Spectrum Protect Plus VM
{: #managingspp-update-os}

To update the operating system of the IBM Spectrum Protect Plus VM, you must log in as the **root** user. The **root** user password is the same as the password from the service details page for IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}.

## Related links
{: #managingspp-related}

* [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} overview](/docs/services/vmwaresolutions/services?topic=vmware-solutions-spp_considerations){:new_window}
* [How to increase vsnap storage for IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} post deployment](https://developer.ibm.com/recipes/tutorials/how-to-increase-vsnap-storage-for-ibm-spectrum-protect-plus-on-ibm-cloud-post-deployment/){:new_window}
* [How to configure IBM Spectrum Protect Plus to offload to IBM Cloud Object Storage](https://developer.ibm.com/recipes/tutorials/how-to-configure-ibm-spectrum-protect-plus-to-offload-to-ibm-cloud-object-storage/){:new_window}
* [IBM Spectrum Protect Plus documentation](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html){:new_window}
