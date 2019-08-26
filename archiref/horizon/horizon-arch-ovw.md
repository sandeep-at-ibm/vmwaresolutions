---

copyright:

  years:  2019

lastupdated: "2019-08-22"

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter Server and VMware Horizon 7 architecture overview
{: #horizon-arch-ovw}

VMware Horizon® 7 for IBM Cloud delivers a seamlessly integrated hybrid cloud for virtual desktops and applications. It combines the enterprise capabilities of the VMware Software-Defined Data Center (SDDC), delivered as a service on IBM Cloud, with the market-leading capabilities of VMware Horizon 7 for a simple, secure, and scalable solution. You can easily address use cases such as on-demand capacity, disaster recovery, and cloud colocation without buying more data center resources.

For customers who are already familiar with Horizon 7 or have Horizon 7 deployed on-premises, Horizon 7 on IBM Cloud helps you leverage a unified architecture and familiar tools. You use the same expertise that you know from VMware vSphere® and Horizon 7 for operational consistency and you leverage the same rich feature set and flexibility you expect. By outsourcing the management of the vSphere platform to IBM, you can simplify management of Horizon 7 deployments.

IT administrators can use this information to deploy Horizon 7 on IBM Cloud. Use this information together with [VMware Horizon 7 documentation](https://docs.vmware.com/en/VMware-Horizon-7/index.html){:external} and the [VMware Workspace ONE and VMware Horizon Reference Architecture](https://techzone.vmware.com/resource/vmware-workspace-one-and-vmware-horizon-7-enterprise-edition-premises-reference){:external}.

## Overview of Horizon 7 on IBM Cloud
{: #horizon-arch-ovw-horizon7}

You can deploy Horizon 7 on IBM Cloud to scale Horizon 7 desktops and applications on an elastic cloud platform.

With IBM Cloud, you can create vSphere Software-Defined Data Centers (SDDCs) by using the VMware vCenter Server on IBM Cloud offering. The vCS offering provides VMware vCenter Server® for VM management with options for VMware vSAN™ or NFS for storage, and VMware NSX® for networking. You can connect an on-premises SDDC to your cloud SDDC or connect to applications hosted by using other IBM Cloud services.

After you deployed an SDDC on IBM Cloud, you can deploy Horizon 7 in that cloud environment just like you would in an on-premises vSphere environment. There is no requirement to purchase new hardware, and you can use the pay-as-you-go option on IBM Cloud.

By using the Cloud Pod Architecture (CPA) Horizon 7 feature, you can scale your Horizon 7 deployment across multiple pods and sites for federated management. You can deploy Horizon 7 in a hybrid cloud environment when you use CPA to interconnect on-premises data centers and IBM Cloud data centers.

A single pod and the Connection Servers in it must be located within a single data center and cannot span locations. Multiple locations must have their own separate pods. These pods can be managed individually or interconnected by using Cloud Pod Architecture (CPA).
{:important}

Since the Horizon 7 architecture is the same on-premises and in IBM Cloud, the deployment and management experience remain the same across on-premises sites and in the cloud. When you use multiple data centers, you must use a storage replication mechanism, such as DFS-R in a hub-spoke topology, for replicating user data.

You can also stretch CPA across two or more IBM Cloud data centers. Usage of CPA is optional. You can choose to deploy Horizon 7 exclusively in a single IBM Cloud data center without linking it to any other data center.

## Differences Between Horizon 7 and Horizon Cloud
{: #horizon-arch-ovw-diffs}

IBM Cloud offers two solutions based on VMware Horizon – Horizon Cloud and Horizon 7 on IBM Cloud. These two solutions share many features but are intended for different use cases. Horizon 7 on IBM Cloud provides some key advantages over Horizon Cloud, including:
* Connectivity to other services that are running in IBM Cloud
* Support for Cloud Pod Architecture to connect on-premises Horizon 7 environments with Horizon 7 environments deployed on IBM Cloud
* Support for smart card Authentication, Linux desktops, and application delivery through VMware App Volumes
* Vendor ISV certification for applications in key verticals like health care and AEC

If you have questions about which Horizon solution on IBM Cloud is right for your use cases, talk to your VMware and IBM Cloud account teams.

## Horizon 7 Deployment Scenarios on IBM Cloud
{: #horizon-arch-ovw-scenarios}

You can deploy Horizon 7 on IBM Cloud for the following scenarios.

### Data center expansion
{: #horizon-arch-ovw-dc-expansion}

Use this scenario if you have an existing on-premises Horizon 7 infrastructure and need to expand capacity but don't want to procure more hardware. Extend the Horizon 7 deployment to IBM Cloud by using Cloud Pod Architecture to connect on-premises pods with a pod in IBM Cloud.

With this strategy, you can use cloud capacity and still manage on-premises and private cloud deployments in a single federated space. You can also use the cloud platform to provide temporary capacity for contractors and seasonal workers.

The on-premises deployment is optional. Based on your needs, you can decide to consolidate and move the on-premises deployment completely to IBM Cloud.

### Application locality
{: #horizon-arch-ovw-app-loc}

Use this scenario when you want to move published applications that are latency-sensitive to IBM Cloud and need virtual desktops and RDS (Remote Desktop Session) hosts to be colocated with your published applications. Layer 2 Adjacency is provided between the vCS service and other services running in IBM Cloud, so it is similar to having your apps and user access layer in the same on-premises datacenter.

You can also have other published applications that are still on-premises. When you extend your Horizon 7 deployment to IBM Cloud, you can allow users to connect to the nearest Virtual Desktop or RDS host to start the application regardless of whether the application is on-premises or on IBM Cloud.

### Business Continuity (BC) and Disaster Recovery (DR)
{: #horizon-arch-ovw-app-bus-cont}

The cost of building an on-premises BCDR infrastructure can be high. When you use IBM Cloud, you pay for the use of BCDR infrastructure during those times when the primary infrastructure is down or when you require a small pilot during normal operations for a quick Recovery Time Objective (RTO) during a disaster event.

Having a unified Horizon 7 architecture across the primary site on-premises and the BCDR site on IBM Cloud makes the failover process simple. You can also deploy Cloud Pod Architecture across multiple IBM Cloud data centers for BCDR Deployment Architecture for Horizon 7 on IBM Cloud.

## Understanding key components of Horizon 7 on IBM Cloud
{: #horizon-arch-ovw-key-comp}

To set up a successful deployment, you must configure the logical network that can support a Horizon 7 deployment on IBM Cloud.

Include the following components in the logical network configuration.

This document describes NSX-V components.
{:note}

### Management component​
{: #horizon-arch-ovw-mgmt-comp}

The management component is VMware vCenter Server with embedded Platform Services Controller.

### Compute component
{: #horizon-arch-ovw-compute-comp}

The compute components are:
* Unified Access Gateway appliances Load balancer
* Horizon Connection Servers
* Cloud Connector
* App Volumes Managers
* Virtual Desktops
* RDSH Servers

### NSX-V components
{: #horizon-arch-ovw-nsxv-comp}

​​VMware NSX Data Center is the network virtualization platform for the Software-Defined Data Center (SDDC), delivering networking and security entirely in software, abstracted from the underlying physical infrastructure.

### Horizon Cloud Connector
{: #horizon-arch-ovw-cloud-connect}

The Horizon Cloud Connector is a new component in the Horizon 7 architecture. It is a virtual appliance that connects to a Horizon pod and bridges it with the Horizon Cloud Service. The Horizon 7 Cloud Connector is required when using the Horizon Universal License for license management and for using Horizon Cloud Control Plane features like Cloud Monitoring Service and the health status dashboard.
