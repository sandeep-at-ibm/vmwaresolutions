---

copyright:

  years:  2020

lastupdated: "2020-10-22"

keywords: vmware solutions shared, get started shared, tech specs shared

subcollection: vmwaresolutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Operating VMware Solutions Shared
{: #shared_vcd-ops-guide}

## VMware vCloud Director tenant portal overview
{: #shared_vcd-ops-guide-port-ovv}

The VMware vCloud Director tenant portal is used for administration of your organization and to create and configure virtual machines (VMs), vApps, and networks within vApps.

You can also configure advanced networking capabilities that are provided by VMware NSX® for vSphere® within a vCloud Director environment. With the tenant portal, you can also create and manage catalogs, vApp, and virtual data center templates.

### Roles, permissions, and users
{: #shared_vcd-ops-guide-roles}

The tenant portal includes a preconfigured set of user roles and their rights. The roles that can access the tenant portal are created by default when an organization is created along with other roles that are created by the organization administrator. Users who are assigned the following organization roles can access the tenant portal. The objects that they see and the actions that they can take depend on the rights that are associated with a role.

* Organization Administrator
* Catalog Author
* vApp Author
* vApp User
* Console Access Only

For more information about roles and permissions, see [VMware Cloud Director Tenant Portal Roles and Rights](https://docs.vmware.com/en/VMware-Cloud-Director/10.1/VMware-Cloud-Director-Tenant-Portal-Guide/GUID-754BD24F-63C7-422F-83BC-BFA275CEDA8E.html){:external}.


#### Managing users
{: #shared_vcd-ops-guide-roles-procedures}

Use the tenant portal to create a user or change passwords or roles for an existing user. For more information on accessing the tenant portal, see [Log In to the VMware Cloud Director Tenant Portal](https://docs.vmware.com/en/VMware-Cloud-Director/10.1/VMware-Cloud-Director-Tenant-Portal-Guide/GUID-28972197-D45B-4156-A733-5966730B5E03.html){:external}.

For more information about creating and modifying tenant portal users, see [Managing users](https://docs.vmware.com/en/VMware-Cloud-Director/10.1/VMware-Cloud-Director-Tenant-Portal-Guide/GUID-FE38C285-7605-4473-870C-6AD44D8BF42E.html){:external}.

## Catalogs
{: #shared_vcd-ops-guide-catalogs}

A catalog is a container for vApp templates and media files in an organization. Organization administrators and catalog authors can create catalogs in an organization. Catalog contents can be shared with other users or organizations in the {{site.data.keyword.vmwaresolutions_full}} Shared installation. Or they can be published externally for access by organizations outside the VMware Solutions Shared installation.

VMware Solutions Shared contains private catalogs, shared catalogs, and externally accessible catalogs. Private catalogs include vApp templates and media files that you can share with other users in the organization. If a system administrator enables catalog sharing for your organization, you can share an organization catalog to create a catalog accessible to other organizations in the VMware Solutions Shared installation.

If a system administrator enables external catalog publishing for your organization, you can publish an organization catalog for access by organizations outside the VMware Solutions Shared installation. An organization outside the VMware Solutions Shared installation must subscribe to an externally published catalog to access its contents.

### VMware Solutions Shared public catalog
{: #shared_vcd-ops-guide-public-cat}

Each organization has access to the VMware Solutions Shared public catalog. The catalog contains IBM-compliant images that are configured, secured, and ready for use.

Review the following considerations for the VMware Solutions Shared public:

* Operating system licensing costs apply for usage. For more information about how commercial operating system license rentals are billed, see [VMware Solutions Shared pricing](/docs/vmwaresolutions?topic=vmwaresolutions-shared_pricing).
* Public templates that are configured to services on the IBM private network require an extra configuration step to enable VM access to the IBM Services network. For more information, see [Enabling VM access to {{site.data.keyword.cloud_notm}} Services by using the private network](/docs/vmwaresolutions?topic=vmwaresolutions-shared_vcd-ops-guide#shared_vcd-ops-guide-enable-access).
* Public templates require a minimum level of customization to establish the initial administrator password. For more information, see [Changing the guest OS customization properties of a VM](#shared_vcd-ops-guide-customization).

The public catalog contains vApp templates for the following components:

| Image | Version |
|---|---|
| CentOS | 7.x and 8.x |
| Microsoft Windows | 2019 Standard |
| Microsoft Windows | 2016 Standard |
| Red Hat Enterprise Linux | 8.1 |
| Red Hat Enterprise Linux | 7.7 |
{: caption="Table 1. vApp templates" caption-side="top"}

#### CentOS templates
{: #shared_vcd-ops-guide-public-cat-centos}

The CentOS templates that are provided in the public catalog have the following characteristics:

* Latest updates installed
* VMware tools installed
* YUM repository enabled configured to the IBM private network YUM repository
* NTP server that is configured to the IBM private network NTP Server

#### Microsoft Windows templates
{: #shared_vcd-ops-guide-public-cat-windows}

The Microsoft Windows templates that are provided in the public catalog have the following characteristics:
* Latest updates installed
* Windows update enabled configured to the IBM private network Windows update server
* VMware tools installed
* Windows Remote Desktop disabled
* Firewall activated
* Windows Defender activated
* NTP server that is configured to the IBM private network NTP Server
* Windows license configured to activate and receive updates by using the IBM Service Network Microsoft Key Management Server (KMS) and not the internet Microsoft KMS

#### Red Hat Enterprise Linux templates
{: #shared_vcd-ops-guide-public-cat-rhel}

The Red Hat Enterprise Linux templates that are provided in the public catalog have the following characteristics:

* Latest updates installed
* VMware tools installed
* Firewall activated
* NTP server that is configured to the IBM private network servers

After you deploy the VM on the tenant portal, register the Red Hat VM with your RHEL activation key in IBM RHEL Capsule Server. To register the Red Hat VM with your RHEL activation key, you must enable VM access to connect to the IBM service network. For more information, see [Enabling VM access to {{site.data.keyword.cloud_notm}} Services by using the private network](/docs/vmwaresolutions?topic=vmwaresolutions-shared_vcd-ops-guide#shared_vcd-ops-guide-enable-access).
{: important}

Complete the following steps to register the Red Hat VM with your RHEL activation key. For more information about accessing instance details, see [Procedure to view virtual data center instances](/docs/vmwaresolutions?topic=vmwaresolutions-shared_managing#shared_managing-viewing).


1. From the {{site.data.keyword.vmwaresolutions_short}} console, click the instance name in the **VMware Solutions Shared** instance table.
2. On the instance details page, locate and make note of the **Red Hat activation key**.
3. Run the following commands from the Red Hat VM.  
  1. ``rpm -ivh http://52.117.132.7/pub/katello-ca-consumer-latest.noarch.rpm``
  2. ``uuid= `uuidgen` ``  
  Where:  
  the character `` ` `` used around uuidgen is the grave accent or backtick.
  3. ``echo '{"dmi.system.uuid": "'$uuid'"}' > /etc/rhsm/facts/uuid_override.facts``
  4. ``cat /etc/rhsm/facts/uuid_override.facts``  
  Ensure the contents of the uuid_override.facts contains a generated UUID.
  5. ``subscription-manager register --org="customer" --activationkey="ACTIVATION_KEY" --force``  
  Where:  
  ``ACTIVATION_KEY`` is the Red Hat activation key that is located on the instance details page.  

You can still use another RHEL Capsule Server or a satellite server if you already have an RHEL subscription outside of IBM. Charges for the RHEL license are incurred against RHEL VMs that are running in a virtual data center instance.
{:note}

### Defining catalogs and policies
{: #shared_vcd-ops-guide-policies}

To create a catalog, you must have either the **Organizational Administrator** or **Catalog Author** tenant portal role.

For more information about defining catalogs and policies, see [Working with Catalogs](https://docs.vmware.com/en/VMware-Cloud-Director/10.1/VMware-Cloud-Director-Tenant-Portal-Guide/GUID-6424C4A7-EA95-49A0-B673-9DDB971AB566.html){:external}.

### Uploading your media or templates
{: #shared_vcd-ops-guide-customer}

OVF packages can be uploaded to a catalog as a vApp template to make the template available to users. For more information, see [Create a vApp Template from an OVF File](https://docs.vmware.com/en/VMware-Cloud-Director/10.1/VMware-Cloud-Director-Tenant-Portal-Guide/GUID-5EA412C4-179A-42CF-9B30-1B81C23551E6.html).

Media files, such as ISO disc images and FLP floppy drive images, can be uploaded to a catalog as a media file. For more information, see [Working with Media Files](https://docs.vmware.com/en/VMware-Cloud-Director/10.1/VMware-Cloud-Director-Tenant-Portal-Guide/GUID-A7530A4B-F782-4848-90FC-BBDE41E3AE85.html).

The maximum import size is 750 GB. Large image files or templates might take extended time to upload. Contact IBM Support for assistance with files larger than 750 GB. For more information, see [Contacting IBM Support](/docs/vmwaresolutions?topic=vmwaresolutions-trbl_support).
{:note}

## Virtual machines
{: #shared_vcd-ops-guide-machines}

When you use the tenant portal, you can create a VM or provision a VM from a template.

For more information, see [Create a New Standalone Virtual Machine
](https://docs.vmware.com/en/VMware-Cloud-Director/10.1/VMware-Cloud-Director-Tenant-Portal-Guide/GUID-12E43116-1120-45FA-A1E7-AEBEE61373C1.html){:external}.

### Customizing virtual machine properties
{: #shared_vcd-ops-guide-cust-properties}

You can edit the properties of a VM, including the virtual machine name and description, hardware and network settings, and guest operating system settings.

For more information about working with VMs, see [Working with virtual machines](https://docs.vmware.com/en/VMware-Cloud-Director/10.1/VMware-Cloud-Director-Tenant-Portal-Guide/GUID-DF0C111D-B638-4EC3-B805-CC33994F8D53.html){:external}.

If you use the tenant portal **Password Reset** field to change your Windows Administrator password, ensure that you adhere to Windows complexity requirements. If you change the password in the tenant portal without doing so, the password does not work in the Windows VM template.
{:important}


#### Changing the general properties of a virtual machine
{: #shared_vcd-ops-guide-change-properties}

You can change the name, description, storage policy, and other general properties of a VM.

##### Switching between storage properties
{: #shared_vcd-ops-guide-change-properties-storage}

1. Power off the VM. For more information, see [Power off a Virtual Machine](https://docs.vmware.com/en/VMware-Cloud-Director/10.0/com.vmware.vcloud.tenantportal.doc/GUID-2323B049-4E36-4510-999E-F2D4A77AC0F9.html){:external}.
2. Change the storage policy. For more information, see [Change the General Properties of a Virtual Machine
](https://docs.vmware.com/en/VMware-Cloud-Director/10.0/com.vmware.vcloud.tenantportal.doc/GUID-8301D672-8333-4FD2-B132-2D4A42E11216.html){:external}.
3. After the VM is moved to the new storage policy, power on the VM. For more information, see [Power on a Virtual Machine](https://docs.vmware.com/en/VMware-Cloud-Director/10.0/com.vmware.vcloud.tenantportal.doc/GUID-33C22124-A610-4C3E-8F40-26CAC570F958.html){:external}.

#### Changing the hardware properties of a virtual machine
{: #shared_vcd-ops-guide-hardware}

You can change the hardware properties of a VM, number of vCPUs, memory, hard disk allocation, and network configuration.

#### Changing the Guest OS Customization properties of a virtual machine
{: #shared_vcd-ops-guide-customization}

Guest OS customization is optional for all platforms. It is required for VMs that must join a Windows domain when the VMs are being powered on.

When you use an IBM template to create the VM, use the **Guest OS Customization** pane to acquire or set the unique password for the OS instance. Ensure that the **Enable guest customization** option is selected and then use one of the **Password Reset** options to establish the initial administrator credential.

For more information, see [Change the Guest OS Customization Properties of a Virtual Machine
](https://docs.vmware.com/en/VMware-Cloud-Director/10.0/com.vmware.vcloud.tenantportal.doc/GUID-2B7A04E8-7479-4EE9-99B0-1A46751BE46F.html){:external}.

#### Changing the advanced properties of a virtual machine
{: #shared_vcd-ops-guide-advanced}

In the Advanced settings, you can configure the resource allocation settings (shares, reservation, and limit) to determine the amount of virtual CPU (vCPU), memory, and storage resources provided for a VM.

For more information, see [Edit Virtual Machine Properties](https://docs.vmware.com/en/VMware-Cloud-Director/10.1/VMware-Cloud-Director-Tenant-Portal-Guide/GUID-FA8C101E-241E-41A5-A3C3-83BDBB4467F1.html){: external}.

### Using IBM templates
{: #shared_vcd-ops-guide-ibm-templates}

If the VM is deployed from the IBM templates that are provided in the public catalog, the initial password that was generated during power-on is required when you first log in to the VM. You can find this password on the VM details page.

If you use the tenant portal **Password Reset** field to change your Windows Administrator password, ensure that you adhere to Windows complexity requirements. If you change the password in the tenant portal without doing so, the password does not work in the Windows VM template.
{:important}

1. From the **Guest OS Customization** pane, click **EDIT**.
2. From the **Edit Guest Properties** pane, locate the password in the **Specify password** field.
2. After a successful login with the initial password, return to the **Edit Guest Properties** pane to reset the password and log in again with the new password.

## vApps
{: #shared_vcd-ops-guide-vapps}

A vApp consists of one or more VMs that communicate over a network and use resources and services in a virtual data center. Create the vApp, then add VMs and networks.

You can now add VMs and networks to the vApp.

For more information about vApps, see [Working with vApps](https://docs.vmware.com/en/VMware-Cloud-Director/10.1/VMware-Cloud-Director-Tenant-Portal-Guide/GUID-AC48FB5E-4ADC-4835-AACE-B949B297A147.html){: external}.

## Networking
{: #shared_vcd-ops-guide-networking}

Every VMware Solutions Shared virtual data center comes configured with one edge gateway with five public IP addresses and one private IBM Services network IP address. You can open an {{site.data.keyword.cloud_notm}} Support ticket to request five additional public IP addresses or an entire subnet for your virtual data center. Include the following details in your support ticket:

* Instance region and location
* Organization ID
* Virtual data center name
* Number of additional IPs required

For more information about opening a support ticket, see [Contacting IBM Support](/docs/vmwaresolutions?topic=vmwaresolutions-trbl_support).

The edge gateway services are customer configurable and require configuration to allow network traffic in and out of their organization virtual data center. Configuration is required for access to the internet and the IBM Services network. The five public addresses are used for public facing vApps for inbound and outbound public internet traffic. The service address is used for access to {{site.data.keyword.cloud_notm}} infrastructure services on the {{site.data.keyword.cloud_notm}} internal private network, including:

* NTP
* Windows operating system licensing and updates
* Red Hat operating system licensing and updates
* Cloud Object Storage

There are two types of organization virtual data center networks available in the VMware Solutions Shared virtual data center: routed or internal.

### Routed network
{: #shared_vcd-ops-guide-routed}

Accessible only by the same organization virtual data center. Only VMs in this organization virtual data center can connect to this network. This network also provides controlled access to an external network. An organization administrator can configure Network Address Translation (NAT), firewall, and VPN settings to make specific VMs accessible from the external network.

### Internal or isolated network
{: #shared_vcd-ops-guide-internal}

Accessible only by the same organization virtual data center. Only VMs in this organization virtual data center can connect to and see traffic on the internal organization virtual data center network.

The isolated organization virtual data center network provides an organization virtual data center with an isolated, private network that multiple VMs and vApps can connect to. This network provides no connectivity to VMs outside the organization virtual data center. VMs that are outside of the organization virtual data center have no connectivity to VMs that are in the organization virtual data center.

### Creating a network
{: #shared_vcd-ops-guide-create-network}

Create a sample network topology that includes: configuring DHCP services, defining Source NAT (SNAT) and Destination NAT (DNAT) rules, and creating firewall rules on the edge gateway to allow access to the internet.

![{{site.data.keyword.vmwaresolutions_short}} Network topology](../images/vcd-sample-topology.svg "{{site.data.keyword.vmwaresolutions_short}} Network topology"){: caption="Figure 1. {{site.data.keyword.vmwaresolutions_short}} Network topology" caption-side="bottom"}

#### Creating a routed organization virtual data center network
{: #shared_vcd-ops-guide-routed-organization}

1. From the tenant portal, and click **Data Centers**.
2. On the main page, under **Virtual Data Center**, click the virtual data center where the network is created.
3. Under the **Networking** section in the left pane, click **Networks**.
4. Click **NEW** in the main pane.
5. Select **Routed** and click **Next**.
6. Provide details for **Name** and **Gateway CIDR**. For example, Name:``Web`` Gateway CIDR:``192.168.100.1/24``
7. (Optional) Enter a description of the organization virtual data center network.
8. (Optional) To make the organization virtual data center network available to other organization virtual data centers within the same organization, set the Shared option. One use case is when an application within an Organization virtual data center has a reservation or allocation pool set as the allocation model. In this case, it might not have enough room to run more VMs. As a solution, you can create a secondary Organization virtual data center with On-demand and run more VMs on that network on a temporary basis. Then, click **Next**.  
  **Note**: Virtual data center instances can only share networks if they are in the same region.  
9. Select the edge. This is the edge that was created when the virtual data center was created.
10. From the **Interface Type** list, select **Distributed** and click **Next**.
11. (Optional) Enter a static IP range and click **ADD**. If static IP addresses are required for the defined subnet, enter the range of addresses. The IP addresses should be from the same subnet as the Gateway CIDR. Click **Next**.
12. (Optional) If known, provide DNS details. Otherwise, click **Next**.
13. Review the **Ready to Complete** page and click **Finish**.
14. (Optional) To create another Organization virtual data center network, repeat the previous process. Give the network a different **Name**: ``App`` and a different **Gateway CIDR**: ``192.168.101.1/24``.

#### Validate that the network is connected to the Edge
{: #shared_vcd-ops-guide-validate-network}

1. From the tenant portal, and select **Data Centers**.
2. Under **Virtual Data Center**, click the virtual data center for that edge gateway.
3. In the left pane under **Networking**, click **Edges**.
4. In the right pane, click the edge then click **SERVICES**.
5. Click the **Routing** tab, then click **Static Routes**.
6. Validate the Organization virtual data center networks that are defined earlier are listed. The Next Hop shows `52.117.132.2`, which is the internal interface of the edge gateway.

#### Edge DHCP configuration
{: #shared_vcd-ops-guide-configure-dhcp}

Optionally, you can configure DHCP on the edge gateway to automatically assign IP addresses to the VMs connected to the Organization virtual data center networks. This is not necessary if using static IP addresses.

1. From the tenant portal, and select **Data Centers**.
2. Click the virtual data center for that edge gateway.
3. In the left pane under **Networking** click **Edges**, then **SERVICES**.
4. Click the **DHCP** tab.
5. Under **DHCP Pools** click **+** to add a pool.
6. Define the IP Range, which is a range from the Organization virtual data center network that is attached to the edge.
7. Define the primary and secondary name servers, if available. These names can be defined or changed later.
8. Define the default gateway, which is the gateway CIDR or the Organization virtual data center network that is attached to the edge.
9. Define the subnet mask and set the lease time. Click **KEEP**.
10. Repeat the process for additional Organization virtual data center networks that are attached to the edge that requires DHCP services.
11. Set the DHCP service status to enabled.
12. Click **Save changes**.

#### Connect the VMs to the network
{: #shared_vcd-ops-guide-connect-vm}

Stand-alone VMs, or VMs in a vApp, can connect to an Organization virtual data center network.  

1. From the tenant portal, click **Data Centers**.
2. Under **Virtual Data Center**, click the virtual data center where the VMs are located.
3. Under **Compute** on the left pane, click **Virtual Machines**.
4. Click **Details** for the VM you want to connect the network to.
5. Scroll down and expand the **Hardware** section.
6. Scroll down to **NICs** and click **Add** to add a new network interface.
7. Select the new network interface.
8. Expand **Network** and select one of the available networks.
9. Check the connect box and select the method that you want to use to assign IP addresses under **IP mode**. Click **Save**.
10. Repeat this process for any other VMs. Click **Save**.

After the VMs are connected to the Organization virtual data center network, they are able to communicate with each other. You can ping from one of the VMs to another to test. If there’s no response from the ping command, check the OS firewalls to see whether ICMP is allowed.

#### Enable inbound and outbound traffic
{: #shared_vcd-ops-guide-enable-traffic}

To enable VMs on the Organization virtual data center Network to reach an external network, you must configure a SNAT (Source Network Address Translation) rule and firewall policy to allow the VM traffic outbound. To allow inbound traffic from an external network, you must configure a DNAT (Destination Network Address Translation) rule and firewall policy.

Before creating our Firewall and NAT Rules, we should capture some information that will be used in subsequent steps.  
1. From the tenant portal, click **Data Centers**.
2. On the main page, under **Virtual Data Center**, click the virtual data center for that edge gateway.
3. In the left pane under **Networking**, click **Edges**.
4. Under Configuration, select **Gateway Interfaces**. Copy the values in the table for the tenant external and the Service networks. With the tenant external addresses, we can route to the external network, and with the service network addresses, we can route to the IBM private network.
5. From the {{site.data.keyword.vmwaresolutions_short}} Shared Resources page, copy the public IP addresses that were assigned to your virtual data center.

##### Create the Organization virtual data center network firewall rule to allow access to the external network
{: #shared_vcd-ops-guide-create-vdc-network-rule-extnetwork}

1. From the tenant portal, click the menu icon at the top of the page and then select **Data Centers**.
2. On the main page, under **Virtual Data Center**, click the virtual data center for that edge gateway.
3. In the left pane under **Networking**, click **Edges** and then **SERVICES**.
4. On the Firewall tab, under Firewall Rules, click the plus sign **+**.
5. Define the name, source, destination, any specific services, and action.  
  1. Provide a **Name**.
  2. Provide the source. The source may be an IP address, a range of addresses or an object. In the **Source** column click the **+** in the upper-right corner of the cell when you hover your mouse in the field.
  3. In the **Browse objects of Type:** dropdown, select **Org Vdc Networks**. Select the organization virtual data center network that you created as the Source. Click the right arrow to move the organization virtual data center network into the **Filter** column.
  4. Keep the remaining default settings.
  5. Set the Action to **Accept**.
  6. Click **KEEP**.

   To define a source IP address or range, click the **IP** in the source cell and set the IP address or range to allow everything on that subnet. For example, ``192.168.100.2`` or ``192.168.100.0/24``. Destination and services are set to **Any** when you choose the defaults.
6. Click **Save changes**.

##### Source NAT definitions to the external network
{: #shared_vcd-ops-guide-source-nat-ext}

A source NAT rule is necessary to allow traffic from the organization virtual data center network outbound to the internet.

1. From the tenant portal, click the menu icon at the top of the page and then select **Data Centers**.
2. On the main page, under **Virtual Data Center**, click the virtual data center for that edge gateway.
3. In the left pane under **Networking**, click **Edges** and then **SERVICES**.
4. From the edge gateway services pane, click the **NAT** tab.
5. Under the **NAT44 Rules**, click **+ SNAT Rule**.
  1. In the **Applied On:** dropdown, select the organization virtual data center external network.
  2. In the **Original Source IP/Range**, enter your organization virtual data center Gateway CIDR.
  3. In the **Translated Source IP/Range**, click the **SELECT** button. In the **Select IP Address** Network dropdown select the external network and choose one of the external network addresses that were assigned to your virtual data center.
  4. (Optional) Enter a destination port.
  5. (Optional) Enter a description. A description can be useful to identify the SNAT rule at a later date.
  6. Set to **Enabled**.
  7. (Optional) Enable logging.
  8. Click **KEEP**.
6. Click **Save changes**.

##### Create the Organization virtual data center network firewall rule to allow access to the {{site.data.keyword.cloud}} Services Network
{: #shared_vcd-ops-guide-create-vdc-network-rule-ibm-services-network}

1. From the tenant portal, click the menu icon at the top of the page and then select **Data Centers**.
2. On the main page, under **Virtual Data Center**, click the virtual data center for that edge gateway.
3. In the left pane under **Networking**, click **Edges** and then **SERVICES**.
4. On the Firewall tab, under Firewall Rules, click the plus sign **+**.
5. Define the name, source, destination, any specific services, and action.  
  1. Provide a **Name**.
  2. The source may be an IP address, a range of addresses, or an object. In the **Source** column click the **+** in the upper-right corner of the cell when you hover your mouse in the field.
  3. In the **Browse objects of Type:** dropdown, select **Org Vdc Networks**. Select the organization virtual data center network created as the Source. Click the right arrow to move the organization virtual data center network into the right-hand filter column.
  4. Click **KEEP**.
  5. The destination may be an IP address, a range of addresses, or an object. In the **destination** column click the **+** in the upper-right corner of the cell when you hover your mouse in the field.
  6. In the **Browse objects of Type:** dropdown, select **Gateway Interfaces**. Select the service network available to your virtual data center. Click the right arrow to move the service network into the right-hand filter column.
  7. Set the **Action** to **Accept**.
   - Click **KEEP**.

   To define a destination IP address or range, click the **IP** in the destination cell and set the IP address or range to allow everything on that subnet. For example, ``192.168.100.2`` or ``192.168.100.0/24``.
6. Click **Save changes**.

##### Source NAT definitions to the IBM Service Network (Private)
{: #shared_vcd-ops-guide-source-nat-int}

A source NAT rule is necessary to allow traffic from the organization virtual data center network into the 	{{site.data.keyword.cloud_notm}} Service Network. This would be used to enable VM access to 	{{site.data.keyword.cloud_notm}} Services such as update servers, DNS servers, NTP servers, or to get to the {{site.data.keyword.cloud_notm}} Object Storage.

1. From the tenant portal, click the menu icon at the top of the page and then select **Data Centers**.
2. On the main page, under **Virtual Data Center**, click the virtual data center for that edge gateway.
3. In the left pane under **Networking**, click **Edges** and then **SERVICES**.
4. From the edge gateway services pane, click the **NAT** tab.
5. Under the **NAT44 Rules**, click **+ SNAT Rule**.
  1. In the **Applied On:** dropdown, select the service network.
  2. In the **Original Source IP/Range**, enter your organization virtual data center Gateway CIDR.
  3. In the **Translated Source IP/Range**, click the **SELECT** button. In the **Select IP Address** Network dropdown, select the service network and choose one of the service network addresses that were assigned to your virtual data center.
  4. (Optional) Enter the destination IP addresses.
  5. (Optional) Enter the destination port.
  6. (Optional) Enter the description. A description can be useful to identify the SNAT rule at a later date.
  7. Set to **Enabled**.
  8. (Optional) Enable logging.
  9. Click **KEEP**.
6. Click **Save changes**.

Depending on the VM operating system and network configuration, and if the DHCP services have been enabled on the Edge, a simple test for internet connectivity is to log in to one of the VMs that are attached to the network for which the firewall and DNAT rules were defined and:  
* For a Windows VM, renew the DHCP lease. Open a command prompt and issue the `ipconfig /renew` command.
* For a Linux VM, type `systemctl restart NetworkManager.service`. Depending on the type and version of Linux, this command might vary. From the command line, ping ``8.8.8.8`` or ``9.9.9.9``. If everything is configured correctly, you receive a reply. If the name resolution is required and no DNS server was defined yet, you can configure either ``9.9.9.9`` or ``8.8.8.8`` on the VM, edit the DHCP pool and define it there.

##### Destination NAT definition and port forwarding
{: #shared_vcd-ops-guide-destination-nat}

A destination NAT allows an outside host, in this case on the internet, to connect to an inside host on the Organization virtual data center network. The destination NAT maps one IP address or port to another IP address or port. The following instructions are an example of configuring DNAT and port forwarding to allow a Windows remote desktop connection to a Windows VM in the Organization virtual data center. Port forwarding is optional.

1. From the tenant portal, click **Data Centers**.
2. Under **Virtual Data Center** on the main page, click the virtual data center that contains the edge gateway for the VMs on which we want to allow connectivity.
3. In the left pane under **Networking**, click **Edges**.
4. In the main pane click the edge, then **SERVICES**.
5. Click the **NAT** tab, under **NAT44 Rules** click **+ DNAT RULE**.
6. Click the **Applied On** arrow and select the ``<datacenter>-w<idx>-tenant-external`` interface, for example, ``dal13-w02-tenant-external``.
7. The **Original IP/Range** is one of the IPs from the Suballocated Public IP address range. Click the **SELECT** button, and select an IP from the **IP Address** menu. This is the `tenant-external IP address` referenced in future steps. Click **KEEP**.
8. (Optional) For port forwarding, click the **Protocol** dropdown arrow and select **TCP**.
9. The **Original Port** in this example is ``8000``. Ports below 1024 are reserved. Select a port that is not previously used with the original IP address or range.
10. If ICMP has been selected in the **Protocol** dropdown, the **ICMP Type** can be selected.
11. The **Translated IP/Range** is the IP address of the VM on the private Organization virtual data center that you want to connect.  
12. The **Translated Port** is the port on the previous VM that the servicer is listening on. In the Windows RDP example, port 3389 is the default remote desktop port.
13. (Optional) Provide a description, then click **KEEP**.
14. Click **Save changes**.
15. Click the **Firewall** tab, and click **+** to add a new Firewall rule.
16. (Optional) If you want to restrict access to the internal Organization virtual data center VM to a specific IP or IP range, the **Source** may be defined.
17. Set the Destination to the `tenant-external IP address` used for **Original IP/Range** in the DNAT rule.
18. Click **+** in the Service column and set the **Protocol** to TCP and the **Destination Port** to the `tenant-external IP address` used in the DNAT rule. In our example, port ``8000`` is used.
19. Click **Save changes** in the upper left corner.
20. Exit the **Edge Gateway** services pane.

To test the configuration, use the remote desktop client and connect to the ``tenant-external IP address:port number`` as the destination in the **Computer** field.

#### Enabling VM access to {{site.data.keyword.cloud_notm}} Services by using the private network
{: #shared_vcd-ops-guide-enable-access}

You can configure vApps and VMs running inside of the virtual data center to use the {{site.data.keyword.cloud_notm}} private network to access {{site.data.keyword.cloud_notm}} services. Accessing {{site.data.keyword.cloud_notm}} services through a private network can save on outbound public networking costs and can provide a higher degree of reliability and security. Virtual data centers route to the {{site.data.keyword.cloud_notm}} private network through a virtual data center service network that is configured as an available external network on virtual data centers edge.

VMware Solutions Shared fully enables access to IaaS endpoints for {{site.data.keyword.cloud_notm}} Virtual Private Cloud (VPC). For more information, see [Endpoints available for VPC](/docs/vpc?topic=vpc-service-endpoints-for-vpc).

The following services are available:

| Service | IP address (Endpoint) |
|---|---|
| Microsoft Windows Update Server | 52.117.132.5 |
| Microsoft Key Management Server | 52.117.132.4 |
| Red Hat Capsule Server | 52.117.132.7 |
| DNS | 161.26.0.10 (rs1.adn.networklayer.com) and 161.26.0.11 (rs2.adn.networklayer.com) |
| Ubuntu and Debian APT Mirrors | 161.26.0.6 (mirrors.adn.networklayer.com) |
| RHEL and CentOS YUM repo | 161.26.0.6 (mirrors.adn.networklayer.com) |
| NTP | 161.26.0.6 (time.adn.networklayer.com) |
| {{site.data.keyword.cloud_notm}} Object Storage | [s3.direct.xxx.cloud-object-storage.appdomain.cloud](/docs/vpc?topic=vpc-connecting-vpc-cos) |
{: caption="Table 2. Available services" caption-side="top"}

Enabling access to the service network is done in two edge configuration steps.

##### Adding the NAT rule
{: #shared_vcd-ops-guide-nat-rule}

Add a NAT rule for translating internal network addresses into the service network IP address space.
1. Log in to the VMware vCloud Director tenant portal.
2. Click the virtual data center **Edges** tab and open the single preconfigured edge.
3. In the **External Networks** section, click the **IP Allocations** link. Find the name of the service network and the IP address that is assigned for the service network interface from the table displayed. The format for the service network name is ``<datacenter>-w<idx>-service<idx>``, for example, ``dal13-w02-service02``.
4. Click **SERVICES** to open the Edge Gateway configuration page. Click the **NAT** tab and click **+ SNAT RULE** to add a SNAT rule.
5. Select the service network next to the **Applied on** field and add the IP addresses or range from one of the virtual data center internal networks to the **Original Source IP/Range** field.
6. In the **Translated Source IP/Range** field, click the **Select** button. From the **Network** dropdown, select the external network. The format for the external network name is ``<datacenter>-w<idx>-tenant-external``. For example, ``dal13-w02-tenant-external``. From the **IP Address** dropdown, select the external IP address you want to use.
7. Optionally, set the **Destination IP Address**, **Destination Port**, and **Description** fields.
8. Verify **Enabled** is selected and click **KEEP**.
9. Click **Save Changes**.

##### Adding the firewall rule
{: #shared_vcd-ops-guide-firewall-rule}

Add a firewall rule to allow the traffic from the internal network to the service network.
1. Click the **Firewall** tab and click **+** to add a firewall rule.
2. Add the IP addresses or range from your internal network to the **Source** field.
3. Add `52.117.132.1/24` in the **Destination** field.
4. Specify `Any` for the **Service** field and `Accept` for the **Action** field.
5. Click **Save changes**.

After the previous configuration is completed, you can use the supported {{site.data.keyword.cloud_notm}} services on the VMs in your virtual data center.

If your vApp or VM is deployed from the IBM templates that are provided in the public catalog, the services are already configured on the VM. To enable the connection, you must complete the previous steps in **Adding the NAT rule** and **Adding the firewall rule**.

#### Creating a vApp Network
{: #shared_vcd-ops-guide-vapp-network}

If you have not already done so, create a vApp containing at least two VMs. For more information, see [Working with vApps](https://docs.vmware.com/en/VMware-Cloud-Director/10.1/VMware-Cloud-Director-Tenant-Portal-Guide/GUID-AC48FB5E-4ADC-4835-AACE-B949B297A147.html){: external}.

1. From the tenant portal, click the menu icon at the top of the page and then select **Data Centers**.
2. From the main page under **Virtual Data Center**, click the virtual data center where you would like to create the vApp network.
3. In the right pane under **Compute**, click **vApps**.
4. Click **Details** on the vApp you would like to add a vApp network to.
5. Click the **Network** tab, and click **New** in the **vApp Fencing** section.
6. Select **vApp Network**.
7. Complete the **Name** and **Gateway CIDR** fields. For example, Name: ``Web`` and Gateway CIDR: ``192.168.33.1/24``.
8. (Optional) Provide the DNS information.
9. Leave the **Static IP Pools** section blank.
10. Set the slider to **Connect to an organization VDC network**.
11. Click **Add**.

## Configuring a private network endpoint
{: #shared_vcd-ops-guide-pne}

Every private network endpoint comes configured with one private network IP address that can be used to configure your virtual data center.

### Prerequisites for configuring a private network endpoint
{: #shared_vcd-ops-guide-pne-prereqs}

* You must have a running VM.
* The VM must be connected to a routed organization virtual data center network. For more information, see [Creating a routed organization virtual data center network](/docs/vmwaresolutions?topic=vmwaresolutions-shared_vcd-ops-guide#shared_vcd-ops-guide-routed-organization) and [Connect the VMs to the network](/docs/vmwaresolutions?topic=vmwaresolutions-shared_vcd-ops-guide#shared_vcd-ops-guide-connect-vm).
* You must have virtual routing and forwarding and service endpoints enabled on the account that the allowlisted IP or subnet belong to. For more information, see [Enabling VRF and service endpoints](/docs/account?topic=account-vrf-service-endpoint).

### Collecting network IP addresses
{: #shared_vcd-ops-guide-pne-IPs}

Collect the service network and private network IP addresses to configure the firewall and DNAT rules.

1. In the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. In the **VMware Solutions Shared** table, click on the virtual data center to configure.
3. In the **Private Network Endpoint** section, collect the **Service network IP** address and **Private network IP** address.

### Configuring firewall rules for the VMware NSX Edge Services Gateway
{: #shared_vcd-ops-guide-pne-firewall-rules}

The firewall rule allows traffic from the private network IP to go through your Edge Service Gateway. You may need to repeat this process (steps 5 to 10) to allow different traffic to enter your virtual data center, depending on which ports and protocols you need to open up.

1. From the tenant portal, click **Data Centers**.
2. From the main page under **Virtual Data Center**, click the virtual data center where you would like to configure the private network.
3. In the left pane under **Networking**, click **Edges**.
4. In the right pane select the network and click **SERVICES**.
5. Click the **Firewall** tab and click **+** to add a firewall rule.
6. Add the private network IP that you collected from the {{site.data.keyword.cloud_notm}} virtual data center details page to the **Source** field.
7. Add the service network IP that you collected from the {{site.data.keyword.cloud_notm}} virtual data center details page to the **Destination** field.
8. Select the **Protocol**, (TCP, UDP, or Any) and specify **ports** for the **Service** field.
9. Select **Accept** for the **Action** field.
10. Click **Save changes**.

### Configuring DNAT rules for the NSX Edge Services Gateway
{: #shared_vcd-ops-guide-pne-dnat-rules}

A Destination NAT rule is necessary to allow traffic from a private network endpoint to the virtual data center.

1. From the **Edge Gateway Services** pane, click the **NAT** tab.
2. Under the **NAT44 Rules**, click **+ DNAT Rule**.
3. Find the name of the service network that is assigned for the service network interface from the **IP Addresses** table in the **Edge Gateway Settings** section. The format for the service network name is ``w<idx>-service<idx>``, for example, ``w02-service02``.
4. Click the **Applied On** arrow and select the **service network** interface.
5. Add the Service network IP to the **Original Source IP/Range**.
6. Click **Protocol** and select the port type for inbound traffic.
7. For the ``TCP`` or ``UDP`` protocols, click **Original Port** and enter the port range you want to allow. Skip this step for the ``Any`` protocol.
8. The **Translated Source IP/Range** is the IP addresses of the VM connected to the routed organization virtual data center.
9. For the ``TCP`` or ``UDP`` protocols, select the **Translated Port** to route the traffic to. Skip this step for the ``Any`` protocol.
10. Skip the **ICMP Type** and optionally enter a description. Click **KEEP**.
11. Click **Save changes**.

### Validating the private network endpoint connection
{: #shared_vcd-ops-guide-pne-validate}

To validate the private network endpoint connection, login to the virtual server instance resource in your {{site.data.keyword.cloud_notm}} infrastructure account and then use SSH, RDP, or Ping (if ICMP is enabled) to connect to a VM in the virtual data center.

Ensure that the organization virtual data center network type is ``routed``.
{:important}

## Related links
{: #shared_vcd-ops-guide-related}

* [VMware Solutions Shared overview](/docs/vmwaresolutions?topic=vmwaresolutions-shared_overview)
* [Ordering virtual data center instances](/docs/vmwaresolutions?topic=vmwaresolutions-shared_ordering)
* [VMware vCloud Director](https://docs.vmware.com/en/VMware-Cloud-Director/10.1/VMware-Cloud-Director-Tenant-Portal-Guide/GUID-74C9E10D-9197-43B0-B469-126FFBCB5121.html){:external}
