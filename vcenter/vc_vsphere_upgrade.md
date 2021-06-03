---

copyright:

  years:  2016, 2021

lastupdated: "2021-06-03"

keywords: vSphere upgrade, NSX upgrade, PSC upgrade

subcollection: vmwaresolutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Upgrading vCenter Server vSphere software from VMware vSphere 6.5 to 6.7
{: #vc_vsphere_upgrade}

The VMware vCenter Server® offering is a fully automated deployment solution for the VMware vSphere® SDDC stack. It includes vSphere, VMware NSX®, and optionally vSAN™ products. While vCenter Server automates the most challenging parts of deploying, expanding, and contracting a VMware SDDC-based infrastructure, it is not a managed service.

vCenter Server has a policy of supporting the automation of VMware® SDDC software versions within the range of N-1. If you want to continue to benefit from the {{site.data.keyword.vmwaresolutions_full}} automation, you must upgrade existing instances of vCenter Server.

If your vCenter Server instance is at a version lower than the version level that is needed for automation support, it continues to be supported as required by the VMware support policy. However, your instance might not function with the current {{site.data.keyword.vmwaresolutions_short}} automation.

You must apply patches and upgrade the VMware software periodically, over the lifecycle of a vCenter Server instance. This maintenance includes upgrading the VMware SDDC software to a version that is supported by the {{site.data.keyword.vmwaresolutions_short}} automation.

The following procedure provides the steps that are required to convert a VMware vSphere 6.5-based instance to a VMware vSphere 6.7-based instance. These steps provide the initial upgrade to vSphere, NSX, and vSAN 6.7. After this upgrade, you might need to use the normal vSphere functions to upgrade virtual machine (VM) hardware levels and tools.

vCenter Server is designed to allow for a “rolling” upgrade. That is, VM workloads that are currently functioning continue to function without an outage if you complete the following procedure. Enterprises must engage their change management policies to enable a structured and communicated upgrade and plan for contingencies. However, during the upgrade process of certain management functions, such as vCenter Server and NSX Manager, temporary outages of management functions, configuration changes, powering off and on VMs, might be impacted.
{:note}

## Before you begin
{: #vc_vsphere_upgrade-prereq}

The time to complete the upgrade is unknown. It is possible that it might take several maintenance windows to completely upgrade an environment. Running up-leveled and down-leveled versions of the SDDC software is supported by VMware during the upgrade process. However, some functions such as vMotion, maybe limited during this process.

Complete the following requirements before you begin the upgrade:  
* Upgrade any extensions or snap-ins within the vCenter Server environment. Review the following documentation before you plan your upgrade:
  * [VMware vCenter Server 6.7 Update 1b Release Notes](https://docs.vmware.com/en/VMware-vSphere/6.7/rn/vsphere-vcenter-server-67u1b-release-notes.html){:external}
  * [About VMware ESXi Upgrade](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.esxi.upgrade.doc/GUID-65B5B313-3DBB-4490-82D2-A225446F4C99.html){:external}
* Set up vSphere Update Manager (VUM) within your vCenter Server instance to download updates from VMware vSphere. For more information, see [VMware Update Manager introduction](/docs/vmwaresolutions?topic=vmwaresolutions-vum-intro#vum-intro).
* Open a support ticket with the {{site.data.keyword.vmwaresolutions_short}} team to notify them that an upgrade is being planned. The ticket remains open until the instance is registered at the upgraded level in the {{site.data.keyword.vmwaresolutions_short}} console.
* Confirm whether the vCenter Server instance that you are upgrading is linked to another vCenter Server instance as primary or secondary in the {{site.data.keyword.vmwaresolutions_short}} console. All linked instances must have their Platform Services Controllers (PSCs) upgraded first as part of a particular site upgrade.
* Confirm the following requirements for vSAN based instances:
  * Ensure that the vSAN Health tool is enabled and reports no critical errors. If critical errors are present, contact the IBM Support team with the upgrade support ticket ID.
  * Ensure that there is space on each node to handle rebuilding redundancy of vSAN objects in case an VMware ESXi™ host fails to come back up during the upgrade. You might need to either reduce disk usage or add an ESXi host before the upgrade.  
  * Verify whether the overall vSAN volume usage is above 70%. You might need to either reduce disk usage or add an ESXi host before the upgrade.
* Verify that the PSC and vCenter `root` user ID with its credentials are visible on the console. If your vCenter Server instance was initially ordered in V2.5 or later, only the account with `customerroot` access is visible on the console. In this case, contact IBM Support for the **root** user ID password for PSC and vCenter Server.
* Confirm that you have a [My VMware](https://my.vmware.com){:external} user ID for which to download the required binary files to upgrade. If you don't, contact IBM Support with the upgrade support ticket ID.
* Confirm that VUM is configured to reach https://www.vmware.com to download patches. If it can't be configured because of security policies, then you must manually download the most recent patch sets and upload them into VUM. For more information, see [VMware Update Manager introduction](/docs/vmwaresolutions?topic=vmwaresolutions-vum-intro#vum-intro).

### Preparing your jump box
{: #vc_vsphere_upgrade-prereq-jumpbox}

As the {{site.data.keyword.cloud_notm}} client access VPN is limited to 512 Kbps, it is recommended that you take one of the following actions:
* Provision an {{site.data.keyword.cloud_notm}} Windows® 2012-2016 server Virtual Server Instance (VSI).
* Set up a similar Windows VM on a separate vCenter Server environment within the same {{site.data.keyword.cloud_notm}} data center.
This VM is used as a jump box into the vCenter Server instance for the upgrade and it allows you to download the binary files from https://my.vmware.com. While it is possible to place this VM on the vCenter Server instance that is being upgraded, it is not recommended.

Complete the following steps to order a VSI jump box.

Skip the first step if you have a VSI jump box in your environment.
{:note}

1. Order an hourly or monthly VSI from the [{{site.data.keyword.cloud_notm}} infrastructure customer portal](https://control.softlayer.com/){:external}. Order the following attributes:
  * Windows 2012 or 2016 Server Standard
  * 2 CPUs
  * 16 GB of memory
  * 100 GB of disk
  * 1 Gbps public and private uplinks
2. When the VSI is provisioned, configure the {{site.data.keyword.cloud_notm}} Access Control Lists (ACLs) to allow all ingress and egress from the private links and egress only from public. You must use the {{site.data.keyword.cloud_notm}} client access VPN for Remote Desktop Protocol (RDP) sessions into the Windows VSI.
3. RDP into the Windows VSI. Modify its Domain Name System (DNS) settings on the private network adapter to point to only the windows AD server within the vCenter Server instance to upgrade.
4. Download and install the Google Chrome™ browser. Mozilla® Firefox® has a cache issue when using the VUM screens on the vCenter Server user interface.
5. Download your preferred SSH terminal software. For example, `putty`.
6. Use Google Chrome to access the vCenter Server instance to upgrade. Use **administrator@vsphere.local** and ensure that you can view the user interface.  
7. Check the vSphere environment for errors and issues as discussed in the previous section.
8. Use your SSH terminal software to access the PSC and vCenter Server with the portal or support supplied passwords for **root**.
9. Optionally, Use the **root** user ID and password noted in the {{site.data.keyword.cloud_notm}} infrastructure control pane to access each ESXi host to verify the **root** password.

#### Downloading binary files
{: #vc_vsphere_upgrade-prereq-jumpbox-binary}

Use your Windows VSI jump box and log in to your https://my.vmware.com account to download the following binary files:

* VMware vSphere 6.7u1 Hypervisor (ESXi ISO) image (Includes VMware Tools)
* vCenter 6.7u1b appliance ISO. Not the update bundle
* NSX for vSphere 6.4.4 Upgrade Bundle

For Intel Optane drives, download the following file to use as part of the post-upgrade process that uses VMware Update Manager to apply patches.

Locate the ``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-8733247.zip`` file for Intel NVMe driver for Intel® Optane™ SSD DC P4800X Series SSDPED1K750GA (750 GB, HHHL) on https://my.vmware.com/group/vmware/details?downloadGroup=DT-ESX67-INTEL-INTEL-NVME-VMD-1401016&productId=742.

#### Backing up components
{: #vc_vsphere_upgrade-backup}

Before you begin the upgrade, back up each component.

* For more information about backing up vCenter Server and PSCs, see [Overview of backup and restore options in vCenter Server 6.x (2149237)](https://kb.vmware.com/s/article/2149237?lang=en_US){:external} and [vCenter file-based backup](/docs/vmwaresolutions?topic=vmwaresolutions-solution_backingup#solution_backingup-vcenter).
* For more information about backing up NSX, see [Backing Up NSX Manager Data](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.3/com.vmware.nsx.upgrade.doc/GUID-2A75A102-518D-4D6C-B23D-877C421B1536.html){:external}.

It is recommended that you use file-based backup. Image-based backup that uses vSphere Data Protection is not supported in VMware vSphere 6.7.
{:note}

## Procedure to upgrade vCenter Server vSphere software from 6.5 to 6.7
{: #vc_vsphere_upgrade-procedure}

### Before you begin
{: #vc_vsphere_upgrade-procedure-before}

* If you encounter a problem during the upgrade process, use the {{site.data.keyword.vmwaresolutions_short}} upgrade ticket that you opened at the beginning of the process to contact IBM Support. IBM Support then opens tickets with VMware Support if required.
* You must follow the support process to ensure that {{site.data.keyword.vmwaresolutions_short}} provides VMware Support with all the information about the vCenter Server design and setup, and the {{site.data.keyword.cloud_notm}} information.
* By following the support process, you ensure that accurate information is shared with VMware Support, which shortens the support experience. After IBM Support provides the necessary information to VMware Support, you can interact with VMware Support directly.
* Ensure that you keep a record of all the new passwords and credentials that you create as part of the upgrade process. IBM Support requires these credentials at the end of the upgrade process to update their internal database.

### Upgrading VMware NSX
{: #vc_vsphere_upgrade-procedure-nsx}

You might need to upgrade your current version of NSX so it’s compatible with VMware vCenter Server 6.7. To determine whether you must upgrade NSX:

1. Go to [VMware Product Interoperability Matrices](https://www.vmware.com/resources/compatibility/sim/interop_matrix.php){:external}. Ensure you’re on the **Interoperability** tab.
2. Under **Select a Solution**:

   1. From the **Select a Solution** list, select VMware vCenter Server.
   2. Click the **All versions** box and select the appropriate 6.7 version. For example, 6.7 U2.

3. Under **Add Platform/Solution**:

   1. From the **Select a Solution** list, select VMware NSX for vSphere.
   2. Click the **All versions** box and review the list of VMware NSX for vSphere versions that are compatible with your selected VMware vCenter Server version. If your current VMware NSX for vSphere version is not listed, you must upgrade to one of the versions in the list.

Upgrading VMware NSX can take some time as the upgrade process updates the vSphere installation bundles on the ESXi hosts and it requires a restart of each host. Therefore, plan your maintenance window accordingly.

#### Before you upgrade VMware NSX
{: #vc_vsphere_upgrade-procedure-nsx-before}

* If you have Zerto on {{site.data.keyword.cloud_notm}} installed on your environment:

  * Ensure that the Zerto version that you have is compatible with the 6.7 version that you are selecting for your upgrade. For more information, see the _Interoperability matrix for Zerto environments_ document at [Zerto technical documentation](https://www.zerto.com/myzerto/technical-documentation/){:external}.

  * Use the Zerto user interface to shut down the zVRA VMs on each host. Select **Allow Zerto to always enter hosts into maintenance mode during remediation** within the Zerto site settings, policies section in the Zerto user interface. Otherwise, Zerto starts the zVRA and keeps the upgrade from proceeding by not allowing the ESXi host that is being upgraded to go into maintenance mode.

* For VMs that don't have VMware Tools installed, manually shut down or forcefully power off before the NSX ESXi host module installation. These VMs keep the target ESXi host from going into maintenance mode.

#### Procedure to upgrade VMware NSX
{: #vc_vsphere_upgrade-procedure-nsx-procedure}

For more information, see the [NSX Upgrade Guide](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.upgrade.doc/GUID-4613AC10-BC73-4404-AF80-26E924EF5FE0.html){:external}.

1. Read the release notes for NSX 6.4.4 to ensure compatibility with your specific environment configuration. For more information, see [VMware NSX Data Center for vSphere 6.4.4 Release Notes](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/rn/releasenotes_nsx_vsphere_644.html){:external}.
2. Upgrade NSX Manager first. If you have multiple NSX environments that use cross vCenter linked mode, upgrade all NSX managers before you upgrade components in the NSX user interface **Upgrade Coordinator**.
3. Use the **Upgrade Coordinator** in the NSX user interface within the vCenter Server user interface to upgrade NSX components.
4. To ensure that the upgrade is progressing until all components are upgraded, continue to review and monitor the NSX upgrade user interface within the vCenter user interface.

### Upgrading the Platform Services Controller
{: #vc_vsphere_upgrade-procedure-psc}

If you have instances that are linked, you must upgrade all PSC instances in the vCenter Server primary and secondary sites. Linked instances create a hub-and-spoke PSC replication topology, where the primary vCenter Server instance is the hub. Therefore, it is recommended that you start by upgrading the primary vCenter Server instance PSC and then upgrade each secondary site PSC.

#### Before you upgrade the Platform Services Controller
{: #vc_vsphere_upgrade-procedure-psc-before}

* Have your vCenter Server and PSC root passwords available for the following procedure. Use the {{site.data.keyword.vmwaresolutions_short}} console to note whether your vCenter Server instance version has been upgraded from V2.4 or earlier to V2.7 or later.
* On the {{site.data.keyword.vmwaresolutions_short}} console, a single password for root for both the PSC and vCenter Server is displayed. However, this password is only for vCenter Server. You must [contact IBM Support](/docs/vmwaresolutions?topic=vmwaresolutions-trbl_support) for the root PSC password.
* To avoid conflicts, use one of the IP addresses near the end of the same subnet that vCenter Server and the PSC are currently using. For example, if your IP addresses range between 10.93.60.135 and 10.93.60.187, you can select 10.93.60.184, 10.93.60.185, etc. You must use a temporary IP address for the new appliance deployment.

#### Procedure to upgrade the Platform Services Controller
{: #vc_vsphere_upgrade-procedure-psc-procedure}

1. Log in to both the PSC, `https://<psc-fqdn>:5480`, and vCenter appliance management user interfaces to confirm whether the root password expired. If the password expiration date is `1970`, then it is expired and you must enable SSH and the bash shell in the PSC appliance management user interface.
    1. SSH into the PSC with the root ID and password. You can log in, even though the password is expired.
    2. Use the shell `passwd` command to set a new root password for both the PSC and vCenter.
    3. Save the passwords that were displayed on the {{site.data.keyword.vmwaresolutions_short}} console or given to you by IBM Support. These passwords are reused later when you upgrade the appliances.
2. Use the built-in Windows ISO mount function to mount the vCenter 6.7u1b ISO within your jump box.
3. Follow the VMware instructions for upgrading all PSCs first. For more information, see [Upgrade a vCenter Server Appliance 6.0 or 6.5 with an External vCenter Single Sign-On or Platform Services Controller Instance by Using the GUI](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vcenter.upgrade.doc/GUID-37BB88CC-7A44-4EC9-8D7B-5D182E471654.html){:external}.

The **You must run the GUI upgrade from a Windows, Linux®, or Mac machine that is in the same network as the appliance that you want to upgrade** stated requirement applies to any subnet within your {{site.data.keyword.cloud_notm}} in your account.
{:note}

It is recommended that you use vCenterServer as your source and target for the upgrade.

### Upgrading vCenter Server
{: #vc_vsphere_upgrade-procedure-vcenter}

For vCenter Server linked instances, it is recommended to upgrade all vCenter Server instances in the vCenter Server secondary sites. However, these upgrades aren't required.

#### Before you upgrade vCenter Server
{: #vc_vsphere_upgrade-procedure-vcenter-before}

* Have your vCenter Server and PSC root passwords available for the following procedure. Use the {{site.data.keyword.vmwaresolutions_short}} console to note whether your vCenter Server instance version has been upgraded from V2.4 or earlier to V2.7 or later.
* To avoid conflicts, use one of the IP addresses near the end of the same subnet that vCenter Server and the PSC are currently using. For example, if your IP addresses range between 10.93.60.135 and 10.93.60.187, you can select 10.93.60.184, 10.93.60.185, etc. You must use a temporary IP address for the new appliance deployment.

#### Procedure to upgrade vCenter Server
{: #vc_vsphere_upgrade-procedure-vcenter-procedure}

1. Log in to both the PSC, `https://<psc-fqdn>:5480`, and vCenter appliance management user interfaces to confirm whether the root password has expired. If the password expiration date is `1970`, then it is expired and you must enable SSH and the bash shell in the PSC appliance management user interface.
    1. SSH into the PSC with the root ID and password. You can log in, even though the password is expired.
    2. Use the shell `passwd` command to set a new root password for both the PSC and vCenter.
    3. Save the passwords that were displayed on the {{site.data.keyword.vmwaresolutions_short}} console or given to you by IBM Support. These passwords are reused later when you upgrade the appliances.
2. Use the built-in Windows ISO mount function to mount the vCenter Server 6.7u1b ISO within your jump box.
3. Follow the VMware instructions for upgrading vCenter. For more information, see [Upgrade a vCenter Server Appliance 6.0 or 6.5 with an External vCenter Single Sign-On or Platform Services Controller Instance by Using the GUI](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vcenter.upgrade.doc/GUID-37BB88CC-7A44-4EC9-8D7B-5D182E471654.html){:external}. The VMware instructions are similar to the upgrade process of PSC. However, instead of pointing to the PSC, you point to the vCenter FQDN/IP for the upgrade process.

**Notes**:
* The stated requirement **You must run the GUI upgrade from a Windows, Linux, or Mac machine that is in the same network as the appliance that you want to upgrade** applies to any subnet within your {{site.data.keyword.cloud_notm}} in your account.
* It is recommended that you use vCenter Server as your source and target for the upgrade.

#### Consolidating the PSC function into vCenter Server

1. After successfully completing the PSC and vCenter Server upgrade, log in to the vCenter FLEX-based user interface and check the health of all services that are related to vCenter Server and the PSC in the **System Configuration** section.  
2. Back up your PSC. It is recommended that you use file-based backup. For more information, see [File-based backup in vSphere 6.7](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vcenter.install.doc/GUID-8A16C037-F1E0-40C9-B106-05C30625B9CB.html){:external}.
3. Go to the ``<VCSA 6.7 iso mount>:\vcsa-converge-cli\templates\converge`` directory.
4. Copy the ``converge.json`` file to a local drive on your jump VM.
  * If this is the first PSC you are consolidating, you must remove the **replication** section from the ``json`` file.
  * If this is a subsequent linked PSC, you must complete the attributes that are requested in the **replication** section of the ``json`` file.
5. Go to the ``<VCSA 6.7 iso mount>:\vcsa-converge-cli\templates\decommission`` directory.
6. Copy the ``decommission_psc.json`` file to a local drive on your jump VM.
7. Edit the ``converge.json`` and ``decommission_psc.json`` files. Instructions for the fields to edit are within the ``json`` files. It is recommended that the ESXi host containing the PSC is used rather than vCenter in the **managing_esxi_or_vc** section.
8. Navigate to the ``<VCSA 6.7 iso mount>:\vcsa-converge-cli\win32`` directory in a command window.
9. Run the ``vcsa-util.exe`` with the **converge** switch and the path to the previously edited ``converge.json`` file. For example, ``vcsa-util converge --no-ssl-certificate-verification c:\temp\converge.json -v``.
   1. Type **Y** to confirm that the PSC has been backed up to proceed.
   2. When the process completes, type **Y** to confirm the restart of vCenter.

   For steps to resolve the converge process fails ``ERROR converge Failed to get vecs users and permissions`` error message, see [vCenter 6.7 Update 1 – Converge to embedded failed!](https://virtualtassie.com/2018/vcenter-6-7-update-1-converge-to-embedded-failed/#comment-3713){:external}.
   {:note}

10. After vCenter Server has been rebooted, verify normal operation by logging in to the vCenter Server user interface.
11. Navigate to the ``<VCSA 6.7 iso mount>:\vcsa-converge-cli\win32`` directory in a command window.
12. Run the ``vcsa-util.exe`` with the **decommission** switch and the path to the previously edited ``decommission_psc.json`` file. For example, ``vcsa-util decommission --no-ssl-certificate-verification c:\temp\decommission_psc.json -v``.
13.	When the command completes successfully, log in to the vCenter flex user interface and verify that the vCenter appliance is the only one listed in non-linked environments and that all services are healthy.
14. Delete the old PSC, vCenter, and the unused consolidated PSC VMs.
15. Rename the vCenter Server within the vCenter Server user interface to **<instancename>_vc_separate**. For example, if your vCenter Server instance name is **production** then the vCenter Server user interface name is **production_vc_separate**. This is necessary so the automation can resume its function for this vCenter Server instance.  

### Upgrading the ESXi hosts
{: #vc_vsphere_upgrade-procedure-esxi}

The VMware Update Manager function within vCenter is used to upgrade and patch the ESXi hosts to the 6.7u1 level. Similar to the NSX upgrade, any VM that cannot vMotion to another host must be shut down without issue, otherwise it might cause the upgrade process to stop.
{:note}

#### Uploading the ESXi ISO into VUM
{: #vc_vsphere_upgrade-procedure-esxi-iso}

1. Ensure that you have VUM configured to download patches from https://www.vmware.com. For more information, see [VMware Update Manager introduction](/docs/vmwaresolutions?topic=vmwaresolutions-vum-intro).
2. Use Flex or HTML to open the vCenter Server user interface and go to the **VUM Admin View**.
3. From the **VUM Admin View**, select the **ESXi Images** tab and select **Import ESXi Images**.
4. Browse for the **ESXi 6.7u1iso** image, which was downloaded from VMware and import it into the VUM repository.

#### Procedure to upgrade the ESXi hosts
{: #vc_vsphere_upgrade-procedure-esxi-upgrade}

1. From the vCenter user interface, navigate to the cluster containing the ESXi hosts to upgrade.
2. Click the **updates** tab in the navigation pane. Go to host updates and click **Attach**.
3. Select the baseline (ISO image for ESXi upgrade) that you uploaded into VUM and click **Remediate**.
4. Accept the user license agreement and click **OK**.
5. Review the hosts to be remediated and confirm the pre-remediation check results.

   You must detach any CDs or DVDs attached to the VMs or the host containing that VM is not allowed to enter maintenance mode.
   {:note}

6. After the pre-remediation check is successful, click **Remediate**. Monitor the upgrade process with the remediate entity task.
7. After the upgrade completes, review the summary section of the host to confirm that ``VMware ESXi, 6.7.0`` displays.

If the upgrade process fails immediately and displays the **host cannot enter maintenance mode** error message, shut down the Zerto ZVAs and try again. The ZVRA VMs automatically start as each server comes out of remediation. For more information about continuing Zerto replication during the upgrade process, see [How to Place a Host with an Associated VRA into Maintenance Mode](https://www.zerto.com/myzerto/knowledge-base/how-to-place-a-host-with-an-associated-vra-into-maintenance-mode/){:external}.
{:note}

#### Adding the Intel NVME driver patch to the VUM repository
{: #vc_vsphere_upgrade-procedure-esxi-nvme}

As described in the binary downloads section, you must import the contents of the ``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-8733247.zip`` file into the repository. It is then be applied in the follow-on section as a non-critical ESXi host extension.

1. Extract the ``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-8733247.zip`` file to a local drive on your jump VM.
2. Use Flex or HTML to open up the vCenter Server user interface and navigate to the **VUM Admin View**.
3. From the **VUM Admin View**, select the **Patch Repository** tab and select **Import Patches**.
4. Browse for the extracted contents of the ``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-8733247.zip`` directory and select the ``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-offline_bundle-8733247.zip`` file. The file imports into the VUM repository immediately.

Locate the image in the patch repository as an **important** Host Extension.

#### Patching the ESXi hosts
{: #vc_vsphere_upgrade-procedure-esxi-patch}

After the upgrade, it is recommended that you apply your custom baseline for the ESXi host patches.

1. Verify the correct version of the supported ESXi host patches. For more information, see [Software BOM for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_bom#vc_bom-software).
2. Create your custom baseline. For more information, see [Creating baselines and attaching to inventory objects](/docs/vmwaresolutions?topic=vmwaresolutions-vum-baselines).
3. From the vCenter Server UI, select the cluster containing the ESXi hosts to be patched.
4. Click the **updates** tab in the navigation pane and select the **Host Updates** tab. Select your custom baseline and repeat the procedure to upgrade the ESXi hosts.

You might need to shut down the Zerto zVRA VMs again as part of this process.
{:note}

### Upgrading more items
{: #vc_vsphere_upgrade-procedure-addtl}

Review the following information for more items you might need to upgrade.

#### Upgrading the vSAN On Disk Format version
{: #vc_vsphere_upgrade-procedure-addtl-vsan}

Upgrade the vSAN Disk Format version to version 7.

1. Go to the cluster that contains the vSAN to upgrade in the vCenter Server user interface.
2. From the cluster object, select **Configuration > vSAN > General**.
3. Click **Pre-check Upgrade** to check the upgrade compatibility and possible issues. Wait for the check to return **Ready to upgrade**.
4. Click **Upgrade**. Since the upgrade processes a disk group at a time, it can take some time to complete depending on the size of the cluster. Optionally, select **reduced redundancy** during the process. While this setting might significantly reduce the time that it takes for the upgrade, it might result in data loss if there is a disk failure during the upgrade process.

#### Upgrading the Virtual Distributed Switch
{: #vc_vsphere_upgrade-procedure-addtl-vds}

Upgrading the Virtual Distributed Switch (VDS) to v6.6.0 also upgrades Network I/O control and adds enhanced Link Aggregation Control Protocol (LACP) support.

1. If you have HCX deployed, you must undeploy the Cloud Gateway portion of HCX before you upgrade the VDS it resides upon. Ensure that HCX is updated to the latest version before redeploying the Cloud Gateway.
2. From the vCenter user interface, go to the **Network** tab.
3. Right-click the distributed switch to upgrade (either **SDDC-Dswitch-Private** or **SDDC-Dswitch-Public**) and select **Upgrade Distributed Switch**.

#### Upgrading vCenter Server user interface extensions and plug-ins
{: #vc_vsphere_upgrade-procedure-addtl-extension}

It is your responsibility to upgrade any extensions or snap-ins within the vCenter Server environment. From the vCenter Server user interface, click **Home > Administration > Solutions** to view the status and enable or disable vCenter extensions and plug-ins.

#### Upgrading VMware tools
{: #vc_vsphere_upgrade-procedure-addtl-tools}

Use the vCenter Server user interface to perform VMware guest tools upgrades. Some VMware tools might be required on some older VMs, which have been migrated into the vCenter Server environment.  

#### Upgrading the VM hardware level
{: #vc_vsphere_upgrade-procedure-addtl-vmhw}

Similar to VMware guest tools, a vCenter Server environment upgrade might cause older VMs to be in an unsupported state at their current hardware level. Use the vCenter Server user interface to find and update these VMs as needed.

#### Upgrading firmware and drivers
{: #vc_vsphere_upgrade-procedure-addtl-nic}

You might need to update your firmware and drivers to a version that is compatible with vSphere 6.7 on the ESXi servers. Check your firmware and drivers versions and if required, complete the necessary upgrades.

#### Setting the Enhanced vMotion Compatibility mode to Intel Skylake
{: #vc_vsphere_upgrade-procedure-addtl-evc}

You can set hosts with the Intel Skylake generation for a cluster into Skylake Enhanced vMotion Compatibility (EVC) mode after the upgrade. Use the following steps to update the EVC mode:

1. From the cluster that contains the hosts, click **configure**.
2. From **VMware EVC**, click **Edit** and change EVC mode to **Intel "Skylake" Generation**.

For more information, see [Enhanced vMotion Compatibility (EVC) processor support](https://kb.vmware.com/s/article/1003212){:external}.

#### Reconfiguring NSX Manager and HCX Manager to point to the PSC

1. From a web browser, navigate to the NSX Manager appliance user interface at ``https://<nsx-manager-ip>`` or ``https://<nsx-manager-hostname>``. Log in with the credentials.
2. From the home page, click **Manage vCenter Registration**.
3. Edit the field **Lookup Service URL** to point to the vCenter Server IP address.

## Results after you upgrade vCenter Server vSphere software
{: #vc_vsphere_upgrade-results}

Running the vSAN health check after your upgrade is complete can result in warnings about firmware updates for the {{site.data.keyword.cloud_notm}}-supplied RAID and network controllers. After you determine the hosts that need firmware updates, open a ticket with IBM Support to get the firmware updated to the recommended versions.

1. From the vCenter Server user interface, select the cluster that contains the vSAN with health issues to be checked.
2. Select the **Monitor** tab and then select the **vSAN** tab.
3. Select **Health** and note any warnings that are displayed.
4. If a **Hardware compatibility** message is displayed, expand the message box and click the **Controller Firmware is VMware certified** message if it is in a warning state.
5. Make note of the hosts listed with firmware update recommendations.
6. Open a ticket with IBM Support to schedule a time to take each host out of service to allow for firmware updates.

When your upgrade is complete, update your support ticket with IBM Support. Provide the new passwords that you created as a part of this upgrade process. For example, provide passwords to deploy appliance management services -PSC and vCenter Server in the support ticket. IBM Support then updates the {{site.data.keyword.vmwaresolutions_short}} console and internal database to resume the {{site.data.keyword.vmwaresolutions_short}} automation at a 6.7 level. This update operation includes adding and deleting, services, hosts, cluster, and secondary vCenter Server instances.

## Related links
{: #vc_vsphere_upgrade-related}

* [VMware NSX Data Center for vSphere 6.4.4 Release Notes](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/rn/releasenotes_nsx_vsphere_644.html){:external}
* [NSX Upgrade Guide](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.upgrade.doc/GUID-4613AC10-BC73-4404-AF80-26E924EF5FE0.html){:external}
* [Contacting IBM Support](/docs/vmwaresolutions?topic=vmwaresolutions-trbl_support)
