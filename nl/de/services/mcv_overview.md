---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-23"

keywords: Mission Critical VMware, request Mission Critical, tech specs Mission Critical

subcollection: vmware-solutions


---

# Mission Critical VMware on IBM Cloud
{: #mcv_overview}

Mission Critical VMware on {{site.data.keyword.cloud}} bietet eine Cloudarchitektur mit mehreren Zonen, die Unternehmen dabei unterstützt, Ausfallzeiten für Cloudanwendungen zu verhindern und Failover-Funktionen in einer Cloudregion zu automatisieren.

Mit dieser Cloudarchitektur kann der Kunde eine höhere Verfügbarkeit und Failover-Erfolgsquote erzielen, als es bei den meisten VMware-Clients mit lokalen Umgebungen oder konkurrierenden Cloudplattformen möglich ist.

Diese Architektur unterstützt vorhandene geschäftskritische traditionelle Workloads, einschließlich nativen Anwendungen (keine Cloudanwendungen), bei einer angestrebten Gesamtverfügbarkeit von 99.99%. {{site.data.keyword.cloud_notm}}-Mehrzonen-Regionen sind so konzipiert, dass bei Ausfall eines Standorts geschäftskritische Workloads online bleiben. Workloads werden nach einem Standortausfall nahezu in Echtzeit automatisch neu gestartet, während die Workloads benachbarter Standorte online und verfügbar bleiben.

Die Architektur umfasst verschiedene Unternehmensservices, wie z. B. Netz- und Speichertools, Tools für die Ausfallsicherheit usw., die für die Überwachung und Fehlerbehebung von cloudbasierten Anwendungen konzipiert sind. Außerdem kann die Architektur in IBM Services Platform with Watson - basierend auf {{site.data.keyword.cloud_notm}} - integriert werden, um eine weitergehende Nutzung der Services zu ermöglichen. Mithilfe der kognitiven Funktionen der Plattform können Kunden ein effektiveres Data-Mining durchführen und die entsprechenden Erkenntnisse ableiten, um zu einem möglichst unterbrechungsfreien Betrieb beizutragen.

## Technische Spezifikationen für Mission Critical VMware on IBM Cloud
{: #mcv_overview-specs}

Die Mission Critical VMware on {{site.data.keyword.cloud_notm}}-Architektur ist eine End-to-End-Referenzarchitektur, die eine automatisierte Failover-Funktionalität für Kundenworkloads zur Verfügung stellt. Die Architektur verwendet eine {{site.data.keyword.cloud_notm}}-Region mit mehreren Zonen mit einem von IBM verwalteten Service, der die folgenden Komponenten umfasst:

* Rechenarchitektur (VMware vSphere)
* Netzarchitektur (derzeit NSX-V)
* Speicherarchitektur (VMware vSAN)
* Integration in IBM Services Platform with Watson, um die Nutzung von Services zu ermöglichen
* Tools für Überwachung, Fehlerbehebung, Leistungs- und Kapazitätsmanagement:
  * vRealize Suite-Muster (Operations, Log Insight und Network Insight)
  * Active Directory-Muster
  * Integration in Netcool/Bluecare für Auto-Ticketing, Alertausgabe und Ereignisaufbereitung
  * Ausfallsicherheitsmuster (Backup und Recovery)

Mission Critical VMware on {{site.data.keyword.cloud_notm}} ist in den folgenden Regionen verfügbar:
* Amerika: NA Süd - alle {{site.data.keyword.cloud_notm}}-Rechenzentren in Dallas und NA Ost: alle {{site.data.keyword.cloud_notm}}-Rechenzentren in Washington, DC
* Europa: alle {{site.data.keyword.cloud_notm}}-Rechenzentren in Frankfurt und London
* Asien/Pazifik: alle {{site.data.keyword.cloud_notm}}-Rechenzentren in Sydney und Tokio

### Architekturspezifikationen der Basisinfrastruktur
{: #mcv_overview-base-specs}

Für die Basisinfrastruktur gelten folgende Spezifikationen:
* Jeder Standort hat seine eigenen dedizierten Edge- und Management-Cluster.
* Der Ressourcencluster ist ein "vSphere + vSAN Stretched Cluster".
* Der Zeugenstandort enthält einen ESXi-Host als Zeugen.
* Architektur mit einem vCenter und NSX Manager
* vCenter Server Appliance mit integriertem Platform Services Controller (PSC), der vCenter High Availability (HA) über eine L3-Netzarchitektur verwendet
* NSX Manager-Wiederherstellung verwendet eine Hot/Standby-Methode, mit der Sicherungsdateien synchronisiert werden

### Spezifikationen für Tools und technologische Architektur
{: #mcv_overview-tooling-specs}

Für die Tools und die technologische Architektur gelten folgende Spezifikationen:
* vRealize Operations, vRealize Log Insight und vRealize Network Insight mit Funktionen für Betrieb und Management, die sich speziell auf die verwendeten VMware-Produkte beziehen (z. B. NSX, vSAN und vSphere)
* IBM Software Defined Environment Automation Tool Health Check (SAT HC) für die Validierung von Bereitstellungen anhand von Best Practices und Sicherheitsrichtlinien
* Optionale Disaster-Recovery (DR) für einen {{site.data.keyword.cloud_notm}}-Standort außerhalb der Region
* Fortigate Security Appliance (oder ähnlich), um einen Internetzugang zu schützen und die Aktiv-Aktiv-Netzintegration mit dem lokalen Netz zu ermöglichen

### Spezifikationen für die "vSphere + vSAN Stretched Cluster"-Architektur
{: #mcv_overview-stretched-cluster-specs}

Für die "vSphere + vSAN Stretched Cluster"-Architektur gelten folgende Spezifikationen:
* Der Cluster bietet Speicher- und Rechenfunktionen, die sich über zwei Standorte erstrecken, um eine verbesserte Verfügbarkeit zu ermöglichen.
* Schreibanforderungen von virtuellen Maschinen (VMs) werden synchron an beiden Standorten geschrieben, wodurch sich eine Netzlatenz zwischen den Standorten ergibt.
* Leseanforderungen von VMs werden lokal an dem physischem Standort erfüllt, an dem sich die VM befindet. Dadurch wird eine zusätzliche Latenz vermieden.
* Der Zeugenstandort und der Zeugenhost agieren als Split Brain/Quorum.
* vSAN Native Encryption (für die Verschlüsselung ruhender Daten) kann in Kombination mit dieser Architektur verwendet werden.

### Spezifikationen für die Netzarchitektur
{: #mcv_overview-network-specs}

Für die Netzarchitektur gelten folgende Spezifikationen:
* Edge/DLR/VXLANs in Kombination mit BGP Metric-based Routing, um ein Aktiv-Aktiv-Standortdesign mit automatisiertem Failover zu ermöglichen.
* Jeder Standort hat ein eigenes Konzept entsprechend den zugehörigen Edges/DLRs und VXLANs.
* Unter normalen Umständen befinden sich alle mit DLR-A verbundenen VMs (z. B. VM-A) in {{site.data.keyword.cloud_notm}}-Verfügbarkeitszone 1 und der eingehende und abgehende Datenverkehr erfolgt lokal.
* Während einer vMotion-Aktivität für VM-A erfolgt der eingehende und abgehende Datenverkehr ebenfalls über die {{site.data.keyword.cloud_notm}}-Verfügbarkeitszone 1.
* Während eines Ausfalls eines Standorts oder einer Edge wird der Datenverkehr über den verbleibenden verfügbaren Standort weitergeleitet.

## Vorgehensweise zum Anfordern von Mission Critical VMware on IBM Cloud
{: #mcv_overview-proc}

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_full}}-Konsole im linken Navigationsfenster auf **Einführung**.
2. Blättern Sie auf der Seite abwärts und klicken Sie unter **VMware Managed Services** auf die Karte **Mission Critical VMware on IBM Cloud**.
3. Klicken Sie auf der Seite "Mission Critical VMware on {{site.data.keyword.cloud_notm}}" im Feld zur **Kontaktaufnahme für Mission Critical VMware** auf **Beratungsgespräch anfordern**.
4. Klicken Sie auf der Seite "IBM Services Expert Hub" auf die Schaltfläche zum **Vereinbaren eines Beratungsgesprächs**, um einen 30-Minuten-Termin mit einem Serviceexperten zu buchen.

  Ein {{site.data.keyword.vmwaresolutions_short}}-Ansprechpartner wird sich dann mit Ihnen über Ihre {{site.data.keyword.cloud_notm}}-Kontaktinformationen in Verbindung setzen, um Sie hinsichtlich der benötigten Lösung zu unterstützen.

## Zugehörige Links
{: #mcv_overview-related}

* [Verwaltete Services aus IMI](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_imi)
* [Verwaltete Services für Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_veeam_services)
* [Verwaltete services für Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_zerto_services)
