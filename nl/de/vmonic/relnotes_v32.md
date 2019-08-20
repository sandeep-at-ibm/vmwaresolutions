---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-06"

keywords: release notes, what's new, version 3.2

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Releaseinformationen für Version 3.2
{: #relnotes_v32}

Dieses Release stellt neue Funktionen, Komponentenaktualisierungen, Verbesserungen des Bedienungskomforts und Fehlerkorrekturen zur Verfügung. Eine Liste mit den in den unterschiedlichen Releases behobenen Problemen, den bekannten Problemen beim Produkt sowie Tipps für die Verwendung von {{site.data.keyword.vmwaresolutions_full}} finden Sie unter [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:external}.

## VMware HCX for IBM Cloud - Verfügbarkeit
{: #relnotes_v32-HCX}

Ab Release 3.2 haben Sie nun die Option, den VMware HCX on {{site.data.keyword.cloud_notm}}-Service mit VMware vCenter Server-Instanzen zu bestellen. Zuvor konnten Sie den HCX {{site.data.keyword.cloud_notm}}-Service nur über die VMware vCenter Server with Hybridity Bundle-Instanz bestellen. Die vCenter Server with Hybridity Bundle-Instanz ist nicht mehr verfügbar.

Für die Bestellung des HCX on {{site.data.keyword.cloud_notm}}-Service ist eine Verpflichtung über 12 Monate erforderlich. Nach Ablauf der 12-monatigen Verpflichtung können Sie den HCX on {{site.data.keyword.cloud_notm}}-Service installieren und deinstallieren sowie Hosts und Cluster ohne Einschränkungen hinzufügen und entfernen. Ihr Konto wird dann auf monatlicher Basis belastet und kann jederzeit storniert werden.

Weitere Informationen enthält der Abschnitt [VMware HCX on IBM Cloud - Übersicht](/docs/services/vmwaresolutions?topic=vmware-solutions-hcx_considerations).

## Unterstützung für VMware vSphere 6.7u2
{: #relnotes_v32-vsphere-v67}

Sie haben nun die Möglichkeit, VMware vSphere Version 6.7u2 mit Ihren VMware vCenter Server-, VMware vCenter Server with NSX-T- und VMware vSphere on IBM Cloud-Instanzen zu bestellen. vSphere Enterprise Plus 6.7u2 ersetzt die Option zur Bestellung von vSphere Enterprise Plus 6.7 Update 1 mit neuen Instanzen. Zudem werden Single-node Trial-Instanzen für Migration und Anwendungsmodernisierung und Single-node Trial-Instanzen für Datenschutz und Disaster-Recovery jetzt mit vSphere Enterprise Plus 6.7u2 bestellt.

vSphere Enterprise Plus 6.7u2 ist verfügbar für Skylake, Cascade Lake und Broadwell {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}.

Wenn Sie über eine vorhandene Instanz mit vSphere Enterprise Plus 6.7 Update 1 verfügen, können Sie neue Hosts entweder mit vSphere Enterprise Plus 6.7 Update 1 oder mit vSphere Enterprise Plus 6.7u2 hinzufügen. Das Hinzufügen eines neuen 6.7 Update 1-Hosts ist jedoch unsicher. Es wird empfohlen, die Hosts so bald wie möglich auf die neueste ESXi-Serverversion zu aktualisieren.{:note}

## Unterstützung für Cascade Lake
{: #relnotes_v32-cascade}

Ab Release V3.2 stehen die folgenden neuen {{site.data.keyword.baremetal_short_sing}}-CPU-Modelle zur Bereitstellung mit Instanzen und Clustern mit VMware vSphere 6.7u2 zur Verfügung. Dies gilt für vCenter Server, vCenter Server with NSX-T und VMware vSphere.

* Dual Intel Xeon Gold 4210-Prozessor / 20 Kerne insgesamt, 2,3 GHz
* Dual Intel Xeon Gold 5218-Prozessor / 32 Kerne insgesamt, 2,3 GHz
* Dual Intel Xeon Gold 6248-Prozessor / 40 Kerne insgesamt, 2,5 GHz

Cascade Lake-{{site.data.keyword.baremetal_short}} sind in Mehrzonen-Regionen (MZR)-{{site.data.keyword.CloudDataCents_notm}} verfügbar. Weitere Informationen finden Sie in [Mehrzonen-Region (MZR) - Übersicht
](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-multi-zone-region-mzr-overview).

Weitere Informationen zu den {{site.data.keyword.baremetal_short_sing}}-Einstellungen finden Sie unter:

* [vCenter Server-Instanzen bestellen](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_orderinginstance#vc_orderinginstance-cascade)
* [vCenter Server with NSX-T-Instanzen bestellen](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_nsx-t_orderinginstance#vc_nsx-t_orderinginstance-cascade)
* [Neue vSphere-Cluster bestellen](/docs/services/vmwaresolutions?topic=vmware-solutions-vs_orderinginstances#vs_orderinginstance-cascade)

## Updates für VMware vCenter Server-Instanzen
{: #relnotes_v32-vcs}

Mit diesem Release werden die folgenden Upgrades und Verbesserungen für neu bereitgestellte Instanzen, Cluster und Hosts angewendet:

* VMware NSX for vSphere 6.4.5 (Build 13282012)
* vSphere ESXi 6.7 EP 10 (Build 6.7.0-13981272)
* vCenter Server Appliance 6.7u2b (6.7.0.-13843469)
* Platform Services Controller 6.7u2b (6.7.0.-13843469)

Weitere Informationen Sie in der [vCenter Server-Teileliste](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom).

### Anfängliche Clusterbenennung
{: #relnotes_v32-vcs-initial-cluster}

Sie können jetzt den Namen Ihres anfänglichen Clusters angeben, der gleichzeitig mit der Festlegung Ihrer Instanzreihenfolge erstellt werden soll. Weitere Informationen finden Sie in den folgenden Abschnitten:

* [vCenter Server-Instanzen bestellen](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_orderinginstance)
* [vCenter Server with NSX-T-Instanzen bestellen](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_nsx-t_orderinginstance)

## Aktualisierungen für for VMware vSphere-Instanzen
{: #relnotes_v32-vss}

Beim Bestellen eines neuen vSphere-Clusters nur mit privatem Netz ist kein öffentliches VLAN mehr erforderlich.

Weitere Informationen finden Sie im Abschnitt *Netzschnittstelleneinstellungen* in [Neue vSphere-Cluster bestellen
](/docs/services/vmwaresolutions?topic=vmware-solutions-vs_orderinginstances#vs_orderinginstances-network-interface-settings).

## Updates für Add-on-Services
{: #relnotes_v32-services}

Mit diesem Release werden die folgenden Servicversionen für neu bereitgestellte Instanzen installiert:

* F5 on {{site.data.keyword.cloud_notm}} 15.0.0
* Veeam on {{site.data.keyword.cloud_notm}} 9.5 Update 4b
* VMware HCX on {{site.data.keyword.cloud_notm}} 3.5.1-14222959
* Zerto on {{site.data.keyword.cloud_notm}} 6.5 Update 4

### VMware vRealize Operations und vRealize Log Insight on IBM Cloud
{: #relnotes_v32-services-vrealize}

Der Service für vRealize Operations und vRealize Log Insight on {{site.data.keyword.cloud_notm}} ist jetzt für VMware vCenter Server-Instanzen verfügbar, die in Version 3.2 oder späteren Releases bereitgestellt oder darauf aktualisiert wurden.

Dieser Service stellt VMware vRealize Log Insight (vRLI) bereit, das mit vRealize Operations Manager (vROps) integriert ist, um Ihnen zu helfen, den Betrieb und die Leistung Ihrer virtualisierten Umgebung zu überwachen und proaktiv zu verwalten sowie um Ursachenanalysen von Problemen durch Filtern und Durchsuchen von Protokollen durchzuführen.

Sie können vCenter Server-Instanzen mit enthaltenem vRealize Operations und vRealize Log Insight on {{site.data.keyword.cloud_notm}} bestellen oder diesen Service zu einem späteren Zeitpunkt über die Registerkarte "Services" auf der Instanzdetailseite zu Ihren vorhandenen Instanzen hinzufügen.

Sie können auch die vRealize Operations- und vRealize Log Insight-Lizenzen Ihres Unternehmens in die Cloud (je CPU oder OSI) bringen oder Lizenzen von IBM Cloud mieten.

Weitere Informationen finden Sie unter [VMware vRealize Operations und vRealize Log Insight on {{site.data.keyword.cloud_notm}} - Übersicht](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vrops_overview).

## Neue und aktualisierte Dokumentation
{: #relnotes_v32-updated-doc}

* Die Dokumentation zu Activity Tracker wird aktualisiert. Weitere Informationen finden Sie unter [Activity Tracker-Ereignisse](/docs/services/vmwaresolutions?topic=vmware-solutions-at-events).

## Updates und Erweiterungen der Benutzerschnittstelle
{: #relnotes_v32-ui}

Die Benutzerschnittstelle wurde aktualisiert und bietet die folgenden Erweiterungen:

* Die Anforderungen an Instanznamen wurden geändert. Weitere Informationen finden Sie in dem entsprechenden Thema für den Instanztyp, den Sie bestellen.
* Das Format des vollständig qualifizierten ESXi-Servers wurde geändert. Weitere Informationen finden Sie in dem entsprechenden Thema für den Instanztyp, den Sie bestellen.
* Es wurden führende Nullen zu Host- und Clusternamen hinzugefügt, um eine ordnungsgemäße Sortierung zu ermöglichen.
* Es sind verschiedene Fehlernachrichten und QuickInfos verfügbar, die Sie bei der Auswahl der geeigneten Einstellung in der Benutzerschnittstelle unterstützen.
