---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-05"

---

#	Orchestrated upgrades

You can use orchestrated upgrades to upgrade the virtual hardware and VMware Tools of virtual machines in the inventory after the updating the vSphere ESXi hosts. After the hosts are updated, the VMware Tools upgrade baseline runs first, followed by the virtual machine hardware upgrade baseline. Orchestrated upgrades can be performed at a cluster, folder, or a data center level.

VUM allows you to perform orchestrated upgrades of hosts and then virtual machines by using baseline groups. A baseline group is used that contains a single host upgrade baseline and multiple patch or extension baselines. VUM first upgrades the hosts and then applies the patch or extension baselines. You perform an orchestrated upgrade of virtual machines by using a virtual machine baseline group that contains the following baselines:
* VM Hardware Upgrade to Match Host
* VMware Tools Upgrade to Match Host

VUM orchestrated upgrades allow you to upgrade the inventory objects in VCSA in a two-step process. First, the vSphere ESXi hosts are upgraded followed by the virtual machine upgrades. This two-step process can be configured on a cluster level or you can configure this at the individual vSphere ESXi host or virtual machine level for more granular control.

In the orchestrated upgrade, the cluster is remediated first against the host baseline group, which applies patches, extensions and upgrades and once upgraded, the virtual machines in the cluster are remediated against the virtual machine upgrade baseline group containing the VM Hardware Upgrade to Match Host and VMware Tools Upgrade to Match Host baselines.

If the baseline group also contains an upgrade baseline, VUM first upgrades the vSphere ESXi hosts and then applies the patch and/or extension baselines as the patches are applicable to the specific host version. For the virtual machines, VMware tools are first updated, followed by the virtual hardware update.

Therefore, during the VMware tools upgrade, the virtual machines are powered on if virtual machines are in a powered-off or suspended state, then VUM will power it on, run the upgrade and restore the original power state of the virtual machine. Therefore, during the virtual hardware upgrade, the VMs must be in powered-off state if there are virtual machines that are powered on, VUM will shut them down, upgrade virtual hardware, and power it back on.

By default, the remediation of vSphere ESXi hosts happens in sequential manner and will remediate one host at a time. When the process is completed for one host, VUM will start remediating the next host. This default can be changed to enable parallel remediation so that more than one host can be remediated at a time, however, this is only possible if you have adequate failover capacity in your cluster.

If the vSphere ESXI hosts are part of a vSAN cluster, the remediation process is always sequential even if you have selected parallel remediation in the remediation wizard, as only one host from a vSAN cluster can be in maintenance mode at any time. VUM is intelligent and carries out a calculation on how many hosts can be remediated in parallel without disrupting DRS settings.

Alternatively, you can define the limit for number of hosts that can be remediated in parallel during the remediation wizard.

The following workflow describes the process to perform an orchestrated upgrade:

## Step 1

1. Use the vSphere Web Client to log in to the VCSA.
2. Select **Home** > **Update Manager**, from the **Objects tab**, select an **Update Manager instance**.
3. Click the **Manage tab**, then the **Host Baselines tab** and click **New Baseline Group**.
4. Enter a unique name for the baseline group and click **Next**.
5. Select a host upgrade baseline to include it in the baseline group.
6. Optionally, create a new host upgrade baseline by clicking **Create a new Host Upgrade Baseline** at the bottom of the Upgrades page, and complete the New Baseline wizard. Click **Next**.
7. Select the patch baselines that you want to include in the baseline group.
8. Optionally, create a new patch baseline by clicking **Create a new Host Patch Baseline** at the bottom of the Patches page, and complete the New Baseline wizard. Click **Next**.
9. Select the extension baselines to include in the baseline group.
10. Optionally, create a new extension baseline by clicking **Create a new Extension Baseline** at the bottom of the Patches page, and complete the New Baseline wizard.
11. Review the Ready to Complete page, click **Finish** and the host baseline group is displayed in the Baseline Groups pane.

## Step 2

1. Create a virtual machine baseline group, containing the VMware Tools Upgrade to Match Host baseline and the VM Hardware Upgrade to Match Host baseline, VUM Administration view.
2. Attach the baseline group to an vCenter container object containing the virtual machines that you want to upgrade.
3. Scan the container object to view the compliance state of the virtual machines in the container. You can start the scan manually or schedule a scan task.
4. Review the scan results displayed in the VUM Client Compliance view.
5. Remediate the non-compliant virtual machines in the container object to make them compliant with the attached baseline group. You can start the remediation manually or schedule a remediation task.
* During an upgrade of VMware Tools, the virtual machines must be powered on. If a virtual machine is in a powered off or suspended state before remediation, VUM powers on the machine. After the upgrade is completed, VUM restarts the machine and restores the original power state of the virtual machine.
* During a virtual machine hardware upgrade, the virtual machines must be shut down. After the remediation is completed, VUM restores the original power state of the virtual machines. If a virtual machine is powered on, VUM powers off the machine, upgrades the virtual hardware, and then powers on the virtual machine.

You can now use these baseline groups in the scan, review, staging, and remediate processes.

### Related links

* [VMware HCX on IBM Cloud Solution](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on IBM Cloud Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (Demos)
