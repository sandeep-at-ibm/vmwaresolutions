---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-13"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Bereitstellungsmodelle für Caveonix RiskForesight
{: #caveonix-deploy}

In diesem Abschnitt werden die Bereitstellungsmodelle für Caveonix RiskForesight sowie der Installationsprozess für die Lösung beschrieben.

Wenn Sie die Option {{site.data.keyword.vmwaresolutions_full}} RiskForesight auswählen, müssen Sie nicht sämtliche Schritte der Bereitstellung befolgen, da die ersten Schritte automatisiert erfolgen. Für die Kenntnis der vollständigen Bereitstellung und Architektur und um die Lösung nach der Erstbereitstellung zu skalieren, ist jedoch ein detailliertes Verständnis erforderlich.

Die RiskForesight-Installation umfasst die folgenden übergeordneten Schritte:

1. [Erste Planung sowie Voraussetzungen](/docs/services/vmwaresolutions/archiref/caveonix?topic=vmware-solutions-caveonix-step1) – Kenntnis und Auswahl einer Bereitstellungsoption sowie Konfiguration von DNS, um eine FQDN/IP-Auflösung für die Anwendungskomponenten bereitzustellen.
2. [Bereitstellung der virtuellen Maschine](/docs/services/vmwaresolutions/archiref/caveonix?topic=vmware-solutions-caveonix-step2) - Bereitstellung der VMs über eine OVF-Vorlage. In der VM sind alle Anwendungskomponenten installiert.
3. [Konfiguration der Anwendung](/docs/services/vmwaresolutions/archiref/caveonix?topic=vmware-solutions-caveonix-step3) – Ausführung des Caveonix-Konfigurationsscripts, mit dem die Anwendungskomponente in jeder der VMs konfiguriert wird.
4. [Einrichtung der Anwendung](/docs/services/vmwaresolutions/archiref/caveonix?topic=vmware-solutions-caveonix-step4) – Einrichtung des Service-Providers und eines Tenants oder einer Organisation, um die Anwendung für Benutzer zugänglich zu machen.

Mit der automatisierten Installation wird genau eine VM bereitgestellt, für die alle Anwendungskomponenten konfiguriert werden.
{:note}

## Dimensionierung der Bereitstellung
{: #caveonix-deploy-sizing}

Die Dimensionierung der Bereitstellung wird anhand der folgenden Volumen berechnet.

Tabelle 1. Volumen

|Datentyp	|Volumen |
|---|---|
|Scans pro Tag	|1 |
|Scandaten (MB)	|20 |
|Protokolldaten (MB)	|500 |
|Flussdaten (MB)	|200 |
|Assetdaten (MB)	|46 |
|Gesamtspeicher pro Asset pro Tag (MB)	|766 |
|Datenreplikations-Multiplikator	|2 |
|Gesamt-Indexspeicher pro Asset pro Tag (MB)	|1532 |

Der Datenreplikations-Multiplikator ist auf 2 gesetzt, da der Indexspeicher (elastische Suche) standardmäßig eine n+1-Replikation der Indizes verwendet.
{:note}

Die Anzahl der Skalierungs-VMs wird aus der Anzahl der Assets und der Anzahl der Tage mit zu indexierenden Daten berechnet.

Tabelle 2. Skalieren der VM-Parameter

|Anzahl der Assets	|100	|500	|5000 |
|---|---|---|---|
|Tage mit Daten	|30	|30	|30 |
|Gesamt-Indexspeicher pro Asset pro Tag (MB)	|1532	|1532	|1532 |
|Gesamt-Indexspeicher pro Asset pro 30 Tage (TB)	|4	|22	|219 |
|Pro Skalierungsknoten unterstützte Daten (TB)	|0	|8	|8 |
|Skalieren der erforderlichen VMs	|0	|3	|27 |

Der erforderliche Speicherplatz wird wie folgt berechnet:

Tabelle 3. Speicherparameter

|Anzahl der Assets	|100	|500	|5000 |
|---|---|---|---|
|Langzeit-Datenaufbewahrung (Monate)	|8	|8	|8 |
|Gesamtspeicher pro Asset pro Tag (MB)	|766	|766	|766 |
|Tage mit Daten	|30	|30	|30 |
|Kurzzeit-Datenaufbewahrung (TB)	|7	|33	|329 |
|Langzeit-Datenaufbewahrung (TB)	|18	|88	|877 |

Aus Datenperspektive werden die Daten wie folgt verwendet:

-	Scandaten werden für Konformitätsmanagement verwendet.
-	Protokolldaten werden für das Forensik-Management verwendet.
-	Richtlinien- und Datenflussdaten werden für das Risikomanagement verwendet; Datenflussdaten sind nur über den NSX-Manager verfügbar.

Für die Datenspeicherung gibt es drei Stufen:

-	Datenspeicherung durch Replikation
-	Kurzzeit-Datenspeicherung
-	Langzeit-Datenspeicherung

Die folgende Tabelle bildet eine Zusammenfassung der Bereitstellungen:

Tabelle 4. Zusammenfassung

|Bereitstellungsmodell	|umfassend	|Teilweise verteilt	|Vollständig verteilt |
|---|---|---|---|
|Anzahl der Assets	|100	|500	|5000 |
|Generierte Online-Daten von 30 Tagen (TB)	|4	|22	|219 |
|Nearline-Datenaufbewahrung (90 Tage) (TB)	|7	|33	|329 |
|Offline-Datenaufbewahrung (8 Monate) (TB)	|18	|88	|877 |
|Gesamtaufbewahrungsdauer für Datenspeicher (1 Jahr) (TB)	|28	|142	|1425 |
|Basis-VMs	|1	|1	|20 |
|Skalierungs-VMs	|0	|3	|28 |
|Gesamtzahl VMs	|1	|4	|48 |

**Hinweise:**
Wenn Sie den Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}-Service entfernen, löscht die {{site.data.keyword.vmwaresolutions_short}}-Automatisierung nur die einzige, umfassende Caveonix-VM, die bereitgestellt wurde, und das dedizierte private Teilnetz, das für diese bestellt wurde. Dies bedeutet Folgendes:
* Wenn Sie die Caveonix-VM auf mehrere VMs horizontal skaliert haben, werden diese zusätzlichen VMs nicht entfernt. 
* Wenn Sie die IP-Adressen des dedizierten privaten Teilnetzes für zusätzliche VMs verwendet haben, müssen diesen VMs neue IP-Adressen zugeordnet werden, damit sie weiter funktionieren. 
* Löschen Sie die vCenter Server-Instanz A mit dem installierten Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}-Service und haben Sie die IP-Adressen des für den Service bestellten dedizierten privaten Teilnetzes in vCenter Server-Instanz B verwendet, wird das dedizierte private Teilnetz bei der Löschung der vCenter Server-Instanz A storniert.

## Zugehörige Links
{: #caveonix-deploy-related}

* [VMware vCenter Server on {{site.data.keyword.cloud_notm}} mit Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
