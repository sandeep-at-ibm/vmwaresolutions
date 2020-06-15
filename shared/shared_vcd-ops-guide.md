---

copyright:

  years:  2020

lastupdated: "2020-06-10"

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

### Procedure to create or modify user settings
{: #shared_vcd-ops-guide-roles-procedure}

You can create a user or change passwords or roles for an existing user.

1. From the tenant portal main menu icon, click **Administration**.
2. Under **Access Control** in the left pane, click **Users**. In the **Users** pane, you can create a user or edit, enable, disable, and unlock existing users.  
3. To create a user, click **NEW** and define the username, password, role, and VM quotas. Then, click **Save**.

For more information about roles and permissions, see [vCloud Director Tenant Portal Roles and Rights](https://docs.vmware.com/en/vCloud-Director/9.7/com.vmware.vcloud.tenantportal.doc/GUID-754BD24F-63C7-422F-83BC-BFA275CEDA8E.html){: external}.

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
  3. ``echo '{"dmi.system.uuid": "'$uuid'"}' > /etc/rhsm/facts/uuid_override.facts``
  4. ``subscription-manager register --org="customer" --activationkey="${activation_key}" --force``  
  Where:  
  ``${activation_key}`` is the Red Hat activation key that is located on the instance details page.  

You can still use another RHEL Capsule Server or a satellite server if you already have an RHEL subscription outside of IBM. Charges for the RHEL license are incurred against RHEL VMs that are running in a virtual data center instance.
{:note}

### Defining catalogs and policies
{: #shared_vcd-ops-guide-policies}

To create a catalog, you must have either the **Organizational Administrator** or **Catalog Author** role.

1. From the **Administration** menu, click the menu icon next to **Administration** at the top of the page, select **Libraries**, and then select **Catalogs** from the left pane.
2. Click **New** to create a catalog.
3. Enter the name and optionally a description of the catalog.
4. Optionally, select if you want to assign a pre-provisioned storage policy to the catalog and select a storage policy. Click **OK**.
5. To publish, share, set, or change storage policies, click the three horizontal dots to the left of the name of the catalog you want to edit.

### Uploading your media or templates
{: #shared_vcd-ops-guide-customer}

Large image files or templates might take extended time to upload.

#### Uploading templates
{: #shared_vcd-ops-guide-templates}

1. From the **Administration** menu, click the menu icon at the top of the page and then select **Libraries**. Click **vApp Templates**.
2. Click **ADD** in the right pane and provide a URL or location from your local computer. Then, click **NEXT**.
3. Review the details and click **NEXT**.
4. Provide a name, description (optional), and the catalog for the template. Click **NEXT and FINISH**.

#### Uploading media
{: #shared_vcd-ops-guide-media}

1. From the Content Library, select **Media & Other**.
2. Click **ADD** in the right pane.
3. Select the catalog, optionally provide a name, and select the media to be uploaded.
4. Click **OK**.

For more information about working with catalogs, see [Working with Catalogs](https://docs.vmware.com/en/vCloud-Director/9.7/com.vmware.vcloud.tenantportal.doc/GUID-6424C4A7-EA95-49A0-B673-9DDB971AB566.html){:external}.

## Virtual machines
{: #shared_vcd-ops-guide-machines}

When you use the tenant portal, you can create a VM or provision a VM from a template.

### Creating a virtual machine
{: #shared_vcd-ops-guide-machine}

1. From the tenant portal, click the menu icon at the top of the page and select **Datacenters**.
2. Under **Virtual datacenters**, click the virtual data center to create the VM in.
3. In the right pane under **Compute**, select **Virtual Machines**.
4. In the left pane, click **NEW VM**.
5. Define the Name, Computer Name, Description (optional). Then, select **New** for the type and the **Power on** option.
6. Select the operating system type for **OS family**, the operating system for **Operating System**, and the image ISO for **Boot image**.
7. If no compute policies are created, the system default is used for **Compute policy**.
8. Select the size for your VM. There are three predefined options: small, medium, and large. Choose custom if the predefined options do not meet your requirements.
9. Define the storage requirements for the virtual machine, storage policy, and size of disk. Add more disks if required.
10. Define the network to connect the VM to, if any networks are created. Click **OK**.

### Creating a virtual machine from a template
{: #shared_vcd-ops-guide-virtual}

1. From the tenant portal, click the menu icon at the top of the page and select **Datacenters**.
2. Under **Virtual Datacenters**, click the virtual data center to create the VM in.
3. On the right pane, under **Compute**, select **Virtual Machines**.
4. In the left pane, click **NEW VM**.
5. Define the Name, Computer Name, and Description (optional). Then, select **From Template** for type and the **Power on** option.
6. Select the template to provision.
7. Select **Use custom storage policy**, if required. If left cleared, the default storage policy is used.
8. Click **OK**.

For more information about working with VMs, see [Working with Virtual Machines](https://docs.vmware.com/en/vCloud-Director/9.7/com.vmware.vcloud.tenantportal.doc/GUID-DF0C111D-B638-4EC3-B805-CC33994F8D53.html){:external}.

### Customizing virtual machine properties
{: #shared_vcd-ops-guide-cust-properties}

You can edit the properties of a VM, including the virtual machine name and description, hardware and network settings, and guest operating system settings.

If you use the tenant portal **Password Reset** field to change your Windows Administrator password, ensure that you adhere to Windows complexity requirements. If you change the password in the tenant portal without doing so, the password does not work in the Windows VM template.
{:important}


#### Changing the general properties of a virtual machine
{: #shared_vcd-ops-guide-change-properties}

You can change the name, description, storage policy, and other general properties of a VM.

#### Changing the hardware properties of a virtual machine
{: #shared_vcd-ops-guide-hardware}

You can change the hardware properties of a VM, number of vCPUs, memory, hard disk allocation, and network configuration.

#### Changing the guest OS customization properties of a VM
{: #shared_vcd-ops-guide-customization}

Guest OS customization is optional for all platforms. It is required for VMs that must join a Windows domain when the VMs are being powered on.

When you use an IBM template to create the VM, use the Guest OS customization to acquire or set the unique password for the OS instance. Ensure that the **Enable guest customization** option is selected and then use one of the **Password Reset** options to establish the initial Administrator credential.

#### Changing the advanced properties of a virtual machine
{: #shared_vcd-ops-guide-advanced}

In the Advanced settings, you can configure the resource allocation settings (shares, reservation, and limit) to determine the amount of virtual CPU (vCPU), memory, and storage resources provided for a VM.

For more information, see [Edit Virtual Machine Properties](https://docs.vmware.com/en/vCloud-Director/9.7/com.vmware.vcloud.tenantportal.doc/GUID-FA8C101E-241E-41A5-A3C3-83BDBB4467F1.html){: external}.

### Using IBM templates
{: #shared_vcd-ops-guide-ibm-templates}

If the VM is deployed from the IBM templates that are provided in the public catalog, the initial password that was generated during power-on is required when you first log in to the VM. You can find this password on the VM **Details** page.

If you use the tenant portal **Password Reset** field to change your Windows Administrator password, ensure that you adhere to Windows complexity requirements. If you change the password in the tenant portal without doing so, the password does not work in the Windows VM template.
{:important}

1. From the **Guest OS Customization** pane, locate the **Password Reset** section. Then, locate the password in the **Specify password** field.
2. After a successful login with the initial password, reset the password and log in again with the new password.

## vApps
{: #shared_vcd-ops-guide-vapps}

A vApp consists of one or more VMs that communicate over a network and use resources and services in a virtual data center.

1. From the tenant portal, click the menu icon at the top of the page and select **Datacenters**.
2. Under **Virtual Datacenters**, click the virtual data center under which to create the vApp.
3. Under **Compute** in the right pane, select **vApp**.
4. In the left pane, click **NEW vAPPS**.
5. Enter the vApp name and click **Create**.

You can now add VMs and networks to the vApp.

For more information about vApps, see [Working with vApps](https://docs.vmware.com/en/vCloud-Director/9.7/com.vmware.vcloud.tenantportal.doc/GUID-AC48FB5E-4ADC-4835-AACE-B949B297A147.html){: external}.

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

1. From the tenant portal, click the menu icon at the top of the page and select **Datacenters**.
2. On the main page, under **Virtual Datacenters**, click the virtual data center where the network is created.
3. Under the **Networking** section in the left pane, click **Networks**.
4. Click **ADD** in the main pane.
5. Select **Routed** and click **Next**.
6. Provide details for **Name** and **Gateway CIDR**. For example, Name:``Web`` Gateway CIDR:``192.168.100.1/24``
7. (Optional) Enter a description of the organization virtual data center network.
8. (Optional) To make the organization virtual data center network available to other organization virtual data centers within the same organization, set the Shared option. One use case is when an application within an Organization virtual data center has a reservation or allocation pool set as the allocation model. In this case, it might not have enough room to run more VMs. As a solution, you can create a secondary Organization virtual data center with On-demand and run more VMs on that network on a temporary basis. Then, click **Next**.  
  **Note**: Virtual data center instances can only share networks if they are in the same region.  
9. Select the edge.
10. From the **Interface Type** list, select **Distributed** and click **Next**.
11. (Optional) Enter a static IP range and click **ADD**. If static IP addresses are required for the defined subnet, enter the range of addresses. Click **Next**.
12. (Optional) If known, provide DNS details. Otherwise, click **Next**.
13. Review the **Ready to Complete** page and click **Finish**.
14. (Optional) To create another Organization virtual data center network, repeat the previous process. Give the network a different **Name**: ``App`` and a different **Gateway CIDR**: ``192.168.101.1/24``.

#### Validate that the network is connected to the Edge
{: #shared_vcd-ops-guide-validate-network}

1. From the tenant portal, click the menu icon at the top of the page and select **Datacenters**.
2. Under **Virtual Datacenters**, click the virtual data center for that edge gateway.
3. In the left pane under Networking, click **Edges**.
4. In the right pane, click the edge then click **CONFIGURE SERVICES**.
5. Click the **Routing** tab, then click **Static Routes**.
6. Validate the Organization virtual data center networks that are defined earlier are listed. The Next Hop shows `10.255.255.250`, which is the internal interface of the edge gateway.

#### Edge DHCP configuration
{: #shared_vcd-ops-guide-configure-dhcp}

Configure DHCP on the edge gateway to automatically assign IP addresses to the VMs connected to the Organization virtual data center networks.

1. From the tenant portal, click the menu icon at the top of the page and select **Datacenters**.
2. Click the virtual data center for that edge gateway.
3. In the left pane under Networking click **Edges**, then **CONFIGURE SERVICES**.
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

1. From the tenant portal, click the menu icon at the top of the page to access the menu and then select **Datacenters**.
2. Under **Virtual Datacenters**, click the virtual data center where the VMs are located.
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

To enable VMs to reach the internet, you must configure a SNAT (Source Network Address Translation) rule and firewall policy to allow the VM traffic outbound. To allow inbound traffic, you must configure a DNAT (Destination Network Address Translation) rule and firewall policy.

1. From the tenant portal, click the menu icon at the top of the page and then select **Datacenters**.
2. On the main page, under **Virtual Datacenters**, click the virtual data center for that edge gateway.
3. In the left pane under **Networking**, click **Edges**.
4. In the right pane click the edge, scroll down to the IP address section, and note the ``location-Customer-External`` IP address. Any of the addresses under **Suballocated IP Pool** for the ``location-Customer-External`` range can also be used for SNAT and DNAT. After the IP addresses are noted, scroll up and click **CONFIGURE SERVICES**.
5. Under **Firewall Rules**, click **+**.
6. Define the name, source, destination, any specific services, and action. The source is an IP address, a range of addresses or an object. To define an IP address, click the **IP** in the source box and set the IP address or range to allow everything on that subnet. For example, ``192.168.100.2`` or ``192.168.100.0/24``. Do the same for destination and services or leave them set to **Any**. Set the Action to **Accept**.
7. Click **Save changes**.

##### Source NAT definitions
{: #shared_vcd-ops-guide-source-nat}

A source NAT rule is necessary to allow traffic from a private network outbound to the internet.

1. From the edge gateway services pane, click the **NAT** tab.
2. Under the **NAT44 Rules**, click **+ SNAT Rule**.
3. Click the **Applied On** arrow and select the ``location-Customer-External`` interface.
4. Define the **Original Source IP/Range**. You can use a one-to-one or many-to-one NAT.
5. The **Translated Source IP/Range** is one of the IP addresses from the Suballocated IP address range.
6. Optionally enter a description. Click **KEEP**.
7. Click **Save changes**.

To test internet connectivity, log in to one of the VMs that are attached to the network for which the firewall and NAT rules were defined and renew the DHCP lease.
* For Windows, open a command prompt and issue the `ipconfig /renew` command.
* For Linux, type `systemctl restart network`. Depending on the type and version of Linux, this command might vary. From the command line, ping ``8.8.8.8`` or ``9.9.9.9``. If everything is configured correctly, you receive a reply. If the name resolution is required and no DNS server was defined, yet you can configure either ``9.9.9.9`` or ``8.8.8.8`` on the VM, edit the DHCP pool and define it there.

##### Destination NAT definition and port forwarding
{: #shared_vcd-ops-guide-destination-nat}

A destination NAT allows an outside host, in this case the internet, to connect to an inside host, the Organization virtual data center. The destination NAT maps one IP address or port to another IP address or port. The following instructions are an example of configuring DNAT and port forwarding to allow a remote desktop connection to a VM in the Organization virtual data center. Port forwarding is optional.

1. From the tenant portal, click the menu icon at the top of the page and then select **Datacenters**.
2. Under **Virtual Datacenters** on the main page, click the virtual data center for that edge gateway.
3. In the left pane under **Networking**, click **Edges**.
4. In the main pane click the edge, then **CONFIGURE SERVICES**.
5. Click the **NAT** tab, under **NAT44 Rules** click **+ DNAT RULE**.
6. Click the **Applied On** down arrow and select the ``location-Customer-External`` interface.
7. The **Original IP/Range** is one of the IPs from the Suballocated IP address range.
8. Optionally, for port forwarding, click the **Protocol** down arrow and select **TCP**.
9. The **Original Port** in this example is ``8000``. Ports below 1024 are reserved. Select a port that is not previously used with the original IP address or range.
10. The **Translated IP/Range** is the IP address of the VM on the private Organization virtual data center you want connected.  
11. The **Translated Port** is the port on the previous VM that the servicer is listening on. In this example, port 3389 is the default remote desktop port.
12. Optionally, define a description, then click **KEEP**.
13. Click **Save changes**.
14. Click the **Firewall** tab, click **+** to add a rule and set the Destination to the Customer-External IP address used for **Original IP/Range** in the DNAT rule.
15. Click **+** in the Service column and set the **Protocol** to TCP and the **Destination Port** to the Customer-External IP address used in the DNAT rule. In the example, port ``8000`` is used.
16. Click **Save changes** in the upper left corner.
17. Exit the **Edge Gateway** services pane.

To test the configuration, use the remote desktop client and connect to the ``Customer-External IP address:port number`` as the destination in the **Computer** field.

#### Enabling VM access to IBM Cloud Services by using the private network
{: #shared_vcd-ops-guide-enable-access}

vApps and VMs running inside of the virtual data center can be configured to use the {{site.data.keyword.cloud_notm}} private network to access {{site.data.keyword.cloud_notm}} services. Accessing {{site.data.keyword.cloud_notm}} services through a private network can save on outbound public networking costs and can provide a higher degree of reliability and security. Virtual data centers route to the {{site.data.keyword.cloud_notm}} private network through a virtual data center service network that is configured as an available external network on virtual data centers edge.

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
| IBM Cloud Object Storage | [s3.direct.xxx.cloud-object-storage.appdomain.cloud](/docs/vpc?topic=vpc-connecting-vpc-cos) |
{: caption="Table 2. Available services" caption-side="top"}

Enabling access to the service network is done in two edge configuration steps.

##### Adding the NAT rule
{: #shared_vcd-ops-guide-nat-rule}

Add a NAT rule for translating internal network addresses into the service network IP address space.
1. Log in to the VMware vCloud Director portal.
2. Click the virtual data center **Edges** tab and open the single preconfigured edge.
3. Find the name of the service network and the IP address that is assigned for the service network interface from the **IP Addresses** table in the **Edge Gateway Settings** section. The format for the service network name is ``w<idx>-service<idx>``, for example, ``w02-service02``.
4. Click **CONFIGURE SERVICES** to open the Edge Gateway configuration page. Click the **NAT** tab and click **+ SNAT RULE** to add a SNAT rule.
5. Select the service network next to the **Applied on** field, add the IP addresses or range from one of the virtual data center internal networks to the **Original** field.
6. Set the translated IP address to the IP address of the network selected in step 3. This address can be found under Network Edge settings for External Networks.
7. Specify `Any` for the **Port** field for the **Original** and **Protocol** fields.
8. Click **Save changes**.

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

If you have not already done so, create a vApp containing at least two VMs. For more information, see [Working with vApps](https://docs.vmware.com/en/vCloud-Director/9.7/com.vmware.vcloud.tenantportal.doc/GUID-AC48FB5E-4ADC-4835-AACE-B949B297A147.html){: external}.

1. From the tenant portal, click the menu icon at the top of the page and then select **Datacenters**.
2. From the main page under **Virtual Datacenters**, click the virtual data center where you would like to create the vApp network.
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

* You must have a running VM. For more information, see [Creating a virtual machine](/docs/vmwaresolutions?topic=vmwaresolutions-shared_vcd-ops-guide#shared_vcd-ops-guide-machine).
* The VM must be connected to a routed organization virtual data center network. For more information, see [Creating a routed organization virtual data center network](/docs/vmwaresolutions?topic=vmwaresolutions-shared_vcd-ops-guide#shared_vcd-ops-guide-routed-organization) and [Connect the VMs to the network](/docs/vmwaresolutions?topic=vmwaresolutions-shared_vcd-ops-guide#shared_vcd-ops-guide-connect-vm).
* You must have virtual routing and forwarding and service endpoints enabled on the account that the whitelisted IP or subnet belong to. For more information, see [Enabling VRF and service endpoints](/docs/account?topic=account-vrf-service-endpoint).

### Collecting network IP addresses
{: #shared_vcd-ops-guide-pne-IPs}

Collect the service network and private network IP addresses to configure the firewall and DNAT rules.

1. In the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. In the **VMware Solutions Shared** table, click on the virtual data center to configure.
3. In the **Private Network Endpoint** section, collect the **Service network IP** address and **Private network IP** address.

### Configuring firewall rules for the VMware NSX Edge Services Gateway
{: #shared_vcd-ops-guide-pne-firewall-rules}

The firewall rule allows traffic from the private network IP to go through your Edge Service Gateway. You may need to repeat this process (steps 5 to 10) to allow different traffic to enter your virtual data center, depending on which ports and protocols you need to open up.

1. From the tenant portal, click the menu icon at the top of the page and then select **Datacenters**.
2. From the main page under **Virtual Datacenters**, click the virtual data center where you would like to configure the private network.
3. In the left pane under **Networking**, click **Edges**.
4. In the right pane select the network and click **Configure Services**.
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
10. Skip the **ICMP Type**. Optionally enter a description. Click **KEEP**.
11. Click **Save changes**.

### Validating the private network endpoint connection
{: #shared_vcd-ops-guide-pne-validate}

To validate the private network endpoint connection, login to the virtual server instance resource in your {{site.data.keyword.cloud_notm}} infrastructure account and then use SSH, RDP, or Ping (if ICMP is enabled) to connect to a VM in the virtual data center.

Ensure that the organization virtual data center network type is ``routed`` and that the interface type of the network is ``SubInterface`` or ``Internal``.
{:important}

## Related links
{: #shared_vcd-ops-guide-related}

* [VMware Solutions Shared overview](/docs/vmwaresolutions?topic=vmwaresolutions-shared_overview)
* [Ordering virtual data center instances](/docs/vmwaresolutions?topic=vmwaresolutions-shared_ordering)
* [VMware vCloud Director](https://docs.vmware.com/en/vCloud-Director/9.7/com.vmware.vcloud.tenantportal.doc/GUID-74C9E10D-9197-43B0-B469-126FFBCB5121.html){:external}
* [Video tutorial: IBM Cloud for VMware Solutions Shared - Setup the Network](https://www.youtube.com/watch?v=gG0jp3TEtt0&list=PLIsX_jY0PwvU4fJ28go4QOau2xdHLXvmE&index=3&t=0s){:external}
* [Video tutorial: IBM Cloud for VMware Solutions Shared - Deploy a VM](https://www.youtube.com/watch?v=5yl-_60gUUw&list=PLIsX_jY0PwvU4fJ28go4QOau2xdHLXvmE&index=4&t=0s){:external}
