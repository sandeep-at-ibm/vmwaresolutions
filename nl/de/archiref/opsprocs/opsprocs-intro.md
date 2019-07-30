---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-01"

---

# Einführung in Betriebsprozesse
{: #opsprocs-intro}

Viele IT-Organisationen dokumentieren ihre Betriebsprozesse in einem Runbook. Ein Runbook ist ein Satz standardisierter Dokumente, Referenzen und Prozeduren, die häufig wiederkehrende IT-Tasks erläutern. IT-Mitarbeiter beziehen sich auf das Runbook, um ihre Arbeit optimal zu erledigen. Runbooks verbessern die organisatorische Effizienz durch Standardisierung und unterstützen ein effizienteres Onboarding von Mitarbeitern. Es gibt zwei Typen von Runbooks:

1. Eine allgemeine Dokumentation der Prozeduren, Leitfäden und Tasks. Diese ist in der Regel eher allgemein gehalten und verweist auf die von Anbietern bereits bereitgestellte Dokumentation.
2. Eine spezialisierte Dokumentation für das Unternehmen. Diese Dokumentation ist für ein System, eine Anwendung oder eine Suite von Anwendungen spezifisch; die darin enthaltenen Themen werden in der Dokumentation der Anbieter nicht abgedeckt. Die folgende Struktur für Ihre spezialisierte Dokumentation wird empfohlen:

 * Übersicht - Eine Übersicht über den Service mit Abschnitten, die Folgendes beschreiben:
    * Was ist der Service und warum ist er für das Unternehmen erforderlich?
    * Wer sind die Hauptansprechpartner für den Service?
    * Wie berichte ich Probleme mit dem Service?
 * Build - Dieser Abschnitt richtet sich an die Entwicklungsteams und stellt die wichtigsten Softwarekomponenten des Service vor, sowie die Art und Weise, wie der Service konstruiert ist. Informationen zu Softwareprodukten, Standorten von OVAs, Verteilerdatenträgern oder der Position des Quellcodes. Die erforderlichen Schritte für die Paketierung oder Verteilung des Release. Er enthält alle erforderlichen Anweisungen für die Einarbeitung eines neuen Entwicklers.
 * Bereitstellung - Dieser Abschnitt richtet sich an das Operationsteam und behandelt die Implementierung der Software. Er enthält Details zur Hardware und virtualisierten Infrastruktur sowie zum Erstellen der virtuellen Maschinen (VMs), einschließlich vCPU, RAM- und Plattenanforderungen, Betriebssystemversion und -konfiguration und die zu installierende Middleware bzw. die zu installierenden Pakete.
 * Prozeduren - Schrittweise Anleitungen für allgemeine Tasks wie das Hinzufügen, Ändern und Löschen, gängige Probleme und ihre Lösungen, Hinweise zur Fehlerbehebung.
 * Fehlerbehebung - Eine Liste gängiger Alerts aus dem Überwachungssystem, einschließlich der schrittweisen Tasks für diese Alerts, sowie allgemeine Hinweise zur Fehlerbehebung für den Service.
 * Disaster-Recovery-Pläne und -Prozeduren - Details zur Wiederherstellung des Service an einem anderen Standort infolge eines Ausfalls am primären Standort.
 * Service-Level-Agreement - Die vereinbarten Serviceparameter, z. B. Vereinbarungen auf Betriebsebene, Schlüsselindikatoren, Zielsetzung für Verfügbarkeit, Wiederherstellungspunkt und Wiederherstellungszeit.

Die meisten IT-Organisationen verfügen über mehrere Runbooks, die als Referenzhandbücher dienen. Diese Dokumentationsreihe soll als allgemeines Runbook für Ihr Unternehmen verwendet werden, das vCenter Server-Instanzen einsetzt. Zwar sind die Inhalte von Runbooks unternehmensspezifisch, aber die Vorgehensweise zur Erstellung des Runbooks besteht im Grunde immer aus zwei Phasen:

1. Die erste Phase ist die Entscheidung, welche Prozeduren dokumentiert werden müssen, und diese dann mit ausreichend Details zu unterlegen.
2. Die zweite Phase endet nie und besteht darin, diese Prozeduren zu verwalten, zu aktualisieren und zu korrigieren, neue Prozeduren hinzuzufügen und nicht mehr benötigte Prozeduren zu entfernen.

Mit {{site.data.keyword.vmwaresolutions_full}} können Sie das Know-how Ihres Teams, die Toolsets und Runbooks nutzen, die lokal vorhanden sind, um Ihre Instanzen in {{site.data.keyword.cloud_notm}} zu verwalten.

In der folgenden Liste werden die gängigsten Prozeduren, Leitfäden und Tasks aufgeführt:
* Konfigurationstasks - Bei diesen Tasks handelt es sich um allgemeine Aktivitäten, die von Systemadministratoren ausgeführt werden müssen, um die Umgebung an die Anforderungen des Unternehmens anzupassen und um auf Serviceanforderungen zu reagieren, z. B. neue VMs hinzuzufügen und die Kapazität zu erhöhen. Diese Tasks können wie folgt klassifiziert werden:
 * Allgemeine Anweisungen
 * VM-Prozeduren
 * vCenter-Prozeduren
 * vSphere ESXi-Hostprozeduren
 * Speicherprozeduren
 * Netzprozeduren
* Alarme - vSphere umfasst ein Ereignis- und Alarmsubsystem, das Ereignisse in der vSphere-Umgebung verfolgt und diese Informationen in vCenter zur Verfügung stellt. In diesem Abschnitt wird dieses Subsystem beschrieben und wie Sie die Alarme in Ihrem Unternehmen aktivieren und verwenden können.
* Proaktive tägliche Prüfungen - Diese Prüfungen ermöglichen es Systemadministratoren, die Umgebung in einem einwandfreien Zustand zu halten. Wenn sie täglich ausgeführt werden, sollten sie viele häufig auftretende Kapazitäts- und Leistungsprobleme verhindern, bevor diese sich auf Ihre Workloads auswirken können.
* Fehlerbehebung - Trotz proaktiven täglichen Prüfungen können Probleme auftreten, die sich auf Ihre Workloads auswirken. Deshalb müssen Sie das zugrunde liegende Problem so schnell wie möglich beheben. Diese Fehlerbehebungshandbücher und einige allgemeine Fehlerbehebungsszenarios unterstützen Systemadministratoren bei der schnellen Identifizierung und Behebung dieser Probleme.
* Konformität - Das Konformitätshandbuch bietet Einblicke in die Bewahrung der Konformität der Umgebung auf der Grundlage gesetzlicher Konformitätsvorschriften oder branchenspezifischen bewährten Verfahren. Der Fokus dieses Handbuchs liegt auf VMware-Härtungsrichtlinien, bei denen es sich um eine Reihe von dokumentierten Listen bewährter Verfahren für eine VMware-Umgebung handelt.

Viele der oben genannten Tasks sind in Operations Management unter {{site.data.keyword.cloud_notm}} automatisiert; für Tasks, die dies nicht sind, vereinfachen diese Tools die manuellen Prozesse für Ihre Systemadministratoren erheblich. Es ist zwingend erforderlich, dass Sie die Kernkomponenten der VMware-Umgebung überwachen. In Operations Management unter {{site.data.keyword.cloud_notm}} wird dies wie folgt realisiert:

## Operations Management unter IBM Cloud
{: #opsprocs-intro-ops-mgmt}

Möglicherweise stehen Ihnen Unternehmenstools zur Verfügung, die Sie nutzen können, um Ihre vCenter Server-Instanz zu überwachen und zu verwalten. Tabelle 1 beschreibt die Kernkomponenten der vCenter Server-Umgebung, warum sie überwacht werden müssen, und wie sie mithilfe von Operations Management unter {{site.data.keyword.cloud_notm}} überwacht werden. Weitere Informationen finden Sie in der Dokumentation der Referenzarchitektur.

Tabelle 1. Kernkomponenten der vCenter Server-Umgebung

| Komponente | Warum | Überwacht von  |
|---|---|---|
| vCenter | vCenter ist die Infrastrukturmanagementkomponente, die die vSphere-Hosts und virtuelle Konstrukte wie Cluster verwaltet. vSAN wird von vCenter überwacht. vSphere-Netze wie verteilte Switches und Portgruppen werden von vCenter überwacht. | vRealize Operations Manager (vROps) und VMware SDDC Health Management Pack. vRealize Log Insights (vRLI) erfasst die Protokolldaten von vCenter und das Content-Pack für vSphere ergänzt die Protokolle um spezifische Informationen und sendet wiederum Alerts an vROPs. |
| vSphere-Hosts | vSphere-Hosts stellen die virtualisierte CPU, RAM und das Netz für die Compute-VMs bereit. | vROps von vCenter. vRLI erfasst die Protokolldaten. |
| vSAN | vSAN stellt einen Datenspeicher bereit, indem Speicher in den Hosts konsolidiert wird und dort von den VMs verwendet werden kann. Kapazitäts- und Leistungsprobleme wirken sich auf die Anwendungen aus, die auf diesen virtuellen Maschinen ausgeführt werden. |vROps und das Management Pack for vSAN stellen zusätzliche Dashboards für die Überwachung von vSAN bereit. vCenter vSAN-Statusprüfungen werden von vROps erfasst. vRLI erfasst die Protokolldaten aus vCenter. |
| NSX | NSX stellt die virtualisierten Netzkomponenten bereit, die von den Compute-VMs genutzt werden; jeder Ausfall des Netzes kann sich auf die Anwendungen auswirken, die auf diesen VMs ausgeführt werden. | vROps und das vROps Management Pack for VMware NSX bieten Einblicke in die Netztopologie. vRLI erfasst die Protokolldaten aus den NSX-Komponenten wie Controllern, ESG und logischen Switches. vRealize Network Insight (vRNI) stellt eine umfassende Fehlerbehebung von Netzproblemen bereit. |

Neben der Überwachung bietet Operations Management unter {{site.data.keyword.cloud_notm}} Unterstützung bei der Konfiguration, Konformität und vielen der proaktiven Tasks, die in dieser Dokumentation ausführlich beschrieben sind.


## Zugehörige Links
{: #opsprocs-intro-links}

* [vSphere-Überwachung](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.monitoring.doc/GUID-A8B06BE0-E5FC-435C-B12F-A31618B21E2C.html){:new_window}
* [VMware-Richtlinien zur Sicherheitshärtung](https://www.vmware.com/uk/security/hardening-guides.html){:new_window}
* [Operations Management unter {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-opsmgmt-intro){:new_window}
* [Hinweise zum Ändern von vCenter Server-Artefakten](/docs/services/vmwaresolutions?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact)
