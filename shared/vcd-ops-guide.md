---

copyright:

  years:  2019

lastupdated: "2019-08-26"

keywords: vmware solutions shared, get started shared, tech specs shared

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# IBM Cloud for VMware Solutions Shared operations
{: #vcd-ops-guide}

## vCloud Director portal overview
{: #vcd-ops-guide-port-ovv}

The tenant portal is used for administration of your organization and to create and configure virtual machines, vApps, and networks within vApps.

You can also configure advanced networking capabilities that are provided by VMware NSX® for vSphere® within a vCloud Director environment. With the vCloud Director tenant portal, you can also create and manage catalogs, vApp and VDC templates, and create and manage cross-virtual data center networks.

### Roles, permissions, and users
{: #vcd-ops-guide-roles}

The tenant portal includes a preconfigured set of user roles and their rights. The roles that can access the tenant portal are the ones that are created by default when an organization is created and other roles that are created by the organization administrator. Users who are assigned the following organization roles can access the tenant portal. The objects that they see and the actions that they can take depend on the rights that are associated with a role.
* Organization Administrator
* Catalog Author
* vApp Author
* vApp User
* Console Access Only

To create a user, or to change passwords or roles for an existing user:
1. From the tenant portal, go to the Administration menu, click the hamburger icon to the right of Administration at the top of the page then click Administration.  
2. Under Access Control in the left pane, click Users.
3. In the Users pane, you can create a user or edit, enable, disable, and unlock existing users.  
4. To create a user click NEW, define the user name, password, role, and virtual machine quotas. Then, click Save.

For more information about roles and permissions, see [vCloud Director Tenant Portal Roles and Rights](https://docs.vmware.com/en/vCloud-Director/9.7/com.vmware.vcloud.tenantportal.doc/GUID-754BD24F-63C7-422F-83BC-BFA275CEDA8E.html){: external}.

## Catalogs
{: #vcd-ops-guide-catalogs}

A catalog is a container for vApp templates and media files in an organization. Organization administrators and catalog authors can create catalogs in an organization. Catalog contents can be shared with other users or organizations in the IBM Cloud for VMware Solutions Shared installation. Or they can be published externally for access by organizations outside the IBM Cloud for VMware Solutions Shared installation.

IBM Cloud for VMware Solutions Shared contains private catalogs, shared catalogs, and externally accessible catalogs. Private catalogs include vApp templates and media files that you can share with other users in the organization. If a system administrator enables catalog sharing for your organization, you can share an organization catalog to create a catalog accessible to other organizations in the IBM Cloud for VMware Solutions Shared installation.

If a system administrator enables external catalog publishing for your organization, you can publish an organization catalog for access by organizations outside the IBM Cloud for VMware Solutions Shared installation. An organization outside the IBM Cloud for VMware Solutions Shared installation must subscribe to an externally published catalog to access its contents.

Each customer organization has access to the IBM Cloud for VMware Solutions Shared Public catalog. The public catalog contains vApp templates for RHEL, CentOS 7, Windows 2016, and Windows 2019. It also contains installation media for CentOS 7, RHEL 7.6, Windows 2016, and Windows 2019. OS licensing cost applies for usage.

### Defining catalogs and policies
{: #vcd-ops-guide-policies}

To create a catalog, you must have either the role of Organizational Administrator or Catalog Author.

1. From the Administration menu, click the hamburger icon to the right of Administration at the top of the page, select Libraries, and select Catalogs from the left pane.
2. Click New to create a catalog.
4. Enter the name and optionally, a description of the catalog.
5. Optionally, select whether you want to assign a pre-provisioned storage policy to the catalog, and select a storage policy.
6. Click OK.
7. To publish, share, set, or change storage policies click the three horizontal dots to the left of the name of the catalog you would like to edit.

### Uploading customer media or templates
{: #vcd-ops-guide-customer}

Large image files or templates might take extended time to upload.

#### Uploading templates
{: #vcd-ops-guide-templates}

1. From the Administration menu, click the hamburger icon at the top of the page select Libraries. Click vApp Templates.
2. Click ADD in the right pane, provide a URL or location from your local computer, and click NEXT.
3. Review the details and click NEXT.
4. Provide a name, description (optional), and the catalog for the template. Click NEXT and FINISH.

#### Uploading media
{: #vcd-ops-guide-media}

1. From the Content Library, select Media & Other.
2. Click ADD in the right pane.
3. Select the catalog, provide a name (optional), and select the media to be uploaded.
4. Click OK.

For more information about working with catalogs, see [Working with Catalogs](https://docs.vmware.com/en/vCloud-Director/9.7/com.vmware.vcloud.tenantportal.doc/GUID-6424C4A7-EA95-49A0-B673-9DDB971AB566.html)

## Virtual machines
{: #vcd-ops-guide-machines}

There are two ways to create virtual machines (VMs) by using the tenant portal, either creating a VM or provisioning a VM from a template.

### Creating a VM from a template
{: #vcd-ops-guide-virtual}

1. From the tenant portal, click the menu, hamburger icon at the top of the page, and select Datacenters.
2. Under Virtual Datacenters, click the virtual datacenter to create the VM in.
3. In the right pane, under Compute, select Virtual Machines.
4. In the left-hand panel, click NEW VM.
5. Define the Name, Computer Name, and Description (optional), and select From Template for Type, and Power on option.
6. Select the template to provision.
7. Select Use custom storage policy if required. If left unchecked, the default storage policy is used. Click OK.

### Creating a VM
{: #vcd-ops-guide-machine}

1. From the tenant portal, click the menu, hamburger icon at the top of the page, and select Datacenters.
2. Under Virtual Datacenters, click the virtual datacenter to create the VM in.
3. In the right pane, under Compute, select Virtual Machines.
4. In the left pane, click NEW VM.
5. Define the Name, Computer Name, Description (optional), and select New for Type, and Power on option.
6. Select the OS type for OS family, the OS for Operating System, and the image ISO for Boot image.
7. If no compute policies are created, the system default is used for the Compute policy.
8. Select the size for your VM. There are three predefined options: small, medium, and large. Choose custom if the predefined options do not meet your requirements.
9. Define the storage requirements for the VM, Storage Policy, and size of disk. Add more disks if required.
10. Define the network to connect the VM to, if any networks are created. Click OK.

For more information about working with VMs, see [Working with Virtual Machines](https://docs.vmware.com/en/vCloud-Director/9.7/com.vmware.vcloud.tenantportal.doc/GUID-DF0C111D-B638-4EC3-B805-CC33994F8D53.html){:external}

### Customizing VM properties
{: #vcd-ops-guide-cust-properties}

You can edit the properties of a VM, including the VM name and description, hardware and network settings, and guest OS settings.

#### Changing the general properties of a VM
{: #vcd-ops-guide-change-properties}

Change the name, description, storage policy, and other general properties of a VM.

#### Changing the hardware properties of a VM
{: #vcd-ops-guide-hardware}

Change the hardware properties of a VM, number of CPUs, memory, hard disk allocation, and network configuration.

#### Changing the guest OS customization properties of a VM
{: #vcd-ops-guide-customization}

Guest OS customization is optional for all platforms. It is required for VMs that must join a Windows domain when powering on. If an IBM template was used to create the VM, you can find the auto-generated password in this section. This password is the onethat is used for the first login. You are required to change the password at first login.

#### Changing the advanced properties of a VM
{: #vcd-ops-guide-advanced}

In the Advanced settings, you can configure the resource allocation settings (shares, reservation, and limit) to determine the amount of CPU, memory, and storage resources provided for a VM.

For more information, see [Edit Virtual Machine Properties](https://docs.vmware.com/en/vCloud-Director/9.7/com.vmware.vcloud.tenantportal.doc/GUID-FA8C101E-241E-41A5-A3C3-83BDBB4467F1.html){: external}.

## vApps
{: #vcd-ops-guide-vapps}

A vApp consists of one or more VMs that communicate over a network and use resources and services in a virtual datacenter.

1. From the tenant portal, click the menu, hamburger icon at the top of the page, and select Datacenters.
2. Under Virtual Datacenters, click the virtual datacenter to create the vApp under.
3. In the right pane, under Compute, select vApp.
4. In the left pane, click NEW vAPP.
5. Enter the vApp name and click Create.

You can now add VMs and networks to the vApp.

For more information about vApps, see [Working with vApps](https://docs.vmware.com/en/vCloud-Director/9.7/com.vmware.vcloud.tenantportal.doc/GUID-AC48FB5E-4ADC-4835-AACE-B949B297A147.html){: external}.

## Networking
{: #vcd-ops-guide-networking}

Every IBM Cloud for VMware Solutions Shared Virtual Data Center comes configured with one edge gateway with five public IP addresses and one private IBM Services network IP address. The edge gateway services are customer configurable and require configuration to allow network
traffic in and out of their organization VDC.

Configuration is required for access to the internet and the IBM Services network. The five public addresses are used for public facing vApps for inbound and outbound public internet traffic. The service address is used for access to IBM Cloud Infrastructure services on the IBM Cloud internal private network, including:
- NTP
- Windows OS licensing and updates
- Red Hat OS licensing and updates
- Cloud Object Storage

There are three types of Organization Virtual Data Center Networks available in the IBM Cloud for VMware Solutions Shared Virtual Data Center, which is routed, internal, or cross-VDC.

### Routed
{: #vcd-ops-guide-routed}

Accessible only by the same organization VDC. Only virtual machines in this organization VDC can connect to this network. This network also provides controlled access to an external network. An organization administrator can configure network address translation (NAT), firewall, and VPN settings to make specific virtual machines accessible from the external network.

### Internal/Isolated
{: #vcd-ops-guide-internal}

Accessible only by the same organization VDC. Only virtual machines in this organization VDC can connect to and see traffic on the internal organization VDC network.

The isolated organization VDC network provides an organization VDC with an isolated, private network that multiple virtual machines and vApps can connect to. This network provides no connectivity to virtual machines outside the organization VDC. Machines outside of the organization VDC have no connectivity to machines in the organization VDC.

### Cross-VDC
{: #vcd-ops-guide-cross-vdc}

This network is part of a stretched network spanning a data center group. A data center group can comprise between two and four organization virtual data centers in a single or multisite vCloud Director deployment. Virtual machines connected to this network are connected to the underlying stretched network.

### Creating a network
{: #vcd-ops-guide-create-network}

This section creates a sample network topology that covers configuring DHCP services, defining Source and Destination NAT rules (SNAT & DNAT),
and creating firewall rules on the edge gateway to allow access to the internet.

![{{site.data.keyword.vmwaresolutions_short}} Network topology](../images/vcd-sample-topology.svg "{{site.data.keyword.vmwaresolutions_short}} Network topology"){: caption="Figure 1. {{site.data.keyword.vmwaresolutions_short}} Network topology" caption-side="bottom"}

#### Create a routed organization VDC network
{: #vcd-ops-guide-routed-organization}

1. From the tenant portal click the menu, hamburger icon at the top of the page, and select Datacenters.
2. On the main page under Virtual Datacenters click the virtual datacenter where the network will be created.
3. Under the Networking section in the left pane click Networks.
4. Click ADD in the main pane.
5. Click the Routed radio button then Next.
6. Fill in the Name and Gateway CIDR. For example, Name: “Web” Gateway CIDR: “192.168.100.1/24”
7. (Optional) Enter a description of the organization VDC network.
8. (Optional) To make the organization VDC network available to other organization VDCs within the same organization, set the Shared option. One potential use case is when an application within an Organization VDC has a reservation or allocation pool set as the allocation model. In this case, it might not have enough room to run more virtual machines. As a solution, you can create a secondary Organization VDC with pay-as-you-go and run more virtual machines on that network on a temporary basis. Note: The Organization VDCs must be backed by the same Provider VDC (If pay go and reserved are different Provider VDC’s this won’t work for customers using both.) Click Next.
9. Select the edge.
10. Click the drop-down for Interface Type and select Distributed. Click Next.
11. Enter a static IP range and click ADD. (This is optional, if static IPs are required for the defined subnet enter the range here and click
ADD, then Next.
12. (Optional) Provide DNS specifics if known currently, otherwise click Next. 
13 Review the Ready to Complete page and click Finish.
14. (Optional) To create another organization VDC network repeat the process above, give it a different Name: “App” and different Gateway CIDR: “192.168.101.1/24”.

#### Validate the network is connected to the Edge
{: #vcd-ops-guide-validate-network}

1. From the tenant portal click the menu, hamburger icon at the top of the page, and select Datacenters.
2. Under Virtual Datacenters, click the virtual datacenter for that edge gateway.
3. In the left pane under Networking click Edges.
4. In the right panel, click the edge then click, CONFIGURE SERVICES.
5. Click the Routing tab, then Static Routes.
6. Validate the organization VDC network/s defined earlier are listed. The Next Hop will show 10.255.255.250, this is the internal interface of the edge gateway.

#### Edge DHCP configuration
{: #vcd-ops-guide-configure-dhcp}

This describes how to configure DHCP on the edge gateway to automatically assign IP addresses to the virtual machines connected to the organization VDC networks.

1. From the tenant portal click the menu, hamburger icon at the top of the page, and select Datacenters.
2. Click the virtual datacenter for that edge gateway.
3. In the left pane under Networking click Edges, then CONFIGURE SERVICES. This starts the edges services pane.
4. Click the DHCP tab.
5. Under DHCP Pools click + to add a pool.
6. Define the IP Range, this is a range from the organization VDC network that is attached to the edge.
7. Define the primary and secondary name servers, if available. These can be defined or changed later.
8. Define the default gateway, this is gateway CIDR or the organization VDC network that is attached to the edge.
9. Define the subnet mask and set the lease time. Click KEEP.
10. Repeat the process for additional organization VDC network attached to the edge requiring DHCP services.
11. Set the DHCP service status to enabled.
12. Click save changes.

#### Connect the VMs to the network
{: #vcd-ops-guide-connect-vm}

Stand-alone virtual machines, or virtual machines in a vApp, can connect to an Org VDC network.  

1. From the tenant portal, click the hamburger icon at the top of the page to access the menu and then select Datacenters.
2. Under Virtual Datacenters, click the virtual datacenter where the VMs are located.
3. On the left pane, under Compute, click Virtual Machines.
4. Click Details for the VM you want to connect the network to.
5. Scroll down and expand the Hardware section.
6. Scroll down to NICs, click the drop-down arrow under Network and select one of the available networks.
7. Check the connect box and set the IP Mode to DHCP. Click Save.
8. Repeat this process for any other virtual machines. Click Save.

Once the virtual machines are connected to the Org VDC network they are able to communicate with each other, ping from one virtual machine the
other to test. If there’s no response from the ping command check the OS firewalls to see if ICMP is allowed.

#### Enable In-bound and Outbound traffic
{: #vcd-ops-guide-enable-traffic}

To enable virtual machines to reach the internet you must configure a SNAT (Source Network Address Translation) rule and firewall policy to allow the virtual machine traffic outbound. To allow in-bound traffic, you must configure a DNAT (Destination Network Address Translation) rule and firewall policy.

1. From the tenant portal click the menu, hamburger icon at the top of the page, and select Datacenters.
2. On the main page under Virtual Datacenters click the virtual datacenter for that edge gateway.
3. In the left pane under Networking click Edges.
4. In the right panel click the edge, scroll down to the IP Address section and note the” location”-Customer-External IP Address. Any of the
addresses under Sub-allocated IP Pool for the “location”-Customer-External range can also be used for SNAT and DNAT. Once the IPs are noted scroll up and click, CONFIGURE SERVICES.
5. Under Firewall Rules click +.
6. Define the name, source, destination, any specific services, and action. The source is an IP address, a range of addresses or an object. To define an IP address, click the IP button in the source box and set the IP address or range, for example, 192.168.100.2 or 192.168.100.0/24 to allow everything on that subnet. Do the same for destination and services or leave them set to Any. Set the Action to Accept.
7. Click save changes in the upper right.

##### Source NAT definitions
{: #vcd-ops-guide-source-nat}

A source NAT rule is necessary to allow traffic from a private network outbound to the internet.

1. While still in the edge gateway services pane, click the NAT tab.
2. Under the NAT44 Rules click + SNAT Rule. The Add SNAT Rule dialog box will be displayed.
3. Click the Applied On drop-down arrow and select the “location”-Customer-External interface.
4. Define the Original Source IP/Range. You may use a one to one or many to one NAT.
5. The Translated Source IP/Range is one of the IP addresses from the Sub-allocated IP Address range.
6. Optionally enter a description. Click KEEP.
7. Click Save changes in the upper right.

To test internet connectivity log in to one of the virtual machines attached to the network that the firewall and NAT rules were defined
for. Renew the DHCP lease, for Windows open a command prompt and issue the command `ipconfig /renew`, for Linux type `systemctl restart
network`. Depending on the flavor and version of Linux this command may vary. From the command line ping 8.8.8.8 or 9.9.9.9, if everything is configured correctly you will get a reply. If name resolution is required and no DNS server was defined yet you can configure either 9.9.9.9 or 8.8.8.8 on the virtual machine or, edit the DHCP pool and define it there.

##### Destination NAT definition and port forwarding
{: #vcd-ops-guide-destination-nat}

A Destination NAT allows a host on the “outside”, in this case the internet, to connect to a host on the “inside”, the Org VDC by mapping one IP address and/or port, to another IP address and/or port. The instructions below are an example of configuring DNAT and port forwarding to allow a remote desktop connection to a virtual machine in the Org VDC. Port forwarding is optional.

1. From the tenant portal click the menu, hamburger icon at the top of the page, and select Datacenters.
2. On the main page under Virtual Datacenters click the virtual datacenter for that edge gateway.
3. In the left panel under Networking click Edges
4. In the main panel click the edge, then CONFIGURE SERVICES.
5. Click the NAT tab, under NAT44 Rules click + DNAT RULE.
6. Click the Applied On drop down arrow and select the ”location”-Customer-External interface.
7. The Original IP/Range will be one of the IP’s from the Sub-allocated IP Address range.
8. Optionally, for port forwarding, click the Protocol drop down arrow and select TCP.
9. The Original Port in this example is 8000. Ports below 1024 are reserved. Select a port not previously used with the original IP address or range.
10. The Translated IP/Range is the IP address of the virtual machine on the private orgVDC you want connected.  
11. The Translated Port is the port on the above virtual machine that the servicer is listening on. In this example, port 3389 is the default remote desktop port.
12. Optionally, define a description, then click KEEP.
13. Click save changes in the upper left corner.
14. Click the Firewall tab, click + to add a rule and set the Destination to the Customer-External IP address used for Original IP/Range in the DNAT rule.
15. Click + in the Service column and set the Protocol to TCP and the Destination Port to the Customer-External IP address used in the DNAT rule. In the example I used port 8000.
16. Click save changes in the upper left corner.
17. Exit the Edge Gateway services panel.

To test the configuration use the remote desktop client and connect to the Customer-External IP address:port number as the destination in the Computer field.

#### Enabling VM access to the IBM Services network:
{: #vcd-ops-guide-enable-access}

The service address is used for access to IBM Cloud Infrastructure services on the IBM Cloud internal private network including:
 - NTP
 - Windows OS licensing and updates
 - RedHat OS licensing and updates
 - Cloud Object Storage

##### Enable access to the service network
{: #vcd-ops-guide-service-network}

1. From the tenant portal click the menu, hamburger icon at the top of the page, and select Datacenters.
2. On the main page under Virtual Datacenters click the virtual datacenter which contains the VMs you would like to allow access to the IBM Services network.
3. In the right panel under Networking click Edges, then on the edge in the main panel.
4. Under Edge Gateway Settings scroll down to IP Addresses.
5. Note the subnet and IP Address for the w02-services02 External Network.
6. Scroll up to the top of the page and click Configure Services.
7. In the Firewall tab of the Edge Gateway services panel click the + to add a new firewall rule.
8. Define a Name for example “IBM Services Outbound”, in the Source column define the IP address or subnet you would like to allow access to the services network, this is a network/subnet or VM you previously create, for example “192.168.33.1/24”. In the Destination column add the IP subnet of the services network noted above.
9. Click Save changes in the upper right corner.
10. Click the NAT tab and add a SNAT Rule in the NAT44 Rules section by clicking the + SNAT RULE box.
11. Select w02-service02 from the drop down in Applied On.
12. Add the subnet or IP address used for the source column in the firewall rule, for example “192.168.33.1/24”
13. Add the IP address from the w02-services02 external network, noted in step 5.
14. Click KEEP. Then Save changes in the upper right corner.
15. Exit the Edge Gateway services panel.

#### Creating a vApp Network
{: #vcd-ops-guide-vapp-network}

If you have not already done so create a vApp containing at least two VMs, see the working with vApp section.

1. From the tenant portal click the menu, hamburger icon at the top of the page, and select Datacenters.
2. On the main page under Virtual Datacenters click the virtual datacenter where you would like to create the vApp network.
3. In the right panel under Compute click vApps.
4. Click Details on the vApp you would like to add a vApp network to.
5. Click the Network tab, under the vApp Fencing section click New.
6. Select vApp Network.
7. Fill in the Name and Gateway CIDR fields. For example, Name: “Web” Gateway CIDR: “192.168.33.1/24”
8. (Optional) Provide DNS information.
9. (Optional) Static IP Pools. Leave blank for now.
10. Set the slider to Connect to an orgVDC network.
11. Click Add.

## Related links
{: #vcd-ops-guide-related}

* [Ordering Shared On-demand](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_ordering_ondemand)
* [Ordering Shared Reserved](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_ordering_reserved)
* [Managing {{site.data.keyword.cloud_notm}} for VMware Solutions Shared](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_managing)
* [VMware vCloud Director](https://docs.vmware.com/en/vCloud-Director/9.7/com.vmware.vcloud.tenantportal.doc/GUID-74C9E10D-9197-43B0-B469-126FFBCB5121.html){:external}
