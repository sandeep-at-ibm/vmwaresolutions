---

copyright:

  years:  2016, 2019

lastupdated: "2018-11-19"

---

# Initial configuration

The IC4VS automation configures the VCSA with a default gateway set to the {{site.data.keyword.cloud}} Backend Customer Router (BCR). However, there's no route to the internet via the BCR. The standard route to the internet from the VMware vCenter Server on {{site.data.keyword.cloud_notm}} instance is via the Management ESG. As it isn't advised to change the configuration of the VCSA or the Management ESG, a proxy server implementation on the customer subnet is recommended to enable VUM.

This approach means that you don't have to reconfigure the VCSA or the Management ESG, however, a small virtual machine (VM) or appliance must be installed. A proxy server is a system, which sits between two endpoint devices and acts as an intermediate device. In this case, it sits between VUM and the update servers at VMware.

When VUM requests a resource from the update server at VMware, the request is sent to the proxy server first and the proxy server then sends the request to the update server. After the resource is obtained by the proxy server, it sends the resource to VUM. A proxy server can be used to facilitate security, administrative controls, and caching services.

This document describes the use of a proxy server based on CentOS and Squid. Squid Proxy is an open source caching proxy for the web and supports many protocols that include HTTP and HTTPS. A number of VM and appliance-based proxies are available, and you must select the appropriate one based on your enterprise’s requirements and install and configure following the vendor’s guidance. Clients electing to use a CentOS/Squid implementation should continue with the following process.

* Download the CentOS ISO to a jump server
* Create a vCenter Library
* Upload the ISO to the vCenter Library
* Create a VM, install, and configure CentOS and install Squid

Before you can start this task, you need to collect information to populate Table 1. Review the suggested values and ensure that they are appropriate for your enterprise. This configuration is based on a small proxy for VUM only that uses CentOS-Minimal and Squid.

Table 1. Deployment values

| Parameter | Suggested Values | Notes |
|:--------- |:-------------- |:------ |
| Proxy CPU | 1 vCPU | Squid has no minimum requirements |
| Proxy RAM | 2 GB | Squid has no minimum requirements |
| Proxy Disk | 25 | GB	Squid has no minimum requirements |
| Hostname | Proxy01 | |
| Address | proxy ip | A spare IP address must be used from the Customer, private portable subnet assigned during the provisioning process. Only two IP addresses would have been reserved on this subnet; one for the BCR and the other for the customer-esg
| Netmask | 255.255.255.192 | |
| Gateway| customer-nsx-edge private uplink ip | This is the default gateway setting for the proxy server, which is the private uplink IP address of customer-nsx-edge. The IP address can be found by reviewing the **Settings** tab for **customer-nsx-edge**. |
| DNS Server | AD/DNS ip | This IP address can be found on the instance page in the {{site.data.keyword.vmwaresolutions_short}} console, the **Deployed Instances** page. |
| BCR IP | bcr ip | This is the IP address of the {{site.data.keyword.cloud_notm}} Backend Customer Router and is the gateway for 10.0.0.0/8 and 161.26.0.0/16. This address is used in a static route in the proxy server so that it can reach the VCSA and the AD/DNS server. |

## Configuring NSX

NSX Customer ESG firewall and NAT settings are required to enable proxy server traffic.

### Firewall

1. Go to **Home** > **Networking & Security**.
2. Select **NSX Edges**, customer-nsx-edge, and then **Firewall**.
3. Click the **+** symbol and add a firewall rule.
4. Supply the required parameters as noted in the following table. The new firewall rule must come before the last rule, the Default Deny rule.

Table 2. Firewall rule

| Parameter | Suggested Values |
|:--------- |:-------------- |
| Name | Outbound Proxy01 |
| Type | User |
| Source | proxy server ip |
| Destination | any |
| Service | HTTP/HTTPS/ICMP Echo |
| Action | Accept |

After parameters are supplied, click **Publish Changes**.

### Installing and configuring a proxy server

The following process deploys a VM to host CentOS and Squid from the Content Library and consists of the following steps. It assumes that you have a Windows VSI provisioned for use as a jumpbox and that you are using Remote Desktop Protocol to connect to the VSI’s public interface:

* Download the CentOS-Minimal ISO file
* Configure a vCenter Content Library and populate it with the CentOS ISO file
* Configure the Proxy VM, install CentOS and Squid

### Downloading the CentOS-Minimal ISO file

