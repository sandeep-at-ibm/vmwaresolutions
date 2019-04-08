---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-13"

subcollection: vmwaresolutions


---

# Vergleichsdiagramm für VMware-Komponenteneditionen
{: #solution-appendix}

## Vergleich der VMware NSX-Editionen
{: #solution-appendix-nsx-editions}

In diesem Design gibt es mehrere Komponenten, für die Lizenzen erforderlich sind. In diesen Informationen werden die Mindestlizenzen erfasst, die für die ordnungsgemäße Funktionsweise der Umgebung erforderlich sind.

Tabelle 1. Lizenzvoraussetzungen

Komponente | Zweck | Lizenz
----------|---------|-------------
**vSphere** | Rechenvirtualisierung | vSphere 6.7 Enterprise Plus
**vCenter Server** | Infrastrukturmanagement | vCenter Server 6.7 Standard
**NSX** | Netzvirtualisierung | NSX Base for Service Providers 6.4
**vSAN** | Speichervirtualisierung | vSAN 6.6 Advanced  

Die NSX Base for Service Providers Edition ist nur für Service-Provider über das VMware vCloud Air Network (vCAN) verfügbar. Die Funktionen in dieser Ausgabe sind in der folgenden Tabelle zu finden.
{:note}

Tabelle 2. Vergleichsdiagramm der VMware NSX-Editionen

| NSX-Feature                                   | Base | Advanced | Enterprise |
|-----------------------------------------------|------|----------|------------|
| Verteiltes Switching und Routing             | •    | •        | •          |
| NSX Edge-Firewall                             | •    | •        | •          |
| NAT (Netzadressumsetzung)                                           | •    | •        | •          |
| NSX Edge-Lastausgleich                       | •    | •        | •          |
| VPN (IPsec)                                   | •    | •        | •          |
| VPN (SSL)                                     | •    | •        | •          |
| API-gesteuerte Automatisierung                         | •    | •        | •          |
| Integration in vRealize und OpenStack\*     | •    | •        | •          |
| Automatische Sicherheitsrichtlinien mit vRealize |      | •        | •          |
| SW L2-Überbrückung zur physischen Umgebung        |      | •        | •          |
| Dynamisches Routing mit ECMP (aktiv-aktiv)     |      | •        | •          |
| Verteilte Firewallfunktionalität                       |      | •        | •          |
| Integration in Active Directory             |      | •        | •          |
| Überwachung der Serveraktivität                    |      | •        | •          |
| Serviceeinfügung (Integration für Drittanbieter)     |      | •        | •          |
| Verteilter Lastausgleich                    |      |          | •          |
| vCenter-übergreifendes NSX                             |      |          | •          |
| NSX-Optimierungen mehrerer Sites                  |      |          | •          |
| Fernes Gateway                                |      |          | •          |
| Integration in HW-VTEPs                     |      |          | •          |
\*Nur L2-, L3- und NSX Edge-Integration. Keine Nutzung von Sicherheitsgruppen.

## Vergleich der VMware vSAN-Editionen
{: #solution-appendix-vsan-editions}

In der folgenden Tabelle sind die verfügbaren Features für die **Advanced Edition** und die **Enterprise Edition** von VMware vSAN aufgeführt, die von der Lösung unterstützt werden.

Tabelle 3. Vergleichsdiagramm der VMware vSAN-Editionen

| vSAN-Feature                                    | Advanced | Enterprise |
|-------------------------------------------------|----------|------------|
| Auf Speicherrichtlinien basierendes Management                 | •        | •          |
| Schreib-/Lese-Flash-Caching                        | •        | •          |
| Verteiltes RAID                                | •        | •          |
| Virtueller verteilter Switch (VDS)                      | •        | •          |
| Rack-Awareness                                  | •        | •          |
| vSphere-Replikation                             | •        | •          |
| Software-Kontrollsumme                               | •        | •          |
| Reine Flash-Hardware                              | •        | •          |
| iSCSI-Zielservice                            | •        | •          |
| IOPS-Limit                                      | •        | •          |
| Deduplizierung und Komprimierung                   | •        | •          |
| RAID-5/6 Erasure Coding                         | •        | •          |
| Verschlüsselung ruhender Daten                         |          | •          |
| Standortübergreifender Cluster mit lokalem Ausfallschutz |          | •          |

## Zugehörige Links
{: #solution-appendix-related}

* [Lösungsübersicht](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview)
* [Übersicht über das Design](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_overview)
* [Komponenten sichern](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_backingup)
