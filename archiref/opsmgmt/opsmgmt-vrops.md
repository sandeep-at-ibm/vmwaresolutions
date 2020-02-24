---

copyright:

  years:  2016, 2020

lastupdated: "2020-01-14"

---

{:external: target="_blank" .external}

# vRealize Operations Manager design
{: #opsmgmt-vrops}

The vROps Analytics Cluster contains the nodes that analyze and store data from the monitored components and in this deployment, four nodes are deployed and two NSX Load Balancers. This size allows monitoring of up to 30,000 VMs and 9,000,000 metrics to be collected.

The 4-node analytics cluster consists of the following components:
* Master Node – The Master node is the initial node in a vROps cluster. In a large environment, this node manages all the other nodes.
* Master Node Replica – This node enables high availability of the master node.
* Data Nodes – The data node enables scale out of vROps in larger environments, two are deployed in this design.

Additionally, the design uses Remote Collector Nodes, which act as a proxy/relay server to collect data only and forward collected data to the Master/Data Nodes. Data Nodes and Remote Collectors can be added to scale up depending on environment size. The placement of vROps components onto VLANs/VXLANs is shown in the following diagram.

![Operations Manager network diagram](../../images/opsmgmt-vropsnw.svg "Operations Manager network diagram"){: caption="Figure 1. Operations Manager networking" caption-side="bottom"}

* Master Node, Master Node Replica, and Data Nodes are deployed on the tooling subnet by using {{site.data.keyword.cloud}} Portable IP addresses to facilitate communication to all components that are addressed out of the {{site.data.keyword.cloud_notm}} RFC1918 address space including; vSphere hosts, vCenter, Platform Services Controller, NSX Manager, and NSX Controllers. An NSX Load Balancer is used along with a VIP for HA.
* As customer workloads use IP addressing from the BYOIP address space then this design uses Remote Collectors that are hosted in a VXLAN. These remote collectors are not configured as part of the {{site.data.keyword.vmwaresolutions_full}} automation and must be manually implemented by the client.

![Operations Manager components diagram](../../images/opsmgmt-vropscomponent.svg "Operations Manager components diagram"){: caption="Figure 2. Operations Manager components" caption-side="bottom"}

The vROps Analytics Cluster is accessed by using a management user interface or by using an API and it integrates with the following components:
* vCenter
* vRealize Log Insight

The client can manually integrate into the following products, if they have been deployed:
* vRealize Automation
* vRealize Business

vROps collects data from the following:
* vSphere - vCenter, Platform Services Controller, vSphere hosts
* NSX - NSX Manager, NSX Controllers, and NSX Edges
* vRLI

The client can configure vROps manually to collect data from vRealize Automation and vRealize Business for Cloud.

## System requirements
{: #opsmgmt-vrops-requirements}

The analytics cluster consists of one master node, one master replica node, and two data nodes to enable scaling out and high availability. Additional data nodes are added to scale up. The analytics cluster can scale to a maximum of eight medium-sized nodes.

| Attribute | Specification |
|---|---|
| vCPU | 8 |
| Memory | 32 GB |
| Disk (thick provisioned) | 254 GB |
{: caption="Table 1. Operations Manager Master/Replica Node system settings" caption-side="bottom"}
{: summary="This table has row and column headers. The row headers identify the attribute of the master ro replica node. The column headers indentify the specification of the attribute. To find the specification of an attribute, navigate to the row, and then find the value in the specification column."}
{: #table1}
{: tab-title="Master/Replica Node system settings"}
{: tab-group="System settings"}
{: class="comparison-tab-table"}
{: row-headers}

| Attribute | Specification |
|---|---|
| vCPU | 8 |
| Memory | 32 GB |
| Disk (thick provisioned) | 254 GB |
{: caption="Table 2. Operations Manager Data Node system settings" caption-side="bottom"}
{: summary="This table has row and column headers. The row headers identify the attribute of the data node. The column headers indentify the specification of the attribute. To find the specification of an attribute, navigate to the row, and then find the value in the specification column."}
{: #table2}
{: tab-title="Data Node system settings"}
{: tab-group="System settings"}
{: class="comparison-tab-table"}
{: row-headers}

If monitoring of the compute VMs is required, the client should install two remote collector nodes on a VXLAN. The size of a Standard Remote Collector Virtual Appliance is 2 vCPU with 4 GB of RAM and the default appliance VMDK size is sufficient. The remote collector nodes are deployed with thin-provisioned disks as the remote collectors do not perform analytics operations or store data.

| Setting | Load Balancer 1 | Load Balancer 2|
|---|---|---|
| Name | vrops-ui | vrops-data |
| Interval | 30 | 5 |
| Timeout | 5 | 15 |
| Max Retries | 3 | |
| Type | HTTPS | TCP |
| Method | Get | -- |
| URL | /suite-api/api/deployment/node/status | -- |
| Receive | ONLINE | -- |
| Algorithm | ROUND-ROBIN | LEASTCONN |
| Pool | Four nodes of vROPs | Four nodes of vROPs |
{: caption="Table 3. Operations Manager Load Balancer settings" caption-side="bottom"}

<!-- For more information, see [vRealize Automation Load Balancing](https://docs.vmware.com/en/vRealize-Automation/7.5/vrealize-automation-load-balancing.pdf){:external}. -->

## Networking
{: #opsmgmt-vrops-network}

Deployment of the vROps appliance requires six IP addresses from the Tooling private portable subnet. Network connectivity vROps requires access to:
* vCenter Appliance
* vRealize Log Insight Appliance
* NSX-V/T Appliances
* Tooling Expansion VXLAN
* Customer Networks
* NTP server (`time.services.softlayer.com`)
* {{site.data.keyword.vmwaresolutions_short}} Active Directory/DNS
* The Remote Collectors require NAT rules on the NSX ESG to enable connectivity to the Master Node, Master Node Replica, and Data Nodes

## Ports
{: #opsmgmt-vrops-ports}

| Component | Protocol | Port |
|---|---|---|
| vCenter | TCP | 443 |
| DNS | TCP/UDP | 53 |
| LDAP/LDAPS | TCP | 389/636 |
| LDAP GC | TCP | 3268/3269 |
| NTP | UDP | 123 |
| SMTP | TCP | 25 |
| SNMP | UDP | 161 |
{: caption="Table 4. Operation Manager ports" caption-side="bottom"}

### Authentication
{: #opsmgmt-vrops-auth}

User Management for vROps requires VMware Identity Manager (vIDM), which integrates with Active Directory. Service accounts are used for application-to-application communication from vRealize Operations Manager to the following adapters with the minimum set of permissions that are required for metric collection and topology mapping:

* NSX Manager
* vCenter
* vSAN

## Management Packs
{: #opsmgmt-vrops-management}

Management Packs for vROps extend operational management capabilities of the vROps platform to provide product specific alerts and dashboards.

The following Management Packs are installed in vROps by default:
* Management Pack for VMware vCenter Server
* Management Pack for vRealize Log Insight
* Management Pack for vSAN
* Management Pack for vRealize Automation
* Management Pack for vRealize Business for Cloud

The following components are installed by {{site.data.keyword.vmwaresolutions_short}}:
* VMware SDDC Health Management Pack
* Management Pack for NSX for vSphere
* vRealize Operations Federation Management pack
* Management Pack for Hybrid Cloud Extension (HCX)

Other management packs can be installed by the client. For more information, see [VMware Solution Exchange](https://marketplace.vmware.com/vsx/?contentType=1&listingStyle=table){:external}.

### Management Pack for VMware vCenter Server
{: #opsmgmt-vrops-management-vCenter}

This default Management Pack extends the functionality of vROps to vCenter to enable the collection of objects, metrics, and alerts.

### Management Pack for vRealize Log Insight
{: #opsmgmt-vrops-management-vrli}

This default Management Pack extends the functionality of vROps to vRLI to enable the monitoring of the vRLI environment as well as the integration of events and alerts from vRLI into vROps.

### Management Pack for vSAN
{: #opsmgmt-vrops-management-vsan}

vRealize Operations Management Pack for vSAN enables vSAN specific dashboards to evaluate, manage, and optimize the performance of vSAN objects and vSAN-enabled objects.

### VMware SDDC Health Management Pack
{: #opsmgmt-vrops-management-sddc}

The VMware SDDC Health Management Pack for vROps monitors the SDDC management stack and provides color coded metrics for health and efficiency of different components present as part of the SDDC management stack. With the dashboards in the VMware SDDC Health Management Pack, you can monitor the following components of the vCenter Server instance and management tooling:
* vRealize Operations Manager
* NSX for vSphere/VMware NSX-T
* VMware vSAN
* vRealize Log Insight
* vCenter Server

Additionally, if the client has installed the following these can be monitored:
* vRealize Automation
* vRealize Orchestrator
* vRealize Business for Cloud
* VMware Site Recovery Manager

The VMware SDDC Health Management Pack provides the following dashboards:
* SDDC Management Health Overview Dashboard - You can use SDDC Management Health overview dashboard to view and analyze the application-specific problems in the SDDC components.
* SDDC Health Historic Trend Dashboard - The VMware SDDC Health Management Pack consists of SDDC health historic trend dashboard, which displays the health trend for each component in the SDDC stack.
* SDDC vRealize Operations Manager Sizing Dashboard - The SDDC vRealize Operations Manager Sizing Dashboard provides vRealize Operations Manager cluster capacity to process object and metrics.

The plug-ins in the VMware SDDC Health Management Pack collect metrics for object types that are contained in the plug-ins. The Management Pack collects health metrics for the following components:
* vCenter Server
* Management Pack for NSX for vSphere
* vRealize Automation
* vRealize Operations Manager
* vRealize Business
* vRealize Log Insight
* VMware Site Recovery Manager
* vCenter HA
* vMware vSAN Health
* Services in vCenter Server Appliance
* vRealize Operations Manager Sizing
* vRealize Orchestrator

### Management Pack for NSX-T
{: #opsmgmt-vrops-management-nsxt}

The NSX-T management pack extends vROps core analytics, correlation, predictive capacity, and visualization capabilities to virtual networks. The pack includes the following:
* Configuration assurance
* Health
* Performance
* Capacity
* Troubleshooting for NSX-T objects

### Management Pack for NSX for vSphere
{: #opsmgmt-vrops-management-nsxv}

The NSX for vSphere management pack offers operations management coverage for deployments of VMware's NSX virtual networking technologies. This management pack extends vROps core analytics, correlation, predictive capacity, and visualization capabilities to virtual networks. Coverage includes configuration assurance, health, performance, capacity, and troubleshooting for NSX logical switches, logical routers, edge services, distributed firewall, and load balancers.

The NSX for vSphere management pack is tightly integrated with vROps and vSphere host data is correlated with the NSX services running on top of these hosts. With log integration via vRLI, error and outage conditions, triggered via log messages, are alerted within the management pack object and problem windows.

### vRealize Operations Federation Management Pack
{: #opsmgmt-vrops-management-federation}

vRealize Operations Federation Management Pack enables a multi-site vROps deployment into a single pane of glass. It allows a deployment of vROps with the capability of receiving key metrics for specified objects from vROps deployments.

### Management Pack for Hybrid Cloud Extension (HCX)
{: #opsmgmt-vrops-management-hcx}

vRealize Operations Management Pack for HCX extends the Operations Management capabilities of vROps to hybrid capabilities presented by HCX. With the management pack, you can collect metrics, change events, and resource topology information from HCX. It enables the monitoring, isolation, and resolution of performance bottlenecks in the HCX Interconnects, Migrations, or Protected workloads.

**Next topic**: [vRealize Log Insights](/docs/services/vmwaresolutions?topic=vmware-solutions-opsmgmt-vrli)

## Related links
{: #opsmgmt-vrops-links}

* [vRealize Operations Manager 7.0 Sizing Guidelines](https://kb.vmware.com/s/article/57903){:external}
* [vRealize Operations Manager documentation](https://docs.vmware.com/en/vRealize-Operations-Manager/index.html){:external}
* [vRealize Operations Management Pack for vSAN 1.0 Guide](https://marketplace.vmware.com/resources/vsx/product_files/31742/original/Management-Pack-for-vSAN-Guide6d2a8895b022a5f626a86e8e84b031b5.pdf){:external}
* [Updating vSAN clusters](/docs/services/vmwaresolutions?topic=vmware-solutions-vum-updating-vsan)
* [vSAN Health Check Information](https://kb.vmware.com/s/article/2114803){:external}
* [Operationalizing VMware NSX](https://www.vmware.com/content/dam/digitalmarketing/vmware/en/pdf/products/nsx/vmware-operationalizing-nsx.pdf){:external}
* [NSX Operations Guide](https://communities.vmware.com/servlet/JiveServlet/previewBody/30079-102-2-40474/NSX-Operations-Guide-v6.1.pdf){:external}
