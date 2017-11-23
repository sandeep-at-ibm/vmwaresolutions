---

copyright:

  years:  2016, 2017

lastupdated: "2017-11-21"

---

# FAQ about IBM Cloud for VMware Solutions

Find answers to the questions that you might have about {{site.data.keyword.vmwaresolutions_full}}.

## What user accounts do I need for IBM Cloud for VMware Solutions?

* **IBMid account**. This account is required to access the {{site.data.keyword.vmwaresolutions_short}} console. This console is a stand-alone user interface that is separate from the {{site.data.keyword.slportal_full}}. For more information, see [Getting started](../index.html).
* **{{site.data.keyword.cloud_notm}} account**. This account is required for provisioning. You can sign up for an {{site.data.keyword.cloud_notm}} infrastructure account by upgrading your **IBMid account** to a Pay-As-You-Go account. The {{site.data.keyword.cloud_notm}} infrastructure account that you are using must meet certain requirements. For more information, see [Signing up for an {{site.data.keyword.cloud_notm}} account](signing_softlayer_account.html) and [{{site.data.keyword.cloud_notm}} account requirements](slaccountrequirement.html).

## How do I associate my IBM Cloud credentials with the IBM Cloud for VMware Solutions console?

When you order your instance for the first time, follow the instructions on the {{site.data.keyword.cloud_notm}}  credentials page to locate and copy the {{site.data.keyword.cloud_notm}} user name and API key from the {{site.data.keyword.slportal}}. The {{site.data.keyword.cloud_notm}} credentials are stored in the {{site.data.keyword.vmwaresolutions_short}} console after the first order. Future orders automatically inherit these credentials.

## How are my VMware virtual platform consumptions billed?

All costs for the physical and virtual infrastructure and the licenses resulting from the instance are charged to your {{site.data.keyword.cloud_notm}} account. When you order an instance, you must have an {{site.data.keyword.cloud_notm}} account and provide the {{site.data.keyword.slapi_short}} key that is associated with the account.

## What are the supported languages?

{{site.data.keyword.vmwaresolutions_short}} is an English-only product. Therefore, all features on the console, including the user documentation, are available in English only.

## What is the difference between a Cloud Foundation instance and vCenter Server instance?

Both instance types provide deployment choices for VMware virtual environments. However, the difference is standardized versus customized.

