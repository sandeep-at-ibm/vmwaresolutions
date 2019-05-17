---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-16"

---

# Integration
{: #opsmgmt-integration}

This documentation has focused on the Operational Management layer of the design, however, some enterprises may want to integrate this layer with their Service Management layer. This section provides guidance on this integration. In this design, vROps is the central point where all alerts are surfaced.

The following categories of integration are possible:
* Northbound – Integration from vROps to other tools:
  * Notification of alerts to SMTP server or tools like Slack or PagerDuty.
  * Ticket integration into a service desk tool like ServiceNow.
  * Initiating vRealize Orchestrator workflows to remediate an issue discovered by vROps.
* Southbound – Integration from service management or cloud management tooling:
  * vRealize Automation configures monitoring when new workload is added.
  * Update vROps objects with event enrichment from external sources.

vROps provides the following outbound alert plug-ins:
* Automated Action – enabled by default.
* Standard Email - uses Simple Mail Transfer Protocol (SMTP) to email vRealize Operations Manager alert notifications to your interested individuals.
* SNMP Trap– logs alerts on your SNMP Trap server.
* REST Notification - sends vROps alerts to another REST-enabled application where you built a REST Web service to accept these messages.
* Log File – enables vROps to log alerts to a file on each of your vRealize Operations Manager nodes. If you installed vRealize Operations Manager as a multiple node cluster, each node processes and logs the alerts for the objects that it monitors. Each node logs the alerts for the objects it processes.
* Smarts SAM Notification - sends alert notifications to EMC Smarts Server Assurance Manager.
* Network Share - sends reports to a shared location, supports SMB version 2.0.

Notifications are alert notifications that meet the filter criteria in the notification rules before they are sent northbound to external systems. Notification rules are configured for the required outbound alerts so that they can be filtered before they are sent to the selected external system. The notifications list is used to manage these rules.

## Integration use case
{: #opsmgmt-integration-usecase}

This example use case is based on an existing generic service management layer used by an enterprise. The client provisioned a vCenter Server instance with the Operations Management option, and they wish to integrate this platform into their service management platform. They use an event aggregation system to integrate the alerts generated from the domain specific monitoring tools:

* A tool set to monitor the OS, middleware and applications across their Unix, Linux and Windows workloads, but this tool does not monitor the infrastructure components like VMware, networking devices, or storage.
* An SNMP manager to receive SNMP traps from their network infrastructure. This tool also collects SNMP metrics to enable performance and capacity alerting.
* A backup management tool to manage their backups.
* Storage management tools to manage their storage arrays.
* An availability tool that uses ping to test the devices reachability.

Their service management layer also consists of:

* A server capacity and performance tool to collect metrics to provide reports.
* A patching and compliance server to update OS, middleware and applications and measure compliance on these platforms.
* A ticketing tool used to manage tickets for, incidents, problems and changes. This tool is also the enterprise’s Configuration Management Database (CMDB). The tool is able to send emails to the operations teams as well as SMS messages.
* An enterprise logging system that captures logs from all systems and managed by the security team.

Now that they have vROps they will integrate this tool by using northbound notification using the SNMP Trap plug in. In order to integrate vROps, the traps sent by vROps needs to be parsed in a way that the client’s event management environment can create alerts and enrich it. The management tool team downloaded the VMware MIBs from VMware and installed them in their event management environment.

vRLI is configured to forward all events to the enterprise logging system in accordance with the client’s policies.

The client wishes to use their existing OS, middleware and application monitoring tools so they have used proxies in {{site.data.keyword.cloud}} to collect and forward metrics and alerts.

![Integration diagram](../../images/opsmgmt-integration.svg "Integration diagram"){: caption="Figure 1. vROps integration service management" caption-side="bottom"}

## Related links
{: #opsmgmt-integration-related}

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle overview](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
* [vRealize Operations RESTful API](https://docs.vmware.com/en/vRealize-Operations-Manager/7.0/vrealize-operations-manager-70-api-guide.pdf){:new_window}
* [VMware Code API Explorer](https://code.vmware.com/apis?socv=1&numPerPage=164&sorter=pv){:new_window}
* [Postman Client Collection Tool for vRealize Operations](https://code.vmware.com/samples/4663/postman-client-collection-for-vrealize-operations-rest-apis){:new_window}
* [VMware PowerCLI blog](https://blogs.vmware.com/PowerCLI/2016/05/getting-started-with-powercli-for-vrealize-operations-vr-ops.html){:new_window}
* [Webhook Shims](https://blogs.vmware.com/management/2017/01/vrealize-webhooks-infinite-integrations.html){:new_window}
