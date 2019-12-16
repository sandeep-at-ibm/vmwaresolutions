---

copyright:

  years:  2016, 2019

lastupdated: "2019-12-12"

keywords: HCX updates, HCX management console, login HCX console

subcollection: vmware-solutions


---

{:external: target="_blank" .external}


# Managing VMware HCX
{: #managinghcx}

## Accessing the HCX management consoles
{: #managinghcx-accessing-consoles}

To manage the HCX service, you must access the HCX Cloud Console or the HCX Manager Admin Console:
1. Use the {{site.data.keyword.cloud}} infrastructure VPN or a jump server to allow access to the IP address of the HCX Manager virtual appliance (HCX Manager). You can find the IP address on the HCX service details page in the {{site.data.keyword.vmwaresolutions_short}} console.
2. To access the HCX Cloud Console, click **View HCX Cloud Console** on the HCX service details page, and then log in by using the vCenter Server credentials.
3. To access the HCX Manager Admin Console, click **View HCX Manager Admin Console** on the HCX service details page, and then log in by using the HCX Manager credentials listed on the same service details page.

For more information, see [Ordering, viewing, and removing services for vCenter Server instances](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservices).

## Applying updates to HCX
{: #managinghcx-updates}

HCX is deployed with the latest tested build of VMware Hybrid Cloud Extension technology. VMware ships updates to these builds regularly, which include important fixes and new features. These builds are pushed to HCX installations automatically, including on-premises HCX installations.

To apply any maintenance fixes pushed to your environment, you must use the HCX Manager Admin Console in your on-premises data center and your vCenter Server instance.

If you do not see a build update that you are expecting, if you have problems with HCX, or if want to have the latest HCX build pushed to your system immediately, open a support ticket by following the steps in [Contacting IBM Support](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support).

## Related links
{: #managinghcx-related}

* [HCX overview](/docs/services/vmwaresolutions?topic=vmware-solutions-hcx_considerations#hcx_considerations)
* [Glossary of HCX terms](/docs/services/vmwaresolutions?topic=vmware-solutions-hcx_glossary)
* [VMware Hybrid Cloud Extension overview](https://cloud.vmware.com/vmware-hcx){:external}
* [VMware Hybrid Cloud Extension documentation](https://cloud.vmware.com/vmware-hcx/resources){:external}
