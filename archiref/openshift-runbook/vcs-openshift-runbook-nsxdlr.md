---

copyright:

  years:  2019

lastupdated: "2019-10-30"

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# OpenShift NSX DLR configuration
{: #openshift-runbook-runbook-nsxdlr-intro}

This section details the NSX distributed logical router that is used to support the OpenShift 4.2 environment. To use this information, you must understand how to create these components and add the configuration.

Review [Distributed Logical Router](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.admin.doc/GUID-A20103B0-ABA1-4884-8EC3-287874E23181.html){:external}. PowerNSX commands are provided if you would want to use this method.

## NSX DLR
{: #openshift-runbook-runbook-nsxdlr-config}

The NSX distributed logical router runs as a kernel module in the hypervisor of each host and is optimized for East-West routing. Optionally, a DLR Control VM can be installed. The DLR Control VM is needed to peer with NSX Edges and NSX Controllers for dynamic routing (OSPF or BGP) updates. In this deployment, static routing is used. However, DLR Control VMs are deployed, in case you require to use a routing protocol.

The NSX DLR Control VMs are configured as an active/passive pair of appliances. During the configuration process, the DLR control VM is deployed in the compact size and the NSX DLR is connected to the OpenShift Edge.

| Component | Configuration |
|-----------|---------------|
| CPU       | 1 vCPU        |
| RAM       | 1 GB          |
| Disk      | 4.5 GB VMDK resident on shared storage with 4 GB swap |
{: caption="Table 1. NSX DLR deployment" caption-side="top"}

Since the NSX DLR Control VMs are configured as active/passive, you must create vSphere Distributed Resource Scheduler (DRS) anti-affinity rules to ensure that NSX Edges do not run on the same host as their respective peer appliance.

| Field     | Value         |
|-----------|---------------|
| Name      | OpenShift-DLR |
| Type      | Separate virtual machines |
| Members   | OpenShift-DLR-0 <br> OpenShift-DLR-1 |
{: caption="Table 2. NSX DLR anti-affinity rules" caption-side="top"}

## NSX DLR interfaces
{: #openshift-runbook-runbook-nsxdlr-interfaces}

The NSX DLR is deployed with a transit network between the OpenShift NSX Edge and the OpenShift Logical switch. The Edge is defined as an uplink interface and the Logical switch is defined as an internal interface.

| Interface name| Interface type | IP addresses | Port group / Logical switch |
| --- | ---| --- | --- |
| OpenShift-LS | Internal | 192.168.133.1 | OpenShift-LS |
| OpenShift-Transit | Uplink | 192.168.100.2/24 | OpenShift-Transit  |
{: caption="Table 3. Configuration for NSX DLR - interfaces" caption-side="top"}

## NSX DLR firewall
{: #openshift-runbook-runbook-nsxdlr-firewall}

The DLR firewall is configured open.

| Firewall rule | Source | Destination | Service | Action |
| --- | --- | --- | --- | --- |
| Default | any | any | any | Accept |
{: caption="Table 4. Configuration for NSX DLR - NSX firewalls" caption-side="top"}

## NSX DLR routes
{: #openshift-runbook-runbook-nsxdlr-routes}

On the Edge, the default route is configured to be to the transit network connection to the OpenShift Edge.

### Global configuration
{: #openshift-runbook-runbook-nsxdlr-global-config}

| Global configuration | vNIC | Gateway IP |
| --- | --- | --- |
| Default Gateway | Transit-Uplink | 192.168.100.1 |
{: caption="Table 5. Configuration for NSX Edge - global configuration" caption-side="top"}

## NSX DHCP relay
{: #openshift-runbook-runbook-nsxdlr-dhcprelay}

For the OpenShift 4.2 environment, the connection to the DHCP Service runs on the OpenShift Edge.

| DCHP relay | Value |
| :--- | --- |
| IP address  | 192.168.101.1 |
{: caption="Table 6. Configuration for NSX Edge - DHCP relay" caption-side="top"}

| DCHP relay | Value |
| :--- | --- |
| Name  | OpenShift-LS |
| Gateway IP | 192.168.133.1 |
{: caption="Table 7. Configuration for NSX Edge - DHCP relay agent" caption-side="top"}

## PowerNSX commands
{: #openshift-runbook-runbook-nsxdlr-powernsx}

This section provides example PowerNSX commands that you can use to automate the provisioning and configuration of the NSX DLR.

Use the following table to document the parameters that you need for your deployment. Examples are shown that match the deployment described previously.

| Parameters | Example | Your Deployment |
| --- | --- | --- |
| vCenter Server IP address | | |
| vCenter User | | |
| vCenter Password | | |
| Transit Logical Switch| OpenShift-Transit | |
| OpenShift Logical Switch | OpenShift-LS | |
| Uplink IP address | 192.168.100.2 | |
| Internal IP address | 192.168.133.1 | |
| DLR Name | OpenShift-DLR | |
| vCenter Server instance Cluster | cluster1 | |
| vCenter Server instance Datastore | vsanDatastore | |
{: caption="Table 8. PowerNSX DLR Parameters" caption-side="top"}

```powernsx
# Connect to NSX Manager
Connect-NsxServer -vCenterServer <IP_Address> -User <UserName> -Password '<Password>'

# Create DLR interface specifications and then create DLR
$uplinkLif = New-NsxLogicalRouterInterfaceSpec -Name ToESG -Type uplink -ConnectedTo (Get-NsxLogicalSwitch OpenShift-Transit) -PrimaryAddress 192.168.100.2 -SubnetPrefixLength 24
$internalLif = New-NsxLogicalRouterInterfaceSpec -Name ToLS -Type internal -ConnectedTo (Get-NsxLogicalSwitch OpenShift-LS) -PrimaryAddress 192.168.133.1 -SubnetPrefixLength 24
$haLif = New-NsxLogicalRouterInterfaceSpec -Name ToHA -Type internal -ConnectedTo (Get-NsxLogicalSwitch OpenShift-HA)
New-NsxLogicalRouter -Name OpenShift-DLR -ManagementPortGroup (Get-NsxLogicalSwitch OpenShift-HA) -Interface $uplinkLif,$internalLif,$haLif -Cluster (Get-Cluster cluster1) -EnableHA -Datastore (Get-Datastore vsanDatastore)

# Configure the default gateway on the DLR to be the ESG
$uplinkVnic = Get-NsxLogicalRouter OpenShift-DLR | Get-NsxLogicalRouterInterface "ToESG"
$uplinkVnicId = $uplinkVnic.index
Get-NsxLogicalRouter OpenShift-DLR | Get-NsxLogicalRouterRouting | Set-NsxLogicalRouterRouting -DefaultGatewayVnic $uplinkVnicId -DefaultGatewayAddress 192.168.100.1 -Confirm:$false

# Configure the default firewall rule on the DLR to "allow"
$dlr = Get-NsxLogicalRouter OpenShift-DLR
$dlr.features.firewall.defaultpolicy.action = "Accept"
$dlr | Set-NsxLogicalRouter -Confirm:$false

# Configure DHCP relay on DLR
$dlrID = (Get-NsxLogicalRouter -Name "OpenShift-DLR").Id
$internalLifVnicId = (Get-NsxLogicalRouter OpenShift-DLR | Get-NsxLogicalRouterInterface "ToLS").index
$uri = "/api/4.0/edges/$($dlrID)/dhcp/config/relay"
$xmlPayload = "
  <relay>
  <relayServer>
    <ipAddress>192.168.100.1</ipAddress>
  </relayServer>
  <relayAgents>
    <relayAgent>
      <vnicIndex>$($internalLifVnicId)</vnicIndex>
      <giAddress>192.168.133.1</giAddress>
    </relayAgent>
  </relayAgents>
 </relay>"

$null = invoke-nsxwebrequest -method "put" -uri $uri -body $xmlPayload -connection $nsxConnection

# Disconnect
Disconnect-NsxServer
```


**Next topic:** [IBM Cloud for VMware Solutions DNS configuration](/docs/services/vmwaresolutions?topic=vmware-solutions-openshift-runbook-runbook-dns-intro)

## Related links
{: #vcs-openshift-runbook-nsxdlr-related}

* [OpenShift Bastion host setup](/docs/services/vmwaresolutions?topic=vmware-solutions-openshift-runbook-runbook-bastion-intro)
* [Red Hat OpenShift 4.2 user provider infrastructure installation](/docs/services/vmwaresolutions?topic=vmware-solutions-openshift-runbook-runbook-install-intro)
