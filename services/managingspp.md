---

copyright:

  years:  2016, 2019

lastupdated: "2019-10-07"

keywords: SPP management console, apply SPP updates, login SPP console

subcollection: vmware-solutions


---

{:external: target="_blank" .external}

# Managing IBM Spectrum Protect Plus
{: #managingspp}

## Accessing the IBM Spectrum Protect Plus management console
{: #managingspp-console}

To manage the {{site.data.keyword.IBM}} Spectrum Protect&trade; Plus service, you must access the IBM Spectrum Protect Plus management console by completing the following steps:
1. Use the {{site.data.keyword.cloud_notm}} infrastructure VPN or a jump server to allow access to the IP address of the IBM Spectrum Protect Plus virtual machine (VM). You can find the IP address on the service details page for IBM Spectrum Protect Plus in the {{site.data.keyword.vmwaresolutions_short}} console.
2. To access the IBM Spectrum Protect Plus management console, click **View IBM Spectrum Protect Plus Console** on the service details page for IBM Spectrum Protect Plus, and then log in by using the credentials listed on the same service details page.

## Applying updates to IBM Spectrum Protect Plus
{: #managingspp-updates}

You are responsible for maintaining IBM Spectrum Protect Plus to keep it updated to the most recent version. Download the required updates from [IBM Spectrum Protect Plus Support](https://www.ibm.com/mysupport/s/topic/0TO50000000IQWtGAO/spectrum-protect-plus){:external}.

For more information, see [Ordering, viewing, and removing services for vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices).

## Updating the operating system of the IBM Spectrum Protect Plus VM
{: #managingspp-update-os}

To update the operating system of the IBM Spectrum Protect Plus VM, you must log in as the **root** user. The **root** user password is the same as the password from the service details page for IBM Spectrum Protect Plus.

## Related links
{: #managingspp-related}

* [IBM Spectrum Protect Plus overview](/docs/services/vmwaresolutions/services?topic=vmware-solutions-spp_considerations){:new_window}
* [How to increase vsnap storage for IBM Spectrum Protect Plus post deployment](https://developer.ibm.com/recipes/tutorials/how-to-increase-vsnap-storage-for-ibm-spectrum-protect-plus-on-ibm-cloud-post-deployment/){:external}
* [How to configure IBM Spectrum Protect Plus to offload to {{site.data.keyword.cloud_notm}} Object Storage](https://developer.ibm.com/recipes/tutorials/how-to-configure-ibm-spectrum-protect-plus-to-offload-to-ibm-cloud-object-storage/){:external}
* [IBM Spectrum Protect Plus documentation](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html){:external}
