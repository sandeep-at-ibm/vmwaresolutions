---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

# Umfassende Bereitstellung
{: #caveonix-allinone}

Eine automatisierte Bereitstellung und Konfiguration einer einzelnen virtuellen Maschine (VM), auf der alle RiskForesight-Anwendungskomponenten gehostet werden. Dieses Bereitstellungsmodell eignet sich für kleine Bereitstellungen mit bis zu 100 Assets und 7-30 Tagen Indexierung. Die Details zur umfassenden VM werden in der folgenden Tabelle beschrieben:

Tabelle 1. Parameter der umfassenden Bereitstellung

|Parameter	|Wert|
|---|---|
|Typ	|Basis|
|Anzahl VMs	|1|
|vCPU	|16|
|RAM	|32 GB|
|Platte	|80 GB|
|BS	|CentOS 7|
|Installierte Anwendungskomponenten|	Benutzerschnittstelle, App, Plug-ins, zentraler Kollektor, Indexdatenspeicher, Messaging-Datenspeicher, relationaler Datenspeicher, Indexdatenspeicher, ferner Kollektor|

Die Details zur VM des zusätzlichen fernen Kollektors werden in der folgenden Tabelle beschrieben.

Tabelle 2. Ferner Kollektor

|Parameter	|Wert|
|---|---|
|Anzahl VMs	|Nach Bedarf|
|vCPU	|8|
|RAM	|8 GB|
|Platte	|1 TB|
|BS	|CentOS 7|
|Installierte Anwendungskomponenten	|Ferner Kollektor|

## Zugehörige Links
{: #caveonix-allinone-related}

*   [VMware vCenter Server on {{site.data.keyword.cloud}} mit Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
