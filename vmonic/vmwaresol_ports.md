---

copyright:

  years:  2020, 2021

lastupdated: "2021-04-01"

keywords: VLAN ports, vmware solutions ports, ports usage vmware solutions

subcollection: vmwaresolutions

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:download: .download}
{:preview: .preview}

# Ports that are used by VMware Solutions
{: #vmwaresol_ports}

A VMware vCenter Server® instance can connect to the following different VLANs for different purposes:
* Public VLAN
* Private VLAN
* Secondary private VLAN
{: shortdesc}

For more information about VLANs, see [{{site.data.keyword.vmwaresolutions_full}} network architecture](/docs/vmwaresolutions?topic=vmwaresolutions-under_the_hood#under_the_hood-network).

## VLANs and subnets in VMware Solutions
{: #vmwaresol_ports-icv4}

The following table provides information about the subnets that are used in each VLAN. You can either order new VLANs or subnets for vCenter Server or you can select existing VLANs. You can define your firewall rules based on the subnets and ports that the network traffic goes through.

It is not recommended to put a firewall on a secondary private VLAN that has storage and vSphere® vMotion® traffic.
{:note}

| Public VLAN | Private VLAN | Secondary private VLAN |
|:------------|:-------------|:-----------------------|
| Primary subnet<br><br>Portable subnets:<br>- Management edge gateway public<br>- Customer edge gateway public | Primary subnet<br><br>Portable subnets:<br>- Infrastructure VMs (CD/vCenter/AD)<br>- NSX host TEP traffic (NSX-T)[^hosttep-v7]<br>- VMware NSX® Host TEP (NSX-V)<br>- Customer edge gateway private | Portable subnets:<br>- vSAN™ traffic<br>- Shared storage traffic<br>- vMotion traffic<br>- NSX host TEP traffic (NSX-T)[^hosttep-v67]<br>- NSX edge TEP traffic (NSX-T)<br>- Customer edge TEP traffic (NSX-T) |
{: caption="Table 1. Subnets for public, private, and secondary private VLANs" caption-side="top"}

[^hosttep-v7]: This is only supported with NSX-T on VMware vSphere 7.

[^hosttep-v67]: This is only supported with NSX-T on VMware vSphere 6.7.

## Ports that are used for deployment and day 2 operations
{: #vmwaresol_ports-vmwaredeploy-day2ops}

The following table provides information about the ports for deployment and day 2 operations.

Review the following information about the ports described in the table:

* Windows® Active Directory™ has two options: single Windows Virtual Service Instance (VSI) and two HA dedicated Windows Server virtual machines (VMs).
   For single Windows VSI, the VSI is in the primary subnet. For Windows server VMs, the VSIs are in the infrastructure VMs subnet.
* {{site.data.keyword.cloud}} infrastructure services network includes the following subnets. For more information, see [IBM Cloud IP ranges](/docs/hardware-firewall-dedicated?topic=hardware-firewall-dedicated-ibm-cloud-ip-ranges#ibm-cloud-ip-ranges).
  * 10.0.0.0/14
  * 10.198.0.0/15
  * 10.200.0.0/14
  * 161.26.0.0/16
* {{site.data.keyword.cloud_notm}} endpoint service network includes 166.8.0.0/14.

For more information about Red Hat® OpenShift® (OCP) networking, see [About the OpenShift SDN network provider](https://docs.openshift.com/container-platform/4.4/networking/openshift_sdn/about-openshift-sdn.html){:external}.

| Source | Subnet/IP range | Target | Subnet/IP range | Port | Protocol | Purpose | Service |
|:-------|:----------------|:-------|:----------------|:-----|:---------|:--------|:--------|
| IBM CloudBuilder<br>IBM CloudDriver | Private primary subnet<br>Infrastructure VMs | ESXi™ host | Private primary subnet | 22 | TCP™ | Set up, configure, patch ESXi host | SSH |
| IBM CloudBuilder<br>IBM CloudDriver | Private primary subnet<br>Infrastructure VMs | ESXi vMotion | vMotion traffic | | ICMP™ | Set up ESXi network | |
| IBM CloudBuilder<br>IBM CloudDriver | Private primary subnet<br>Infrastructure VMs | ESXi vSAN™  | vSAN traffic | | ICMP | Set up ESXi network | |
| IBM CloudBuilder<br>IBM CloudDriver | Private primary subnet<br>Infrastructure VMs | ESXi shared storage | Shared storage traffic | | ICMP | Set up ESXi network | |
| IBM CloudBuilder<br>IBM CloudDriver | Private primary subnet<br>Infrastructure VMs | Customer edge private | Customer edge gateway private | | ICMP | Set up NSX edge network | |
| IBM CloudBuilder<br>IBM CloudDriver | Private primary subnet<br>Infrastructure VMs | Windows Active Directory  | Private primary subnet (for Windows VSI)/<br>Infrastructure VMs (for Windows VMs) | 5986 | TCP | Set up and configure Windows Active Directory and DNS  | |
| IBM CloudBuilder | Private primary subnet | vCenter Server | Infrastructure VMs | | ICMP | Install and set up vCenter Server | |
| IBM CloudBuilder<br>IBM CloudDriver | Private primary subnet<br>Infrastructure VMs | vCenter Server | Infrastructure VMs | 22 | TCP | Set up and configure vCenter Server | SSH |
| IBM CloudBuilder<br>IBM CloudDriver | Private primary subnet<br>Infrastructure VMs | vCenter Server | Infrastructure VMs | 443 | TCP | Install and configure vCenter Server and cluster | SSH |
| IBM CloudBuilder<br>IBM CloudDriver | Private primary subnet<br>Infrastructure VMs | vCenter Server | Infrastructure VMs | 9443 | TCP | Install and configure vCenter Server and cluster | |
| IBM CloudBuilder<br>IBM CloudDriver | Private primary subnet<br>Infrastructure VMs | vCenter Server | Infrastructure VMs | 5489 | TCP | Install and configure vCenter Server and cluster | |
| IBM CloudBuilder | Private primary subnet<br>Infrastructure VMs | NSX Manager | Infrastructure VMs | | ICMP | Install and set up NSX Manager | |
| IBM CloudBuilder | Private primary subnet<br>Infrastructure VMs | NSX Manager | Infrastructure VMs | 443 | TCP | Set up and configure NSX Manager | HTTPS |
| IBM CloudBuilder | Private primary subnet<br>Infrastructure VMs | NSX Manager | Infrastructure VMs | 80 | TCP | Set up and configure NSX Manager | HTTP |
| IBM CloudBuilder<br>IBM CloudDriver | Private primary subnet<br>Infrastructure VMs | {{site.data.keyword.cloud_notm}} infrastructure provisioning API | {{site.data.keyword.cloud_notm}} infrastructure services network | 443 | TCP | Order and provision {{site.data.keyword.cloud_notm}} infrastructure resources | HTTPS |
| IBM CloudBuilder<br>IBM CloudDriver | Private primary subnet<br>Infrastructure VMs | {{site.data.keyword.cloud_notm}} infrastructure DNS service | {{site.data.keyword.cloud_notm}} infrastructure services network | 53 | UDP™ | Use {{site.data.keyword.cloud_notm}} infrastructure DNS service | |
| IBM CloudBuilder<br>IBM CloudDriver | Private primary subnet<br>Infrastructure VMs | {{site.data.keyword.cloud_notm}} infrastructure NTP service | {{site.data.keyword.cloud_notm}} infrastructure services network | 123 | UDP | Use {{site.data.keyword.cloud_notm}} infrastructure NTP service | |
| IBM CloudBuilder<br>IBM CloudDriver | Private primary subnet<br>Infrastructure VMs | {{site.data.keyword.cloud_notm}} infrastructure endurance storage | {{site.data.keyword.cloud_notm}} infrastructure services network | Any | ICMP and TCP | Set up endurance storage for ESXi host | |
| IBM CloudBuilder<br>IBM CloudDriver | Private primary subnet<br>Infrastructure VMs | {{site.data.keyword.cloud_notm}} Service - Cloud Object Storage | {{site.data.keyword.cloud_notm}} endpoint service network | 443 | TCP | Use {{site.data.keyword.cloud_notm}} Object Storage service | HTTPS |
| IBM CloudBuilder<br>IBM CloudDriver | Private primary subnet<br>Infrastructure VMs | {{site.data.keyword.cloud_notm}} Service - Rabbit MQ<br>166.9.48.91, 166.9.51.14, 166.9.58.39 | {{site.data.keyword.cloud_notm}} endpoint service network | 32378 | TCP | Use {{site.data.keyword.cloud_notm}} Rabbit MQ service | |
| IBM CloudBuilder<br>IBM CloudDriver | Private primary subnet<br>Infrastructure VMs | {{site.data.keyword.cloud_notm}} Activity Tracker service | {{site.data.keyword.cloud_notm}} endpoint service network | 443 | TCP | Use {{site.data.keyword.cloud_notm}} Activity Tracker service | HTPPS |
| Windows Active Directory | Private primary subnet<br>Infrastructure VMs | {{site.data.keyword.cloud_notm}} infrastructure DNS service | {{site.data.keyword.cloud_notm}} infrastructure services network | 53 | UDP | Use {{site.data.keyword.cloud_notm}} infrastructure DNS service | |
| Windows Active Directory | Private primary subnet<br>Infrastructure VMs | {{site.data.keyword.cloud_notm}} infrastructure NTP service | {{site.data.keyword.cloud_notm}} infrastructure services network | 123 | UDP | Use {{site.data.keyword.cloud_notm}} infrastructure NTP service | |
| Windows Active Directory | Private primary subnet<br>Infrastructure VMs | {{site.data.keyword.cloud_notm}} infrastructure WSUS service | {{site.data.keyword.cloud_notm}} infrastructure services network | 80 | TCP | Use {{site.data.keyword.cloud_notm}} infrastructure WSUS service | HTTP |
| Windows Active Directory | Private primary subnet<br>Infrastructure VMs | {{site.data.keyword.cloud_notm}} infrastructure Windows KMS service | {{site.data.keyword.cloud_notm}} infrastructure services network | 1688 | TCP | Use {{site.data.keyword.cloud_notm}} infrastructure Windows KMS service | |
| ESXi host | Private primary subnet | {{site.data.keyword.cloud_notm}} infrastructure NTP service | {{site.data.keyword.cloud_notm}} infrastructure services network | 123 | UDP | Use {{site.data.keyword.cloud_notm}} infrastructure NTP service | |
| vCenter Server | Infrastructure VMs | {{site.data.keyword.cloud_notm}} infrastructure NTP service | {{site.data.keyword.cloud_notm}} infrastructure services network | 123 | UDP | Use {{site.data.keyword.cloud_notm}} infrastructure NTP service | |
| NSX Manager | Infrastructure VMs | {{site.data.keyword.cloud_notm}} infrastructure NTP service | {{site.data.keyword.cloud_notm}} infrastructure services network | 123 | UDP | Use {{site.data.keyword.cloud_notm}} infrastructure NTP service | |
| NSX Manager | Infrastructure VMs | TEP subnet | TEP traffic | 443 |  |  |  |
| NSX Manager | Infrastructure VMs | Customer edge subnet | Customer edge private traffic | 443 |  |  |  |
| ESXi host shared storage | ESXi shared storage | {{site.data.keyword.cloud_notm}} infrastructure endurance storage | {{site.data.keyword.cloud_notm}} infrastructure services network | 111, 635, and 2049 | TCP and UDP | Use {{site.data.keyword.cloud_notm}} infrastructure endurance storage | |
| IBM CloudBuilder<br>IBM CloudDriver<br>Windows Active Directory (VSI) | Private primary subnet | {{site.data.keyword.cloud_notm}} infrastructure engine | {{site.data.keyword.cloud_notm}} infrastructure services network | 80 | TCP | Provision IBM CloudBuilder, IBM CloudDriver, and Windows Active Directory (VSI) | |
| {{site.data.keyword.cloud_notm}} infrastructure engine | {{site.data.keyword.cloud_notm}} infrastructure services network | IBM CloudBuilder<br>IBM CloudDriver<br>Windows Active Directory (VSI) | Private primary subnet | Any | TCP and UDP | Provision IBM CloudBuilder, IBM CloudDriver, and Windows Active Directory (VSI) | |
| {{site.data.keyword.cloud_notm}} infrastructure engine | {{site.data.keyword.cloud_notm}} infrastructure services network | ESXi host management0 | Private primary subnet | 623 | TCP and UDP | {{site.data.keyword.cloud_notm}} infrastructure IPMI | |
{: caption="Table 2. Ports for deployment and day 2 operations" caption-side="top"}

## Ports that are used by VMware
{: #vmwaresol_ports-vmwareuses}

The following table shows the ports that are used by VMware®. The ports in VMware traffic are disclosed in {{site.data.keyword.vmwaresolutions_short}} deployment and day 2 operations.

| Source | Subnet | Target | Subnet | Port | Protocol |
|:-------|:-------|:-------|:-------|:-----|:---------|
| ESXi host | Private primary subnet | vCenter Server | Infrastructure VMs | 902 | TCP and UDP |
| ESXi host | Private primary subnet | vCenter Server | Infrastructure VMs | 443 | TCP |
| ESXi host | Private primary subnet | NSX Manager | Infrastructure VMs | 5671 | TCP |
| ESXi host | Private primary subnet | NSX Manager | Infrastructure VMs | 1234 and 1235 | TCP and UDP |
| ESXi host | Private primary subnet | NSX Controllers | Infrastructure VMs | 1234 and 1235 | TCP |
| ESXi host | Private primary subnet | Windows Active Directory | Private primary subnet<br>Infrastructure VMs | 88 | TCP and UDP |
| ESXi host | Private primary subnet | Windows Active Directory | Private primary subnet<br>Infrastructure VMs | 445 | TCP |
| vCenter Server | Infrastructure VMs | ESXi host | Private primary subnet | 902 | TCP and UDP |
| vCenter Server | Infrastructure VMs | ESXi host | Private primary subnet | 443 | TCP |
| vCenter Server | Infrastructure VMs | ESXi host | Private primary subnet | 9080 | TCP |
| vCenter Server | Infrastructure VMs | Windows Active Directory | Private primary subnet<br>Infrastructure VMs | 53 | UDP |
| vCenter Server | Infrastructure VMs | Windows Active Directory | Private primary subnet<br>Infrastructure VMs | 389 | TCP and UDP |
| vCenter Server | Infrastructure VMs | Windows Active Directory | Private primary subnet<br>Infrastructure VMs | 445 | TCP |
| vCenter Server | Infrastructure VMs | Windows Active Directory | Private primary subnet<br>Infrastructure VMs | 88 | TCP and UDP |
| NSX Manager | Infrastructure VMs | ESXi host | Private primary subnet | 443 | TCP |
| NSX Manager | Infrastructure VMs | Windows Active Directory | Private primary subnet<br>Infrastructure VMs | 53 | UDP |
{: caption="Table 3. Ports used by VMWare" caption-side="top"}

For more information, see [TCP and UDP ports required to access VMware components](https://kb.vmware.com/s/article/1012382){:external}.

## Ports for services
{: #vmwaresol_ports-vmware-optional-services}

The following topics provide information about the ports that are used by the services.

### Ports for Caveonix RiskForesight
{: #vmwaresol_ports-vmware-optional-services-caveonix}

The following table provides information about the Caveonix RiskForesight™ ports.

| Source | Subnet/IP range | Target | Subnet/IP range |  Port | Protocol | Purpose | Service |
|:-------|:----------------|:-------|:----------------|:------|:---------|:--------|:--------|
| Caveonix | New subnet ordered in private VLAN | vCenter Server | Infrastructure VMs | 443 | TCP | Use vCenter Server REST service | HTTPS |
| Caveonix | New subnet ordered in private VLAN | Windows Active Directory | Private primary subnet<br>Infrastructure VMs | 53 | UDP | Use Windows DNS service | DNS |
| Caveonix | New subnet ordered in private VLAN | {{site.data.keyword.cloud_notm}} infrastructure Redis service | {{site.data.keyword.cloud_notm}} infrastructure services network | 6379 | TCP | Use {{site.data.keyword.cloud_notm}} infrastructure Redis service | |
| IBM CloudDriver | Private primary subnet<br>Infrastructure VMs | Caveonix | New subnet ordered in private VLAN | 1337 | TCP | Set up and configure Caveonix | |
| IBM CloudDriver | Private primary subnet<br>Infrastructure VMs | Caveonix | New subnet ordered in private VLAN | 8080 | TCP | Set up and configure Caveonix | |
{: caption="Table 4. Caveonix RiskForesight ports" caption-side="top"}

### Ports for F5 BIG-IP
{: #vmwaresol_ports-vmware-optional-services-f5bigip}

The following table provides information about the F5 BIG-IP® ports.

| Source | Subnet/IP range | Target | Subnet/IP range |  Port | Protocol | Purpose | Service |
|:-------|:----------------|:-------|:----------------|:------|:---------|:--------|:--------|
| BigIP | New subnet ordered in private VLAN | Windows Active Directory | Private primary subnet<br>Infrastructure VMs | 53 | UDP | Use Windows DNS service | DNS |
| Management-nsx-edge public IP | Public subnet for management edge | BigIP license server | 104.219.111.132/32 | 443 | TCP | License registration | HTTPS |
{: caption="Table 5. F5 BIG-IP ports" caption-side="top"}

### Ports for FortiGate Virtual Appliance
{: #vmwaresol_ports-vmware-optional-services-fortigate}

The following table provides information about the FortiGate® Virtual Appliance ports.

| Source | Subnet/IP range | Target | Subnet/IP range |  Port | Protocol | Purpose | Service |
|:-------|:----------------|:-------|:----------------|:------|:---------|:--------|:--------|
| Management-nsx-edge public IP | Public subnet for management edge | Fortinet® servers | 208.91.112.0/22 | 443 | TCP | FortiGate installation | HTTPS |
| Management-nsx-edge public IP | Public subnet for management edge | Fortinet servers | 96.45.33.0/24 | 443 | TCP | FortiGate installation | HTTPS |
| Management-nsx-edge public IP | Public subnet for management edge | Fortinet servers | 66.35.17.248 | 443 | TCP | FortiGate installation | HTTPS |
{: caption="Table 6. FortiGate Virtual Appliance ports" caption-side="top"}

### Ports for VMware HCX
{: #vmwaresol_ports-vmware-optional-services-hcx}

The following table provides information about the VMware HCX™ ports.

| Source | Subnet/IP range | Target | Subnet/IP range |  Port | Protocol | Purpose | Service |
|:-------|:----------------|:-------|:----------------|:------|:---------|:--------|:--------|
| HCX | New subnet ordered in private VLAN | Windows Active Directory | Private primary subnet<br>Infrastructure VMs | 53 | UDP | Use Windows DNS service | DNS |
| HCX | New subnet ordered in private VLAN | vCenter Server | Infrastructure VMs | 443 | TCP | Use vCenter Server REST service | HTTPS |
| HCX | New subnet ordered in private VLAN | NSX Manager | Infrastructure VMs | 443 | TCP | Use NSX Manager registration service | HTTPS |
| HCX public IP | New subnet ordered in public VLAN | connect.hcx.<br>vmware.com | Public IP 45.60.63.140 | 443 | TCP | Registration service | HTTPS |
| vCenter Server | Infrastructure VMs | HCX | New subnet ordered in private VLAN | 443 | TCP | Use HCX REST service | HTTPS |
| IBM CloudDriver | Private primary subnet<br>Infrastructure VMs | HCX | New subnet ordered in private VLAN | 443 | TCP | Use HCX REST service | HTTPS |
| IBM CloudDriver | Private primary subnet<br>Infrastructure VMs | HCX | New subnet ordered in private VLAN | 9443 | TCP | Use HCX Virtual Appliance Management Interface for HCX system configuration | HTTPS |
{: caption="Table 7. VMware HCX ports" caption-side="top"}

### Ports for HyTrust CloudControl, HyTrust DataControl, and HyTrust KeyControl
{: #vmwaresol_ports-vmware-optional-services-hytrust}

The following table provides information about the HyTrust® CloudControl™, HyTrust DataControl®, and HyTrust KeyControl™ ports.

| Source | Subnet/IP range | Target | Subnet/IP range | Port | Protocol | Purpose | Service |
|:-------|:----------------|:-------|:----------------|:-----|:---------|:--------|:--------|
| HyTrust CloudControl | Infrastructure VMs | {{site.data.keyword.cloud_notm}} infrastructure NTP service | {{site.data.keyword.cloud_notm}} infrastructure services network | 123 | UDP | Use {{site.data.keyword.cloud_notm}} infrastructure NTP service | NTP |
| HyTrust CloudControl | Infrastructure VMs | Windows Active Directory and DNS server | Private primary subnet<br>Infrastructure VMs | 53 | UDP | Use Windows DNS service | DNS |
| HyTrust CloudControl | Infrastructure VMs | Windows Active Directory | Private primary subnet<br>Infrastructure VMs | | ICMP | Ping | Ping |
| HyTrust CloudControl | Infrastructure VMs | Windows Active Directory | Private primary subnet<br>Infrastructure VMs | 443 | TCP | Access Windows Active Directory | HTTPS |
| HyTrust DataControl | Infrastructure VMs | Windows Active Directory | {{site.data.keyword.cloud_notm}} infrastructure services network | 123 | UDP | Use {{site.data.keyword.cloud_notm}} infrastructure NTP service | NTP |
| HyTrust DataControl | Infrastructure VMs | Windows Active Directory | Private primary subnet<br>Infrastructure VMs | 53 | UDP | Use Windows DNS service | DNS |
| HyTrust KeyControl | Infrastructure VMs | {{site.data.keyword.cloud_notm}} infrastructure NTP service | {{site.data.keyword.cloud_notm}} infrastructure services network | 123  | UDP | Use {{site.data.keyword.cloud_notm}} infrastructure NTP service | NTP |
| HyTrust KeyControl | Infrastructure VMs | Windows Active Directory | Private primary subnet<br>Infrastructure VMs | 53 | UDP | Use Windows DNS service | DNS |
{: caption="Table 8. HyTrust CloudControl, HyTrust DataControl, and HyTrust KeyControl ports" caption-side="top"}

### Ports for IBM Spectrum Protect Plus
{: #vmwaresol_ports-vmware-optional-services-spp}

The following table provides information about the IBM Spectrum® Protect Plus ports.

| Source | Subnet/IP range | Target | Subnet/IP range |  Port | Protocol | Purpose | Service |
|:-------|:----------------|:-------|:----------------|:------|:---------|:--------|:--------|
| IBM Spectrum Protect Plus | Infrastructure VMs | {{site.data.keyword.cloud_notm}} infrastructure NTP service | {{site.data.keyword.cloud_notm}} infrastructure services network | 123 | UDP | Use {{site.data.keyword.cloud_notm}} infrastructure NTP service | NTP |
{: caption="Table 9. IBM Spectrum Protect Plus ports" caption-side="top"}

### Ports for Juniper vSRX
{: #vmwaresol_ports-vmware-optional-services-juniper-vsrx}

The following table provides information about the Juniper® vSRX ports.

| Source | Subnet/IP range | Target | Subnet/IP range |  Port | Protocol | Purpose | Service |
|:-------|:----------------|:-------|:----------------|:------|:---------|:--------|:--------|
| IBM CloudDriver | Private primary subnet<br>Infrastructure VMs | vSRX private IPs | New subnet ordered in private VLAN | 22 | TCP | Set up and configure vSRX | SSH |
| IBM CloudDriver | Private primary subnet<br>Infrastructure VMs | vSRX private IPs | New subnet ordered in private VLAN | 830 | TCP | Set up and configure vSRX by NETCONF over SSH | |
| vSRX | vSRX Private IP | vRealize Log Insight (if vROPs service is installed) | vRealize Log Insight FQDN | 514 | UDP | Remote syslog to vRealize Log Insight if vROPs service is installed | Syslog |
{: caption="Table 10. Juniper vSRX ports" caption-side="top"}

### Ports for Red Hat OpenShift for VMWare
{: #vmwaresol_ports-vmware-optional-services-red-hat-openshift}

The following table provides information about the Red Hat OpenShift ports.

| Source | Subnet/IP range | Target | Subnet/IP range |  Port | Protocol | Purpose | Service |
|:-------|:----------------|:-------|:----------------|:------|:---------|:--------|:--------|
| OCP | New subnet ordered in private VLAN | Windows Active Directory | Private primary subnet<br>Infrastructure VMs | 53 | UDP | Use Windows DNS service | DNS |
| OCP | New subnet ordered in private VLAN | vCenter Server | Infrastructure VMs | 443 | TCP | Use vCenter Server REST service | HTTPS |
| OCP | New subnet ordered in private VLAN | {{site.data.keyword.cloud_notm}} infrastructure NTP service | {{site.data.keyword.cloud_notm}} infrastructure services network | 123 | UDP | Use {{site.data.keyword.cloud_notm}} infrastructure NTP service | NTP |
| OCP | New subnet ordered in private VLAN | OCP cluster network | OCP internal IP range 10.128.0.0/14 | 5443/8443 | TCP | OCP cluster management | WEBREST API |
| OCP edge public IPs | New subnet ordered in public VLAN | Public websites required for OpenShift installation[^osinst] | | 80/123/443 | TCP and UDP | Time service, OpenShift installation content, and images | NTP/HTTP/HTTPS |
| IBM CloudDriver | Private primary subnet<br>Infrastructure VMs | OCP | New subnet ordered in private VLAN | 22 | TCP | Set up and configure OCP | SSH |
{: caption="Table 11. Red Hat OpenShift for VMWare ports" caption-side="top"}
[^osinst]: For more information, see [Configuring your firewall](https://docs.openshift.com/container-platform/4.4/installing/install_config/configuring-firewall.html){:external}.

For more information about OCP networking, see [About the OpenShift SDN network provider](https://docs.openshift.com/container-platform/4.4/networking/openshift_sdn/about-openshift-sdn.html){:external}.

### Ports for Veeam
{: #vmwaresol_ports-vmware-optional-services-veeam}

The following table provides information about the Veeam® ports.

| Source | Subnet/IP range | Target | Subnet/IP range |  Port | Protocol | Purpose | Service |
|:-------|:----------------|:-------|:----------------|:------|:---------|:--------|:--------|
| Veeam | Private primary subnet | {{site.data.keyword.cloud_notm}} infrastructure DNS service | Private primary subnet<br>Infrastructure VMs | 53 | UDP | Use {{site.data.keyword.cloud_notm}} infrastructure DNS service | UDP |
| Veeam | Private primary subnet | {{site.data.keyword.cloud_notm}} infrastructure NTP service | {{site.data.keyword.cloud_notm}} infrastructure services network | 123 | UDP | Use {{site.data.keyword.cloud_notm}} infrastructure NTP service | NTP |
| Veeam | Private primary subnet | {{site.data.keyword.cloud_notm}} infrastructure service - Provision Windows VSI | {{site.data.keyword.cloud_notm}} infrastructure services network | | ICMP | Use infrastructure services to provision Windows VSI for Veeam | Ping |
| Veeam | Private primary subnet | {{site.data.keyword.cloud_notm}} infrastructure service - Provision Windows VSI | {{site.data.keyword.cloud_notm}} infrastructure services network | 10000 | TCP | Use infrastructure services to provision Windows VSI for Veeam | |
| Veeam | Private primary subnet | {{site.data.keyword.cloud_notm}} infrastructure service - Provision Windows VSI | {{site.data.keyword.cloud_notm}} infrastructure services network | 10001 | TCP | Use infrastructure services to provision Windows VSI for Veeam | |
| Veeam | Private primary subnet | {{site.data.keyword.cloud_notm}} infrastructure service - Provision Windows VSI | {{site.data.keyword.cloud_notm}} infrastructure services network | 88 | TCP and UDP | Use infrastructure services to provision Windows VSI for Veeam | |
| Veeam | Private primary subnet | {{site.data.keyword.cloud_notm}} infrastructure Windows KMS service | {{site.data.keyword.cloud_notm}} infrastructure services network | 1688 | TCP | Use {{site.data.keyword.cloud_notm}} infrastructure Windows KMS service | |
| Veeam | Private primary subnet | {{site.data.keyword.cloud_notm}} service - Cloud Object Storage | {{site.data.keyword.cloud_notm}} endpoint service network | 443 | TCP | Use {{site.data.keyword.cloud_notm}} Object Storage service | HTTPS |
| Veeam | Private primary subnet | {{site.data.keyword.cloud_notm}} infrastructure WSUS service | {{site.data.keyword.cloud_notm}} infrastructure services network | 80 | TCP | Use {{site.data.keyword.cloud_notm}} infrastructure WSUS service | HTPP |
| Veeam | Private primary subnet | {{site.data.keyword.cloud_notm}} infrastructure endurance storage | {{site.data.keyword.cloud_notm}} infrastructure services network | 3260 | TCP | Use {{site.data.keyword.cloud_notm}} infrastructure endurance storage | ISCSI |
| {{site.data.keyword.cloud_notm}} infrastructure Service - Provision Windows VSI | {{site.data.keyword.cloud_notm}} infrastructure services network 10.0.0.0/14 | Veeam | Private primary subnet | 8051 | TCP | EMC2 (Legato) Networker or Sun Solstice Backup | |
| {{site.data.keyword.cloud_notm}} infrastructure Service - Provision Windows VSI | {{site.data.keyword.cloud_notm}} infrastructure services network 10.200.0.0/14 | Veeam | Private primary subnet | | ICMP | ICMP | Ping |
{: caption="Table 12. Veeam ports" caption-side="top"}

### Ports for vRealize Operations and Log Insight
{: #vmwaresol_ports-vmware-optional-services-vrops-loginsight}

The following table provides information about the vRealize Operations™ and vRealize Log Insight™ (vROps) ports when vROps is deployed in a vCenter Server with NSX-V instance.

| Source | Subnet/IP range | Target | Subnet/IP range |  Port | Protocol | Purpose | Service |
|:-------|:----------------|:-------|:----------------|:------|:---------|:--------|:--------|
| ESXi host | Private primary subnet | vROps | New subnet ordered in private VLAN | 514 | UDP | Remote syslog | Syslog |
| vCenter Server | Infrastructure VMs | vROps | New subnet ordered in private VLAN | 514 | UDP | Remote syslog | Syslog |
| Local address (192.168.100.3) | Local address | vROps | New subnet ordered in private VLAN | 514 | UDP | Remote syslog | Syslog |
| vROps | New subnet ordered in private VLAN | Windows Active Directory | Private primary subnet<br>Infrastructure VMs| 53 | TCP and UDP | Use Windows DNS service | DNS |
| vROps | New subnet ordered in private VLAN | vCenter Server | Infrastructure VMs | 443 | TCP | vROps configuration | HTTPS |
| vROps | New subnet ordered in private VLAN | NSX Manager | Infrastructure VMs | 443 | TCP | vROps configuration | HTTPS |
| NSX Manager | Infrastructure VMs | vROps | New subnet ordered in private VLAN | 514 | UDP | Remote syslog | Syslog |
| Management edge private IP | Infrastructure VMs | vROps | New subnet ordered in private VLAN | 514 | UDP | Remote syslog | Syslog |
| Customer-nsx-edge private IP | Customer edge gateway private | vROps | New subnet ordered in private VLAN | 514 | UDP | Remote syslog | Syslog |
| IBM CloudDriver | Private primary subnet<br>Infrastructure VMs | vROps | New subnet ordered in private VLAN | 22 | TCP | Set up and configure vROps | SSH |
| IBM CloudDriver | Private primary subnet<br>Infrastructure VMs | vROps | New subnet ordered in private VLAN | 443 | TCP | Set up and configure vROps | HTTPS |
| Windows Active Directory | Private primary subnet<br>Infrastructure VMs | vROps | New subnet ordered in private VLAN | 9543 | TCP | Set up and configure vROps | |
{: caption="Table 13. vROps ports for NSX-V instances" caption-side="top"}

The following table provides information about the vROps ports for vCenter Server with NSX-T instances.

| Source | Subnet/IP range | Target | Subnet/IP range |  Port | Protocol | Purpose | Service |
|:-------|:----------------|:-------|:----------------|:------|:---------|:--------|:--------|
| ESXi host | Private primary subnet | vROps | New subnet ordered in private VLAN | 514 | UDP | Remote syslog | Syslog |
| vCenter Server | Infrastructure VMs | vROps | New subnet ordered in private VLAN | 514 | UDP | Remote syslog | Syslog |
| vROps | New subnet ordered in private VLAN | Windows Active Directory | Private primary subnet<br>Infrastructure VMs | 53 | TCP and UDP | Use Windows DNS service | DNS |
| vROps | New subnet ordered in private VLAN | vCenter Server | Infrastructure VMs | 443 | TCP | vROps configuration | HTTPS |
| vROps | New subnet ordered in private VLAN | NSX-T Manager and NSX-T Controllers | Infrastructure VMs | 443 | TCP | vROps configuration | HTTPS |
| vROps | New subnet ordered in private VLAN | NSX-T Manager and NSX-T Controllers | Infrastructure VMs | 1234 | TCP | NSX messaging | |
| vROps | New subnet ordered in private VLAN | NSX-T Manager and NSX-T Controllers | Infrastructure VMs | 1235 | TCP | NSX messaging |  |
| vROps | New subnet ordered in private VLAN | NSX-T virtual IP | Infrastructure VMs | 443 | TCP | vROps configuration | HTTPS |
| NSX-T Manager and NSX-T Controllers | Infrastructure VMs | vROps | New subnet ordered in private VLAN | 514 | UDP | Remote syslog | Syslog |
| Customer-nsx-edge private IP  | Customer edge gateway private | Windows Active Directory | Private primary subnet<br>Infrastructure VMs | 53 | TCP and UDP | Use Windows DNS service | DNS |
| Customer-nsx-edge private IP  | Customer edge gateway private | NSX-T Manager and NSX-T Controllers | Infrastructure VMs | 1234 | TCP | NSX messaging | |
| Customer-nsx-edge private IP  | Customer edge gateway private | NSX-T Manager and NSX-T Controllers | Infrastructure VMs | 1235 | TCP | NSX messaging | |
| Customer-nsx-edge private IP  | Customer edge gateway private | vROps | New subnet ordered in private VLAN | 514 | UDP | Remote syslog | Syslog |
| IBM CloudDriver | Private primary subnet<br>Infrastructure VMs | vROps | New subnet ordered in private VLAN | 22 | TCP | Set up and configure vROps | SSH |
| IBM CloudDriver | Private primary subnet<br>Infrastructure VMs | vROps | New subnet ordered in private VLAN | 443 | TCP | Set up and configure vROps | HTTPS |
| IBM CloudDriver | Private primary subnet<br>Infrastructure VMs | vROps | New subnet ordered in private VLAN | 9543 | TCP | Set up and configure vROps | HTTPS |
| Windows Active Directory | Private primary subnet<br>Infrastructure VMs | vROps | New subnet ordered in private VLAN | 9543 | TCP | Set up and configure vROps | |
| Service edge | Infrastructure VMs | Windows Active Directory | Private primary subnet<br>Infrastructure VMs | 53 | TCP and UDP | Use Windows DNS service | DNS |
| Service edge | Infrastructure VMs | {{site.data.keyword.cloud_notm}} infrastructure DNS service | {{site.data.keyword.cloud_notm}} infrastructure services network | 53 | UDP | Use {{site.data.keyword.cloud_notm}} infrastructure NTP | DNS |
| Service edge | Infrastructure VMs | {{site.data.keyword.cloud_notm}} infrastructure NTP service | {{site.data.keyword.cloud_notm}} infrastructure services network | 123 | UDP | Use {{site.data.keyword.cloud_notm}} infrastructure NTP | NTP |
{: caption="Table 14. vROps ports for NSX-T instances" caption-side="top"}

For more information about port requirements for vROPs, see [TCP and UDP ports required to access VMware vRealize Operations Manager](https://kb.vmware.com/s/article/52964){:external}.

### Ports for Zerto
{: #vmwaresol_ports-vmware-optional-services-zert0}

The following table provides information about Zerto ports.

| Source | Subnet/IP range | Target | Subnet/IP range |  Port | Protocol | Purpose | Service |
|:-------|:----------------|:-------|:----------------|:------|:---------|:--------|:--------|
| Zerto Management VSI (ZVM) | Private primary subnet<br>Infrastructure VMs | Zerto VRA agents | New subnet ordered in private VLAN | 4006 | TCP | TLS over TCP communication between the ZVM and local site VRAs | |
| Zerto Management VSI (ZVM) | Private primary subnet<br>Infrastructure VMs | Zerto VRA agents | New subnet ordered in private VLAN | 4009 | TCP | TLS over TCP communication between the ZVM and local site VRAs to handle checkpoints | |
| Zerto Management VSI (ZVM) | Private primary subnet<br>Infrastructure VMs | Zerto VRA agents | New subnet ordered in private VLAN | | ICMP | Check network connectivity from ZVM to the VRAs | Ping |
{: caption="Table 15. Zerto ports" caption-side="top"}

For more information about Zerto networking, see [Zerto - prerequisites and requirements for vSphere environments](http://s3.amazonaws.com/zertodownload_docs/Latest/Zerto%20Virtual%20Replication%20vSphere%20Enterprise%20Guidelines.pdf){:external}.

## Related links
{: #vmwaresol_ports-related}

* [VMware Solutions network architecture](/docs/vmwaresolutions?topic=vmwaresolutions-under_the_hood#under_the_hood-network)
