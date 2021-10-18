---

copyright:

  years:  2016, 2021

lastupdated: "2021-10-13"

keywords: NSX license, upgrade license, Hybridity license

subcollection: vmwaresolutions


---

{{site.data.keyword.attribute-definition-list}}

# Upgrading NSX licenses for vCenter Server with Hybridity Bundle instances
{: #vc_hybrid_upgrade-lic}

You can upgrade the VMware NSX® license for your instance to a later edition. Reverting the license to an earlier edition is not supported.

## Procedure to upgrade your NSX license
{: #vc_hybrid_upgrade-lic-nsx}

1. From the {{site.data.keyword.vmwaresolutions_full}} console, click **Resources** from the left navigation pane.
2. In the **vCenter Server instances** table, click the instance to upgrade the NSX license for.
3. On the **Summary** page, verify that all instance details are displayed correctly. Then, click **Infrastructure** on the left navigation pane to verify the details on the **Infrastructure** page.

   If the details are not displayed, a connectivity problem might occur with the {{site.data.keyword.IBM}} 
	CloudDriver Virtual Server Instance (VSI), as a result of a firewall rule or a networking issue. Resolve the problem before you with the next step, otherwise the upgrade might fail.

4. Click **Licensing** on the left navigation pane and click **Upgrade**. In the **Upgrade NSX license edition** window, select the edition that you want to upgrade to and click **Upgrade**.

   The license upgrade replaces all existing NSX licenses on the instance. Additional charges might be incurred from an overlap of old and new licenses if you upgrade in the middle of a billing cycle. To avoid additional charges, it is recommended to upgrade the license at the end of the billing cycle.
   {: note}

## Related links
{: #vc_hybrid_upgrade-lic-related}

* [vCenter Server with Hybridity Bundle overview](/docs/vmwaresolutions?topic=vmwaresolutions-vc_hybrid_overview#vc_hybrid_overview)
* [Contacting IBM Support](/docs/vmwaresolutions?topic=vmwaresolutions-trbl_support)
* [FAQs](/docs/vmwaresolutions?topic=vmwaresolutions-faq-vmwaresolutions)
