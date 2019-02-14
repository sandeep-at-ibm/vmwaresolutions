---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

# Übersicht über die Architektur

Die {{site.data.keyword.vmwaresolutions_full}}-Produktangebote stellen eine Automatisierung zur weltweiten Bereitstellung von VMware-Technologiekomponenten in {{site.data.keyword.CloudDataCents_notm}} bereit.
Die Architektur besteht aus einer einzelnen Cloudregion und unterstützt die Erweiterung in weitere Cloudregionen, die sich in einem anderen geografischen Gebiet oder in einem anderen {{site.data.keyword.cloud_notm}}-Pod innerhalb desselben Rechenzentrums befinden.

Die Produkte {{site.data.keyword.cloud_notm}} Private und Cloud Automation Manager (CAM) können manuell auf Ihrer lokalen Virtualisierungsplattform bereitgestellt werden und ermöglichen so das Cloud-Management am lokalen Standort. Alternativ werden {{site.data.keyword.icpfull_notm}} und CAM als Serviceerweiterungen für eine vorhandene oder neue VMware vCenter Server on {{site.data.keyword.cloud_notm}}-Bereitstellung per Automation angeboten, wodurch das Cloud-Management über die {{site.data.keyword.cloud_notm}} ermöglicht wird.

{{site.data.keyword.cloud_notm}} Private ist eine Anwendungsplattform für die Entwicklung und das Management von lokalen containerisierten Anwendungen. Bei {{site.data.keyword.cloud_notm}} Private handelt es sich um eine integrierte Umgebung für die Verwaltung von Containern, die Kubernetes als Container-Orchestrator, ein privates Image-Repository, eine Managementkonsole und Überwachungsframeworks enthält.

IBM Multi-Cluster Manager (MCM) bietet Benutzertransparenz, anwendungsorientiertes Management (Richtlinien, Bereitstellungen, Vitalität, Betrieb) und die richtlinienbasierte Konformität über Clouds und Cluster hinweg. Mit MCM erhalten Sie die Kontrolle über Ihre Kubernetes-Cluster. Mit MCM können Sie sicherstellen, dass Ihre Cluster sicher sind, effizient arbeiten und eine Service-Management-Plattform zur Verfügung stellen, die unter {{site.data.keyword.cloud_notm}} Private ausgeführt wird und die Entwickler und Administratoren dabei unterstützt, die Anforderungen des Unternehmens zu erfüllen.

Mit dem Service Composer von Cloud Automation Manager können Sie Hybrid-Cloud-Services im {{site.data.keyword.cloud_notm}} Private-Katalog anzeigen.

## IBM Cloud-seitige Plattform für das Cloud-Management

Das folgende Diagramm ist ein Beispiel für eine {{site.data.keyword.icpfull_notm}}- und CAM-Bereitstellung mit der {{site.data.keyword.cloud_notm}}-Infrastruktur sowie Verbindungen zur lokalen vCenter- und {{site.data.keyword.containerlong_notm}}-Bereitstellung in {{site.data.keyword.cloud_notm}}. Benutzer können virtuelle Maschinen (VMs) lokal und in einer vCenter Server-Instanz sowie Container im {{site.data.keyword.icpfull_notm}}- und {{site.data.keyword.containerlong_notm}}-Cluster bereitstellen.

Abbildung 1. Cloud-Management aus Sicht der Cloud

![Cloud-Management aus Sicht der Cloud](vcsicp-oncloud-cloudmgt.svg)

Im Diagramm erstellt CAM logische Cloudverbindungen zu den vCenter-Instanzen, Cloud-Providern sowie den {{site.data.keyword.icpfull_notm}}- und {{site.data.keyword.containerlong_notm}}-Umgebungen. {{site.data.keyword.icpfull_notm}}-Cluster müssen in jeder Cloudumgebung jedes Rechenzentrums bereitgestellt werden. MCM stellt den Mechanismus zur Verfügung, mit dem die ICP-Cluster in einer Managementansicht verbunden werden können.

{{site.data.keyword.icpfull_notm}} kann mit NSX-V- oder NSX-T-Komponenten bereitgestellt werden. Bei {{site.data.keyword.icpfull_notm}} mit NSX-V können die {{site.data.keyword.icpfull_notm}}-VMs im VXLAN-Netz ausgeführt werden und das interne Netz von Kubernetes Calico nutzen.

Bei {{site.data.keyword.icpfull_notm}} mit NSX-T können die Benutzer den Netzbetrieb, Teilnetze und Richtlinien von der zentralen Benutzerschnittstelle (NSX-T Manager) steuern und konfigurieren. Informationen zu den Unterschieden zwischen NSX-V und NSX-T finden Sie im [Leitfaden für den vCenter Server-Netzbetrieb](/docs/services/vmwaresolutions/archiref/vcsnsxt/vcsnsxt-intro.html).

## Lokale Cloud-Management-Plattform

Das folgende Diagramm ist ein Beispiel für eine {{site.data.keyword.icpfull_notm}}- und CAM-Bereitstellung in der lokalen Infrastruktur mit Verbindungen zur vCenter- und {{site.data.keyword.containerlong_notm}}-Bereitstellung in {{site.data.keyword.cloud_notm}}. Benutzer können VMs und Container lokal, VMs in vCenter Server-Instanzen sowie Container im IKS-Cluster bereitstellen.

Abbildung 2. Lokales Cloud-Management
![Lokales Cloud-Management](vcsicp-onprem-cloudmgt.svg)

Das strongSwan-VPN wird verwendet, um die Verbindung zu den bereitgestellten {{site.data.keyword.containerlong_notm}}-Containern einzurichten. Das strongSwan-VPM kann durch Direct Link-Konnektivität ersetzt werden.

Im Diagramm erstellt CAM logische Cloudverbindungen zu den vCenter-Instanzen, Cloud-Providern sowie den {{site.data.keyword.icpfull_notm}}- und {{site.data.keyword.containerlong_notm}}-Umgebungen. {{site.data.keyword.icpfull_notm}}-Cluster müssen in jeder Cloudumgebung jedes Rechenzentrums bereitgestellt werden. MCM stellt den Mechanismus zur Verfügung, mit dem die ICP-Cluster in einer Managementansicht verbunden werden können.

### Zugehörige Links

* [Übersicht über vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs/vcs-hybridity-intro.html)
