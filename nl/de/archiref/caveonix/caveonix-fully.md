---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-05"

subcollection: vmware-solutions


---

# Vollständig verteilt
{: #caveonix-fully}

Zusätzliche virtuelle Basismaschinen (VMs) und Scale-out-VMs werden entsprechend der Anzahl der Assets und Datenaufbewahrungsanforderungen hinzugefügt.

Tabelle 1. Basis - Benutzerschnittstelle

|Parameter	|Wert|
|---|---|
|Typ	|Basis|
|Anzahl VMs	|2|
|vCPU	|2|
|RAM	|6 GB|
|Platte	|60 GB|
|BS	|CentOS 7|
|Installierte Anwendungskomponenten	|Benutzerschnittstelle|

Tabelle 2. Basis - Anwendungen und Plug-ins

|Parameter	|Wert|
|---|---|
|Typ	|Basis|
|Anzahl VMs	|2|
|vCPU	|8|
|RAM	|16 GB|
|Platte	|500 GB|
|BS	|CentOS 7|
|Installierte Anwendungskomponenten	|App, Plug-ins|

Tabelle 3. Basis - zentraler Kollektor

|Parameter	|Wert |
|---|---|
|Typ	|Basis |
|Anzahl VMs	|3 |
|vCPU	|8 |
|RAM	|16 GB |
|Platte	|500 GB |
|BS	|CentOS 7 |
|Installierte Anwendungskomponenten	|Zentraler Kollektor (Cluster) |

Tabelle 4. Basis - relationale Datenbank

|Parameter	|Wert |
|---|---|
|Typ	|Basis |
|Anzahl VMs	|2 |
|vCPU	|8 |
|RAM	|16 GB |
|Platte	|1 TB |
|BS|CentOS 7 |
|Installierte Anwendungskomponenten	|Relationaler Datenspeicher (primär/sekundär) |

Tabelle 5. Basis - Messaging-Datenspeicher

|Parameter	|Wert |
|---|---|
|Typ	|Basis |
|Anzahl VMs	|3 |
|vCPU	|8 |
|RAM	|16 GB |
|Platte	|1 TB |
|BS	|CentOS 7 |
|Installierte Anwendungskomponenten	|Messaging-Datenspeicher (Cluster) |

Tabelle 6. Basis - Indexdatenspeicher (Masterknoten)

|Parameter	|Wert |
|---|---|
|Typ	|Basis |
|Anzahl VMs	|3 |
|vCPU	|8 |
|RAM	|16 GB |
|Platte	|1 TB |
|BS	|CentOS 7 |
|Installierte Anwendungskomponenten	|Indexdatenspeicher (Masterknoten) |

Tabelle 7. Datenbank - Indexdatenspeicher (Datenknoten)

|Parameter	|Wert |
|---|---|
|Typ	|Basis |
|Anzahl VMs	|5 |
|vCPU	|8 |
|RAM	|16 GB |
|Platte	|4 TB |
|BS	|CentOS 7 |
|Installierte Anwendungskomponenten	|Indexdatenspeicher (Datenknoten) |

Die Details zu den Scale-out-VMs werden in der folgenden Tabelle beschrieben.

Tabelle 8. Scale-out - Datenknoten

|Parameter	|Wert |
|---|---|
|Typ	|Scale-out |
|Anzahl VMs	28 |
|vCPU	|8 |
|RAM	|16 GB |
|Platte	|4 TB |
|BS	|CentOS 7 |
|Installierte Anwendungskomponenten	|Datenknoten (Scale-out) |

Die Details zur VM des fernen Kollektors werden in der folgenden Tabelle beschrieben.

Tabelle 9. Ferner Kollektor

|Parameter	|Wert |
|---|---|
|Anzahl VMs	|Nach Bedarf |
|vCPU	|8 |
|RAM	|8 GB |
|Platte	|1 TB |
|BS	|CentOS 7 |
|Installierte Anwendungskomponenten	|Ferner Kollektor |
