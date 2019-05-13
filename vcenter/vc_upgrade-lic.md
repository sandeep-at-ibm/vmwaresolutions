---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-30"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Upgrading licenses for vCenter Server instances
{: #vc_upgrade-lic}

You can upgrade your VMware vCenter Server instances to vCenter Server with Hybridity Bundle only if your instance is at V2.3 or later.

IBM Business Partner users do not have the option to upgrade to the Hybridity Bundle.
{:note}

## Before you upgrade your license to Hybridity Bundle
{: #vc_upgrade-lic-upgrade-prereq}

Review the following actions that are taken when you upgrade to the Hybridity Bundle:

* If your vCenter Server instance has the VMware NSX Base edition installed, your NSX license will be automatically upgraded to the NSX Advanced edition.
* If your vCenter Server instance has NFS storage, you will not be charged for VMware vSAN storage. However, you will be charged for the vSAN license that is included with the Hybridity Bundle.

## Procedure to upgrade to Hybridity Bundle (V2.3 or later instances)
{: #vc_upgrade-lic-procedure-upgrade-to-hybridity}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. In the **vCenter Server Instances** table, click the instance to upgrade to Hybridity Bundle.
3. On the **Summary** page, verify that all instance details are displayed correctly. Then click **Infrastructure** on the left navigation pane to verify the details on the **Infrastructure** page.

   If the details are not displayed, this might indicate a connectivity problem with the IBM CloudDriver VSI, as a result of a firewall rule or other networking issue. Resolve the problem before continuing with the next step, otherwise the upgrade might fail.

4. Click **Update and Patch** on the left navigation pane.
5. To apply the Hybridity Bundle license upgrade, in the **License Upgrades** table, click **Upgrade** in the **Action** column. Review the estimated cost and click **Upgrade**.
6. Optionally, you can deploy the VMware HCX on {{site.data.keyword.cloud_notm}} service. When the Hybridity Bundle is enabled in the **License Upgrades** table, complete the following steps:
  1. In the **License Upgrades** table, click **Deploy HCX on {{site.data.keyword.cloud_notm}}** in the **Action** column.
  2. Scroll to the **HCX on {{site.data.keyword.cloud_notm}}** card and click **Select Service**.
  3. Scroll down and specify the required settings for the service and click **Next**.
  4. Review the terms that apply to the service, review the estimated cost, and click **Place Order**.

## Procedure to upgrade your NSX license (V2.1 or later instances)
{: #vc_upgrade-lic-nsx}

This procedure applies to instances that are deployed in V2.1 or later. For instances that are deployed in V2.0 and earlier, you must upgrade the NSX license manually.

You can upgrade the NSX license for your instance to a later edition. License edition downgrades are not supported.

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. In the **vCenter Server Instances** table, click the instance to upgrade the NSX license for.
3. On the **Summary** page, verify that all instance details are displayed correctly. Then click **Infrastructure** on the left navigation pane to verify the details on the **Infrastructure** page.

   If the details are not displayed, this might indicate a connectivity problem with the IBM CloudDriver Virtual Server Instance (VSI), as a result of a firewall rule or a networking issue. Resolve the problem before continuing with the next step, otherwise the upgrade might fail.

4. Click **Update and Patch** on the left navigation pane and click **Upgrade**. In the **Upgrade NSX License Edition** window, select the edition that you want to upgrade to and click **Upgrade**.

   The license upgrade replaces all existing NSX licenses on the instance. Additional charges may be incurred from an overlap of old and new licenses if you upgrade in the middle of a billing cycle. To avoid additional charges, it is recommended to upgrade the license at the end of the billing cycle.
   {:note}

## Related links
{: #vc_upgrade-lic-related}

* [vCenter Server with Hybridity Bundle overview](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_hybrid_overview#vc_hybrid_overview)
* [Contacting IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [FAQs](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
