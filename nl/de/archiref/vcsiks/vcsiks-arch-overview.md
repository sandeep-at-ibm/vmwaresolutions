---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-16"

---

# Übersicht über die Architektur
Die {{site.data.keyword.vmwaresolutions_full}}-Produktangebote stellen eine Automatisierung zur weltweiten Bereitstellung von VMware-Technologiekomponenten in {{site.data.keyword.CloudDataCents_notm}} bereit. Die Architektur besteht aus einer einzelnen Cloudregion und unterstützt die Erweiterung in weitere Cloudregionen, die sich in einem anderen geografischen Gebiet und/oder in einem anderen {{site.data.keyword.cloud_notm}}-Pod innerhalb desselben Rechenzentrums befinden.

Die Produkte {{site.data.keyword.cloud_notm}} Private (ICP) und Cloud Automation Manager (CAM) können manuell auf Ihrer lokalen Virtualisierungsplattform bereitgestellt werden und ermöglichen so das Cloud-Management am lokalen Standort. Alternativ werden ICP und CAM als Serviceerweiterungen für eine vorhandene oder neue VMware vCenter Server on {{site.data.keyword.cloud_notm}}-Bereitstellung per Automation angeboten, wodurch das Cloud-Management über die {{site.data.keyword.cloud_notm}} ermöglicht wird.

ICP ist eine Anwendungsplattform für die Entwicklung und das Management von lokalen containerisierten Anwendungen. Bei ICP handelt es sich um eine integrierte Umgebung für die Verwaltung von Containern, die Kubernetes als Container-Orchestrator, ein privates Image-Repository, eine Managementkonsole und Überwachungsframeworks enthält.

IBM Multi-Cluster Manager (MCM) bietet Benutzertransparenz, anwendungsorientiertes Management (Richtlinien, Bereitstellungen, Vitalität, Betrieb) und die richtlinienbasierte Konformität über Clouds und Cluster hinweg. Mit IBM Multi-Cluster Manager erhalten Sie die Kontrolle über Ihre Kubernetes-Cluster. Sie können sicherstellen, dass Ihre Cluster sicher sind, effizient arbeiten und das von Anwendungen erwartete Service-Level zur Verfügung stellen.

{{site.data.keyword.cloud_notm}} Automation Manager (CAM) ist eine Self-Service-Managementplattform für mehrere Clouds, die unter {{site.data.keyword.cloud_notm}} Private ausgeführt wird und es Entwicklern und Administratoren ermöglicht, die Anforderungen des Unternehmens zu erfüllen. Der Service Composer von Cloud Automation Manager ermöglicht es Ihnen, Hybrid-Cloud-Services im IBM Cloud Private-Katalog zugänglich zu machen.

## IBM Cloud-seitige Plattform für das Cloud-Management

Das folgende Diagramm zeigt ICP und CAM mit Bereitstellung in der {{site.data.keyword.cloud_notm}}-Infrastruktur mit Verbindungen zum lokalen, auf {{site.data.keyword.cloud_notm}} bereitgestellten vCenter Service und IBM Kubernetes Service (IKS). Benutzer können virtuelle Maschinen (VMs) lokal und in vCenter Server-Instanzen sowie Container im ICP- und IKS-Cluster bereitstellen.

Abbildung 1. Cloud-Management aus Sicht der Cloud
![Cloud-Management aus Cloud-Sicht](vcsiks-oncloud-cloudmgt.svg)

Im Diagramm erstellt CAM logische Cloudverbindungen zu den vCenter-, Cloud-Provider-, ICP- und IKS-Umgebungen. ICP-Cluster müssen in jedem Rechenzentrum oder jeder Cloudumgebung bereitgestellt werden. MCM stellt den Mechanismus zur Verfügung, mit dem die ICP-Cluster in einer Managementansicht verbunden werden können.

ICP kann mit NSX-V- oder NSX-T-Komponenten bereitgestellt werden. Bei ICP mit NSX-V können die ICP-VMs im VXLAN-Netz ausgeführt werden und das interne Netz von Kubernetes Calico nutzen.

Bei ICP mit NSX-T können die Benutzer den Netzbetrieb, Teilnetze und Richtlinien von der zentralen Benutzerschnittstelle (NSX-T Manager) steuern und konfigurieren. Informationen zu den Unterschieden zwischen NSX-V und NSX-T enthält der Abschnitt [Referenzarchitektur für den Netzbetrieb mit {{site.data.keyword.cloud_notm}} VCS](../vcsnsxt/vcsnsxt-intro.html).

## Lokale Cloud-Management-Plattform

Das folgende Diagramm zeigt ICP und CAM mit Bereitstellung in der lokalen Cloudinfrastruktur und Verbindungen zu vCenter und IKS, die in der {{site.data.keyword.cloud_notm}} bereitgestellt sind. Benutzer können VMs und Container lokal, VMs in vCenter Server-Instanzen sowie Container im IKS-Cluster bereitstellen.

Abbildung 2. Cloud-Management aus Sicht des lokalen Standorts
![Cloud-Management - lokaler Standort](vcsiks-onprem-cloudmgt.svg)

Das strongSwan-VPN wird verwendet, um die Verbindung zu den bereitgestellten IKS-Containern einzurichten. strongSwan könnte später dann durch Direct Link-Konnektivität ersetzt werden.

Im Diagramm erstellt CAM logische Cloudverbindungen zu den vCenter-, Cloud-Provider-, ICP- und IKS-Umgebungen. ICP-Cluster müssen in jedem Rechenzentrum oder jeder Cloudumgebung bereitgestellt werden. MCM stellt den Mechanismus zur Verfügung, mit dem die ICP-Cluster in einer Managementansicht verbunden werden können.

### Zugehörige Links

* [Übersicht über vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](../vcs/vcs-hybridity-intro.html)
