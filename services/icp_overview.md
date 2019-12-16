---

copyright:

  years:  2016, 2019

lastupdated: "2019-12-12"

keywords: IBM Cloud Private

subcollection: vmware-solutions


---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# IBM Cloud Private Hosted - Deprecated
{: #icp_overview}

The {{site.data.keyword.cloud}} Private Hosted service is deprecated. Use the [Red Hat OpenShift for VMware](/docs/services/vmwaresolutions?topic=vmware-solutions-ocp_overview) service instead.
{:deprecated}

The {{site.data.keyword.cloud_notm}} Private Hosted service automatically deploys {{site.data.keyword.cloud_notm}} Private Hosted and {{site.data.keyword.cloud_notm}} Automation Manager on your VMware vCenter Server instances. This service brings the power of microservices and containers to your VMware environment on {{site.data.keyword.cloud_notm}}. With this service, you can extend the same familiar VMware and {{site.data.keyword.cloud_notm}} Private operational model and tools from on-premises into the {{site.data.keyword.cloud_notm}}.
{: shortdesc}

## Resource requirements for IBM Cloud Private Hosted
{: #icp_overview-resource-req}

The following table lists the resource requirements of the {{site.data.keyword.cloud_notm}} Private Hosted service in Production-Ready environment.

| Node type  | CPU cores   |  Memory (GB) | Disk 1 (GB) | Disk 2 (GB) | Number of VMs |
|:---------- |:----------- |:------------ |:----------- |:----------- |:------------- |
| Boot       | 12 | 24 | 100 | 1 | 1 |   
| Management | 8 | 64 | 500 | 3 | 3 |
| Master     | 8 | 64 | 200 | 3 | 3 |  
| Proxy      | 2 | 4  | 150 | 3 | 3 |
| Worker     | 4 | 16 | 200 | 300 | 6 |
| Vulnerability advisor | 8 | 16 | 500 | 1 | 1 |
| GlusterFS  | 8 | 16 | 150 | 50 | 3 |
| NFS server | 8 | 4  | 350 | 1 | 1 |
| NSX Edge Services Gateway | 2 | 1 | 0.5 | 0.5 | 2 |
| Documented constraints | 52 | 640 |  | 8,000 |   |
{: caption="Table 1. Production-Ready environment" caption-side="top"}

The following table lists the resource requirements of the {{site.data.keyword.cloud_notm}} Private Hosted service in the Development and Test environments.

| Node type  | CPU cores   |  Memory (GB) | Disk 1 (GB) | Disk 2 (GB) | Number of VMs |
|:---------- |:----------- |:------------ |:----------- |:----------- |:------------- |
| Boot       | 12 | 24 | 100 | 1 | 1 |   
| Management | 8 | 16 | 150 | 1 | 1 |
| Master     | 8 | 16 | 200 | 1 | 1 |  
| Proxy      | 2 | 4  | 150 | 1 | 1 |
| Worker     | 4 | 16 | 200 | 300 | 3 |
| Vulnerability advisor | 8 | 16 | 150 | 1 | 1 |
| GlusterFS  | 8 | 16 | 150 | 50 | 3 |
| NFS server | 8 | 4  | 350 | 1 | 1 |
| NSX Edge Services Gateway | 2 | 1 | 0.5 | 0.5 | 2 |
| Documented constraints | 30 | 200 |  | 4,000 |  |
{: caption="Table 2. {{site.data.keyword.cloud_notm}} Development and Test environments" caption-side="top"}

## Deploying additional nodes
{: #icp_overview-deploy-nodes}

If you want to deploy additional nodes, review the following information:
* Use the {{site.data.keyword.cloud_notm}} Private Ubuntu template (Ubuntu1604) that is deployed with your initial {{site.data.keyword.cloud_notm}} Private Hosted installation.
* To find the Ubuntu template, in the VMware vSphere Web Client, go to the **VMs and Templates** tab, under the `cam` folder.
* The default password for the Ubuntu template is `icponcloud`. It is recommended that you change this password before you use the template.
* {{site.data.keyword.vmwaresolutions_short}} does not offer support for applying updates and patches for the Ubuntu template. You must monitor and apply these updates yourself.

## Considerations when you remove IBM Cloud Private Hosted
{: #icp_overview-remove}

* Only the virtual machines (VMs) that were deployed during the initial installation of the {{site.data.keyword.cloud_notm}} Private Hosted service are deleted. Any node that is deployed after the installation will not be cleaned up.
* {{site.data.keyword.cloud_notm}} will delete the VXLAN, DLR, and the Edge Gateway that was created during the initial deployment of {{site.data.keyword.cloud_notm}} Private Hosted. The VMs that you deployed on VXLAN will lose connectivity after the removal of the {{site.data.keyword.cloud_notm}} Private Hosted service is started.

## Related links
{: #icp_overview-related}

* [Open a Ticket for {{site.data.keyword.cloud_notm}} Private](https://www.ibm.com/mysupport/s/?language=en_US){:external}
* [{{site.data.keyword.cloud_notm}} Automation Manager licensing](https://www.ibm.com/support/knowledgecenter/en/SS2L37_3.1.2.0/licensing.html){:external}
* [{{site.data.keyword.cloud_notm}} Automation Manager components](https://www.ibm.com/support/knowledgecenter/en/SS2L37_3.1.2.0/cam_managed_components.html){:external}
* [Contacting IBM Support](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support)
* [FAQ](/docs/services/vmwaresolutions?topic=vmware-solutions-faq)
