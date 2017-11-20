---

copyright:

  years:  2016, 2017

lastupdated: "2017-11-10"

---

# Ordering vSphere clusters based on existing configurations

You can order a VMware vSphere cluster based on a configuration template that you saved. Use this procedure to define a new cluster configuration based on an existing cluster configuration.

## Requirements

Ensure that you completed the following tasks:
*  You configured the{{site.data.keyword.cloud}} infrastructure credentials on the **Settings** page. For more information, see [User accounts and settings](../vmonic/useraccount.html).
*  You meet the requirements and you reviewed the considerations in [Requirements and planning for vSphere clusters](vs_planning.html).

## Procedure

1. Click **Getting Started** or **Order Instance** from the left navigation pane.
2. On the **vSphere Cluster** card, click **Order Instance**. Ensure that you are on the **Create new cluster** tab.
3. Select the configuration template that you saved from the **Cluster Configurations** list and review the cluster settings that are automatically filled in, such as the domain name, the selected VMware components and their settings, bare metal servers, and the network details.
4. Enter a new cluster name.
5. Review and update the settings of the cluster according to your requirements and click **Next**.
6. On the **Summary** page, verify the cluster configuration before you place the order.
   1. Review the settings for the cluster.
   2. Click the link or links of the terms that apply to your order, and ensure that you agree with these terms before you continue.
   3. Review the estimated cost of the cluster by clicking the price link under **Estimated Cost**. To save or print your order
   summary, click the **Print** or **Download** icon on the upper right of the PDF window.
   4. To save the cluster configuration as a new template without placing an order, click **Save Configuration**.
   5. To place the order, click **Place Order**.

## Results

If you saved the cluster configuration as a template, you get a console notification that the configuration was saved. You can then find the template in the **Cluster Configurations** list on the **Basics** page.

If you placed an order, the deployment of the cluster starts automatically, and you receive an email confirmation that the order is being processed. When the cluster is ready to use, you are notified by email.

## Related links

* [Ordering new vSphere clusters](vs_orderinginstances.html)
* [Scaling existing vSphere clusters](vs_scalingexistingclusters.html)
* [Scaling clusters created outside of the console](vs_orderingforclustersoutside.html)
