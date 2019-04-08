---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

subcollection: vmwaresolutions


---

# Produktinformation zu NSX Edge Services Gateway
{: #nsx_overview}

Die VMware NSX Edge Services Gateway-Lösung (ESG) ist eine Erweiterung der Angebote VMware Cloud Foundation on {{site.data.keyword.cloud}} und vCenter Server on {{site.data.keyword.cloud_notm}}, die derzeit für die {{site.data.keyword.cloud_notm}} verfügbar sind. In der Lösungsarchitektur für Cloud Foundation und vCenter Server werden die Komponenten der Lösung und die allgemeine Konfiguration aller Komponenten im Design beschrieben.

Weitere Informationen zum Cloud Foundation- und vCenter Server-Design finden Sie in der [Lösungsübersicht](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview).

## Übersicht über NSX Edge Services Gateway
{: #nsx_overview-nsx-esg}

Das NSX Edge Services Gateway verbindet isolierte Stubnetze mit gemeinsam genutzten Netzen (Uplink) durch die Bereitstellung von allgemeinen Gateway-Services wie Dynamic Host Configuration Protocol (DHCP), Virtual Private Network (VPN), Network Address Translation (NAT), dynamischem Routing und Lastausgleich. Gängige Bereitstellungen von NSX Edge sind Demilitarized Zone (DMZ), VPN-Extranets und Multi-Tenant-Cloudumgebungen, in denen NSX Edge virtuelle Begrenzungen für alle Tenant-, Workload- oder Managementkomponenten erstellt. Die im Folgenden aufgeführten Features sind in NSX Edge Service Gateway verfügbar.

Tabelle 1. Features, die für NSX Edge Service Gateway verfügbar sind

| Feature | Beschreibung |
|:------- |:----------- |
| NSX Edge Service Routing | Stellt die erforderlichen Weiterleitungsinformationen zwischen Broadcastdomänen der Ebene 2 bereit, wodurch Sie die Broadcastdomänen der Ebene 2 verringern und die Netzeffizienz und -skalierung verbessern können. NSX erweitert diese Informationen und gibt an, wo sich die Workloads für das Ost-West-Routing befinden. Dies ermöglicht eine direktere Kommunikation zwischen virtuellen Maschinen ohne den Zeit- und Kostenaufwand einer Erweiterung der Hops. Gleichzeitig stellt NSX auch eine Nord-Süd-Konnektivität bereit und ermöglicht den Tenants den Zugriff auf öffentliche Netze. |
| Firewall | Die unterstützten Regeln der Firewall umfassen die IP-5-Tupel-Konfiguration mit IP- und Portbereichen für die statusabhängige Überprüfung für alle Protokolle. |
| NAT | Stellt separate Steuermechanismen für Quellen- und Ziel-IP-Adressen sowie für die Portübersetzung bereit. |
| DHCP | Ermöglicht die Konfiguration von IP-Pools, Gateways, DNS-Servern und Suchdomänen. |
| Site-to-Site VPN | Verwendet standardisierte IPSec-Protokolleinstellungen für die Interoperabilität mit allen wichtigen VPN-Anbietern. |
| L2VPN | Erweitert L2-Netze über L3-Topologien hinweg. |
| SSL VPN-Plus |  SSL VPN-Plus ermöglicht es fernen Benutzern, eine sichere Verbindung zu privaten Netzen hinter einem NSX Edge-Gateway herzustellen. |
| Load Balancing | Stellt einfache und dynamisch konfigurierbare virtuelle IP-Adressen und Servergruppen bereit. |
| High Availability | Stellt sicher, dass es eine aktive NSX Edge im Netz gibt, falls die primäre NSX Edge-Maschine nicht verfügbar ist. |

## Zugehörige Links
{: #nsx_overview-related}

* [Lösungsübersicht](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview)
