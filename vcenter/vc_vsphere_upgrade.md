---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-28"

keywords: vSphere upgrade, NSX upgrade, PSC upgrade

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Upgrading vCenter Server vSphere software from VMware vSphere 6.5 to 6.7
{: #vc_vsphere_upgrade}

The vCenter Server on {{site.data.keyword.cloud}} offering is a fully automated deployment solution for the VMware vSphere SDDC stack including vSphere, NSX, and optionally vSAN products. While vCenter Server automates the most challenging parts of deploying, expanding, and contracting a VMware SDDC-based infrastructure, it is not a managed service. As vCenter Server has a policy of supporting the automation of VMware SDDC software versions within the range of N-1, you must upgrade existing instances of vCenter Server if you want to continue to benefit from the {{site.data.keyword.vmwaresolutions_short}} automation.

vCenter Server versions outside of the levels needed for automation support continue to be supported as required by the VMware support policy, but no longer function with the {{site.data.keyword.vmwaresolutions_short}} automation. You must perform periodic patching and upgrading of the VMware software over the lifecycle of a vCenter Server instance. This includes upgrading the VMware SDDC software to a version that is supported by the {{site.data.keyword.vmwaresolutions_short}} automation as needed.

The following procedure provides the steps required to convert a vCenter Server VMware vSphere 6.5 based instance to a vCenter Server VMware vSphere 6.7 based instance. These steps provide the initial upgrade to the latest 6.7 level of vSphere, NSX, and vSAN. Following this upgrade, you may need to use the normal vSphere functionality to upgrade virtual machine (VM) hardware levels and tools.

vCenter Server is designed to allow for a “rolling” upgrade. That is, VM workloads that are currently functioning continue to function without an outage if you complete the following procedure. Enterprises must engage their change management policies to enable a structured and communicated upgrade and plan for contingencies. However, during the upgrade process of certain management functions, such as vCenter and NSX manager, temporary outages of management functions, configuration changes, powering off and on VMs, may be impacted.
{:note}

## Before you begin
{: #vc_vsphere_upgrade-prereq}

The estimated time to perform the upgrade is unknown. It is possible that it may take several maintenance windows to completely upgrade an environment. Running up-leveled and down-leveled versions of the SDDC software is supported by VMware during the upgrade process. However, some functions such as vMotion, maybe limited during this process.

Complete the following requirements before you begin the upgrade:  
* It is your responsibility to upgrade any extensions or snap-ins within the vCenter Server environment. Review the following documentation before you plan your upgrade:
  * [VMware vCenter Server 6.7 Update 1b Release Notes](https://docs.vmware.com/en/VMware-vSphere/6.7/rn/vsphere-vcenter-server-67u1b-release-notes.html){:external}
  * [About VMware ESXi Upgrade](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.esxi.upgrade.doc/GUID-65B5B313-3DBB-4490-82D2-A225446F4C99.html){:external}
* Set up vSphere Update Manager (VUM) within your vCenter Server instance to download the latest updates from VMware vSphere. For more information, see [VMware Update Manager introduction](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vum-intro#vum-intro).
* Open a support ticket with the {{site.data.keyword.vmwaresolutions_short}} team to notify them that an upgrade is being performed. The ticket remains open until the instance is registered at the upgraded level in the {{site.data.keyword.vmwaresolutions_short}} console.
* Confirm whether or not the vCenter Server instance that you are upgrading is linked to another vCenter Server instance as primary or secondary in the {{site.data.keyword.vmwaresolutions_short}} console. All linked instances must have their Platform Services Controllers (PSCs) upgraded first as part of a particular site upgrade.
* Confirm the following for vSAN based instances:
  * Ensure that the vSAN Health tool is enabled and reports no critical errors. If critical errors are present, contact the IBM Support team with the upgrade support ticket ID.
  * Ensure that there is  space on each node to handle rebuilding redundancy of vSAN objects should an ESXi host fail to come back up during the upgrade. You may need to either reduce disk usage or add an additional ESXi host prior to upgrade.  
  * Verify whether or not the overall vSAN volume is above 70 percent utilized. You may need to either reduce disk usage or add an additional ESXi host prior to upgrade.
* If your vCenter Server instance started out as an {{site.data.keyword.vmwaresolutions_short}} V2.5 or later, you must contact IBM Support for the **root** user ID password for both the PSC and vCenter as only a services account with **customerroot** access is visible on the portal. If the PSC and vCenter **root** user ID is visible with its password, then this step is not required.
* Confirm that you have a https://my.vmware.com user ID for which to download the required upgrade binaries. If you don't, contact the IBM Support with the upgrade support ticket ID.
* Confirm that VUM is configured to reach https://www.vmware.com to download patches. If it can't be configured because of security policies, then you must manually download the latest patch sets and upload them into the VUM. For more information, see [VMware Update Manager introduction](/docs/services/vmwaresolutions?topic=vmware-solutions-vum-intro#vum-intro).

### Preparing your jumpbox
{: #vc_vsphere_upgrade-prereq-jumpbox}

As the {{site.data.keyword.cloud_notm}} client access VPN is limited to 512 Kbps, it is recommended that you either provision an {{site.data.keyword.cloud_notm}} Windows 2012-2016 server Virtual Server Instance (VSI) or setup a similar Windows VM on a separate vSphere vCenter Server environment within the same {{site.data.keyword.CloudDataCent_notm}}. This is used as a jumpbox into the vCenter Server instance to upgrade and allows for quick downloads from https://my.vmware.com for the binaries. While it is possible to place this VM on the vCenter Server instance that is being upgraded, it is not recommended.

Complete the following steps to order a VSI jumpbox.

Skip the first step if you already have a VSI jumpbox in your environment.
{:note}

1. Order an hourly or monthly VSI from the [IBM Cloud infrastructure customer portal](https://control.softlayer.com/){:external}. Order the following attributes:
  * Windows 2012 or 2016 Server Standard
  * 2 CPUs
  * 16 GB of memory
  * 100 G of disk
  * 1 Gbps public and private uplinks
2. When the VSI is provisioned, configure the {{site.data.keyword.cloud_notm}} Access Control Lists (ACLs) within the control panel to allow all ingress and egress from the private links and egress only from public. You must use the {{site.data.keyword.cloud_notm}} client access VPN for Remote Desktop Protocol (RDP) sessions into the Windows VSI.
3. RDP into the Windows VSI. Modify its Domain Name System (DNS) settings on the private network adapter to point to only the windows AD server within the vCenter Server instance to upgrade.
4. Download and install the Google Chrome browser. You can use Mozilla Firefox, but it does have a cache issue when using the VUM screens within the vCenter user interface.
5. Download your preferred SSH terminal software. For example, Putty.
6. Use Google Chrome to access the vCenter Server instance to upgrade. Use **administrator@vsphere.local** and ensure that you can view the user interface.  
7. Check the vSphere environment for errors and issues as discussed in the previous section.
8. Use your SSH terminal software to access the PSC and vCenter with the portal or support supplied passwords for **root**.
9. Optionally, Use the **root** user ID and password noted in the SL control panel to access each ESXi host to verify the **root** password.

#### Downloading binary files
{: #vc_vsphere_upgrade-prereq-jumpbox-binary}

Use your Windows VSI jumpbox and log into your https://my.vmware.com account to download the following binary files:

* VMware vSphere 6.7u1 Hypervisor (ESXi ISO) image (Includes VMware Tools)
* vCenter 6.7u1b appliance ISO. Not the update bundle.
* NSX for vSphere 6.4.4 Upgrade Bundle

For Intel Optane drives, download the following file to use as part of the post upgrade patching process that utilizes VMware Update Manager.

Locate the ``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-8733247.zip`` file for Intel NVMe driver for Intel® Optane™ SSD DC P4800X Series SSDPED1K750GA (750 GB, HHHL) on https://my.vmware.com/group/vmware/details?downloadGroup=DT-ESX67-INTEL-INTEL-NVME-VMD-1401016&productId=742.

#### Backing up components

Before you begin the upgrade, back up each component.

* For information about backing up vCenter Server and PSCs, see [Overview of Backup and Restore options in vCenter Server 6.x (2149237)](https://kb.vmware.com/s/article/2149237?lang=en_US){:external}.
* For additional considerations and information on backing up vCenter Server and PSCs, see [vCenter file-based backup](/docs/services/vmwaresolutions?topic=vmware-solutions-solution_backingup#solution_backingup-vcenter).
* For information about backing up NSX, see [Backing Up NSX Manager Data](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-72EFCAB1-0B10-4007-A44C-09D38CD960D3.html){:external}.

It is recommended that you use file-based backup. Image-based backup (using vSphere Data Protection) is not supported in VMware vSphere 6.7.
{:note}

## Procedure to upgrade IBM vCenter Server vSphere software from 6.5 to 6.7
{: #vc_vsphere_upgrade-procedure}

If you encounter a problem at any time during the upgrade process, use the {{site.data.keyword.vmwaresolutions_short}} upgrade ticket you opened at the beginning of the process to contact IBM Support. IBM Support opens tickets with VMware support as required.

**Important**:

* You must use this path to ensure that {{site.data.keyword.vmwaresolutions_short}} provides VMware support with all of the information they need about the vCenter Server design, setup, and {{site.data.keyword.cloud_notm}} information. Following this process to ensure that accurate information is shared with VMware support shortens the support experience. After IBM Support provides the necessary information to VMware support, you can directly interact with VMware support as needed.
* Ensure that you keep record of all the new passwords and credentials that you create as a part of this upgrade process. IBM support requires these credentials at the end of the upgrade process to update their internal database.

### Upgrading VMware NSX
{: #vc_vsphere_upgrade-procedure-nsx}

Upgrading VMware NSX can take some time as the upgrade process updates vSphere Installation Bundles on the ESXi hosts and  requires a reboot of each host. Plan your maintenance window accordingly.

#### Before you upgrade VMware NSX
{: #vc_vsphere_upgrade-procedure-nsx-before}

* If you have Zerto for {{site.data.keyword.cloud_notm}} installed on your environment, use the Zerto user interface to shut down the zVRA VMs on each host. Select **allow Zerto to always enter hosts into maintenance mode during remediation** within the Zerto site settings, policies section in the Zerto user interface. Otherwise Zerto starts up the zVRA and keeps the upgrade from proceeding by not allowing the ESXi host being upgraded to go into maintenance mode.
* For VMs that don't have VMware tools installed, manually shut down or forcefully power off before the NSX ESXi host module install. These VMs keep the target ESXi host from going into maintenance mode.

#### Procedure to upgrade VMware NSX
{: #vc_vsphere_upgrade-procedure-nsx-procedure}

Refer to the [NSX Upgrade Guide](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.upgrade.doc/GUID-4613AC10-BC73-4404-AF80-26E924EF5FE0.html){:external} for details related to the following procedure.

1. Read the release notes for NSX 6.4.4 to ensure compatibility with your specific environment configuration. For more information, see [VMware NSX Data Center for vSphere 6.4.4 Release Notes](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/rn/releasenotes_nsx_vsphere_644.html){:external}.
2. Upgrade the NSX manager first. If you have multiple NSX environments that use cross vCenter linked mode, upgrade all NSX managers before you upgrade components in the NSX user interface **Upgrade Coordinator**.
3. Use the **Upgrade Coordinator** in the NSX user interface within the vCenter user interface to upgrade NSX components.
4. Continue to review and monitor the NSX upgrade user interface within the vCenter user interface as possible issues are resolved to ensure the upgrade is proceeding until all components are upgraded.

### Upgrading the Platform Services Controller
{: #vc_vsphere_upgrade-procedure-psc}

If you have vCenter Server linked instances, you must upgrade all PSC instances in the vCenter Server primary and secondary sites. Since linked vCenter Server instances create a hub and spoke PSC replication topology with the primary vCenter Server instance being the hub, it is recommended that you start by upgrading the primary vCenter Server instance PSC and then upgrade each secondary site PSC.

#### Before you upgrade the Platform Services Controller
{: #vc_vsphere_upgrade-procedure-psc-before}

* Have your vCenter and PSC root passwords available for the following procedure. Use the {{site.data.keyword.vmwaresolutions_short}} console to note whether or not your vCenter Server instance version has been upgraded from V2.4 or earlier to V2.7 or later.
* On the {{site.data.keyword.vmwaresolutions_short}} console, a single password for root for both the PSC and vCenter is displayed. However, this is only the vCenter password. You must [contact IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support) for the root PSC password.
* To avoid conflicts, use the IP address in the upper part of the same subnet that vCenter and the PSC are currently using. You must use a temporary IP address for the new appliance deployment.

#### Procedure to upgrade the Platform Services Controller
{: #vc_vsphere_upgrade-procedure-psc-procedure}

1. Log in to both the PSC, `https://<psc-fqdn>:5480`, and vCenter appliance management user interfaces to confirm whether or not the root password has expired. If the password expiration date is **1970** then it has expired and you must enable SSH and the bash shell in the PSC appliance management user interface.
    1. SSH into the PSC with the root ID and password. Even though the password has expired it allows you to log in.
    2. Use the shell **passwd** command to set a new root password for both the PSC and vCenter.
    3. Save the passwords that were displayed on the {{site.data.keyword.vmwaresolutions_short}} console or given to you by IBM Support. These passwords are reused later when you upgrade the appliances.
2. Use the built in Windows ISO mount function to mount the vCenter 6.7u1b ISO within your jump box.
3. Follow the VMware instructions for upgrading all PSCs first. For more information, see [Upgrade a vCenter Server Appliance 6.0 or 6.5 with an External vCenter Single Sign-On or Platform Services Controller Instance by Using the GUI](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vcenter.upgrade.doc/GUID-37BB88CC-7A44-4EC9-8D7B-5D182E471654.html){:external}.

The **You must run the GUI upgrade from a Windows, Linux, or Mac machine that is in the same network as the appliance that you want to upgrade** stated requirement applies to any subnet within your {{site.data.keyword.cloud_notm}} in your account.
{:note}

It is recommended that you use vCenter as your source and target for the upgrade.

### Upgrading vCenter
{: #vc_vsphere_upgrade-procedure-vcenter}

For vCenter Server linked instances, although it is recommended to upgrade all vCenter instances in the vCenter Server primary secondary sites, it is not required.

#### Before you upgrade vCenter
{: #vc_vsphere_upgrade-procedure-vcenter-before}

* Have your vCenter and PSC root passwords available for the following procedure. Use the {{site.data.keyword.vmwaresolutions_short}} console to note whether or not your vCenter Server instance version has been upgraded from V2.4 or earlier to V2.7 or later.
* To avoid conflicts, use the IP address in the upper part of the same subnet that vCenter and the PSC are currently using. You must use a temporary IP address for the new appliance deployment.

#### Procedure to upgrade vCenter
{: #vc_vsphere_upgrade-procedure-vcenter-procedure}

1. Log in to both the PSC, ``https://<psc-fqdn>:5480``, and vCenter appliance management user interfaces to confirm whether or not the root password has expired. If the password expiration date is **1970** then it has expired and you must enable SSH and the bash shell in the PSC appliance management user interface.
    1. SSH into the PSC with the root ID and password. Even though the password has expired it allows you to log in.
    2. Use the shell **passwd** command to set a new root password for both the PSC and vCenter.
    3. Save the passwords that were displayed on the {{site.data.keyword.vmwaresolutions_short}} console or given to you by IBM Support. These passwords are reused later when you upgrade the appliances.
2. Use the built in Windows ISO mount function to mount the vCenter 6.7u1b ISO within your jump box.
3. Follow the VMware instructions for upgrading vCenter. For more information, see [Upgrade a vCenter Server Appliance 6.0 or 6.5 with an External vCenter Single Sign-On or Platform Services Controller Instance by Using the GUI](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vcenter.upgrade.doc/GUID-37BB88CC-7A44-4EC9-8D7B-5D182E471654.html){:external}. The VMware instructions are similar to the upgrade process of PSC. However, instead of pointing to the PSC, you point to the vCenter FQDN/IP for the upgrade process.

**Notes**:
* The stated requirement **You must run the GUI upgrade from a Windows, Linux, or Mac machine that is in the same network as the appliance that you want to upgrade** applies to any subnet within your {{site.data.keyword.cloud_notm}} in your account.
* It is recommended that you use vCenter as your source and target for the upgrade.

#### Consolidating the PSC function into vCenter

1. After successfully completing the PSC and vCenter upgrade, log in to the vCenter FLEX based user interface and check the health of all services related to vCenter and the PSC in the **System Configuration** section.  
2. Backup your PSC.  It is recommended that you use file based backup. For more information, see [File based backup in vSphere 6.7](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vcenter.install.doc/GUID-8A16C037-F1E0-40C9-B106-05C30625B9CB.html){:external}.
3. Navigate to the ``<VCSA 6.7 iso mount>:\vcsa-converge-cli\templates\converge`` directory.
4. Copy the ``converge.json`` file to a local drive on your jump VM.
  * If this is the first PSC you are consolidating, you must remove the **replication** section from the ``json`` file.
  * If this is a subsequent linked PSC, you must fill in the attributes requested in the **replication** section of the ``json`` file.
5. Navigate to the ``<VCSA 6.7 iso mount>:\vcsa-converge-cli\templates\decommission`` directory.
6. Copy the ``decommission_psc.json`` file to a local drive on your jump VM.
7. Edit the ``converge.json`` and ``decommission_psc.json`` files. Instructions for the fields to edit are within the ``json`` files. It is recommended that the ESXi host containing the PSC is used rather than vCenter in the **managing_esxi_or_vc** section.
8. Navigate to the ``<VCSA 6.7 iso mount>:\vcsa-converge-cli\win32`` directory in a command window.
9. Run the ``vcsa-util.exe`` with the **converge** switch and the path to the previously edited ``converge.json`` file. For example, ``vcsa-util converge --no-ssl-certificate-verification c:\temp\converge.json -v``.
   1. Type **Y** to confirm the PSC has been backed up to proceed.
   2. When the process completes, type **Y** to confirm the reboot of vCenter.

   If the converge process fails with the ``ERROR converge Failed to get vecs users and permissions`` message, see [Converge to embedded failed!](https://virtualtassie.com/2018/vcenter-6-7-update-1-converge-to-embedded-failed/#comment-3713){:external} for steps to resolve the error.
   {:note}

10. After vCenter has been rebooted, verify normal operation by logging into the vCenter user interface.
11. Navigate to the ``<VCSA 6.7 iso mount>:\vcsa-converge-cli\win32`` directory in a command window.
12. Run the ``vcsa-util.exe`` with the **decommission** switch and the path to the previously edited ``decommission_psc.json`` file. For example, ``vcsa-util decommission --no-ssl-certificate-verification c:\temp\decommission_psc.json -v``.
13.	When the command completes successfully, log in to the vCenter flex user interface and verify that the vCenter appliance is the only one listed in non-linked environments and that all services are healthy.
14. Delete the old PSC, vCenter, and the unused consolidated PSC VMs.
15. Rename the vCenter Server within the vCenter user interface to **<instancename>_vc_separate**. For example, if your vCenter Server instance name is **production** then the vCenter user interface name is **production_vc_separate**. This is necessary so the automation may resume its function for this vCenter Server instance.  

### Upgrading the ESXi hosts
{: #vc_vsphere_upgrade-procedure-esxi}

The VMware Update Manager function within vCenter is utilized to upgrade and patch the ESXi hosts to the 6.7u1 level. Similar to the NSX upgrade section of this document, any VM that may not vMotion to another host must be shut down without issue, otherwise it may cause the upgrade process to stall.
{:note}

#### Uploading the ESXi ISO into VUM
{: #vc_vsphere_upgrade-procedure-esxi-iso}

1. Ensure you have VUM configured to download patches from https://www.vmware.com. For more information, see [VMware Update Manager introduction](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-intro#vmware-update-manager-introduction).
2. Use Flex or HTML to open the vCenter user interface and navigate to the **VUM Admin View**.
3. From the **VUM Admin View**, select the **ESXi Images** tab and select **Import ESXi Images**.
4. Browse for the **ESXi 6.7u1iso** image which was downloaded from VMware and import it into the VUM repository.

#### Procedure to upgrade the ESXi hosts
{: #vc_vsphere_upgrade-procedure-esxi-upgrade}

1. From the vCenter user interface, navigate to the cluster containing the ESXi hosts to upgrade.
2. Click the **updates** tab in the navigation panel. Go to host updates and click **Attach**.
3. Select the baseline (ISO image for ESXi upgrade) that you uploaded into VUM and click **Remediate**.
4. Accept the End User License Agreement and click **OK**.
5. Review the hosts to be remediated and confirm the pre-remediation check results.

   You must detach any CDs or DVDs attached to the VMs or the host containing that VM is not allowed to enter into maintenance mode.
   {:note}

6. After the pre-remediation check is successful, click **Remediate**. Monitor the upgrade process with the remediate entity task.
7. After the upgrade completes, review the summary section of the host to confirm that ``VMware ESXi, 6.7.0`` displays.

If the upgrade process fails immediately and displays the **host cannot enter maintenance mode** error message, shutdown the Zerto ZVAs and try again. The ZVRA VMs automatically start as each server comes out of remediation. For information about continuing Zerto replication during the upgrade process, see [How to Place a Host with an Associated VRA into Maintenance Mode](https://www.zerto.com/myzerto/knowledge-base/place-host-into-maintenance-mode-with-vra/){:external}.
{:note}

#### Adding the Intel NVME driver patch to the VUM repository
{: #vc_vsphere_upgrade-procedure-esxi-nvme}

As described in the binary downloads section, you must import the contents of the ``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-8733247.zip`` file into the repository. It is then be applied in the follow-on section as a non-critical ESXi host extension.

1. Extract the ``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-8733247.zip`` file to a local drive on your jump VM.
2. Use Flex or HTML to open up the vCenter user interface and navigate to the **VUM Admin View**.
3. From the **VUM Admin View**, select the **Patch Repository** tab and select **Import Patches**.
4. Browse for the extracted contents of the ``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-8733247.zip`` directory and select the ``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-offline_bundle-8733247.zip`` file. The file imports into the VUM repository immediately.

Locate the image in the patch repository as an **important** Host Extension.

#### Patching the ESXi Hosts
{: #vc_vsphere_upgrade-procedure-esxi-patch}

Post upgrade it is recommended that you apply all critical and non-critical ESXi host patches.

1. From the vCenter user interface, select the cluster containing the hosts to be patched.
2. Click the **updates** tab in the navigation panel and select the **Host Updates** tab. Select **Critical Host Patches (Predefined)**. Repeat the procedure to upgrade the ESXi hosts.
3. Click the **updates** tab in the navigation panel and select the **Host Updates** tab. Select **Non-Critical Host Patches (Predefined)**. Repeat the procedure to upgrade the ESXi hosts.

You may need to shut down the Zerto zVRA VMs again as part of this process.
{:note}

### Upgrading additional items
{: #vc_vsphere_upgrade-procedure-addtl}

#### Upgrading the vSAN On Disk Format version upgrade
{: #vc_vsphere_upgrade-procedure-addtl-vsan}

Upgrade the vSAN Disk Format version to version 7.

1. Navigate to the cluster containing the vSAN to upgrade in the vCenter user interface.
2. From the cluster object, select **Configuration > vSAN > General**.
3. Click **Pre-check Upgrade** to check the upgrade compatibility and possible issues. Wait for the check to return **Ready to upgrade..**.
4. Click **Upgrade**. Since the upgrade processes a disk group at a time, it can take some time to complete depending on the size of the cluster. Optionally select **reduced redundancy** during the process. While this can significantly reduce the time that it takes for the upgrade, it could result in data loss if there is a disk failure during the upgrade process.

#### Upgrading the Virtual Distributed Switch
{: #vc_vsphere_upgrade-procedure-addtl-vds}

Upgrading the Virtual Distributed Switch (VDS) to v6.6.0 also upgrades Network I/O control and adds enhanced Link Aggregation Control Protocol (LACP) support.

1.	If you have HCX deployed, you must un-deploy the Cloud Gateway portion of HCX to prior to upgrading the VDS it resides upon. Ensure HCX is updated to the latest version prior to redeploying the Cloud Gateway.
2.	From the vCenter user interface, navigate to the **Network** tab.
3.	Right-click the distributed switch to upgrade (either **SDDC-Dswitch-Private** or **SDDC-Dswitch-Public**) and select **Upgrade Distributed Switch**.

#### Upgrading vCenter user interface extensions and plug-ins
{: #vc_vsphere_upgrade-procedure-addtl-extension}

It is your responsibility to upgrade any extensions or snap-ins within the vCenter Server environment. From the vCenter user interface, click **Home > Administration > Solutions** to view the status and enable or disable vCenter extensions and plug-ins.

#### Upgrading VMware tools
{: #vc_vsphere_upgrade-procedure-addtl-tools}

Use the vCenter user interface to perform VMware guest tools upgrades. Some VMware tools may be required on some older VMs which have been migrated into the vCenter Server environment.  

#### Upgrading the virtual machine hardware level
{: #vc_vsphere_upgrade-procedure-addtl-vmhw}

Similar to VMware guest tools, a vCenter Server environment upgrade may cause older VMs to be in an unsupported state at their current hardware level. Use the vCenter user interface to find and update these VMs as needed.  

#### Setting the Enhanced vMotion Compatibility mode to Intel Skylake
{: #vc_vsphere_upgrade-procedure-addtl-evc}

You can set hosts with the Intel Skylake generation for a cluster into Skylake Enhanced vMotion Compatibility (EVC) mode after the upgrade. Use the following steps to update the EVC mode:

1. From the cluster containing hosts, click **configure**.
2. From **VMware EVC**, click **Edit** and change EVC mode to **Intel "Skylake" Generation**.

For more information, see [Enhanced vMotion Compatibility (EVC) processor support (1003212)](https://kb.vmware.com/s/article/1003212){:external}.

#### Reconfiguring the NSX manager and HCX manager to point to the PSC

1. From a web browser, navigate to the NSX Manager appliance user interface at ``https://<nsx-manager-ip>`` or ``https://<nsx-manager-hostname>``. Log in with the credentials.
2. From the home page, click **Manage vCenter Registration**.
3. Edit the **Lookup Service URL** to point to the vCenter IP. Use the embedded **PSC doesn’t exist anymore** PSC standalone.

## Results after you upgrade vCenter Server vSphere software
{: #vc_vsphere_upgrade-results}

Running the vSAN health check after your upgrade is complete may bring up warnings about firmware updates for the IBM Cloud supplied RAID and network controllers. After you determine the hosts that need firmware updates, open a ticket with IBM Support to get the firmware updated to the recommended versions.

1. From the vCenter user interface, select the cluster containing the vSAN with health to be checked.
2. Select the **Monitor** tab and then select the **vSAN** tab.
3. Select **Health** and note any warnings displayed.
4. If a **Hardware compatibility** warning displays, expand the warning and click the **Controller Firmware is VMware certified** message if it is in a warning state.
5. Make note of the hosts listed with firmware update recommendations.
6. Open a ticket with IBM Support to schedule a time to take each host out of service to allow for firmware updates.

When your upgrade is complete, update your support ticket with IBM Support. Provide the new passwords that you created as a part of this upgrade process. For example, provide passwords to deploy appliance management services -PSC and vCenter in the support ticket. IBM Support then updates the {{site.data.keyword.vmwaresolutions_short}} console and internal database to resume the {{site.data.keyword.vmwaresolutions_short}} automation at a 6.7 level. This includes adding and removing, services, hosts, cluster, and secondary vCenter Server instances.

## Related links
{: #vc_vsphere_upgrade-related}

* [VMware NSX Data Center for vSphere 6.4.4 Release Notes](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/rn/releasenotes_nsx_vsphere_644.html){:external}
* [NSX Upgrade Guide](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.upgrade.doc/GUID-4613AC10-BC73-4404-AF80-26E924EF5FE0.html){:external}
* [Contacting IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