* When you order a VMware Cloud Foundation instance, you deploy a unified software-defined data center (SDDC) platform. For more information about what is deployed on a Cloud Foundation platform, see [Cloud Foundation instance  components](../sddc/sd_cloudfoundationoverview.html#cloud-foundation-components).
* When you order a VMware vCenter Server instance, you deploy a VMware virtual environment with customized compute, storage, and network resources. For more information about what is deployed on a vCenter Server platform, see [vCenter Server instance components](../vcenter/vc_vcenterserveroverview.html#vcenter-server-instance-components).

## What is included in a Cloud Foundation instance?

For more information, see [Cloud Foundation instance  components](../sddc/sd_cloudfoundationoverview.html#cloud-foundation-components).

## What is included in a vCenter Server instance?

For more information, see [vCenter Server instance components](../vcenter/vc_vcenterserveroverview.html#vcenter-server-instance-components).

## Is a two-node vCenter Server instance highly available?

It is strongly recommended to deploy production workloads into environments that have at least three nodes.

Although VMware vSphere DRS (Distributed Resource Scheduler) and VMware HA (High Availability) are enabled by default, best practices from VMware suggests that each of the three NSX Controllers is placed on an individual node.

In the two-node minimum deployment, one node has one NSX Controller, and the other node has two NSX Controllers. If the node with two NSX Controllers goes down, NSX Controller operations are placed in read-only mode, and new VMs (virtual machines) or vMotion VMs may experience networking issues.

When a third node is added to a two-node cluster, vCenter Server automatically rebalances the three NSX Controllers across the three nodes and creates a highly available environment.

## Does the management services NSX Edge pose a security risk?

Although the VMware NSX Edge for management services is on a public subnet, security measures are in place to ensure that it does not pose a security risk. These measures are:
*  The NSX Edge firewall is configured to allow only outgoing HTTPS (port 443) traffic that is initiated by the management virtual machines.
*  SNAT (source network address translation) is used so that private IP addresses are not visible outside the private network.
*  Remote access for the management services NSX Edge appliance is disabled.
*  Passwords for accessing the management services NSX Edge from the private network are randomized and encrypted.

## Does the customer-managed NSX Edge pose a security risk?

Although the customer-managed NSX Edge is connected to the public VLAN, security measures are in place to ensure that it does not pose a security risk. These measures are:
*  A firewall rule is in place to allow only outgoing traffic from the private subnet range of IP addresses.
*  A SNAT (Source Network Address Translation) rule (disabled by default) is in place to translate all IP addresses from the private subnet to a single IP address on the public subnet.
*  Remote access for the customer-managed NSX Edge appliance is disabled.
*  Passwords for accessing the customer-managed NSX Edge from the private network are randomized and encrypted.

## How do I choose the data centers for my instances?

The unified Cloud Foundation and vCenter Server deployments have strict requirements on the physical infrastructure. The physical infrastructure varies among {{site.data.keyword.CloudDataCents_notm}}. Therefore, you can deploy instances only in data centers that meet the requirements. The available data centers are listed when you order your instances, and you can select the one that you want from the list.

For more information, see the _Available data centers_ sections in:
* [Requirements and planning for Cloud Foundation instances](../sddc/sd_planning.html).
* [Requirements and planning for vCenter Server instances](../vcenter/vc_planning.html).

## How long does it take for my instance to be deployed?

You can check the status of the instance deployment by viewing the deployment history on the instance details page from the {{site.data.keyword.vmwaresolutions_short}} console.

## How many ESXi servers can I add to my instances?

* For Cloud Foundation instances, the standard configuration has four ESXi servers. You can add a maximum of 28 servers (to a total of 32 servers). For Cloud Foundation instances in a multi-site configuration, you can have a maximum of 128 ESXi servers across all instances.
* For vCenter Server instances, you can configure the number of ESXi servers in the range 2 - 20 per cluster. Each deployed instance can have a maximum of 128 nodes across all clusters.

**Note**: If your configuration requires a multi-site deployment with more than 128 nodes, [contact IBM Support](trbl_support.html) for assistance.

## Does VMware vSphere on IBM Cloud leverage automation to install, configure, and bring up the VMware stack?

No. VMware vSphere on {{site.data.keyword.cloud_notm}} does not leverage the advanced automation found in the Cloud Foundation and vCenter Server  platforms. Based on what you order, the platform delivers optional VMware licenses, ESXi servers, and optional HA-pair of FortiGate physical firewalls. If a new cluster is created, one new public and two new private VLANs are also provisioned.

VMware ESXi is automatically installed on each bare metal server, but you are responsible for installing any additional VMware components like vCenter Server or NSX. While vSphere on {{site.data.keyword.cloud_notm}} helps ensure that VMware-compatible hardware is ordered based on the VMware components selected, there is no automation in place to configure and bring up the VMware environment. You are responsible for designing and architecting the IBM-hosted environment.

## Where do I manage the VMware licenses, ESXi servers, and other networking components that are ordered through VMware vSphere on IBM Cloud?

After an order to create a new cluster for VMware vSphere on {{site.data.keyword.cloud_notm}} is placed, the licenses, servers, and any other components are delivered and can be managed from the {{site.data.keyword.slportal}}. After deployment, return to the {{site.data.keyword.vmwaresolutions_short}} console to scale the new cluster using the saved configuration. For more information on scaling, see [Scaling existing vSphere clusters](../vsphere/vs_scalingexistingclusters.html).

## How can I view the list of all notifications?

To view the complete notification history, click **Notifications** from the left navigation pane. Notifications with a severity level of **Informational** and **Warning** are listed.

## What if I have a problem with IBM Cloud for VMware Solutions?

If you need assistance with {{site.data.keyword.vmwaresolutions_short}}, contact IBM Support through one of the support channels. For more information, see [Contacting IBM Support](trbl_support.html).

## Related links

* [Notifications](notifications.html)
* [Cloud Foundation instances](../sddc/sd_cloudfoundationoverview.html)
* [vCenter Server instances](../vcenter/vc_vcenterserveroverview.html)
* [Accessing the console](loginmethod.html)
* [User accounts and settings](useraccount.html)
