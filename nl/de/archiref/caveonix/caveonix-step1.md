---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

# Schritt 1 - Erste Planung sowie Voraussetzungen
{: #caveonix-step1}

Jede Caveonix RiskForesight-Anwendungskomponente ist lose gekoppelt, wird aber zentral verwaltet. Daher können sie in einem umfassenden Bereitstellungsmuster der virtuellen Maschine (VM) bereitgestellt werden oder die Anwendungskomponenten können skaliert und auf mehreren VMs bereitgestellt werden, um höhere Verfügbarkeit, Leistung und Kapazität zu erreichen.

Die Bereitstellungsmuster basieren sowohl auf den Verfügbarkeitsanforderungen als auch auf der Dimensionierung der Datenaufbewahrung. Die RiskForesight-Bereitstellungsknoten lassen sich wie folgt charakterisieren:

-	Basis-VMs: Die Basis-VMs hosten die Anwendungskomponenten, die aufgrund der Datenaufbewahrung nicht skaliert werden können. Diese Komponenten sind die RiskForesight-Benutzerschnittstelle, die RiskForesight-App, RiskForesight-Plug-ins, zentraler Kollektor, ferner Kollektor, Indexdatenspeicher, Messaging-Datenspeicher und relationaler Datenspeicher.
-	Scale-out-VMs: Die Scale-out-VMs, die Datenbank und der Datenindex, können entsprechend der Anzahl der Assets und der erforderlichen Datenaufbewahrung skaliert werden, die eine Nachfrage nach weiterem Scale-out-Festplattenspeicherplatz und damit weiteren Scale-out-VMs erzeugt.

Es gibt drei Bereitstellungsmodelle für Caveonix RiskForesight:

-	Umfassend: Eine automatisierte Bereitstellung und Konfiguration von 1 VM, die alle Anwendungskomponenten hostet:
  - Alle Anwendungskomponenten, die auf einer VM installiert sind.
  - Ferne Kollektoren können auf unterschiedlichen VMs installiert werden.
  - Kleine Bereitstellungen: Bis zu 100 Assets mit 7-30 Tagen Indexierung.
-	Teilweise verteilt: Nach Abschluss der automatisierten Bereitstellung können Sie manuell skalieren, indem Sie den Arbeitsspeicher und die Platte in der ersten VM vergrößern und drei Scale-out-VMs hinzufügen.
  - Bereitstellung von Benutzerschnittstelle, App, Plug-ins, zentralem Kollektor, fernem Kollektor, Indexdatenspeicher, Messaging-Datenspeicher und relationalem Datenspeicher auf nur einer VM.
  - Auf unterschiedlichen VMs installierte ferne Kollektoren.
  -	Auf unterschiedlichen VMs bereitgestellte Indexdatenknoten.
  -	Kleine bis mittelgroße Bereitstellungen: Bis zu 500 Assets mit 30 Tagen Indexierung.
- Vollständig verteilt: Sie können weitere Basis-VMs und Scale-out-VMs entsprechend der Anzahl der Assets und den Datenaufbewahrungsanforderungen hinzufügen:
  - Auf unterschiedlichen VMs verteilte Anwendungskomponenten, die eine Skalierung ermöglichen.
  -	Erforderliches Bereitstellungsmuster bei einer Erhöhung der Anzahl von Assets im Bereich von 500 bis 100.000.
  -	Auf unterschiedlichen VMs installierte ferne Kollektoren.
  -	Benutzerschnittstelle auf mehreren VMs.
  -	App und Plug-ins auf mehreren VMs.
  -	Zentraler Kollektor, der in einem Cluster konfiguriert ist.
  -	In einem primären/sekundären Modell bereitgestellter relationaler Datenspeicher.
  -	In einem Cluster bereitgestellter Messaging-Datenspeicher.
  -	Mit Master- und Datenknoten bereitgestellter Indexdatenspeicher.
  -	Weitere Datenknoten, die bei steigender Anzahl von Assets für das Scale-out verwendet werden.

Alle Komponenten müssen über einen vollständig qualifizierten Domänennamen (FQDN = Fully Qualified Domain Name) verfügen und vor jeder VM-Bereitstellung beim DNS registriert sein. Dieser Schritt erfolgt durch die IC4VS-Automatisierung für die erste umfassende Bereitstellung; liegt aber bei der Skalierung der Bereitstellung in der Verantwortlichkeiten des Kunden.

## Zugehörige Links
{: #caveonix-step1-related}

* [VMware vCenter Server on {{site.data.keyword.cloud}} mit Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs/vcs-hybridity-intro.html)
