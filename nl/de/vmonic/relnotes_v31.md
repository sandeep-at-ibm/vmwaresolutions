---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-01"

keywords: release notes, what's new, version 3.1

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Releaseinformationen für Version 3.1
{: #relnotes_v31}

Dieses Release stellt neue Funktionen, Komponentenaktualisierungen, Verbesserungen des Bedienungskomforts und Fehlerkorrekturen zur Verfügung. Eine Liste mit den in den unterschiedlichen Releases behobenen Problemen, den bekannten Problemen beim Produkt sowie Tipps für die Verwendung von {{site.data.keyword.vmwaresolutions_full}} finden Sie unter [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:external}.

## Single-node Trial-Instanzen für Datenschutz und Disaster-Recovery
{: #relnotes_v31-dr-bundle}

Mit Single-node Trial für Datenschutz und Disaster-Recovery können Sie schnell überprüfen, ob in {{site.data.keyword.cloud_notm}} VMware-Workloads nach {{site.data.keyword.cloud_notm}} migriert und wiederhergestellt werden. Diese Testversion von VMware vCenter Server on IBM Cloud ist eine Single-Tenant-VMware-Plattform, die mit den gleichen Tools wie in lokalen Umgebungen verwaltet werden kann. Diese Testversion umfasst die Services 'Veeam on {{site.data.keyword.cloud_notm}}', 'VMware HCX on {{site.data.keyword.cloud_notm}}' und 'Zerto on {{site.data.keyword.cloud_notm}}'.

Weitere Informationen finden Sie unter [Übersicht über Single-node Trial für Disaster-Recovery](/docs/services/vmwaresolutions?topic=vmware-solutions-dr_backup_bundle_overview).

## IBM Cloud Expert Services
{: #relnotes_v31-expert-services}

Sie können jetzt IBM Expert Services beauftragen, mit Ihrem internen Team beim Bereitstellen, Migrieren und Verwalten Ihrer eigenen {{site.data.keyword.cloud_notm}}-Lösung von der Planung bis zur Modernisierung oder in einer beliebigen Phase dazwischen zusammenzuarbeiten.

Sie können {{site.data.keyword.cloud_notm}} Expert Services jederzeit zu Ihrer Instanzbestellung hinzufügen, indem Sie auf der Seite **Erste Schritte** ein Beratungsgespräch anfordern. Weitere Informationen finden Sie unter [{{site.data.keyword.cloud_notm}} Expert Services anfordern](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_ices).

## Integration in IBM Cloud-Kostenschätzer

Sie können die Kosten für Ihre {{site.data.keyword.vmwaresolutions_short}}-Ressourcen jetzt in einem vereinheitlichten Schätztool schätzen, das vom {{site.data.keyword.cloud_notm}}-Framework bereitgestellt wird. Mit dieser Funktion können Sie einen Snapshot der Ressourcen im gesamten {{site.data.keyword.cloud_notm}}-Katalog speichern und diese in einer einzigen PDF-Datei speichern, die Sie herunterladen können, um sie zu einem späteren Zeitpunkt zu überprüfen. Der Kostenschätzer ist kein Vertrag oder Angebot, sondern nur eine Schätzung Ihrer Gesamtkosten.

Weitere Informationen zum Kostenschätzer finden Sie unter [Kosten schätzen](/docs/billing-usage?topic=billing-usage-cost).

## Updates für VMware vCenter Server-Instanzen
{: #relnotes_v31-vcs}

Mit diesem Release werden die folgenden Upgrades und Verbesserungen für neu bereitgestellte Instanzen, Cluster und Hosts angewendet:

* vSphere ESXi 6.5 Update 2 (Build 6.5.0-13635690)
* vCenter Server Appliance 6.5 Update 2g (Build 6.5.0-13638625)

Weitere Informationen Sie in der [vCenter Server-Teileliste](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom).

### Konfiguration eines alternativen ESXi-Servers für Cluster
{: #relnotes_v31-esxi-config}

Sie können jetzt einem vorhandenen Cluster neue ESXi-Server hinzufügen, indem Sie entweder eine vorhandene Konfiguration oder eine alternative Konfiguration als die vorhandenen Hosts im Cluster auswählen. Wenn Sie im Fenster **Server hinzufügen** neue Server bestellen, können Sie sofort eine vorhandene Konfiguration im Cluster oder eine neue {{site.data.keyword.baremetal_short_sing}}-Konfiguration auswählen. Dies gilt für alle vCenter Server-, vCenter Server with Hybridity- und vCenter Server with NSX-T-Instanzen.

Zur Vermeidung von Leistungs- und Stabilitätsproblemen wird empfohlen, für die Cluster dieselbe oder eine ähnliche Konfiguration für CPU, RAM und Speicher zu verwenden. Diese Funktion ist für Hardwareaktualisierungen innerhalb desselben Clusters nützlich.

Weitere Informationen finden Sie unter [Kapazität für vCenter Server-Instanzen erweitern und verringern](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservers).

### Aktualisierungen für Richtlinienkonfigurationen
{: #relnotes_v31-policy-config}

Die Länge des generierten vCenter-Kennworts für primäre vCenter Server-Instanzen beträgt jetzt 15 Zeichen; für die Konfiguration des Kennworts und der Sperrrichtlinie gelten die folgenden Regeln:

* Die Mindestlänge für die vCenter-Kennwortrichtlinie beträgt jetzt 15 Zeichen.
* Die vCenter-Sperrrichtlinie ermöglicht jetzt maximal 3 fehlgeschlagene Anmeldeversuche.
* Die vCenter-Sperrrichtlinie ermöglicht jetzt ein zweites Zeitintervall von 900 Sekunden zwischen Fehlern.

Die Länge des generierten NSX Manager-Kennworts für primäre vCenter Server-Instanzen beträgt jetzt 15 Zeichen. Vorher betrug die Länge des generierten Kennworts acht Zeichen.

 Weitere Informationen finden Sie unter [Konformitätsinformationen für vCenter Server-Instanzen](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_compl_info#vc_compl_info-default-policy-config).

## Updates für Add-on-Services
{: #relnotes_v31-services}

### Caveonix RiskForesight on IBM Cloud
{: #relnotes_v31-services-caveonix}

Vom aktuellen Release wird Caveonix RiskForesight 2.2.1 auf allen neu bereitgestellten Instanzen installiert. Weitere Informationen zu Caveonix RiskForesight finden Sie auf der [Caveonix-Website](https://www.caveonix.com/){:external}.

### Automatische Verlängerung von HyTrust-Lizenzen
{: #relnotes_v31-services-ht}

Von {{site.data.keyword.vmwaresolutions_short}} wird jetzt Unterstützung für die automatische Verlängerung von HyTrust-Lizenzen bereitgestellt, für die die Call-Home-Funktion aktiviert ist. Diese Unterstützung wird ab den folgenden Versionen bereitgestellt:

* HyTrust CloudControl 5.5.1 und höher
* HyTrust DataControl 4.3.2 und höher
* HyTrust KeyControl 4.3.2 und höher

Sie müssen das Verfahren zum Aktivieren des Internetzugriffs für die virtuellen HyTrust-Maschinen ausführen, um die automatische Erneuerung Ihrer Lizenz sicherzustellen. Wenn Sie diese Prozedur nicht ausführen läuft Ihre Lizenz weiterhin jährlich ab.
{:important}

Weitere Informationen finden Sie in den folgenden Abschnitten:

* [Internetzugang für virtuelle HyTrust CloudControl-Maschinen aktivieren](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtcc#managinghtcc-internet-access)
* [Internetzugang für virtuelle HyTrust DataControl-Maschinen aktivieren](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtdc#managinghtdc-internet-access)
* [Internetzugang für virtuelle HyTrust KeyControl-Maschinen aktivieren](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtkc#managinghtkc-internet-access)

### Veeam on IBM Cloud
{: #relnotes_v31-services-veeam}

Im aktuellen Release wird Veeam Availability Suite 9.5 auf allen neu bereitgestellten Instanzen installiert. Darüber hinaus werden mehrere Aktualisierungen an den Veeam-VSIs und Veeam-Konfigurationsrepositorys vorgenommen. Weitere Informationen enthält der Abschnitt [Veeam on {{site.data.keyword.cloud_notm}} - Übersicht](/docs/services/vmwaresolutions?topic=vmware-solutions-veeam_considerations).

### Zerto on IBM Cloud
{: #relnotes_v31-services-zerto}

Bei neuen Instanzen, die ab Version 3.1 bereitgestellt werden, ist für Installationen von 'Zerto on {{site.data.keyword.cloud_notm}}' ein gebührenpflichtiges {{site.data.keyword.cloud_notm}}-Konto erforderlich. Für die Kosten der VM-Replikation wird jetzt ein kostenpflichtiger {{site.data.keyword.cloud_notm}}-Plan anstatt einer Abrechnung über die {{site.data.keyword.cloud_notm}}-Infrastruktur verwendet.

Damit Sie 'Zerto on {{site.data.keyword.cloud_notm}}' bestellen können, muss Ihr {{site.data.keyword.cloud_notm}}-Konto die folgenden Voraussetzungen erfüllen. Wenn Sie über eine vorhandene Installation von 'Zerto on {{site.data.keyword.cloud_notm}}' verfügen, können Sie den Abrechnungstyp für Zerto-VMs in ein kostenpflichtiges Konto umwandeln. Weitere Informationen hierzu finden Sie unter [Abrechnung für Zerto-Replikation](/docs/services/vmwaresolutions?topic=vmware-solutions-zerto_ordering#zerto_ordering-billing).

## Neue und aktualisierte Dokumentation
{: #relnotes_v31-updated-doc}

* Die Managementereignisse und Ereignisse der Activity Tracker-Instanz für den Service 'KMIP for VMware on IBM Cloud' werden aktualisiert. Weitere Informationen finden Sie unter [Activity Tracker-Ereignisse](/docs/services/vmwaresolutions?topic=vmware-solutions-at-events).
* Die Referenzdokumentation zur Benutzer-ID wird unter Verwendung der Benutzer-IDs für die Installation und Konfiguration von Services durch die {{site.data.keyword.cloud_notm}}-Serviceautomatisierung aktualisiert. Weitere Informationen finden Sie im Abschnitt *Servicebenutzer-ID* in [IBM Benutzer-IDs](/docs/services/vmwaresolutions?topic=vmware-solutions-audit_user_ids).
* Für die neue API ``Detaillierte Netzschnittstelle eines Clusters abrufen`` steht Referenzdokumentation zur Verfügung. Weitere Informationen finden Sie in [API-Referenz](https://cloud.ibm.com/apidocs/vmware-solutions){:external}.
* Die folgenden technischen Dokumente im Abschnitt *Referenz* der Benutzerdokumentation sind neu:
  * [Operations Management](/docs/services/vmwaresolutions?topic=vmware-solutions-opsmgmt-intro)
  * [Tag 2 - Betriebsprozesse](/docs/services/vmwaresolutions?topic=vmware-solutions-opsprocs-intro)

## Updates und Erweiterungen der Benutzerschnittstelle
{: #relnotes_v31-ui}

Die Benutzerschnittstelle wurde aktualisiert und bietet die folgenden Erweiterungen:
* Auf der Detailseite **Cluster** wird jetzt der Speichertyp angezeigt, der vom Cluster verwendet wird.
* Es sind verschiedene Fehlernachrichten und QuickInfos verfügbar, die Sie bei der Auswahl der geeigneten Einstellung in der Benutzerschnittstelle unterstützen.
