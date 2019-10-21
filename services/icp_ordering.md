---

copyright:

  years:  2016, 2019

lastupdated: "2019-09-25"

keywords: IBM Cloud Private Hosted, ICP configuration, order Cloud Private

subcollection: vmware-solutions


---

# Ordering IBM Cloud Private Hosted
{: #icp_ordering}

You can order the {{site.data.keyword.cloud}} Private Hosted service when you order a new instance with the service included or by adding the service to your existing instance.

## Ordering IBM Cloud Private Hosted for a new instance
{: #icp_ordering-new}

You can order a new instance with the {{site.data.keyword.cloud_notm}} Private Hosted service included by using one of the following methods:
* From the {{site.data.keyword.vmwaresolutions_short}} console, when you order a new instance, click **IBM Cloud Private Hosted** under the **Hosting** category in the **Optional Services** section.
* From the {{site.data.keyword.cloud_notm}} catalog, click the **VMware** icon on the left navigation pane, and then click **IBM Cloud Private Hosted** on the **App Modernization** card in the **Services** section. Specify the service settings and select **Add to New Instance**.

## Ordering IBM Cloud Private Hosted for an existing instance
{: #icp_ordering-existing}

You can add the {{site.data.keyword.cloud_notm}} Private Hosted service into an existing instance by using one the following methods:
* From the {{site.data.keyword.vmwaresolutions_short}} console, view the instance that you want to add the service for, click **Services** on the left navigation pane, and then click **Add**.
* From the {{site.data.keyword.cloud_notm}} catalog, click the **VMware** icon on the left navigation pane, and then click **IBM Cloud Private Hosted** on the **App Modernization** card in the **Services** section. Specify the service settings and select **Add to Existing Instance**.

## IBM Cloud Private Hosted service configuration
{: #icp_ordering-config}

When you order the service, provide the following settings:
* Select **Production-Ready** or **Development/Test** according to your needs.
* Select the required check box to certify that you have already obtained the license that is required to deploy the {{site.data.keyword.cloud_notm}} Private Hosted service.

## Deploying additional nodes
{: #icp_ordering-deploy-nodes}

If you want to deploy additional nodes, review the following information:
* Use the {{site.data.keyword.cloud_notm}} Private Ubuntu template (Ubuntu1604) that is deployed with your initial {{site.data.keyword.cloud_notm}} Private Hosted installation.
* To find the Ubuntu template, in the VMware vSphere Web Client, go to the **VMs and Templates** tab, under the `cam` folder.
* The default password for the Ubuntu template is `icponcloud`. It is recommended that you change this password before you use the template.
* {{site.data.keyword.vmwaresolutions_short}} does not offer support for applying updates and patches for the Ubuntu template. You must monitor and apply these updates yourself.

## Related links
{: #icp_ordering-related}

* [IBM Cloud Private Hosted overview](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_overview)
* [Ordering, viewing, and removing services for vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [Ordering, viewing, and removing services for vCenter Server with Hybridity Bundle instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)
* [Contacting IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [FAQ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
