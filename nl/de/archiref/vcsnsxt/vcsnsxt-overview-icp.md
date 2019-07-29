---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

subcollection: vmware-solutions


---

# IBM Cloud Private
{: #vcsnsxt-overview-icp}

{{site.data.keyword.icpfull_notm}} ist eine Anwendungsplattform zur Entwicklung und Verwaltung von containerisierten Anwendungen. Es handelt sich um eine integrierte Umgebung, die Kubernetes als Container-Orchestrator, ein privates Image-Repository, eine Managementkonsole, Überwachungsframeworks und eine grafische Benutzerschnittstelle enthält, von der aus Sie Ihre Anwendungen zentral bereitstellen, verwalten, überwachen und skalieren können.

{{site.data.keyword.cloud_notm}} Private ist mit den folgenden Funktionen ausgestattet:
-	**Einheitliches Installationsprogramm** - Das auf Ansible basierende Installationsprogramm richtet in kürzester Zeit einen Kubernetes-basierten Cluster mit Master-, Worker- und Proxyknoten ein.
-	**{{site.data.keyword.cloud_notm}} Private-Managementkonsole** - Hiermit können Sie Ihre Anwendungen und Cluster von einer einzigen, zentralen und sicheren Managementkonsole aus verwalten, überwachen und Fehler beheben.
-	**Private Docker-Image-Registry** - Diese lokale Registry besitzt dieselbe Funktionalität wie Docker Hub, ermöglicht Ihnen jedoch zusätzlich Einschränkungen hinsichlich der Benutzer, die Images anzeigen oder extrahieren dürfen.
-	**Katalog der containerisierten Software und Services** - Der Katalog ist eine zentrale Position, von der aus Sie Pakete suchen und in Ihrem Cluster installieren können. Pakete für zusätzliche IBM Produkte sind aus kuratierten Repositorys verfügbar, die in der Standardliste des {{site.data.keyword.cloud_notm}} Private-Repositorys enthalten sind.
-	**Isolierte Tenantnetze** - Calico ermöglicht eine verbesserte Leistung und Netzisolation innerhalb Ihres Clusters. Mit Calico können Sie für jedes Projekt in Ihrem Cluster ein isoliertes Teilnetz erstellen. Diese Netzisolation bietet Ihnen zusätzliche Sicherheit bei Datenübertragungen und verringert das Risiko von Beeinträchtigungen der Anwendungen und ihrer Daten. Calico vereinfacht darüber hinaus die Erstellung neuer Netzrichtlinien, die eine differenziertere Steuerung der gemeinsamen Nutzung von Objekten in einem einzigen Namensbereich ermöglichen können.
-	**Leistungsfähige Überwachung und Protokollierung mit ELK-Stack** - {{site.data.keyword.cloud_notm}} Private verwendet Elasticsearch, Logstash, Filebeat und Heapster für die Erfassung, Speicherung und Abfrage von Protokollen und Metriken. Dieser Überwachungs- und Protokollierungsprozess stellt einen zentralen Speicher für alle Protokolle und Metriken bereit und bietet eine verbesserte Leistung sowie erhöhte Stabilität beim Zugriff auf bzw. Abfragen von Protokollen und Metriken.

## Komponenten von IBM Cloud Private
{: #vcsnsxt-overview-icp-comp}

Ein {{site.data.keyword.cloud_notm}} Private-Cluster verfügt über vier Hauptklassen von Knoten: Bootknoten, Masterknoten, Workerknoten und Proxy-Knoten. Optional können Sie in Ihrem Cluster Managementknoten, Vulnerability Advisor-Knoten (VA-Knoten) und etcd-Knoten angeben.
-	**Bootknoten** - Ein Bootknoten wird für die Ausführung der Installation, Konfiguration, Knotenskalierung und für Clusteraktualisierungen verwendet.
-	**Masterknoten** - Ein Masterknoten stellt Management-Services zur Verfügung und steuert die Workerknoten in einem Cluster. Masterknoten sind Hostprozesse, die für die Ressourcenzuordnung, die Statusverwaltung, die Zeitplanung und die Überwachung verantwortlich sind.
-	**Workerknoten** - Ein Workerknoten ist ein Knoten, der eine containerisierte Umgebung für die Ausführung von Tasks zur Verfügung stellt. Wenn die Anforderungen steigen, können Sie Ihrem Cluster leicht weitere Workerknoten hinzufügen, um die Leistung und Effizienz zu verbessern.
-	**Proxy-Knoten** - Ein Proxy-Knoten ist ein Knoten, der externe Anforderungen an die Services überträgt, die in Ihrem Cluster erstellt wurden.
-	**Managementknoten** - Ein Managementknoten ist ein optionaler Knoten, der nur Management-Services wie Überwachung, Messung und Protokollierung bietet. Durch die Konfiguration dedizierter Managementknoten können Sie verhindern, dass der Masterknoten überlastet wird.
-	**Vulnerability Advisor-Knoten (VA-Knoten)** - Ein VA-Knoten ist ein optionaler Knoten, der für die Ausführung der Vulnerability Advisor-Funktion verwendet wird.
-	**etcd-Knoten** - Ein etcd-Knoten ist optional; er wird zur Ausführung des verteilten etcd-Schlüsselwertspeichers verwendet.

## Privater IBM Cloud-Netzbetrieb
{: #vcsnsxt-overview-icp-networking}

Das {{site.data.keyword.icpfull_notm}}-Netzmanagement wird durch die Verwendung von Calico vereinfacht.
Calico verwendet Layer 3 oder die Vermittlungsschicht des Modells von Open System Interconnection (OSI). Mithilfe von Border Gateway Protocol (BGP) erstellt Calico Routing-Tabellen, die die Kommunikation zwischen Agentenknoten vereinfachen.

Weitere Informationen zum Netzbetrieb von Calico enthält der Abschnitt [{{site.data.keyword.containerlong_notm}}](/docs/services/vmwaresolutions/archiref/vcsnsxt?topic=vmware-solutions-vcsnsxt-overview-iks).

## Zugehörige Links
{: #vcsnsxt-overview-icp-related}

* [Übersicht über vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
