---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

# Schritt 4 - Anwendungskonfiguration
{: #caveonix-step4}

Nachdem die virtuellen Maschinen (VMs) bereitgestellt und die Anwendungskomponenten installiert sind, steht die Caveonix RiskForesight-Lösung zur Konfiguration für den Service-Provider und den ersten Tenant oder die erste Organisation zur Verfügung.

Der Service-Provider ist die Organisation der höchsten Ebene und es gibt mindestens einen Tenant/eine Organisation, der/die vom Service-Provider bedient wird bzw. werden. Der Service-Provider ordnet die von vCenter erfassten Assets dem Tenant oder den Organisationen zu, die sie anschließend zu Anwendungen oder Unteranwendungen zuordnen. Diese Anwendungen unterliegen dann den Konformitätsvorschriften.

Dieser Schritt wird zunächst von der IC4VS-Automatisierung anhand von Informationen ausgeführt, die der Kunde während des Bestellprozesses angibt, sowie anhand von Standardinformationen. Der Konfigurationsprozess kann vom Kunden nach der Bereitstellung gestartet werden, um den Service-Provider oder die Tenant-Organisation gegebenenfalls nach der Installation zu ändern.

Die Konfiguration des Service-Providers erfolgt in acht Unterschritten:
-	Schritt 1: Organisationsdetails - Fügen Sie die Details für die übergeordnete Organisation für Ihren Cloud-Service-Provider hinzu. Diese Organisation kann über mehrere physische Standorte und mehrere Rechenzentren verfügen. Organisationen für Ihre Tenants und Unterorganisationen für Ihren Service-Provider werden später hinzugefügt.
-	Schritt 2: Standorte - Ordnen Sie die Infrastruktur unter "Locations" in RiskForesight zu, da die Assets nach Standort, Cloud-Provider und Asset-Repository gruppiert sind.
-	Schritt 3: Umgebungen - Optional. Umgebungen sind eine Möglichkeit, Assets zu gruppieren. Beispiel: DevOps, DR Site oder Produktion.
-	Schritt 4: Cloud-Provider - Fügen Sie die "Provider" hinzu, die die Infrastruktur bereitstellen, auf der Ihre Anwendung ausgeführt wird.
-	Schritt 5: Asset-Repositorys - Ein Asset-Repository verknüpft eine Gruppe von Assets mit einer Organisation, einem Cloud-Provider und einem Standort.
-	Schritt 6: Organisationen - Erstellen Sie eine Unterorganisation für Ihre eigenen Operationen und weiteren Organisationen, eine für jeden Ihrer Service-Provider-Tenants. Jeder Tenant muss eigens eingerichtet werden, einschließlich der Erstellung eigener Unterorganisationen.
-	Schritt 7: Organisationsbenutzer - Erstellen Sie Benutzer und ordnen Sie sie Tenantorganisationen und Unterorganisationen des Service-Providers zu.
-	Schritt 8: Konfigurieren Sie Tasks für folgende Zwecke: Synchronisation mit dem Asset-Repository, Ausführung von SCAP-Schwachstellen- und Konformitätsscans, Erfassen von NSX-Netzflüssen, Erfassung von Informationen zu der Software, die auf den überwachten Assets ausgeführt wird, sowie Erfassung von Systemprotokollen und Systemereignissen für Assets.

Die Konfiguration des Tenants oder der Organisation erfolgt in sieben Unterschritten:

-	Schritt 1: Organisation - Fügen Sie Details für Ihre primäre Organisation hinzu. Sie können auch Unterorganisationen erstellen. Verwenden Sie Organisationen, um Ihre Benutzer zu segmentieren, oder als eine Möglichkeit, Ihre Assets zu gruppieren. Sie können weitere Organisationen mit einer Ihrer vorhandenen Organisationen als übergeordnetem Element erstellen. Wenn Sie eine neue Organisation erstellen, können Sie den Wert für den Einfluss auf die Geschäftsabläufe auswählen, der zum Generieren der Scores für das Cyberrisiko verwendet wird.
-	Schritt 2: Organisations-Assets - Neue Assets oder Workloads werden automatisch nach Standort, Cloud-Provider und Asset-Repository gruppiert. Assets können jeweils nur einer Organisation zugewiesen sein. Der Service-Provider muss Assets zu einer Organisation zuordnen.
-	Schritt 3: Umgebung und Standort zuordnen - Optional. Umgebungen werden vom Service-Provider definiert.
-	Schritte 4 und 5: Unteranwendungen oder Anwendungen erstellen - Dies geschieht, um Assets über Standorte und Organisationen hinweg zu gruppieren und die zugehörigen Flüsse und Richtlinien anzuzeigen. Erstellen Sie Anwendungen, die Business- und IT-Services entsprechen. Beispiel: Anwendung = SAP, Unteranwendungen = SAP-Front-End, SAP-Mittelschicht und SAP-Back-End. Der Wert für den Einfluss auf die Geschäftsabläufe entspricht einer Anwendung, die Konformitätsvorschriften gelten für eine Anwendung.
-	Schritt 6: Fernzugriff - Dieser ist erforderlich, um Scans an Assets durchzuführen. Dabei kann es sich um ein Standard-Servicekonto oder ein Asset-spezifisches Konto handeln.
-	Schritt 7: Task-Scheduler - Sie können die Ausführung von Scans in regelmäßigen Abständen planen. Typen von Tasks sind SCAP-Sicherheitslücken-Scan, SCAP-XCCDF-Scan, Scan von NSX-Datenflüssen, Software-Scan oder Scans von Protokollauszügen.

Die folgenden Informationen werden vom Benutzer zum Zeitpunkt der Bestellung erfasst und in der Anwendungskonfiguration verwendet.

Tabelle 1. Vom Benutzer erfasste Informationen

|Stufe der Konfiguration |Parameter |
|---|---|
|Organisation / Asset-Repositorys | Name der Organisation |
|Organisation | Telefonnummer |
|Organisation | E-Mail |
|Organisation / Asset-Repositorys | Adresszeile 1 |
|Cloud-Provider / Asset-Repositorys |Name |
|Cloud-Provider |Beschreibung |
|Cloud-Provider |PoC-E-Mail |
|Cloud-Provider |Typ|
|Cloud-Provider |PoC-Name |
|Cloud-Provider |PoC-Telefonnummer |

Die folgenden Standardinformationen werden in der Anwendungskonfiguration verwendet.

Tabelle 2. Für die Anwendungskonfiguration verwendete Standardinformationen

|Stufe der Konfiguration |Parameter |
|---|---|
|Umgebung |Umgebungsname auf “Initial” gesetzt |
|Umgebung | Score auf 5 gesetzt |
|Asset-Repository |Es werden zwei Asset-Repositorys konfiguriert: vCenter und NSX-Manager. Die Host-URL wird festgelegt auf https://*vCenter fqdn* und https://*NSX Manager fqdn*|
|Asset-Repository |Es werden zwei Asset-Repositorys konfiguriert: vCenter und NSX-Manager. Für beide wird derselbe Benutzername verwendet. Der Benutzername wird auf den Benutzernamen des vCenter-Administrators gesetzt|
|Asset-Repository |Es werden zwei Asset-Repositorys konfiguriert: vCenter und NSX-Manager. Für beide wird dasselbe Kennwort verwendet. Das Kennwort wird auf das Kennwort des vCenter-Administrators gesetzt
|Asset-Repository |Es werden zwei Asset-Repositorys konfiguriert: vCenter und NSX-Manager. Für beide wird dasselbe Kennwort verwendet. Der Typ wird für das eine Repository auf vCenter, für das andere auf NSX gesetzt
|Task |Es werden vier Tasks konfiguriert: Asset-Scan, Scan von NSX-Datenflüssen, Scan der VMware-Infrastruktur und Scan auf VMware-Sicherheitslücken. Der Name des Scans wird auf DC1AssetScan, NSXFlows, VMWInfraScan oder VMWVulnScan gesetzt |
|Task |Es werden vier Tasks konfiguriert: Asset-Scan, Scan von NSX-Datenflüssen, Scan der VMware-Infrastruktur und Scan auf VMware-Sicherheitslücken. Der Typ wird auf vCenter, NSX, VMWareInfrastructureScan oder VMWareVulnerabilityScan gesetzt |
|Task |Der Zeitplan wird für DC1AssetScan auf 'stündlich' und für die anderen auf 'täglich' gesetzt |

## Zugehörige Links
{: #caveonix-step4-related}

* [VMware vCenter Server on {{site.data.keyword.cloud}} mit Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs/vcs-hybridity-intro.html)
