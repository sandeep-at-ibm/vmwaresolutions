---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-28"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Releaseinformationen für V2.3
{: #relnotes_v23}

Dieses Release stellt neue Funktionen, Komponentenaktualisierungen, Verbesserungen des Bedienungskomforts und Fehlerkorrekturen zur Verfügung. Eine Liste mit den in den unterschiedlichen Releases behobenen Problemen, den bekannten Problemen beim Produkt sowie Tipps für die Verwendung von {{site.data.keyword.vmwaresolutions_full}} finden Sie unter [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Korrektur für Spectre und Meltdown

{{site.data.keyword.vmwaresolutions_short}} hat als Reaktion auf Sicherheitslücken, die unter den Begriffen "Spectre" und "Meltdown" bekannt sind, Patches aus VMware freigegeben (CVE-2017-5753, CVE-2017-5715 und CVE-2017-5754).

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

Weitere Informationen enthält der Abschnitt [Gegenmaßnahmen für Sicherheitslücken "Spectre" und "Meltdown"](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_fix_spectre).

## VMware vCenter Server on IBM Cloud with Hybridity Bundle

In diesem Release wird das VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle-Angebot eingeführt. Das vCenter Server with Hybridity Bundle ist eine gehostete private Cloud und unterstützt Sie bei der schnellen und einfachen Erweiterung Ihrer lokalen Infrastruktur in die Cloud. Die VMware-Umgebung basiert auf von IBM bereitgestellten VMware Software Defined Data Center-Lizenzen und umfasst den Service "VMware HCX on {{site.data.keyword.cloud_notm}}" zur einfachen und sicheren Verbindung einer lokalen vSphere 5.0+-Umgebung mit {{site.data.keyword.cloud_notm}}-Standorten zur Erreichung einer reibungslosen Hybridität der Infrastruktur und einer realen Anwendungsmobilität.

Der Service "HCX on {{site.data.keyword.cloud_notm}}" steht nur über die vCenter Server with Hybridity Bundle-Instanz zur Verfügung. Sie können für Ihre vorhandene vCenter Server-Instanz ein Upgrade auf eine vCenter Server with Hybridity Bundle-Instanz durchführen, nachdem Sie das Basis-Software-Update für vCenter Server V2.3 angewendet haben. Weitere Informationen enthält der Abschnitt [Updates auf vCenter Server-Instanzen anwenden](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_applyingupdates).

Weitere Informationen zu vCenter Server with Hybridity Bundle finden Sie in den folgenden Abschnitten:

* [Übersicht über vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_overview)
* [Voraussetzungen und Planung für vCenter Server with Hybridity Bundle-Instanzen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_planning)
* [vCenter Server with Hybridity Bundle-Instanzen bestellen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance)

## Clusterunterstützung für vCenter Server- und Cloud Foundation-Instanzen löschen

Sie können Cluster nun aus einer Instanz löschen, ohne dass hierzu die gesamte Instanz gelöscht werden muss. Für Cluster, die in Instanzen mit V2.2 oder älteren Releases bereitgestellt wurden, müssen Sie ein Upgrade der Instanz auf V2.3 durchführen, um die Cluster löschen zu können, die Sie zu der Instanz hinzugefügt haben.

Weitere Informationen finden Sie in den folgenden Abschnitten:

* [Cluster für vCenter Server-Instanzen hinzufügen, anzeigen und löschen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-adding-and-viewing-clusters-for-vcenter-server-instances#deleting-clusters-from-vcenter-server-instances)
* [Cluster für Cloud Foundation-Instanzen hinzufügen, anzeigen und löschen](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-adding-and-viewing-clusters-for-cloud-foundation-instances#deleting-clusters-from-cloud-foundation-instances)

## Updates für VMware vCenter Server-Instanzen

Mit diesem Release werden die folgenden Upgrades und Verbesserungen angewendet:
*	VMware vSphere ESXi 6.5 U1g (ESXi 6.5u1 mit angewendetem Patch-Level ESXi650-201803001)
*	VMware vCenter Server 6.5 Update 1g

### Erweiterungen für vCenter Server-Instanzen und -Cluster

Ab Release V2.3 stehen die folgenden neuen CPU-Modelle für die Bereitstellung zur Verfügung, wenn Sie die Bare-Metal-Einstellung **Angepasst** auswählen:
* Dual Intel Xeon Silver 4110-Prozessor / 16 Kerne insgesamt, 2,1 GHz
* Dual Intel Xeon Gold 5120-Prozessor / 28 Kerne insgesamt, 2,2 GHz

Weitere Informationen finden Sie in den folgenden Abschnitten:

* [vCenter Server-Instanzen bestellen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [Cluster für vCenter Server-Instanzen hinzufügen, anzeigen und löschen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-adding-and-viewing-clusters-for-vcenter-server-instances)

## Updates für VMware Cloud Foundation-Instanzen

Mit diesem Release werden die folgenden Upgrades und Verbesserungen angewendet:
*	VMware vSphere ESXi 6.5 U1g (ESXi 6.5u1 mit angewendetem Patch-Level ESXi650-201803001)
*	VMware vCenter Server 6.5 Update 1g
*	VMware NSX for vSphere 6.3.5

## Updates für Add-on-Services

### HyTrust CloudControl on IBM Cloud

Der Service "HyTrust CloudControl on {{site.data.keyword.cloud_notm}}" ist nun für VMware Cloud Foundation-Instanzen und VMware vCenter Server-Instanzen verfügbar, auf denen vSphere 6.5 ausgeführt wird und die in V2.3 oder höheren Releases bereitgestellt werden oder für die ein Upgrade auf diese Releases durchgeführt wurde. Der Service erzwingt und steuert die Einhaltung der Sicherheitsstandards und stellt die rollenbasierte Zugriffssteuerung (RBAC = Role-Based Access Control) bereit. In Kombination mit HyTrust DataControl kann der Service sicherstellen, dass virtuelle Maschinen und Workloaddaten eine bestimmte Region, einen bestimmten Cluster oder einen bestimmten ESXi-Server innerhalb des {{site.data.keyword.cloud_notm}}-Rechenzentrums nicht verlassen.

Sie können Instanzen bestellen, die den Service enthalten, oder diesen Service später zu Ihren vorhandenen Instanzen hinzufügen.

Weitere Informationen finden Sie in den folgenden Abschnitten:
* [Komponenten und Hinweise für HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_considerations)
* [HyTrust CloudControl on {{site.data.keyword.cloud_notm}} verwalten](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtcc)

### HyTrust DataControl on IBM Cloud

Der Service "HyTrust DataControl on {{site.data.keyword.cloud_notm}}" ist nun für VMware Cloud Foundation-Instanzen und VMware vCenter Server-Instanzen verfügbar, auf denen vSphere 6.5 ausgeführt wird und die in V2.3 oder höheren Releases bereitgestellt werden oder für die ein Upgrade auf diese Releases durchgeführt wurde. Der Service bietet eine starke Verschlüsselung mit integriertem Schlüsselmanagement, um Workloads über ihren gesamten Lebenszyklus hinweg zu sichern. Der Service kann die Verschlüsselung sowohl auf Betriebssystemebene als auch auf Datenebene bereitstellen. Dies bedeutet, dass alle Verzeichnisse, Ordner oder Dateien innerhalb einer Workload ver- und entschlüsselt werden können.

Sie können Instanzen bestellen, die den Service enthalten, oder diesen Service später zu Ihren vorhandenen Instanzen hinzufügen.

Weitere Informationen finden Sie in den folgenden Abschnitten:
* [Komponenten und Hinweise für HyTrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_considerations)
* [HyTrust DataControl on {{site.data.keyword.cloud_notm}} verwalten](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtdc)

### IBM Spectrum Protect Plus on IBM Cloud

Das aktuelle Release installiert IBM Spectrum Protect&trade; Plus V10.1.1 als den standardmäßigen Sicherungsservice auf allen neu bereitgestellten Instanzen. Weitere Informationen zu den neuen Funktionen in IBM Spectrum Protect Plus V10.1.1 finden Sie unter [Updates für IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.1/spp/r_techchg_spp.html){:new_window}.

## Neue und aktualisierte Dokumentation

Eine neue developerWorks-Anleitung ist verfügbar, die Schritt für Schritt erläutert, wie Speicher zu IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} nach der Bereitstellung hinzugefügt werden kann. Weitere Informationen finden Sie unter [Speicher zu IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} nach der Bereitstellung hinzufügen](https://developer.ibm.com/recipes/tutorials/how-to-increase-vsnap-storage-for-ibm-spectrum-protect-plus-on-ibm-cloud-post-deployment/).

## Updates und Erweiterungen der Benutzerschnittstelle

Die Benutzerschnittstelle wurde aktualisiert und bietet die folgenden Erweiterungen:
* **Konsistenz**: Die Benutzerschnittstelle bietet nun eine konsistente Darstellung und Funktionsweise in Bezug auf andere Services in {{site.data.keyword.cloud_notm}}.
* **Einfacher Zugriff**: Sie können nun auf die VMware-Angebote direkt über den **Katalog** von {{site.data.keyword.cloud_notm}} zugreifen.
* **Optimiertes und vereinfachtes Bestellverfahren**: Sie können die Bestellung einer VMware-Instanz und die Bereitstellung der entsprechenden Add-on-Services nun über eine einzige Schnittstelle durchführen. Darüber hinaus werden die geschätzten Kosten berechnet und sofort in derselben Schnittstelle angezeigt, sodass Sie Ihre Konfiguration auf Basis Ihres Kostenplans anpassen können.
* Die BYOL-Option (BYOL = Bring Your Own License) beim Bestellen von Instanzen oder Hinzufügen von Clustern steht für Benutzer der Kategorie "Business Partner" nicht zur Verfügung.
* Es sind verschiedene Fehlernachrichten und QuickInfos verfügbar, die Sie bei der Auswahl der geeigneten Einstellung in der Benutzerschnittstelle unterstützen.
