---

copyright:

  years:  2019, 2021

lastupdated: "2021-01-28"

subcollection: vmwaresolutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# vSRX deployment
{: #vcsvsrx-deployment}

Deploy the vCenter Server instance before the vSRX edge gateway appliance order is placed.

## Ordering Juniper gateway devices
{: #vcsvsrx-deployment-order-gateway}

The following procedure assumes that you are deploying the IaaS KVM-based Juniper vSRX HA cluster. If you want to build your own gateway by using ESXi, then order the No-OS gateway option instead. For more information, see [Ordering a Bring Your Own Gateway Appliance](/docs/gateway-appliance?topic=gateway-appliance-order-byoa).

Open the [IBM Cloud infrastructure customer portal](https://control.softlayer.com), then select Infrastructure > Network > Gateway Appliances > Create Gateway.
- Gateway vendor: Juniper.
- Gateway Appliance.
  - Hostname: Provide hostname for node 1 in the gateway cluster.
      - Example: gateway01
      - NOTE: Select a hostname consistent with the existing vCenter Server naming convention since the vSRX nodes are manually added to the vCenter Server AD/DNS server for hostname resolution.
  - Domain: Enter the applicable domain name for the gateway cluster.
    -  Example: `myvcsdomain.local`

        Where myvcsdomain.local is the domain that is assigned to the previously deployed vCenter Server instance.
  - Select High availability.
    - HA Hostname: Provide hostname for node 2 in the gateway cluster.
      - Example: gateway02
      - NOTE: Select a hostname consistent with the existing vCenter Server naming convention since the vSRX nodes are manually added to the vCenter Server AD/DNS server for hostname resolution.
    - HA Domain: Verify that this value is the same domain name that is provided for node1.
        - Example: myvcsdomain.local
- Location.
  - Select geography. Example: NA South.
    - Select dataCenter. Example: Dallas 10.
- POD.
  - Select POD where existing vCenter Server instance is deployed to. Example: dal10.pod01.
  - Make sure that you order the vSRX in the same POD as your vCenter Server instance. VLANs don't span PODs so you must deploy to the correct POD.
    - Determining SoftLayer_Network_Pod

      SoftLayer_Network_Pod refers to a portion of a data center that share a Backend Customer Router (BCR) and usually a front-end counterpart that is known as a Frontend Customer Router (FCR). A Pod primarily denotes a logical location within the network and the physical aspects that support networks, in contrast to representing a specific physical location.

      A Pod is identified by a name, which is unique. A Pod name follows the format ‘dddnn.podii’. ‘ddd’ is a data center code, ‘nn’ is the data center number, and ‘pod’ is a literal string. ‘ii’ is a two-digit number, zero-padded to the left, which corresponds to a Backend Customer Router (BCR) of the data center. Examples:

      dal09.pod01 = Dallas 9, Pod 1 (that is, bcr01)
      sjc01.pod04 = San Jose 1, Pod 4 (that is, bcr04)
      ams01.pod01 = Amsterdam 1, Pod 1 (that is, bcr01)

- Select Dual Processor hardware option.
  - Select: Intel Xeon 5120, 28 core.
- RAM.
  - 192 GB.
- Add-ons.
  - Accept defaults.
- Storage Disks.
  - Type: RAID1.
  - \# Disks: 2.
  - Disk Media: SATA (preselected).
  - Disk Size: 4 TB.
- Network interface.
  - Uplink Port Speeds: 10 Gbps Public & Private Network Uplinks.
    - Ensure that you enable both public and private NICs (four ports total).
  - Add-ons.
    - Accept defaults. Optionally select IPv6 address.

Review order, then select Create. Provisioning takes three to four hours.

## Post deployment
{: #vcsvsrx-deployment-post}

If you deployed the IaaS KVM-based Juniper vSRX HA Cluster, you can continue with configuration of the vSRX cluster as described in [IBM Cloud performing vSRX basics](/docs/vsrx?topic=vsrx-performing-ibm-cloud-juniper-vsrx-basics).

If you opted to deploy the No-OS gateway offering, then follow the guidance in [Installing an Operating System on the Gateway](/docs/gateway-appliance?topic=gateway-appliance-order-byoa#installing-an-operating-system-on-the-gateway) to prepare the hosts for your appliance.

**Next topic:** [vSRX base and advanced licensing](/docs/vmwaresolutions?topic=vmwaresolutions-vcsvsrx-licensing)

## Related links
{: #vcsvsrx-deployment-related}

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle overview](/docs/vmwaresolutions?topic=vmwaresolutions-vcs-hybridity-intro)
* [Getting Started With IBM Cloud Juniper vSRX](/docs/vsrx?topic=vsrx-getting-started)
* [Juniper Networks vSRX Deployment Guide for VMware](https://www.juniper.net/documentation/en_US/vsrx/information-products/pathway-pages/security-vsrx-vmware-guide-pwp.html){:external}
* [Juniper Networks Requirements for vSRX on VMware](https://www.juniper.net/documentation/en_US/vsrx/topics/reference/general/security-vsrx-vmware-system-requirement.html){:external}
* [Juniper Networks vSRX installation with vSphere web client](https://www.juniper.net/documentation/en_US/vsrx/topics/task/installation/security-vsrx-vsphere-client-installing.html){:external}
* [Juniper Networks configuring a vSRX Chassis Cluster in Junos OS](https://www.juniper.net/documentation/en_US/vsrx/topics/task/multi-task/security-vsrx-chassis-cluster-configuring.html){:external}
* [Configure ECMP on VMware NSX](https://letsv4real.com/2016/09/23/configure-ecmp-on-vmware-nsx/){:external}
