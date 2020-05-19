---

copyright:

  years:  2016, 2020

lastupdated: "2020-04-07"

subcollection: vmwaresolutions


---

{:external: target="_blank" .external}

# Troubleshooting
{: #opsprocs-trouble}

To troubleshoot your vCenter Server instance issues, your system administrators must identify the symptoms of the issue, determine which of the solution components are affected, research, and propose a fix or workaround, and test the fix.

* Identifying Symptoms - A number of potential causes might lead to the under-performance or non-performance of your instance. The first step in efficient troubleshooting is to identify exactly what is going wrong. These symptoms might be reported from: vSphere events and alarms, Operations Management in 	{{site.data.keyword.cloud}} or reported via your Service Desk from one of your users.
* Isolating the affected components - After you have identified the symptoms of the issue, you must identify the software or hardware components that are affected and might be causing the issue and those components that are not involved. Tools such as vCenter Operations Management in {{site.data.keyword.cloud_notm}} assist with this step.
* Proposing a fix or workaround - Once you understand the symptoms and have isolated the components, you can research possible fixes and workarounds. Your system administrators also use the {{site.data.keyword.cloud_notm}} Portal, including the troubleshooting scenarios in this document, IBM ServiceNow, and VMware Knowledgebase. In addition, there are many wikis and blogs that might help. For even quicker resolutions, Operations Management in {{site.data.keyword.cloud_notm}} includes a number of remediations for identified issues.
* Testing Possible Solutions - When you know what the symptoms of the issue are, which components are involved and have proposed a fix/workaround, your system administrators test the solutions systematically until the issue is resolved.

vSphere includes a user-configurable events and alarms subsystem, which tracks events that occur throughout the vSphere environment and stores the data in log files and the vCenter database. This subsystem also enables system administrators to specify the conditions under which alarms are triggered. Alarms change state from warnings to more serious alerts as system conditions change, and can trigger automated alarm actions such as to email the system administrator team. This functionality is useful when you want to be informed, or take immediate action, when certain events or conditions occur for a specific inventory object, or group of objects.

More tools such as those incorporated into the Operations Management on {{site.data.keyword.cloud_notm}} architecture provide greater assistance with; identifying symptoms, isolating the affected components and proposing a fix or workaround.

## Guidelines
{: #opsprocs-trouble-guidelines}

The following guidelines are considered best practices for troubleshooting your {{site.data.keyword.vmwaresolutions_short}} issue:
* Approach troubleshooting and problem-solving systematically.
* Are the symptoms related to; availability, utilization, or configuration:
 *  Availability - These symptoms relate to the availability of hardware and software components and are typified by a no response. Often high availability design masks these issues so that they do not impact your workloads and users directly.
 * Utilization - These symptoms relate to capacity and performance and are typified by slow-running or in-ability to load. Proactively managing capacity drastically reduces these issues.
 * Configuration - These issues are typically discovered in the provision of new services or a result to applying a change. Incorrect settings can surface as either availability or utilization symptoms. For example, an incorrect IP address is displayed as an availability issue, whereas virtual machine (VM) RAM settings being too low cause utilization symptoms.
* Try to isolate the issue to a component in the environment.
* Take notes so you can trace your steps.
* Understand and document you software versions.
* Document your subnets and IP address usage, including VIP and NAT addresses.
* Have diagrams of your network. You need a number of diagrams that show the physical (underlay) and logical (overlay) layers.
* Understand any recent changes to the environment.
* Research the impact of the fix, do not lock yourself out of any management interfaces.
* Ensure that you have backups of all key components in case they need to be reloaded or reset.
* Do not change more than one thing at a time.
* Document each change and its result.
* When you open a support request, ensure that you document carefully and provide pertinent information. Be clear in the symptoms that you are seeing and identify the components that you believe are  faulty. Ensure that you use the correct terminology. Try to minimize any confusion or ambiguity in your choice of words.
* vSphere ESXi and vCenter Server configuration files control the behavior of the system, understand where they are. Most configuration file settings are set during installation, but can be modified after installation.
* Log files capture messages that are generated by the kernel and different subsystems and services. vSphere ESXi and vCenter services maintain separate log files. Understand where they are located and how they can be accessed.
* Understand how to use popular system administration tools for help in diagnostics.

For more information, see [Troubleshooting Guidelines KB0012073](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=4a205910dbe0f7c06001327e9d96197b){:external}.

## Troubleshooting with log files
{: #opsprocs-trouble-logs}

Log files are an excellent source of information to troubleshoot issues. However, the number of log files and the vast amount of entries in each log make it difficult to diagnose. [Troubleshooting with Log Files KB0012074](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=c74f91d0dbe4f7c06001327e9d9619b1){:external} details where these log files are located in the VMware environment. Due to the number of log files and the vast number of entries in each log, you should consider the tooling in the Operations Management on {{site.data.keyword.cloud_notm}} to help capturing and analyzing event logs.

## Troubleshooting common scenarios
{: #opsprocs-trouble-common}

In an aid to isolating the affected components, this documentation on troubleshooting common scenarios has been classified into the following:

* Virtual machines - these troubleshooting topics provide guidance to potential issues on VMs.
* Hosts  - these troubleshooting topics provide guidance on vSphere ESXi host issues.
* Storage - these troubleshooting topics provide guidance on resolving vSAN and NFS storage issues.
* Network - these troubleshooting topics provide guidance on resolving network issues.
* vCenter - these troubleshooting topics provide guidance on resolving vCenter issues.
* Licenses - these troubleshooting topics provide guidance on resolving license issues. These typically relate to clients who have brought their own licenses to {{site.data.keyword.cloud_notm}}.

| Title | Description |
|---|---|
| Generic VM troubleshooting | For more information, see [Troubleshooting Virtual Machines](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-EE645240-83CA-4F9E-B2F7-BECE864982C3.html){:external}. |
| VM performance issues | For information about troubleshooting the symptoms of VM performance issues, including guest OS boots slowly, applications perform poorly, applications take a long time to launch, or applications become unresponsive, see [Troubleshooting ESX/ESXi virtual machine performance issues (2001003)](https://kb.vmware.com/s/article/2001003){:external}. |
| Recover orphaned VM | For information about recovering orphaned VMs, which are VMs that exist in the vCenter database, but are not recognized by the vSphere ESXi host, see [Knowledge - KB0012862 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=57c90b74dbdd7300c4fa302f9d96199e){:external}. |
| VM does not power on | For more information, see [Troubleshooting a virtual machine that is unable to power on (2001005)](https://kb.vmware.com/s/article/2001005){:external}. |
| VM does not power on after cloning or deploying from a template | [VMware article](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-2742CE14-20FD-416F-B89C-A156053A973F.html){:external} looks at issues that affect a VM after it has been cloned or deployed from a template. |
| VMware Tools are outdated or not installed - VMware Tools should be installed on the VMs and kept up-to-date. | [IBM Cloud KB0012161](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=797afaf0dbb477486001327e9d9619e6){:external} provides guidance on these tasks. |
| Old VM network devices | If VM network devices are not kept up-to-date network performance and application performance might be impacted. For more information about deploying a new virtual network device and driver, see [Choosing a network adapter for your virtual machine (1001805)](https://kb.vmware.com/s/article/1001805){:external}. |
| Virtual Machine Memory Limit | Memory limits are often used. However, if a guest OS cannot access the memory it needs, the applications inside the guest OS might perform poorly. For more information about resolving the issue, see [Configuring Resource Allocation Settings](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.resmgmt.doc/GUID-14102AB7-2CF9-42E3-9642-3EB6629EF530.html){:external}. |
| VM snapshots | While snapshots are useful, the quantity and age of a VM's snapshots directly impact the performance of the VM. For information about resolving the issue, see [Consolidate Snapshots](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-2F4A6D8B-33FF-4C6B-9B02-C984D151F0D5.html){:external}. |
| VM logging | If logging has not been configured correctly the capacity of the datastore might be adversely impacted. For information about resolving the issue, see [Configuring Logging Levels for the Guest Operating System](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.monitoring.doc/GUID-F465D340-6556-49E8-B137-C0B4A060E83B.html){:external}. |
| Troubleshooting network connection issues | Symptoms can include VM fails to connect to the network, or no network connectivity to or from a single VM. For information about resolving the issue, see [Troubleshooting virtual machine network connection issues (1003893)](https://kb.vmware.com/s/article/1003893?CoveoV2.CoveoLightningApex.getInitializationData=1&r=2&ui-communities-components-aura-components-forceCommunity-seoAssistant.SeoAssistant.getSeoData=1&other.KM_Utility.getArticleDetails=1&other.KM_Utility.getArticleMetadata=2&other.KM_Utility.getUrl=1&other.KM_Utility.getUser=1&other.KM_Utility.getAllTranslatedLanguages=2&ui-comm-runtime-components-aura-components-siteforce-qb.Quarterback.validateRoute=1){:external}.  |
| Determining whether multiple virtual CPUs are causing performance issues  | For information about troubleshooting VMs experiencing performance issues when they are configured with multiple CPUs, see [Determining if multiple virtual CPUs are causing performance issues (1005362)](https://kb.vmware.com/s/article/1005362?CoveoV2.CoveoLightningApex.getInitializationData=1&r=2&ui-communities-components-aura-components-forceCommunity-seoAssistant.SeoAssistant.getSeoData=1&other.KM_Utility.getArticleDetails=1&other.KM_Utility.getArticleMetadata=2&other.KM_Utility.getUrl=1&other.KM_Utility.getUser=1&other.KM_Utility.getAllTranslatedLanguages=2&ui-comm-runtime-components-aura-components-siteforce-qb.Quarterback.validateRoute=1){:external}. These issues can include poor transfer speeds when copying data to or from a VM, backup jobs timeout or very slow, or a VM performs poorly.  |
| A VM was powered off or restarted  | For information about resolving the issue, see [Determining why a virtual machine was powered off or restarted (1019064)](https://kb.vmware.com/s/article/1019064?CoveoV2.CoveoLightningApex.getInitializationData=1&r=2&ui-communities-components-aura-components-forceCommunity-seoAssistant.SeoAssistant.getSeoData=1&other.KM_Utility.getArticleDetails=1&other.KM_Utility.getArticleMetadata=2&other.KM_Utility.getUrl=1&other.KM_Utility.getUser=1&other.KM_Utility.getAllTranslatedLanguages=2&ui-comm-runtime-components-aura-components-siteforce-qb.Quarterback.validateRoute=1){:external}. |
| One or more of your VMs has a poor response time |  For information about isolating a performance issue on a vSphere ESXi host, see [Troubleshooting ESX/ESXi virtual machine performance issues (2001003)](https://kb.vmware.com/s/article/2001003?lang=en_US){:external}. Performance issues can be caused by CPU constraints, memory over commitment, storage latency, or network latency. |
{: caption="Table 1. Virtual machine troubleshooting" caption-side="bottom"}
{: summary="This table has row and column headers. The row headers identify the potential issues. The column headers identify the description of the guidance on resolving the issues. To find the guidance on resolving a certain issue, navigate to the row, and then find the information in the description column."}
{: #table1}
{: tab-title="Virtual machines"}
{: tab-group="Troubleshooting common scenarios"}
{: class="comparison-tab-table"}
{: row-headers}

| Title | Description |
|---|---|
| ESXI Commands | For an overview of the command‐line interfaces in vSphere, the ESXi Shell commands, and the vCLI (VMware® vSphere Command‐Line Interface) commands, see [Getting Started with vSphere Command-Line Interfaces](https://vdc-download.vmware.com/vmwb-repository/dcr-public/bc4fa31a-40ac-4aa9-a6a1-7171d1fff7f4/740990ee-4d65-4627-a9d4-0f046cb78aec/vsphere-esxi-vcenter-server-67-command-line-interface-getting-started-guide.pdf){:external}. |
| vSphere HA Host States | If vCenter reports a vSphere HA host state that indicates an error condition on the host, these need to be remediated as this issue can prevent vSphere HA from restarting VMs after a failure. For more information, see [Troubleshooting vSphere HA Host States](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-DF7CEF44-98EC-458A-8614-50CCAEC0A7C5.html){:external}. |
| vSphere ESXi host is in a non-responding state | For information about troubleshooting a vSphere ESXi host that shows as Not Responding, Disconnected, or the VMs on the host show as unavailable in vCenter, see [ESX/ESXi hosts do not respond and is grayed out (1019082)](https://kb.vmware.com/s/article/1019082){:external}. |
| When powering on a VM, you see a `File not found` error | For information about re-creating a lost virtual disk descriptor file (VMDK), see [Re-creating a missing virtual machine disk descriptor file (1002511)](https://kb.vmware.com/s/article/1002511){:external}. |
| VM Performance issues | For information about isolating a performance issue on a vSphere ESXi host, see [Troubleshooting ESX/ESXi virtual machine performance issues (2001003)](https://kb.vmware.com/s/article/2001003?lang=en_US){:external}. Performance issues can be caused by CPU constraints, memory over commitment, storage latency, or network latency. |
| Bare Metal Server is down | If the bare metal server running vSphere ESXi is unresponsive or down then log on to the {{site.data.keyword.cloud_notm}} management UI or console and check the status. If required, open a case to get assistance with your bare metal server. For more information, see [Working with support cases](/docs/get-support?topic=get-support-open-case#open-case){:external}. |
| vSphere ESXi host is in disconnected or a not responding state  | For more information, see [Troubleshooting an ESXi/ESX host in non responding state (1003409)](https://kb.vmware.com/s/article/1003409?lang=en_US){:external}. |
| Purple screen of death  | The Purple Screen of Death (PSOD) is a kernel panic and the vSphere ESXi kernel (vmkernel) triggers this safety measure in response to an event or error that is unrecoverable and would mean that continuing to run would pose a high risk for the services and VMs. When the panic occurs and the vSphere ESXi host crashes, it ends all the services running on it together with all the VMs hosted. The VMs are not gracefully shut down, but rather abruptly powered off. If the host is part of a cluster and you configured HA, these VMs are restarted on the other hosts in the cluster. For more information, see [Knowledge - KB0012864 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=dd5d2330db11f300c4fa302f9d96198d){:external}. |
{: caption="Table 2. Typical vSphere ESXi hosts troubleshooting" caption-side="bottom"}
{: summary="This table has row and column headers. The row headers identify the potential issues. The column headers identify the description of the guidance on resolving the issues. To find the guidance on resolving a certain issue, navigate to the row, and then find the information in the description column."}
{: #table2}
{: tab-title="Hosts"}
{: tab-group="Troubleshooting common scenarios"}
{: class="comparison-tab-table"}
{: row-headers}

| Title | Description |
|---|---|
| Storage troubleshooting | For more information about slow performance, unpredictable failures, disk corruption, or VM corruption, see [Troubleshooting storage issues when using VMware products (2013160)](https://kb.vmware.com/s/article/2013160?lang=en_US){:external}. |
| vSAN troubleshooting | For more information, see [Failure Handling in vSAN](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-monitoring.doc/GUID-35A4B700-6640-4519-A885-440A1AE8D3BD.html){:external}.  |
| vSAN Disk Failure | For more information about how to identify a specific disk failure in a vSAN deduplication cluster, see [Identifying specific disk failure in a vSAN deduplication cluster (2149067)](https://kb.vmware.com/s/article/2149067){:external}. |
| Clear vSAN health issues | In the VMware vSphere Web Client Monitor page, you might see alerts and warnings that relate to vSAN Health issues. For information about clearing these issues, see [Virtual SAN Health alerts and warnings](/docs/vmwaresolutions?topic=vmwaresolutions-trbl_vsan_alerts#trbl_vsan_alerts){:external}.|
| vSAN rebalance | If disks report errors in the health check indicating that the cluster is imbalanced and there are disks that are high on space usage while others are low, and you should run a proactive rebalance. This manually initiates a rebalance of the objects in a vSAN cluster. For more information about vSAN proactive rebalance and when it might be applicable, see [vSAN proactive rebalance (2149809)](https://kb.vmware.com/s/article/2149809){:external}. |
| Initiate vSAN health test | If you suspect there is an issue with vSAN, you can initiate a health test to verify that the cluster components are working as expected. Running the VM creation test creates a VM on each host in the cluster and then deletes it. If these tasks are successful, then the cluster components are working as expected and the cluster is functional. Then, network performance test is used to detect and diagnose connectivity issues, and to ensure that the network bandwidth between the hosts is adequate. For more information, see [Proactive Tests](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-monitoring.doc/GUID-B88B5900-33A4-4821-9659-59861EF70FB8.html){:external}. |
| Monitoring vSAN performance | For more information, see [Monitoring vSAN Performance](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-monitoring.doc/GUID-3D2D1382-9DDC-44D4-AF3B-ACA4F1DDBDCC.html){:external}. Performance charts are available for clusters, hosts, physical disks, VMs, and virtual disks. |
| vSAN troubleshooting | For more information, see [Handling Failures and Troubleshooting vSAN](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-monitoring.doc/GUID-0F3C4D3F-9B86-4879-9C60-D6A977523112.html){:external}. |
{: caption="Table 3. Typical storage troubleshooting" caption-side="bottom"}
{: summary="This table has row and column headers. The row headers identify the potential issues. The column headers identify the description of the guidance on resolving the issues. To find the guidance on resolving a certain issue, navigate to the row, and then find the information in the description column."}
{: #table3}
{: tab-title="Storage"}
{: tab-group="Troubleshooting common scenarios"}
{: class="comparison-tab-table"}
{: row-headers}

| Title | Description |
|---|---|
|  NSX Edge /var/log is getting full on active Edge | For information about a workaround if you are alerted that the Edge disk is filling up and discover that the /var/log partition is getting full, see [NSX Edge /var/log is getting full on active Edge (50108355)](https://kb.vmware.com/s/article/50108355){:external}.  |
| Testing HCX bandwidth  | For information about using `perftest` to find the available bandwidth within the HCX tunnels if you believe that you have a network bandwidth issue with HCX, see [Steps to Run Perftest in HCX (56211)](https://kb.vmware.com/s/article/56211?lang=en_US){:external}. Bidirectional tests are carried out for each `perftest`. For the pair of gateways, one is inside the source data center (on-premises), and the other one is in {{site.data.keyword.cloud_notm}}. The way `perftest` throughput works is to have the sender try to send as fast as the link can sustain. Therefore, for each test, you see a higher "sender" rate than the "receiver" rate. You can consider the "receiver" rate value as a one-way throughput result. |
| HCX troubleshooting | For more information, see [HCX troubleshooting](/docs/vmwaresolutions?topic=vmwaresolutions-hcxclient-troubleshooting). |
| HCX Syncing state with 0% progress and 0 bytes with status Error | For more information, see [HCX replication are in Syncing state with 0% progress and 0 bytes with status Error (56710)](https://kb.vmware.com/s/article/56710?lang=en_US#q=HCX){:external}. |
| Poor VM network performance | Review the VM virtual NIC settings. VMware recommends VMXNET 3 virtual NICs for VMs as it is the latest generation of paravirtualized NICs designed for performance. Check for compatibility of VMXNET 3 using the VMware compatibility list, and if supported change the virtual NIC for additional network performance. For more information, see [Troubleshooting Networking](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.networking.doc/GUID-217384C2-B361-471D-90C8-BC2676A0ECA6.html){:external}. |
{: caption="Table 4. Typical network troubleshooting" caption-side="bottom"}
{: summary="This table has row and column headers. The row headers identify the potential issues. The column headers identify the description of the guidance on resolving the issues. To find the guidance on resolving a certain issue, navigate to the row, and then find the information in the description column."}
{: #table4}
{: tab-title="Network"}
{: tab-group="Troubleshooting common scenarios"}
{: class="comparison-tab-table"}
{: row-headers}

| Title | Description |
|---|---|
| Virtual Machine Console Access | For more information, see [Knowledge - KB0012863 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=5446a73cdb1db300c4fa302f9d961934){:external}. |
| New vCenter Server Certificate Does Not Appear to Load | After the replacement of the default vCenter Server certificates, the new certificates might not appear to load. For more information, see [New vCenter Server Certificate Does Not Appear to Load](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-415CF843-42E8-4AD7-98EC-7265227337B6.html){:external}. |
| vCenter Server Cannot Connect to Managed Hosts | After the replacement of the default vCenter Server certificates and restarting the system, vCenter Server cannot connect to managed hosts. For more information, see [vCenter Server Cannot Connect to Managed Hosts](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-8D3DCEC4-50B6-4523-BF24-0DE6C65600E9.html){:external}. |
| Cannot Configure vSphere HA When Using Custom SSL Certificates | After the installation of custom SSL certificates, attempts to enable vSphere High Availability (HA) fail. For more information, see [Cannot Configure vSphere HA When Using Custom SSL Certificates](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-3FC16DC8-7157-4340-AB8A-B8DC87D7DC0F.html){:external}. |
{: caption="Table 5. Typical vCenter troubleshooting" caption-side="bottom"}
{: summary="This table has row and column headers. The row headers identify the potential issues. The column headers identify the description of the guidance on resolving the issues. To find the guidance on resolving a certain issue, navigate to the row, and then find the information in the description column."}
{: #table5}
{: tab-title="vCenter"}
{: tab-group="Troubleshooting common scenarios"}
{: class="comparison-tab-table"}
{: row-headers}

| Title | Description |
|---|---|
|  Incompatible or incorrect license configuration | For more information, see [Troubleshooting Host Licensing](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-B9DAAF47-94EC-47F5-8523-9C8C019412E1.html){:external}. |
|  VM does not power on | There might be a license issue if you can't power on a VM on a vSphere ESXi host and you receive the ``The 60-day evaluation period of the host is expired or the license of the host is expired`` message. For more information, see [Unable to Power On a Virtual Machine](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-D4770546-9F9A-4F1E-AC1C-CF313E6130F4.html){:external}. |
| A feature is unavailable or inability to change a configuration  | For more information, see [Unable to Configure or Use a Feature](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-26C0E2F0-A581-4A5A-B1F7-2BA4F151E27A.html){:external}.  |
{: caption="Table 6. Typical license troubleshooting" caption-side="bottom"}
{: summary="This table has row and column headers. The row headers identify the potential issues. The column headers identify the description of the guidance on resolving the issues. To find the guidance on resolving a certain issue, navigate to the row, and then find the information in the description column."}
{: #table6}
{: tab-title="Licenses"}
{: tab-group="Troubleshooting common scenarios"}
{: class="comparison-tab-table"}
{: row-headers}

**Next topic**: [Compliance](/docs/vmwaresolutions?topic=vmwaresolutions-opsprocs-compliance)

## Related links
{: #opsprocs-trouble-links}

* [Contacting IBM Support](/docs/vmwaresolutions?topic=vmwaresolutions-trbl_support#trbl_support)
* [vSphere troubleshooting overview](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-C70D5A5E-7D84-446C-B8CE-0766AA7351A4.html){:external}
* [vSphere troubleshooting with logs](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-552CC9E8-441C-434A-88FC-3F50881245D7.html){:external}
* [Operations management on {{site.data.keyword.cloud_notm}}](/docs/vmwaresolutions?topic=vmwaresolutions-opsmgmt-intro)
* [Support log gathering](https://kb.vmware.com/s/article/1010705){:external}
* [Monitoring events, alarms, and automated actions](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.monitoring.doc/GUID-9272E3B2-6A7F-427B-994C-B15FF8CADC25.html){:external}
* [vSphere System Log files](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.monitoring.doc/GUID-DABCB024-E083-4A4D-8AE0-D1AF4CB3800C.html){:external}
* [Considerations about changing vCenter Server artifacts](/docs/vmwaresolutions?topic=vmwaresolutions-vcenter_chg_impact#vcenter_chg_impact)
