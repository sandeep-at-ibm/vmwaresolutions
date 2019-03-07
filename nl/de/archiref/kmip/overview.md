---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# KMIP for VMware - Übersicht
{: #kmip-overview}

Diese Lösungsarchitektur beschreibt die KMIP on VMware-Architektur für den Schutz Ihrer VMware on {{site.data.keyword.cloud_notm}}-Instanzen. Für den Schutz Ihrer VMware-Workload sind viele Optionen zur Speicherverschlüsselung verfügbar. KMIP for VMware arbeitet mit der nativen vSphere-Verschlüsselung und der vSAN-Verschlüsselung von VMware zusammen, um ein vereinfachtes Speicherverschlüsselungsmanagement sowie die Sicherheit und Flexibilität der vom Kunden verwalteten Schlüssel von {{site.data.keyword.cloud_notm}} Key Protect zu gewährleisten.

Diese Lösung gilt als zusätzliche Komponente und Erweiterung der Lösungsangebote von vCenter Server und VMware Cloud Foundation unter {{site.data.keyword.cloud_notm}}. Aus diesem Grund deckt dieses Dokument die vorhandene Konfiguration dieser Basislösungen in {{site.data.keyword.cloud_notm}} nicht ab. Weitere Informationen zur grundlegenden Lösungsarchitektur finden Sie in der Dokumentation der [VMware on {{site.data.keyword.cloud_notm}}-Lösungsarchitektur](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview).

## Hauptvorteile
{: #kmip-overview-benefits}

Während für Ihre VMware-Workload viele Speicherverschlüsselungslösungen zur Verfügung stehen, bietet KMIP for VMware die folgenden Vorteile:

* Integration in die vSAN-Verschlüsselung und vSphere-Verschlüsselung von VMware. Beide werden in der Hypervisorebene und nicht in der Ebene des Speichers oder der virtuellen Maschinen implementiert. Dieser Ansatz ermöglicht ein einfaches Management sowie Transparenz für Ihre Speicherlösung und Anwendung.
* Ein vollständig verwalteter Schlüsselmanagementserver ist in vielen IBM Cloud-Multizone-Regionen (MZRs) verfügbar.
* Durch die Integration Ihres VMware-Clusters in IBM Cloud Key Protect erhalten Sie vollständig vom Kunden verwaltete Schlüssel, die Sie jederzeit widerrufen können.

## Zugehörige Links
{: #kmip-overview-related}

* [Lösungsdesign](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip-design)
* [Bereitstellung und Verwaltung](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip-implementation)
