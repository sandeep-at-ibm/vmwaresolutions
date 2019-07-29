---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-15"

subcollection: vmware-solutions


---

# Schritt 3 - Konfiguration der Anwendung
{: #caveonix-step3}

Bei diesem Schritt wird das Caveonix RiskForesight-Konfigurationsscript verwendet. Für die umfassende Bereitstellung wird dieses Script über die IBM Cloud for VMware Solutions-Automatisierung gestartet.

Für die Skalierung muss der Client das Script aufrufen, um die teilweise oder vollständig verteilten Topologien bereitzustellen. Das Script konfiguriert die RiskForesight-Services:
- Caveonix-Apps (API, zentraler Kollektor)
- Elastische Suche
- PostgresSQL
- Ferner Kollektor
- Benutzerschnittstelle
- Kafka
- Kibana
- Zertifikate für alle Services

Am Ende dieses Schritts werden die Anwendungskomponenten auf den erforderlichen virtuellen Maschinen (VMs) installiert.

## Zugehörige Links
{: #caveonix-step3-related}

* [VMware vCenter Server on {{site.data.keyword.cloud}} mit Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
