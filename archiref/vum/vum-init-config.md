---

copyright:

  years:  2016, 2021

lastupdated: "2021-08-17"

subcollection: vmwaresolutions

---

# Initial configuration
{: #vum-init-config}

The {{site.data.keyword.vmwaresolutions_full}} automation configures the vCenter Server® Appliance (VCSA) with a default gateway set to the {{site.data.keyword.cloud_notm}} Backend Customer Router (BCR). However, there's no route to the internet via the BCR. The standard route to the internet from the VMware® vCenter Server instance is via the Management ESG. As it isn't advised to change the configuration of the VCSA or the Management ESG, a proxy server implementation on the customer subnet is recommended to enable VMware Update Manager (VUM).

This approach means that you don't have to reconfigure the VCSA or the Management ESG, however, a small virtual machine (VM) or appliance must be installed. A proxy server is a system, which sits between two endpoint devices and acts as an intermediate device. In this case, it sits between VUM and the update servers at VMware.

When VUM requests a resource from the update server at VMware, the request is sent to the proxy server first and the proxy server then sends the request to the update server. After the resource is obtained by the proxy server, it sends the resource to VUM. A proxy server can be used to facilitate security, administrative controls, and caching services.

You can use a proxy server based on CentOS and Squid. Squid Proxy is an open source caching proxy for the web and supports many protocols that include HTTP and HTTPS. A number of VM and appliance-based proxies are available, and you must select the appropriate one based on your enterprise’s requirements and install and configure following the vendor’s guidance. If you select to use a CentOS/Squid implementation, continue with the following process.

* Download the CentOS ISO to a jump server.
* Create a vCenter Library.
* Upload the ISO to the vCenter Library.
* Create a VM, install, and configure CentOS and install Squid.

## Finding the subnet information
{: #vum-init-config-subnet}

Before you can start this task, collect the information to populate the following table. Review the suggested values and ensure that they are appropriate for your environment. This configuration is based on a small proxy for VUM only that uses CentOS-Minimal and Squid.

To find the customer's private portable subnet, complete the following steps:

1. Go to the **Resources** page in the {{site.data.keyword.vmwaresolutions_short}} console.
2. Select the required **Instance**, select **Infrastructure** and then the required **Cluster**.
3. Select **Private VLAN** and locate the subnet that is labeled `Private subnet for customer workload edge`.
4. Select the **subnet** and you are redirected to the subnet details page that displays the IP addresses and their allocations.
5. Using the information, select a non-allocated IP address and update the **Note** with appropriate comments. Use this IP address for the `proxy ip` parameter in the following table.

| Parameter | Suggested values | Notes |
|:--------- |:---------------- |:----- |
| Proxy CPU | 1 vCPU | Squid has no minimum requirements |
| Proxy RAM | 2 GB | Squid has no minimum requirements |
| Proxy Disk | 25 | GB	Squid has no minimum requirements |
| Hostname | Proxy01 | |
| Address | Proxy IP | A spare IP address must be used from the Customer, private portable subnet assigned during the provisioning process. Only two IP addresses are reserved on this subnet; one for the BCR and the other for the customer-esg
| Netmask | 255.255.255.192 |None |
| Gateway| customer-nsx-edge private uplink IP | This parameter is the default gateway setting for the proxy server, which is the private uplink IP address of customer-nsx-edge. The IP address can be found by reviewing the **Settings** tab for **customer-nsx-edge**. |
| DNS Server | AD/DNS IP | This IP address can be found on the instance page in the {{site.data.keyword.vmwaresolutions_short}} console, the **Resources** page. |
| BCR IP | BCR IP| On the same page where you selected the proxy IP, note the address that is labeled **Gateway**. This address is the IP address of the {{site.data.keyword.cloud_notm}} Backend Customer Router and is the gateway for 10.0.0.0/8 and 161.26.0.0/16. You use this address later in a static route in the proxy server so that it can reach the VCSA and the AD/DNS server. |
| NAT IP | customer-nsx-edge public uplink IP | The public address of the customer NSX ESG serves as the public NAT address for the proxy. This IP address can be found by reviewing the **Settings** tab for **customer-nsx-edge**. |
{: caption="Table 1. Deployment values" caption-side="top"}

## Configuring NSX
{: #vum-init-config-config-nsx}

NSX Customer ESG firewall and NAT settings are required to enable proxy server traffic.

### Setting up the firewall
{: #vum-init-config-firewall}

1. Go to **Home** > **Networking & Security**.
2. Select **NSX Edges**, customer-nsx-edge, and then **Firewall**.
3. Click the **+** symbol and add a firewall rule.
4. Supply the required parameters that are noted in the following table. The new firewall rule must come before the last rule, the Default Deny rule.

| Parameter | Suggested values |
|:--------- |:---------------- |
| Name | Outbound Proxy01 |
| Type | User |
| Source | Proxy server IP |
| Destination | Any |
| Service | HTTP/HTTPS/ICMP Echo |
| Action | Accept |
{: caption="Table 2. Firewall rule" caption-side="top"}

After parameters are supplied, click **Publish Changes**.

### Defining the NAT rule
{: #vum-init-config-nat}

1. Select **NAT**.
2. Click the **+** symbol and add a SNAT rule.
3. Supply the required parameters that are noted in the following table and click **OK**. Then, click **Publish Changes**.

| Parameter | Suggested values |
|:--------- |:---------------- |
| Rule Type | USER |
| Action | SNAT |
| Applied On | Public Uplink |
| Original Protocol | Any |
| Original Source IP | Proxy server IP |
| Original Source Ports | Any |
| Original Destination IP | Any |
| Original Destination Ports | Any |
| Translated IP Address | NAT IP |
| Translated Port Range | Any |
| Status | Enable |
| Logging | Enable |
| Description | Proxy01 SNAT |
{: caption="Table 3. NAT rule" caption-side="top"}

### Installing and configuring a proxy server
{: #vum-init-config-inst-cfg-proxy}

The following steps deploy a VM to host CentOS and Squid from the Content Library. Before you start, ensure that you have a Windows® VSI provisioned for use as a jump server and that you are using Remote Desktop Protocol to connect to the VSI’s public interface.

* Download the CentOS-Minimal ISO file.
* Configure a vCenter Content library and populate it with the CentOS ISO file.
* Configure the proxy VM, install CentOS and Squid.

### Downloading the CentOS-Minimal ISO file
{: #vum-init-config-downloading-centos}

Using a browser on your jump-server to download the CentOS-Minimal ISO file from [CentOS](https://www.centos.org/download/). {{site.data.keyword.cloud_notm}} maintains a mirror of many popular Linux® distributions. This mirror is only available on the private network, and the CentOS ISOs are available at http://mirrors.service.softlayer.com/centos/7/isos/x86_64/.

### Configuring a content library and populating it with the CentOS ISO file
{: #vum-init-config-config-conent-library}

Create a local vCenter content library. The library is accessible only in the vCenter Server instance where it is created. Populate the library with templates and ISOs required to deploy VMs.

1. In the vSphere Web Client, go to **Home** > **Content library** > **Objects** > **Create a new content library** > **Create subscribed library on the vCenter**.
2. Enter a name for the content library, for example, ISO, and in the Notes text box, enter a description for the library and click **Next**.
3. Select **Local content library** and click **Next**.
4. Select a data store and then click a suitable data store, for example, `vsanDatastore`.
5. Review the information on the **Ready to Complete** page and click **Finish**.

### Configuring the Proxy VM and installing CentOS and Squid
{: #vum-init-config-config-proxy}

#### Creating a new VM
{: #vum-init-config-create-new-vm}

This task creates a new VM ready for use as the proxy server. Use the settings from Table 1 Deployment Values to populate the configuration.

1.	In the vSphere Web Client, go to **Home** > **VMs and Templates**.
2.	In the Navigator pane, right-click **datacenter1**, and then click **New Virtual Machine** > **New Virtual Machine**.
3.	Select **Create a new Virtual Machine** and then click **Next**.
4.	Enter a Name for the VM, for example, Proxy01, and select **datacenter1**, then click **Next**.
5.	Select **cluster1** and then click **Next**.
6.	Select an appropriate data store, for example, vsanDatastore; and click **Next** and **Next** again.
7.	In **Guest OS Family**, select **Linux**; in **Guest OS version**, select **CentOS 7 (64-bit)**; and then click **Next**.
8.	Under the **Customized Hardware** tab for Virtual Hardware, set **CPU to 1**, **Memory to 2048 MB** and **New hard disk to 25 GB**. Under **New CD/DVD drive** select **Content Library ISO File** and then **CentOS-7-x86_64-Minimal**, click **OK** and the tick the **Connected** box.
9.	In the New device box, select **Network** and then click **Add**.
10.	Select the **SDDC-DPortGroup-Mgmt** network and ensure that the Connect checkbox is ticked, click **Next**.
11.	Review and click **Finish**.

#### Installing CentOS
{: #vum-init-config-install-centos}

This task installs and configures the newly created VM ready for the Squid installation

1.	In the vSphere Web Client, select the **VM** just created, which is Proxy01; and then click the **Summary** tab.
2.	Click **"Play"** to power on the VM.
3.	The VM powers on and boot from the CentOS 7 ISO. Start either a **Remote Console or Web Console** to the VM. You must install Remote Console and the system that is running the web browser must resolve the vSphere ESXi hosts by name.
4.	On the Welcome to CentOS 7 screen, select your required language and click **Continue**.
5.	At the **LOCALIZATION** screen, click **DATE & TIME** and select your time zone and then click **Done**.
6.	At the **LOCALIZATION** screen, click **KEYBOARD** to change from the default, if required and then press **Done**.
7.	At the **LOCALIZATION** screen, click **INSTALLATION DESTINATION**, click the **VMware virtual disk** icon, and then click **Done**.
8.	At the **LOCALIZATION** screen, click **NETWORK & HOSTNAME**, change the host name to your chosen hostname for example, Proxy01.
9.	Click **Configure**, then **IPv4 Settings**. In the **Method** box, select **Manual**.
10.	Click **Add** to insert _Address Netmask_ and _Gateway_ from _Table 1 – Deployment Values_.
11.	Enter the _DNS server IP address_ from Table 1 – Deployment Values.
12.	Click **Routes** and add the following static routes; _10.0.0.0/8 and 161.26.0.0/16_ with a gateway IP address of the _BCR IP address_ from Table 1 Deployment Values, as the gateway. This static route allows the proxy server to reach the DNS server.
13.	Click **Save** and then ensure that the Ethernet interface is On and showing as connected. Click **Done** and **Begin Installation**.
14.	As the installation continues, set a root password and set up a user.
15.	When the installation is complete, log in as the user and then enter the command _ping vmware.com_. The name is resolved to an IP address and you receive a response. If you do not get responses check; IP addresses, firewall rules and NAT settings.

#### Installing and configuring Squid
{: #vum-init-config-install-cfg-squid}

Squid does not have any minimum hardware requirements, but the amount of RAM might vary according to the users that are accessing the internet through your proxy and the objects that are stored in the cache. As the proxy server is accessed only by VUM and the cache is not enabled, only a small VM is configured.

1. Using either the Web Console or Remote Console from the vSphere Web Client, log in to the proxy server as the user and then `su` to root.
2. Before you install any packages, you must use the following command to update the system and packages:
   `yum -y update`

3. To install Squid, you must install EPEL repository to the system because Squid is not available in the default yum repository. Run the following command to install the EPEL repository:
   `yum -y install epel-release`

4. Update and clean by using the following commands:

   `yum -y update`
   `yum clean all`

5. Squid is installed by using the `yum -y install squid` command.
6. After installed, start Squid immediately by using the `systemctl start squid` command.
7. Run the `systemctl enable squid` command to automatically start Squid at boot time.
8. Run the `systemctl status squid` command to ensure that Squid is running.
9. The CentOS firewall needs to allow access to the Squid port, TCP 3128 by using the `firewall-cmd –add-port=3128/tcp –permanent` command.
10. To save the rule and restart the service, use the `firewall-cmd –reload` command.

## Setting up VUM initially
{: #vum-init-config-init-setup-vum}

Configure VUM to use the proxy server to access the repositories on the internet.
1. In the vSphere Web Client, go to **Home** > **Update Manager**. Click your vCenter Server.
2. Select the **Manage** tab and click **Settings**.
3. Select **Download Settings** and then under _Proxy settings_ click **Edit**.
4. Check the **Use Proxy** box and enter the _proxy server IP address_ and _port 3128_, click **OK**. The Connectivity Status changes to _Validating_ and then to _Connected_.

   Do not be concerned if you receive the ``Some URLs have been accessed successfully, but others are inaccessible`` message when you test the connection to the proxy server.
   {: note}

5. Click **Download Now**. When the downloaded is completed, it is displayed in the **Recent Tasks** pane.
6. If this activity fails, reboot the VCSA:
   1. Log in to the VCSA management interface at `https://vcsaFQDN:5480` as **root**.
   2. Click **Summary** and click **Reboot**.
   3. In the confirmation box, click **Yes** to confirm the operation.

**Next topic:** [Collecting the metadata ](/docs/vmwaresolutions?topic=vmwaresolutions-vum-metadata)

## Related links
{: #vum-init-config-related}

* [VMware HCX solution architecture](/docs/vmwaresolutions?topic=vmwaresolutions-hcx-archi-intro#hcx-archi-intro)
* [{{site.data.keyword.vmwaresolutions_short}} Demos](https://www.ibm.com/demos/collection/IBM-Cloud-for-VMware-Solutions/) (demonstrations)
