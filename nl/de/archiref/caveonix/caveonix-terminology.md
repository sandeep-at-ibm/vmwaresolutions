---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-06"

subcollection: vmwaresolutions


---

# Glossar der Caveonix-Begriffe
{: #caveonix-terminology}

Dieses Glossar enthält einige Beschreibungen für Begriffe, die zu der Caveonix RiskForesight-Lösung gehören:

-	**NIST Special Publication 800-53:** Ein Risikomanagement-Framework für die Adressen-Sicherheitssteuerung.
-	**Security Content Automation Protocol (SCAP):** Eine Methode zur Verwendung bestimmter Standards, die das automatisierte Schwachstellenmanagement, die Messung und die Bewertung der Richtlinienkonformität von Systemen ermöglichen, die in einer Organisation bereitgestellt sind. Prüflisten standardisieren und ermöglichen die Automatisierung der Verbindung zwischen Computer-Sicherheitskonfigurationen und dem Kontroll-Framework NIST Special Publication 800-53.
  - Die National Vulnerability Database (NVD) ist das Inhaltsrepository der US-Regierung für SCAP.
  -	SCAP ermöglicht es Sicherheitsadministratoren, Computer, Software und andere Einheiten auf Grundlage einer vordefinierten Sicherheits-Baseline zu scannen, um zu ermitteln, ob die Konfigurations- und Software-Patches in dem Standard implementiert sind, mit dem sie verglichen werden.
  Die SCAP-Komponenten sind folgende:
  -	Common Vulnerabilities and Exposures (CVE) - Eine Liste der öffentlich bekannten Cybersicherheits-Schwachstellen.
  -	Common Configuration Enumeration (CCE) - Eine Liste der sicherheitsrelevanten Probleme der Systemkonfiguration.
  -	Common Platform Enumeration (CPE) - Ein strukturiertes Benennungsschema für Informationstechnologie-Systeme, -Software und -Pakete.
  -	Common Weakness Enumeration (CWE) - Eine Liste allgemeiner Sicherheitslücken im Bereich der Softwaresicherheit.
  -	Common Vulnerability Scoring System (CVSS) - Bietet eine Möglichkeit, die Hauptmerkmale einer Schwachstelle zu erfassen und eine numerische Bewertung zu erzeugen, die ihre Wertigkeit widerspiegelt.
  -	Extensible Configuration Checklist Description Format (XCCDF) - Eine Spezifikationssprache zum Schreiben von Sicherheitsprüflisten, Benchmarks und verwandten Arten von Dokumenten. Ein XCCDF-Dokument stellt eine strukturierte Sammlung von Sicherheitskonfigurationsregeln für eine bestimmte Gruppe von Zielsystemen dar.
  -	Open Vulnerability and Assessment Language (OVAL) – Eine Sprache, die zum Codieren von Systemdetails verwendet wird, sowie ein Sortiment von Content-Repositorys. Die Sprache standardisiert die drei Hauptschritte des Bewertungsprozesses:
      - Darstellung von Konfigurationsinformationen von Systemen für Tests.
      -	Analyse des Systems (Anfälligkeit, Konfiguration und Patch-Status).
      -	Berichterstellung zu den Ergebnissen dieser Bewertung.
-	**Security Technical Implementation Guide (STIG):** Eine Cybersecurity-Methode zur Standardisierung von Sicherheitsprotokollen in Netzen, Servern, Computern und logischen Designs zur Erhöhung der Gesamtsicherheit. Diese Leitfäden erhöhen mit ihrer Implementierung die Sicherheit für Software, Hardware, physische und logische Architekturen und bieten damit eine weitere Reduktion von Sicherheitslücken.
-	**Service-Provider:** Die übergeordnete Organisation.
-	**Cloud-Provider** - Stellt die Infrastruktur bereit, auf der die softwaredefinierte Cloud ausgeführt wird. RiskForesight kann für mehrere Cloud-Provider konfiguriert werden.
-	**Organisationen:** Tenant-Organisationen und -Unterorganisationen des Service-Providers. Wenn das Asset-Repository vCenter ist, muss die Organisations-/Tenantliste manuell erstellt werden.
-	**Rollen:** Vorkonfigurierte Rollen und Service-Provider haben Rollen erstellt. Vorkonfigurierte Rollen können vom Service-Provider nicht bearbeitet werden.
-	**Benutzer der Organisation:** Benutzer der Tenantorganisationen und -Unterorganisationen.
-	**Asset-Repository:** Ein Integrationspunkt, der es RiskForesight ermöglicht, das aktuelle Asset über die CSP-Managementzone und die Kundenzone zu synchronisieren. Die aktuelle Version von RiskForesight unterstützt die Synchronisation für VMware vCloud Director und vCenter Server. Sie unterstützt auch die Datenerfassung von VMware NSX Manager. Assets werden aus dem Asset-Repository erfasst. Der Service-Provider ordnet Assets zu, die aus vCenter für Tenant-Organisationen und -Unterorganisationen des Service-Providers erfasst werden. Ein Asset kann nur einer einzigen Organisation zugeordnet werden.
-	**Fernzugriff:** Stellt Endmaschinenberechtigungsnachweise bereit, um Scans für die Sicherheitslücken- und Konformitätsüberwachung zu aktivieren und Systemereignisprotokolle zu erfassen. Der Service-Provider kann Fernzugriff nur für eigene Assets aktivieren. Tenants haben die Kontrolle über den Fernzugriff von ihren Assets aus.
-	**Anwendungen und Unteranwendungen:** Eine logische Methode zum Gruppieren von Assets. Beispielanwendung: SAP; Beispiel-Unteranwendungen: SAP-Front-End, SAP-Mittelschicht, SAP-Back-End.
-	**Orte:** Assets sind eindeutig nach Standort, Cloud-Provider und Asset-Repository gruppiert.
-	**Umgebungen:** Eine Möglichkeit, Assets und Anwendungen zu gruppieren. Jeder Umgebung ist ein Risikofaktor von 1 bis 10 zugeordnet. Dieser Faktor wird in der Berechnung der Risikobewertung angewendet. Der Service-Provider definiert die Umgebungen.
-	**Tasks:** Wird in RiskForesight für folgende Zwecke verwendet:
  -	Regelmäßige Synchronisation des Asset-Repositorys mit RiskForesight.
  -	Durchführung von SCAP-Scans auf Schwachstellen und Konformität.
  -	Sammeln von Netzflüssen und anderen Informationen, die NSX-Scans verwenden.
  -	Erfassen von Informationen zu der Software, die auf überwachten Assets ausgeführt wird.
  -	Erfassen von Syslog- und Systemereignissen für Assets.
-	**Tasktypen:** Die folgenden Tasks werden unterstützt:
  -	**VMware vCenter-Scan:** Erfasst Assets aus vCenter.
	- **VMware-VCD-Scan:** Erfasst Assets von VCD.
  -	**VMware-NSX-Scan:** Erfasst Netzinformationen und den Netzfluss vom NSX-Manager.
  - **SCAP-Scan:** Dieser Scantyp wird zum Scannen von Workloads für Konformitäts- und Cyberrisiko verwendet. Dieser Scan basiert auf dem SCAP (Security Content Automation Protocol). Für künftige Releases ist geplant, dass sie angepassten Inhalt im OVAL-Format unterstützen.
  - **Software-Scan:** Dieser Scan erfasst das Softwareinventar, das in der Zielworkload unter der Verwaltung installiert ist. Dieses Inventar ist anschließend für die Suche über die Suchoption in der oberen Leiste der Benutzerschnittstelle verfügbar.
  - **LogExtract:** Dieser Scan unterstützt die Protokollerfassung aus Windows- und Linux-Workloads. Dies wird für Forensikzwecke verwendet und durch maschinelles Lernen eingepflegt, um nützliche Informationen zu erzeugen.
  - **AMQP-Task:** Diese AMQP-Task wird für die Erfassung von Live-Ereignissen aus VCD verwendet, um die Echtzeitsynchronisation zu ermöglichen. RiskForesight verarbeitet Ereignisse von Hinzufügungen, Löschungen und Aktualisierungen und veranlasst entsprechende Aktionen. Wird z. B. ein neues Asset hinzugefügt und RiskForesight hat diese Benachrichtigung über AMQP erhalten, aktualisiert es die Datenbank sofort und startet die Überprüfung der Konformitäts- und Cyberrisiken.
  - **VMware-Infrastruktur-Scan:** Dieser Scan führt eine Infrastrukturüberprüfung der VMware-Assets durch.
  -	**VMware-Schwachstellenscan:** Dieser Scan führt eine Schwachstellenprüfung der VMware-Assets durch.
-	**Konformitätsvorschriften:** Nur mit Lizenz verfügbar; NIST, NESA, PCI, ISO, HIPAA, DSGVO, Custom, FFIEC, FedRAMP Low, FedRAMP Moderate, FedRAMP High
-	**Richtlinienmanager:** Der Richtlinienmanager dient der Funktion zur Richtlinienerstellung für eine Organisation auf Grundlage der Ausgabe des maschinellen Lernens. Caveonix stellt standardmäßig drei Typen von Maschinenlernjobs pro Organisation bereit. Diese sind nicht bearbeitbar; weitere Jobs werden noch nicht unterstützt. Folgende Typen von Maschinenlernjobs werden derzeit unterstützt:
  -	Caveo-Protokolle
  -	Caveo-Netze
  -	Caveo-Scan
-	**Anomalie:** Basierend auf den Anomalien, die in den Daten gefunden werden, können die Richtlinien so konfiguriert werden, dass sie auf Grundlage der vom Benutzer definierten Bedingungen Aktionen ausführen. Sie können den Jobtyp auswählen und boolesche Bedingungen für die Anomaliebewertung konfigurieren und die Aktion bei einer wahren Bedingung definieren. Beispiel:
```
Job: "Caveo-Protokolle". Wenn der Anomalie-Score bei > 90 liegt, markieren Sie das Asset für die Quarantäne und senden Sie eine Benachrichtigung an den Slack-Kanal.`
Job: "Caveo-Netz". Wenn der Anomalie-Score bei > 95 liegt, markieren Sie das Asset für die Quarantäne und senden Sie sowohl eine E-Mail- als auch eine UI-Benachrichtigung.
```

## Zugehörige Links
{: #caveonix-terminology-related}

* [VMware vCenter Server on {{site.data.keyword.cloud}} mit Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
