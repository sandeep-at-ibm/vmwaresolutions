---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-05"

subcollection: vmware-solutions


---

# Teilweise verteilt
{: #caveonix-partially}

Nach Abschluss der automatisierten Bereitstellung können Sie durch Vergrößerung des Arbeitsspeichers und der Platte in der ersten virtuellen Maschine (VM) ein manuelles Scale-out durchführen und drei Scale-out-VMs hinzufügen. Das Riskforesight-Konfigurationsscript kann ausgeführt werden, um die Anwendungskomponenten für alle vier VMs zu aktivieren und zu konfigurieren.

Dieses Bereitstellungsmodell bedient voraussichtlich bis zu 500 Assets mit bis zu 30 Tagen der Datenindexierung.

Wählen Sie die nächsten verfügbaren IP-Adressen aus dem privaten portierbaren {{site.data.keyword.cloud}}-Teilnetz aus. Konfigurieren Sie FQDN-Namen in ADDNS.

Die Dimensionierung der VMs ist wie folgt:

Tabelle 1. Basis-Parameter

|Parameter	|Wert|
|---|---|
|Typ	|Basis|
|Anzahl VMs	|1|
|vCPU	|16|
|RAM	|64 GB|
|Platte	|1000 GB|
|BS	|CentOS 7|
|Installierte Anwendungskomponenten	|Benutzerschnittstelle, App, Plug-ins, zentraler Kollektor, Indexdatenspeicher, Messaging-Datenspeicher, relationaler Datenspeicher, ferner Kollektor|

Die Details der Scale-out-VMs sind wie folgt:

Tabelle 2. Parameter der Scale-out-VMs

| Parameter	| Wert |
|---|---|
| Typ	| Scale-out |
| Anzahl VMs	| 3 |
| vCPU	| 8 |
| RAM	| 16 GB |
| Platte	| 4 TB |
| BS	| CentOS 7 |
| Installierte Anwendungskomponenten	| Datenknoten (Scale-out) |

Die Details zur VM des fernen Kollektors werden in der folgenden Tabelle beschrieben.

Tabelle 3. Parameter des fernen Kollektors

|Parameter	|Wert|
|---|---|
|Anzahl VMs	|Nach Bedarf|
|vCPU	|8|
|RAM	|8 GB|
|Platte	|1 TB|
|BS	|CentOS 7|
|Installierte Anwendungskomponenten	|Ferner Kollektor|
