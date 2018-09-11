---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-14"

---

# Design der Infrastruktur für angehängten Speicher

{{site.data.keyword.vmwaresolutions_full}} bietet VMware-Technologie, die weltweit automatisiert in {{site.data.keyword.CloudDataCents_notm}} bereitgestellt wird. Innerhalb des {{site.data.keyword.cloud_notm}}-Lösungsportfolios besteht das VMware vCenter Server on {{site.data.keyword.cloud_notm}}-Basisangebot aus bis zu 20 vSphere-Hosts, einem einzelnen Platform Services Controller (PSC) und einer vCenter Server Appliance, die in der Lage ist, bis zu 100 Hosts und 1.000 virtuelle Maschinen zu verwalten.

Die Architektur, die hier dargestellt wird, ergänzt die vCenter Server-Lösung durch Hinzufügen von angehängtem Speicher als gemeinsam genutzte Speichereinheit für die Umgebung. Die angehängte Speichereinheit befindet sich innerhalb desselben {{site.data.keyword.CloudDataCent_notm}} wie die vCenter Server-Bereitstellung und besteht aus einer einzelnen NFS-Freigabe (NFS = Network File System) oder mehreren NFS-Exporten aus {{site.data.keyword.cloud_notm}}.

In der folgenden Abbildung ist die Gesamtarchitektur von NetApp ONTAP Select für die vCenter Server-Bereitstellung dargestellt.

Abbildung 1. Allgemeine Architektur von NetApp ONTAP Select on {{site.data.keyword.cloud_notm}}

![NetApp ONTAP Select-Architektur](../../netapp/np_architecture.svg "Allgemeine Architektur von NetApp ONTAP Select on IBM Cloud")

## Design der physischen Infrastruktur

Die physische Infrastruktur besteht aus drei Hauptkomponenten, einschließlich physischer Rechenleistung, physischem Speicher und physischem Netz. Diese Lösung umfasst das {{site.data.keyword.cloud_notm}}-Servicenetz sowie den physischen Speicher, der von der Infrastruktur genutzt wird.

## Design des physischen Netzes

Der physische Netzbetrieb wird von {{site.data.keyword.cloud_notm}} gesteuert. Im vorliegenden Abschnitt wird das physische Netz beschrieben, das von {{site.data.keyword.cloud_notm}} bereitgestellt wird, da es in Zusammenhang zum angehängten Speicher steht.

### IBM Cloud-Netzübersicht

Das physische Netz von {{site.data.keyword.cloud_notm}} ist in drei verschiedene Netze unterteilt: öffentliches Netz, privates Netz und Managementnetz. Weitere Informationen über das öffentliche, das private und das Managementnetz finden Sie in der [Lösungsübersicht](../solution/solution_overview.html).

Weitere Informationen zum {{site.data.keyword.cloud_notm}}-Netz finden Sie im [{{site.data.keyword.cloud_notm}}-Netz](https://www.ibm.com/cloud-computing/bluemix/our-network){:new_window}.

Lesen Sie die folgenden Informationen, um eine Beschreibung des Servicenetzes zu erhalten, das Teil des privaten Netzes ist.

### Privates Servicenetz

{{site.data.keyword.cloud_notm}} enthält ein privates Servicenetz, das häufig verwendete Services wie beispielsweise Block Storage-, File Storage- und Object Storage-Services, DNS-Auflösungsservices und NTP-Server zur Verfügung stellt. Dieses private Netz arbeitet vom privaten Netz des Kunden getrennt und ermöglicht Umgebungen die reibungslose Verbindung zu Services, die sich in {{site.data.keyword.cloud_notm}} befinden. Das private Netz ist mehrschichtig gestaltet, sodass Server und andere Infrastrukturkomponenten mit zusammengefassten Back-end-Kundenswitches (BCS - Back-end Customer Switch) verbunden sind. Diese zusammengefassten Switches sind mit einem Paar separater Router (Back-end-Kundenroutern, BCR) für den L3-Netzbetrieb verbunden. Das private Netz unterstützt zudem die Möglichkeit, Jumbo-Frames (MTU 9000) für physische Hostverbindungen zu verwenden.

### VLANs

Weitere Informationen zu VLANs finden Sie im Abschnitt zum _physischen Netzdesign_ unter [Design der physischen Infrastruktur](../solution/design_physicalinfrastructure.html).

## Design des physischen Speichers

In diesem Abschnitt wird die Konfiguration der angehängten Speichereinheit dargestellt, die in {{site.data.keyword.cloud_notm}} vorhanden ist. Die angehängte Speichereinheit ergänzt die vorhandene vCenter-Server-Lösung. Demzufolge werden lokal angeschlossene Platteneinheiten, die interne Komponenten der physischen Hosts sind, nicht dargestellt.

## Leistung des angehängte Speichers

Leistungs- und Endurance-Speicher stellen {{site.data.keyword.cloud_notm}}-Speicherlösungen dar, die zur Unterstützung von Anwendungen mit hohem E/A-Aufkommen entworfen werden, bei denen verlässliche Leistungsstufen gewährleistet werden müssen. Diese verlässliche Leistung wird durch die Zuordnung von IOPS (E/A-Operationen pro Sekunde) auf Protokollebene zu einzelnen Datenträgern erreicht.

IOPS zwischen 100 und 48.000 können mit Speichergrößen zwischen 20 GB und 12 TB bereitgestellt werden. Leistungs- und Endurance-Speicherdatenträger stehen sowohl für Block Storage als auch für File Storage zur Verfügung.

In diesem Design bietet die vCenter Server-Lösung Endurance-Speicher für den angehängten Speicher. Demzufolge können Sie (via Automatisierung) Endurance NFS-Exporte auswählen und anhängen, deren Größe zwischen 20 GB und maximal 12 TB liegen kann. Mit {{site.data.keyword.cloud_notm}} können bis zu 64 vSphere ESXi-Hosts mit einem einzigen Endurance NFS-Export verbunden werden.

Endurance steht in drei IOPS-Leistungsstufen zur Unterstützung unterschiedlicher Anwendungsanforderungen zur Verfügung. Hierbei ist zu beachten, dass für eine NFS-Freigabe nach der Bereitstellung die Größe nicht mehr geändert und auch keine Rekonfiguration mehr durchgeführt werden kann, um eine größere oder geringere Anzahl von IOPS zu ermöglichen.

Detaillierte Informationen zu den IOPS-Optionen finden Sie im Abschnitt mit den _Speichereinstellungen_ unter dem Thema zum [Bestellen von vCenter Server-Instanzen](../../vcenter/vc_orderinginstance.html).

Zusätzlich zu den Speicherstufen unterstützt der {{site.data.keyword.cloud_notm}}-Endurance-Speicher eine umfangreiche Palette von Anwendungsanforderungen einschließlich der Erstellung von Momentaufnahmen und Replikationen sowie der Verschlüsselung an den {{site.data.keyword.CloudDataCent_notm}}-Standorten.

### Zugehörige Links

* [Lösungsübersicht](../solution/solution_overview.html)