Using a browser on your jump-server download the CentOS-Minimal ISO file from [CentOS](https://www.centos.org/download/). Note that {{site.data.keyword.cloud_notm}} maintains a mirror of many popular Linux distributions. This mirror is only available only on the private network, and the CentOS ISOs are available at the following address: `http://mirrors.service.softlayer.com/centos/7/isos/x86_64/`

### Configuring a content library and populating it with the CentOS ISO file

Create a local vCenter content library. The library is accessible only in the vCenter Server instance where it is created. Populate the library with templates and ISOs required to deploy VMs.

1. Via the vSphere Web Client, navigate to **Home** > **Content library** > **Objects** > **Create a new content library** > **Create subscribed library on the vCenter**.
2. Enter a name for the content library, for example, ISO, and in the Notes text box, enter a description for the library and click **Next**.
3. Select **Local content library** and click **Next**.
4. Select a datastore and then click a suitable datastore, for example, vsanDatastore.
5. Review the information on the **Ready to Complete** page and click **Finish**.

### Configuring the Proxy VM, install CentOS and Squid

This activity has the following tasks:

*	Create a New VM
*	Install CentOS
*	Install Squid

#### Create a New VM

This task creates a new VM ready for use as the proxy server. The settings from Table 1 Deployment Values should be used to populate the configuration.

1.	Via the vSphere Web Client, navigate to **Home** > **VMs and Templates**.
2.	In the Navigator pane, click **datacenter1** and then right-click and select; **New Virtual Machine** > **New Virtual Machine**.
3.	Select **Create a new Virtual Machine** and then click **Next**.
4.	Enter a Name for the VM, for example, Proxy01, and select **datacenter1**, then click **Next**.
5.	Select **cluster1** and then click **Next**.
6.	Select an appropriate datastore for example, vsanDatastore and click **Next** and **Next** again.
7.	In **Guest OS Family** select **Linux** and in **Guest OS version** select **CentOS 7 (64-bit)** and click **Next**.
8.	Set **CPU to 1**, **Memory to 2048 MB** and **New Hard disk to 25 GB**. Select **Content Library ISO File** and then **CentOS-7-x86_64-Minimal**, click **OK** and the tick the **Connected** box.
9.	In the New device box, select **Network** and then click **Add**.
10.	Select the **SDDC-DPortGroup-Mgmt** network and ensure that the Connect checkbox is ticked, click **Next**.
11.	Review and click **Finish**.

#### Install CentOS

This task installs and configures the newly created VM ready for the Squid installation

1.	In the Navigator pane of the vSphere Web Client select the **VM** just created, Proxy01 and then select the **Summary Tab**.
2.	Click **"Play"** to power on the VM.
3.	The VM powers on and boot from the CentOS 7 ISO. Start either a **Remote Console or Web Console** to the VM. You must install Remote Console and the system that is running the web browser must resolve the vSphere ESXi hosts by name.
4.	On the Welcome to CentOS 7 screen, select your required language and click **Continue**.
5.	At the **LOCALIZATION** screen, click **DATE & TIME** and select your time zone and then click **Done**.
6.	At the **LOCALIZATION** screen, click **KEYBOARD** to change from the default, if required and then press **Done**.
7.	At the **LOCALIZATION** screen, click **INSTALLATION DESTINATION**, click the **VMware virtual disk icon** and then click **Done**.
8.	At the **LOCALIZATION** screen, click **NETWORK & HOSTNAME**, change the Host name to your chosen hostname for example, Proxy01.
9.	Click **Configure**, then **IPv4 Settings**. In the **Method** box, select **Manual**.
10.	Using the **Add** button insert _Address Netmask_ and _Gateway_ from _Table 1 – Deployment Values_.
11.	Enter the _DNS server IP address_ from Table 1 – Deployment Values.
12.	Click the **Routes** button and add the following static routes; _10.0.0.0/8 and 161.26.0.0/16_ with a gateway IP address of the _BCR IP Address_ from Table 1 Deployment Values, as the gateway. This static route allows the proxy server to reach the DNS server.
13.	Click **Save** and then ensure that the Ethernet interface is On and showing as connected. Click **Done** and **Begin Installation**.
14.	As the installation continues, set a root password and set up a user.
15.	When the installation is complete, log in as the user and then enter the command _ping vmware.com_. The name is resolved to an IP address and you receive a response. If you do not get responses check; IP addresses, firewall rules and NAT settings.

#### Install and configure Squid

Squid does not have any minimum hardware requirements, but the amount of RAM might vary according to the users that are accessing the internet through your proxy and the objects that are stored in the cache. As the proxy server is accessed only by VUM and the cache is not enabled, only a small VM is configured.

1. Using either the Web Console or Remote Console from the vSphere Web Client, log in to the proxy server as the user and then `su` to root.
2. Before you install any packages, you must use the following command to update the system and packages:
  `yum -y update`

3. To install Squid, you need to install EPEL repository to the system as Squid is not available in the default yum repository. Run the following command to install the EPEL repository:
  `yum -y install epel-release`

4. Update and clean by using the following commands:

  `yum -y update`
  `yum clean all`

5. Squid is installed by using the following command: `yum -y install squid`.
6. After installed, start Squid immediately by using the following command: `systemctl start squid`.
7. Run the following command to automatically start Squid at boot time run the following command: `systemctl enable squid`.
8. Run the following command to ensure that Squid is running: `systemctl status squid`.
9. The CentOS firewall needs to allow access to the Squid port, TCP 3128 by using the following command:  `firewall-cmd –add-port=3128/tcp –permanent`.
10.	To save the rule and restart the service, use the following command: `firewall-cmd –reload`.

## The initial setup of VUM

Configure VUM to use the proxy server to access the repositories on the internet.
1. Using the vSphere Web Client navigate to **Home** > **Update Manager**. Click your vCenter Server.
2. Select the **Manage Tab** and click the **Settings** button.
3. Select **Download Settings** and then under _Proxy settings_ click **Edit**.
4. Check the **Use Proxy** box and enter the _proxy server IP Address_ and _port 3128_, click **OK**. The Connectivity Status changes to _Validating_ and then to _Connected_.
5. Click **Download Now**. In the _Recent Tasks_ pane you should see this activity complete.

### Related links

* [VMware HCX on {{site.data.keyword.cloud_notm}} Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (demonstrations)
