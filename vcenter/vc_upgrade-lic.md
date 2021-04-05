---

copyright:

  years:  2016, 2021

lastupdated: "2021-03-18"

keywords: NSX license upgrade, upgrade license hybridity, hybridity license

subcollection: vmwaresolutions

---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:help: data-hd-content-type='help'}
{:support: data-reuse='support'}

# Upgrading licenses for vCenter Server with NSX-V instances
{: #vc_upgrade-lic}

You can upgrade your VMware NSX® license for V2.1 or later instances.

## Procedure to upgrade your NSX license
{: #vc_upgrade-lic-nsx}
{: help}
{: support}

This procedure applies to instances that are deployed in V2.1 or later. For instances that are deployed in V2.0 and earlier, you must upgrade the VMware NSX® license manually.

You can upgrade the NSX license for your instance to a later edition. License edition downgrades are not supported.

1. From the {{site.data.keyword.vmwaresolutions_full}} console, click **Resources** from the left navigation pane.
2. In the **vCenter Server instances** table, click the instance to upgrade the NSX license for.
3. On the **Summary** page, verify that all instance details are displayed correctly. Then, click **Infrastructure** on the left navigation pane to verify the details on the **Infrastructure** page.

   If the details are not displayed, this might indicate a connectivity problem with the IBM CloudDriver Virtual Server Instance (VSI), as a result of a firewall rule or a networking issue. Resolve the problem before you continue with the next step, otherwise the upgrade might fail.

4. Click **Licensing** on the left navigation pane and click **Upgrade** in the **License upgrades** table. In the **Upgrade NSX license edition** window, select the edition that you want to upgrade to and click **Upgrade**.

   The license upgrade replaces all existing NSX licenses on the instance. Additional charges can be incurred from an overlap of old and new licenses if you upgrade in the middle of a billing cycle. To avoid additional charges, it is recommended to upgrade the license at the end of the billing cycle.
   {:note}

## Related links
{: #vc_upgrade-lic-related}

* [Contacting IBM Support](/docs/vmwaresolutions?topic=vmwaresolutions-trbl_support)
* [FAQs](/docs/vmwaresolutions?topic=vmwaresolutions-faq-vmwaresolutions)
