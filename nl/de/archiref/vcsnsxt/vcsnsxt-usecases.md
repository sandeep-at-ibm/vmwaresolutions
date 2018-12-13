---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-01"

---

# Anwendungsfälle

## Migration von VMware-Workloads auf IBM Cloud

Acme Skateboards möchte die lokale VMware-SDDC-Instanz nahtlos in eine VCS-Instanz unter {{site.data.keyword.cloud}} erweitern. Gleichzeitig sollen die Geschäftsabläufe aber nach Möglichkeit nicht unterbrochen und die Ausfallzeiten auf ein Minimum beschränkt werden. Das Rekonfigurieren der Anwendungen für die Ausführung in der Cloud ist keine optimal Lösung.

{{site.data.keyword.cloud_notm}} vCenter Server with Hybridity Bundle ermöglicht die Erstellung einer nahtlosen Verbindung zwischen VCS-Instanzen und einem lokalen virtuellen VMware-Rechenzentrum.

Die VMware HCX-Komponenten, die als virtuelle Maschinen am VCS-Zielstandort bereitgestellt werden, ermöglichen den Aufbau einer Verbindung mit den VMware HCX-Komponenten, die am lokalen Peerquellenstandort installiert sind.

Abbildung 1. VMware-Erweiterungsservice für Hybrid-Cloud
![VMware-Erweiterungsservice für Hybrid-Cloud](vcsnsxt-hcx-1.svg)

Die flexible Verbindung zwischen lokalen Standorten und {{site.data.keyword.cloud_notm}} stellt z. B. folgende Funktionalität zur Verfügung:
-	**Einfache Interkonnektivität** - Logische Netzverbindungen können ohne großen Aufwand über eine beliebige physische Verbindung hergestellt werden, z. B. über das öffentliche Internet, ein privates VPN oder Direct Link.
-	**Layer-2-Erweiterung** - Lokale Netze werden in die Cloud erweitert, einschließlich lokaler Teilnetze und IP-Adressierung.
-	**Verschlüsselung** - Der Datenaustausch im Netz wird zwischen den beiden Standorten sicher verschlüsselt.
-	**Netzoptimierung** - Wählt die beste Verbindung aus und nutzt die Verbindung effizient aus, sodass der Datenaustausch im Netz mit maximaler Geschwindigkeit erfolgt.
-	**Datendeduplizierung** - Eine Reduzierung von bis zu 50% des Netzverkehrs ist möglich.
-	**Intelligentes Routing** - Wenn eine Workload verlagert wird, kann das "Proximity Routing" den Netzpfad (d. h. Gateway) ändern, sodass der Datenaustausch im Netz das Gateway des Zielstandorts verwendet (anstelle des ursprünglichen Standorts).
-	**Migration ohne Ausfallzeit** - Ein aktives System kann mit vMotion in die Cloud verlagert werden (oder umgekehrt).
-	**Geplante Migration**: Eine beliebige Anzahl von VMs kann an den Zielstandort repliziert und dann zu einem bestimmten Zeitpunkt an diesem Standort aktiviert werden, um die Systeme, die am ursprünglichen Standort ausgeführt werden, zu ersetzen.
-	**Migration von Sicherheitsrichtlinien** - Wenn NSX lokal verwendet wird, werden alle Sicherheitsrichtlinien, Firewalls usw. zusammen mit der Workload verlagert.

## Bereitstellung einer Hybridarchitektur

Acme Skateboards möchte für den Anwendungsmodernisierungsprozess eine Hybridarchitektur in {{site.data.keyword.cloud_notm}} bereitstellen, die aus vCenter Server with Hybridity Bundle (VCS) und {{site.data.keyword.cloud_notm}} Private (ICP) besteht. Dabei sollen die Datenbanken auf VMs ausgeführt werden, die Anwendungen und Webschnittstellen in Containern, und es soll eine gemeinsame Gruppe von Tools für das Netz- und Sicherheitsmanagement verwendet werden.

{{site.data.keyword.vmwaresolutions_short}} stellt eine Automatisierung zur weltweiten Bereitstellung von VMware-Technologiekomponenten in {{site.data.keyword.CloudDataCents_notm}} bereit. Die Architektur besteht aus einer einzelnen Cloudregion und unterstützt die Erweiterung in weitere Cloudregionen, die sich in einem anderen geografischen Gebiet und/oder in einem anderen {{site.data.keyword.cloud_notm}}-Pod innerhalb desselben Rechenzentrums befinden.

