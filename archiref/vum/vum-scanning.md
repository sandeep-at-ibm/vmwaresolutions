---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-01"

---

# Scanning and review

When you scan hosts, virtual machines (VMs), and virtual appliances, you evaluate them against baselines and baseline groups to determine their level of compliance. Inventory objects are scanned, and the results are reviewed to determine how they comply with the baselines and baseline groups. Scan results can be filtered by text search, group selection, baseline selection, and compliance status selection. You can initiate the following scans:
*	**Manually Initiate a Scan of vSphere ESXi Hosts** - You can scan vSphere ESXi hosts in the vSphere inventory against attached baselines and baseline groups.
*	**Manually Initiate a Scan of Virtual Machines and Virtual Appliances** - You can scan VMs and virtual appliances in the vSphere inventory against attached baselines and baseline groups.
*	**Manually Initiate a Scan of a Container Object** - Start a simultaneous scan of hosts, VMs, and virtual appliances, by scanning a container object that is a data center or a data center folder.
*	**Schedule a Scan** - You can configure the vSphere Web Client to scan VMs, virtual appliances, and ESXi hosts at specific times or at intervals that are convenient for you.

## Manually initiating a scan of vSphere ESXi hosts

1. Click **Scan for Updates**, select **Patches and Extensions and Upgrades**, then click **OK**.
2. When the scan completes, select **Critical Host Patches**. In the lower pane, review the patch details for each host by clicking the number in **Number of Patches**. A window shows the patch information.
3. Review and repeat for **Non-Critical Patches**.

  The VUM log files are located at _/var/log/vmware/vmware-updatemgr/vum-server/vmware-vum-server-log4cpp.log_

## Manually initiating a scan of virtual machines and virtual appliances

You can scan VMs and virtual appliances in the vSphere inventory against attached baselines and baseline groups. The VMs and appliances that you select are scanned against the attached baselines, depending on the options that you select. All child objects are also scanned, so the larger the virtual infrastructure and the higher up in the object hierarchy that you initiate the scan, the longer the scan takes and the more accurate the compliance view is.

1.	Using the vSphere Web Client, select **Home** > **VMs and Templates**.
2.	Right-click a _virtual machine_, _virtual appliance_, or a _folder of virtual machines and appliances_ and click **Scan for Updates**.
3.	Select the types of updates to scan for. The options are _Virtual Appliance upgrades, VM Hardware upgrades_, and _VMware Tools upgrades_.
4.	Click **Scan**.

##	Manually Initiating a scan of a container object

Start a simultaneous scan of hosts, VMs, and virtual appliances, by scanning a container object that is a data center or a data center folder.
1.	Using the vSphere Web Client, select **Home** > **VMs and Templates**.
2.	Right-click a _datacenter_ or _datacenter folder_ and click **Scan for Updates**.
3.	Select the types of updates to scan for. The options are _Virtual Appliance upgrades, VM Hardware upgrades_, and _VMware Tools upgrades_.
4.	Click **Scan**.

##	Scheduling a scan

You can configure the vSphere Web Client to scan VMs, virtual appliances, and vSphere ESXi hosts at specific times or at intervals that are convenient for you.

1.	Using the vSphere Web Client select an object from the inventory. All child objects of the object that you select are also scanned.
2.	Select the **Monitor tab** and click **Task & Events**.
3.	Select **Scheduled Tasks** and click **Schedule a New Task**.
4.	Select **Scan for Updates** from the drop-down list that appears. The Scan for Updates wizard opens.
5.	On the Edit Settings page, select the types of updates to scan the inventory object for. You must select at least one scan type. On the Scheduling options page, describe and schedule the scan task.
6.	Enter a unique name, and optionally, a description for the scan task. Click **Change** to set the frequency and the start time for the scan task. Click **OK**.
7.	The scan task is listed in the Scheduled Tasks view of the vSphere Web Client.

### Related links

* [VMware HCX on 	{{site.data.keyword.cloud}} Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on 	{{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (Demos)
