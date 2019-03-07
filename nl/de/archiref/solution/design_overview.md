---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---
# Übersicht über das Design
{: #design_overview}

{{site.data.keyword.vmwaresolutions_full}} stellt eine Automatisierung zur weltweiten Bereitstellung von VMware-Technologiekomponenten in {{site.data.keyword.CloudDataCents_notm}} bereit.

## Lösungsangebote
{: #design_overview-offerings}

Die Lösungsangebote beinhalten die folgenden VMware vSphere-Produkte in einem automatisch bereitgestellten und konfigurierten Cluster:
* VMware Cloud Foundation: vSphere ESXi, Platform Services Controller (PSC), VMware vCenter Server Appliance, SDDC Manager, VMware NSX und VMware vSAN.
* VMware vCenter Server: vSphere ESXi, Platform Services Controller (PSC), vCenter Server Appliance, NSX und optional vSAN.

In diesem Design wird bei der Erstbestellung eine Instanz in einem einzelnen Pod in einem {{site.data.keyword.CloudDataCent_notm}} (Rechenzentrum) bereitgestellt. Nach der Erstbereitstellung können Sie die virtuelle Umgebung auf weitere Pods im selben Rechenzentrum oder in anderen Rechenzentren erweitern.

Das Design ermöglicht außerdem eine automatisierte Erweiterung und Verkleinerung der virtuellen Kapazität in einer Cloud Foundation- oder vCenter Server-Instanz.

## VMware on IBM Cloud-Komponenten
{: #design_overview-comp}

Abbildung 1. Komponenten von VMware on {{site.data.keyword.cloud_notm}}
![Komponenten von VMware on {{site.data.keyword.cloud_notm}}](design_overview.svg "Die Lösung umfasst die physische Infrastruktur, die virtuelle Infrastruktur, das Infrastrukturmanagement und allgemeine Services.")

## Zugehörige Links
{: #design_overview-related}

* [Design der physischen Infrastruktur](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_physicalinfrastructure)
* [Design der virtuellen Infrastruktur](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_virtualinfrastructure)
* [Design der allgemeinen Services](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_commonservice)
* [Design des Infrastrukturmanagements](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_infrastructuremgmt)
