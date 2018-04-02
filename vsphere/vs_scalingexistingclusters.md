---

copyright:

  years:  2016, 2018

lastupdated: "2018-03-27"

---

# Scaling existing vSphere clusters

You can scale out an existing VMware vSphere cluster that you ordered or saved in the {{site.data.keyword.vmwaresolutions_full}} console by adding ESXi servers or ordering an HA-pair of FortiGate 300 series Security Appliance for it.

## Requirements

Ensure that you completed the following tasks:
*  You configured the {{site.data.keyword.cloud_notm}} infrastructure credentials on the **Settings** page. For more information, see [User accounts and settings](../vmonic/useraccount.html).
*  You meet the requirements and you reviewed the considerations in [Requirements and planning for vSphere clusters](vs_planning.html).

## Procedure

1. Click **Getting Started** on the left navigation pane.
2. On the **VMware vSphere on IBM Cloud** card, click **Order Instance**.
3. On the **Basics** page, click the **Scale existing cluster** tab.
4. Select the cluster you want to scale from the **Cluster Configurations** list.
5. Review the cluster settings, which are automatically filled in, such as the cluster name, the selected VMware components and their settings, and the network details.
6. Select the number of {{site.data.keyword.baremetal_short}} that you want to add to the cluster.
7. If the cluster does not include the HA-pair of FortiGate 300 series Security Appliance on its public VLAN, you can order one for it
by selecting **Include with purchase** under **FortiGate Physical Appliance 300 Series HA Pair**.
8. Click **Next**.
9. On the **Summary** page, verify the cluster configuration before you place the order.
   1. Review the settings for the cluster.
   2. Click the link or links of the terms that apply to your order, and ensure that you agree with these terms before you order the
   cluster.
   3. Review the estimated cost of the cluster by clicking the price link under **Estimated Cost**. To save or print your order
   summary, click the **Print** or **Download** icon on the upper right of the PDF window.
   4. Click **Create**.

## Results

The scale cluster deployment starts automatically, and you receive an email confirmation that the order is being processed. When the cluster is ready to use, you are notified by email.

**Note:** The vSphere clusters are not displayed on the **Deployed Instances** page, together with the vCenter Server and Cloud Foundation instances.

## Related links

* [Ordering new vSphere clusters](vs_orderinginstances.html)
* [Ordering vSphere clusters based on existing configurations](vs_orderingbasedonexistingconfig.html)
* [Scaling clusters created outside of the console](vs_orderingforclustersoutside.html)
