---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-17"

subcollection: vmware-solutions


---

# VMware HCX on IBM Cloud - Einführung
{: #hcxclient-vcs-intro}

Vom Service 'VMware HCX on IBM Cloud' wird die Erstellung einer nahtlosen Verbindung zwischen IBM Cloud for VMware Solutions und einem lokalen virtualisierten VMware-Rechenzentrum ermöglicht.

IBM Cloud for VMware Solutions umfasst voll automatisierte schnelle Bereitstellungen von Konfigurationen für VMware vCenter Server (VCS) in IBM Cloud. Diese Angebote ergänzen die lokale Infrastruktur und ermöglichen die Ausführung vorhandener und zukünftiger Workloads in IBM Cloud ohne Konvertierung, da sie dieselben Tools, Kenntnisse und Prozesse verwenden, die auch lokal verwendet werden. Weitere Informationen finden Sie im Abschnitt zur [Virtualisierung für die Erweiterung der virtualisierten privaten Cloud](https://www.ibm.com/cloud/garage/architectures/virtualizationArchitecture).

Vom Service 'VMware HCX on IBM Cloud' wird diese Hybridität ausgebaut, da von ihm die Erstellung nahtloser Netzerweiterungen und die bidirektionale Migration von Workloads ermöglicht wird und so vCenter Server-Instanzen mit vorhandenen lokalen virtualisierten Rechenzentren zusammengeführt werden.

Die VMware HCX on IBM Cloud-Komponenten, die als virtuelle Maschinen am IBM Cloud VMware-Zielstandort bereitgestellt werden, ermöglichen den Aufbau einer Verbindung zu den VMware HCX on IBM Cloud-Komponenten, die am lokalen Peer-Quellenstandort installiert sind.

![VMware vCenter Server – Hybrid-Cloud-Services](../../images/cloudfoundation_hybrid_cloud_services.svg "VMware vCenter Server – Hybrid-Cloud-Services")

Durch diese Verbindung wird eine flexible Interkonnektivität zwischen lokalen Standorten und IBM Cloud hergestellt und es werden u. a. folgende Funktionen ermöglicht:
* Einfache Interkonnektivität - Logische Netzverbindungen können ohne großen Aufwand über eine beliebige physische Verbindung hergestellt werden, z. B. über das öffentliche Internet, ein privates VPN oder eine direkte Verbindung.
* Layer-2-Erweiterung - Lokale Netze werden in die Cloud erweitert. Zu diesen Netzen zählen auch lokale Teilnetze und IP-Adressierung.
* Verschlüsselung - Der Datenaustausch im Netz wird zwischen den beiden Standorten sicher verschlüsselt.
* Netzoptimierung - Wählt die beste Verbindung aus und nutzt die Verbindung effizient aus, sodass der Datenaustausch im Netz mit maximaler Geschwindigkeit erfolgt.
* Datendeduplizierung – Eine Reduktion des Netzverkehrs um bis zu 50 % kann durch intelligentes Routing erreicht werden: Wenn eine Workload verschoben wird, kann durch das 'Proximity Routing' der Netzpfad (d. h. das Gateway) geändert werden, sodass vom Datenaustausch im Netz das Gateway des Zielstandorts verwendet wird (anstelle eines 'Hairpinnings' zum ursprünglichen Standort).
* Migration ohne Ausfallzeit – Ein aktives System kann mit vMotion in oder aus der Cloud verschoben werden.
* Geplante Migration - Eine beliebige Anzahl virtueller Maschinen kann an den Zielstandort repliziert und dann zu einem bestimmten Zeitpunkt an diesem Standort aktiviert werden und die Systeme ersetzen, die am ursprünglichen Standort ausgeführt werden.
* Migration von Sicherheitsrichtlinien - Wenn NSX lokal verwendet wird, werden zusammen mit der Workload alle vorhandenen Sicherheitsrichtlinien oder Firewalls verschoben.

## Zugehörige Links
{: #hcxclient-vcs-intro-related}

* [Glossar der HCX-Komponenten und -Begriffe](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-components)
* [Installationsumgebung vorbereiten](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [Bereitstellung des HCX-Clients](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [Lokales HCX-Servicenetz](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [VMware Hybrid Cloud-Migrationen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [Überwachung von Parametern und Komponenten](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [Fehlerbehebung für HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)