Die Produkte "ICP" und "Cloud Automation Manager" (CAM) können manuell auf Ihrer lokalen Virtualisierungsplattform bereitgestellt werden und ermöglichen so das Cloud-Management am lokalen Standort. Alternativ werden ICP und CAM als Serviceerweiterung für eine vorhandene oder neue VCS-Bereitstellung angeboten, wodurch das Cloud-Management über {{site.data.keyword.cloud_notm}} ermöglicht wird.

Das folgende Diagramm stellt ICP bei Ausführung auf einer VCS-Instanz dar. NSX-V ist mit einem dedizierten Switch/VXLAN, einem DLR (Distributed Logical Switch) und einem ESG (Edge Services Gateway) speziell für das ICP-Overlay-Netz konfiguriert. Das Routing wird über das ESG für den Zugriff auf das Underlay-Netz eingerichtet.

Mithilfe der {{site.data.keyword.cloud_notm}}-Automatisierung kann Acme Skateboards eine Hybridlösung zur Verfügung stellen, die VCS zur Ausführung der Datenbank-VMs umfasst und ICP auf VCS zur Ausführung der Anwendungen und Front-End-Web-Services in Containern. NSX bietet ihnen eine gemeinsame Gruppe von Management-Tools für den Netzbetrieb und die Sicherheit im Overlay-Netz.

Weitere Informationen zu NSX-V enthält der Abschnitt [Übersicht über NSX-V](vcsnsxt-overview-ic4vnsxv.html). Zusätzliche Angaben über die VCS- und ICP-Angebote finden Sie unter [vCenter Server und {{site.data.keyword.cloud_notm}} Private](../vcsicp/vcsicp-intro.html).

Abbildung 2. VCS mit ICP
![VCS mit ICP](vcsnsxt-nsxvhl.svg)

Dadurch wird eine flexible Verbindung zwischen Standorten und {{site.data.keyword.cloud_notm}} eingerichtet und z. B. folgende Funktionalität zur Verfügung gestellt:
-	**Einfache Interkonnektivität** - Logische Netzverbindungen können ohne großen Aufwand über eine beliebige physische Verbindung hergestellt werden, z. B. über das öffentliche Internet, ein privates VPN oder Direct Link.
-	**Layer-2-Erweiterung** - Lokale Netze werden in die Cloud erweitert, einschließlich lokaler Teilnetze und IP-Adressierung.
-	**Verschlüsselung** - Der Datenaustausch im Netz wird zwischen den beiden Standorten sicher verschlüsselt.
-	**Netzoptimierung** - Wählt die beste Verbindung aus und nutzt die Verbindung effizient aus, sodass der Datenaustausch im Netz mit maximaler Geschwindigkeit erfolgt.
-	**Datendeduplizierung** - Eine Reduzierung von bis zu 50% des Netzverkehrs ist möglich.
-	**Intelligentes Routing** - Wenn eine Workload verlagert wird, kann das "Proximity Routing" den Netzpfad (d. h. Gateway) ändern, sodass der Datenaustausch im Netz das Gateway des Zielstandorts verwendet (anstelle des ursprünglichen Standorts).
-	**Migration ohne Ausfallzeit** - Ein aktives System kann mit vMotion in die Cloud verlagert werden (oder umgekehrt).
-	**Geplante Migration**: Eine beliebige Anzahl von VMs kann an den Zielstandort repliziert und dann zu einem bestimmten Zeitpunkt an diesem Standort aktiviert werden, um die Systeme, die am ursprünglichen Standort ausgeführt werden, zu ersetzen.
-	**Migration von Sicherheitsrichtlinien** - Wenn NSX lokal verwendet wird, werden alle Sicherheitsrichtlinien, Firewalls usw. zusammen mit der Workload verlagert.

Mithilfe dieser Lösung konnte Acme Skateboards die VMware-Workloads erfolgreich auf die {{site.data.keyword.cloud_notm}} migrieren - bei minimaler (oder ganz ohne) Ausfallzeit und ohne erneute Anwendungskonfiguration. Weitere Informationen zu vCenter Server with Hybridity Bundle finden Sie auf der Seite [VMware HCX on {{site.data.keyword.cloud_notm}} Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf).

### Zugehörige Links

* [Übersicht über VCS Hybridity Bundle](../vcs/vcs-hybridity-intro.html)
