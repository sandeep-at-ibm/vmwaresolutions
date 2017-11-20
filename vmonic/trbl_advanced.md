---

copyright:

  years:  2016, 2017

lastupdated: "2017-11-10"

---

# Assisted troubleshooting

## Problem

In some situations, a more complicated issue might occur, and log files are not enough to complete the root cause analysis and provide a solution.

## Resolution

To troubleshoot and resolve this type of issues, the {{site.data.keyword.vmwaresolutions_full}} Support team needs access to the {{site.data.keyword.cloud_notm}} Management virtual machine (VM). This management VM, called IBM CloudDriver, is the main interface that is used to manage the deployed VMware Cloud Foundation instances and VMware vCenter Server instances.

For security reasons, access to IBM CloudDriver is restricted. The {{site.data.keyword.vmwaresolutions_short}} Support team will request customer approval and after it obtains it, the team can access the CloudDriver component using an {{site.data.keyword.cloud_notm}} infrastructure virtual server. This server bridges into the environment over the {{site.data.keyword.cloud_notm}} infrastructure Frontend Customer Router (FCR) public network.

Next, the {{site.data.keyword.vmwaresolutions_short}} Support team uses the {{site.data.keyword.cloud_notm}} infrastructure {{site.data.keyword.slapi_short}} key that was provided for the ordering and configuration of the instance (or, if required, the updated key that is provided by the customer) to deploy an hourly {{site.data.keyword.cloud_notm}} infrastructure virtual server.

The customer account is charged for the usage of the IBM CloudBuilder tools for troubleshooting purposes. After the debug and remediation is completed, the IMB CloudBuilder component is released.

The {{site.data.keyword.cloud_notm}} infrastructure virtual server that is used for troubleshooting is deployed with the following specifications:

* A CentOS 7 public node VSI (Virtual Service Instance) is used with 1 CPU and 1 GB of RAM.
* The VSI is deployed in the same data center on the same primary public and private VLAN that the instance is on.
*  A postinstallation script is used with the VSI deployment to set firewall rules that allow only incoming SSH connections from a specific set of IP addresses that are owned and used by the {{site.data.keyword.vmwaresolutions_short}} Support team.
* The support launch system that uses those IP addresses runs on an {{site.data.keyword.cloud_notm}} infrastructure VM that is accessible only through a private {{site.data.keyword.cloud_notm}} infrastructure network and is secured with a pair of HA (High Availability) {{site.data.keyword.cloud_notm}} infrastructure Vyatta systems.
* IBM Security tools, such as QRadar®, Nessus and IBM BigFix®, are used to monitor the support launch system against any security threats.
