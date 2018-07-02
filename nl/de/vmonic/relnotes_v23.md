---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-28"

---

# Releaseinformationen für V2.3

Dieses Release stellt neue Funktionen, Komponentenaktualisierungen, Verbesserungen des Bedienungskomforts und Fehlerkorrekturen zur Verfügung. Eine Liste mit den in den unterschiedlichen Releases behobenen Problemen, den bekannten Problemen beim Produkt sowie zusätzlichen Tipps für die Verwendung von {{site.data.keyword.vmwaresolutions_full}} finden Sie unter [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Korrektur für Spectre und Meltdown

{{site.data.keyword.vmwaresolutions_short}} hat als Reaktion auf Sicherheitslücken, die unter den Begriffen "Spectre" und "Meltdown" bekannt sind, Patches aus VMware freigegeben (CVE-2017-5753, CVE-2017-5715 und CVE-2017-5754).

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

Weitere Informationen enthält der Abschnitt [Gegenmaßnahmen für Sicherheitslücken "Spectre" und "Meltdown"](../vmonic/trbl_fix_spectre.html).

## VMware vCenter Server on IBM Cloud with Hybridity Bundle

In diesem Release wird das VMware vCenter Server on IBM Cloud with Hybridity Bundle-Angebot eingeführt. Das vCenter Server with Hybridity Bundle ist eine gehostete private Cloud und unterstützt Sie bei der schnellen und einfachen Erweiterung Ihrer lokalen Infrastruktur in die Cloud. Die VMware-Umgebung basiert auf von IBM bereitgestellten VMware Software Defined Data Center-Lizenzen und umfasst den Service "VMware HCX on {{site.data.keyword.cloud_notm}}" zur einfachen und sicheren Verbindung einer lokalen vSphere 5.0+-Umgebung mit IBM Cloud-Standorten zur Erreichung einer reibungslosen Hybridität der Infrastruktur und einer realen Anwendungsmobilität.

Der Service "HCX on {{site.data.keyword.cloud_notm}}" steht nur über die vCenter Server with Hybridity Bundle-Instanz zur Verfügung. Sie können für Ihre vorhandene vCenter Server-Instanz ein Upgrade auf eine vCenter Server with Hybridity Bundle-Instanz durchführen, nachdem Sie das Basis-Software-Update für vCenter Server V2.3 angewendet haben. Weitere Informationen enthält der Abschnitt [Updates auf vCenter Server-Instanzen anwenden](../vcenter/vc_applyingupdates.html#applying-updates-to-vcenter-server-instances.html).

Weitere Informationen zu vCenter Server with Hybridity Bundle finden Sie in:

* [Überblick zu vCenter Server with Hybridity Bundle](../vcenter/vc_hybrid_overview.html)
* [Voraussetzungen und Planung für vCenter Server with Hybridity Bundle-Instanzen](../vcenter/vc_hybrid_planning.html)
* [vCenter Server with Hybridity Bundle-Instanzen bestellen](../vcenter/vc_hybrid_orderinginstance.html)

## Clusterunterstützung für vCenter Server- und Cloud Foundation-Instanzen löschen

Sie können Cluster nun aus einer Instanz löschen, ohne dass hierzu die gesamte Instanz gelöscht werden muss. Für Cluster, die in Instanzen mit V2.2 oder älteren Releases bereitgestellt wurden, müssen Sie ein Upgrade der Instanz auf V2.3 durchführen, um die Cluster löschen zu können, die Sie zu der Instanz hinzugefügt haben.

Weitere Informationen enthalten die folgenden Abschnitte:

* [Cluster für vCenter Server-Instanzen hinzufügen, anzeigen und löschen](../vcenter/vc_addingviewingclusters.html#deleting-clusters-from-vcenter-server-instances)
* [Cluster für Cloud Foundation-Instanzen hinzufügen, anzeigen und löschen](../sddc/sd_addingviewingclusters.html#deleting-clusters-from-cloud-foundation-instances)

## Updates für VMware vCenter Server-Instanzen

Mit diesem Release werden die folgenden Upgrades und Verbesserungen angewendet:
*	VMware vSphere ESXi 6.5 U1g (ESXi 6.5u1 mit angewendetem Patch-Level ESXi650-201803001)
*	VMware vCenter Server 6.5 Update 1g

### Erweiterungen für vCenter Server-Instanzen und -Cluster

Ab Release V2.3 stehen die folgenden neuen CPU-Modelle für die Bereitstellung zur Verfügung, wenn Sie die Bare-Metal-Einstellung **Angepasst** auswählen:
* Dual Intel Xeon Silver 4110-Prozessor / 16 Kerne insgesamt, 2,1 GHz
* Dual Intel Xeon Gold 5120-Prozessor / 28 Kerne insgesamt, 2,2 GHz

Weitere Informationen enthalten die folgenden Abschnitte:

* [vCenter Server-Instanzen bestellen](../vcenter/vc_orderinginstance.html)
* [Cluster für vCenter Server-Instanzen hinzufügen, anzeigen und löschen](../vcenter/vc_addingviewingclusters.html)

## Updates für VMware Cloud Foundation-Instanzen

Mit diesem Release werden die folgenden Upgrades und Verbesserungen angewendet:
*	VMware vSphere ESXi 6.5 U1g (ESXi 6.5u1 mit angewendetem Patch-Level ESXi650-201803001)
*	VMware vCenter Server 6.5 Update 1g
*	VMware NSX for vSphere 6.3.5

## Updates für VMware Federal-Instanzen

### DNS-Konfiguration für VMware Federal-Instanzen

Sie haben jetzt die Möglichkeit, die Bereitstellung einer einzigen Virtual Server-Instanz (VSI) von Microsoft Windows für Microsoft Active Directory (AD) oder aber zwei virtuelle Microsoft Windows-Maschinen für die Hochverfügbarkeit im Management-Cluster auszuwählen. Für V2.2 wurde die einzelne Microsoft Windows-VSI für Microsoft AD standardmäßig automatisch bereitgestellt. Die neue Option zur Auswahl von zwei virtuellen Microsoft Windows-Maschinen bietet mehr Datenschutz und die Möglichkeit, die virtuellen Maschinen mit dem Veeam-Service zu sichern und wiederherzustellen.

**Hinweis:** Sie müssen zwei Lizenzen für Microsoft Windows Server 2012 R2 bereitstellen, wenn Sie Ihre Instanz für die Verwendung der beiden virtuellen Microsoft Windows-Maschinen konfigurieren. Verwenden Sie die Lizenz für Microsoft Windows Server 2012 R2 Standard Edition und/oder die Lizenz für Microsoft Windows Server 2012 R2 Datacenter Edition. Sie haben 30 Tage Zeit, um die virtuellen Maschinen zu aktivieren.

Weitere Informationen finden Sie unter *Netzschnittstelleneinstellungen* im Abschnitt [VMware Federal-Instanzen bestellen](../vcenter/vc_fed_orderinginstance.html#network-interface-settings).

### Clusterunterstützung für VMware Federal-Instanzen hinzufügen und löschen

Sie können jetzt ESXi-Server in VMware Federal-Instanzen, die in V2.3 und höheren Releases bereitgestellt werden, mithilfe von Clustern verwalten und so ein besseres Ressourcenmanagement und eine hohe Verfügbarkeit erreichen. Die ESXi-Server, die Sie bei der Bestellung einer Instanz konfiguriert haben, werden standardmäßig unter **cluster1** gruppiert. Auf der Seite mit der Instanzübersicht können Sie die Clusterdetails anzeigen oder bis zu insgesamt zehn Cluster zu einer Instanz hinzufügen. Wenn Sie die Kapazität für eine Instanz erweitern oder verringern, können Sie auswählen, in welchem Cluster ESXi-Server hinzugefügt oder entfernt werden sollen.

Sie haben auch die Möglichkeit, einzelne oder mehrere Cluster aus einer Instanz zu löschen, ohne dass hierzu die gesamte Instanz gelöscht werden muss.

Weitere Informationen finden Sie unter [Cluster für VMware Federal-Instanzen hinzufügen, anzeigen und löschen](../vcenter/fed_addviewdeleteclusters.html).

## Updates für Add-on-Services

### HyTrust CloudControl on IBM Cloud

Der Service "HyTrust CloudControl on {{site.data.keyword.cloud_notm}}" ist nun für VMware Cloud Foundation-Instanzen und VMware vCenter Server-Instanzen verfügbar, auf denen vSphere 6.5 ausgeführt wird und die in V2.3 oder höheren Releases bereitgestellt werden oder für die ein Upgrade auf diese Releases durchgeführt wurde. Der Service erzwingt und steuert die Einhaltung der Sicherheitsstandards und stellt die rollenbasierte Zugriffssteuerung (RBAC = Role-Based Access Control) bereit. In Kombination mit HyTrust DataControl kann der Service sicherstellen, dass virtuelle Maschinen und Workloaddaten eine bestimmte Region, einen bestimmten Cluster oder einen bestimmten ESXi-Server innerhalb des {{site.data.keyword.cloud_notm}}-Rechenzentrums nicht verlassen.

Sie können Instanzen bestellen, die den Service enthalten, oder diesen Service später zu Ihren vorhandenen Instanzen hinzufügen.

Weitere Informationen enthalten die folgenden Abschnitte:
* [Komponenten und Hinweise für HyTrust CloudControl on IBM Cloud](../services/htcc_considerations.html)
* [HyTrust CloudControl on IBM Cloud verwalten](../services/managinghtcc.html)

### HyTrust DataControl on IBM Cloud

Der Service "HyTrust DataControl on {{site.data.keyword.cloud_notm}}" ist nun für VMware Cloud Foundation-Instanzen und VMware vCenter Server-Instanzen verfügbar, auf denen vSphere 6.5 ausgeführt wird und die in V2.3 oder höheren Releases bereitgestellt werden oder für die ein Upgrade auf diese Releases durchgeführt wurde. Der Service bietet eine starke Verschlüsselung mit integriertem Schlüsselmanagement, um Workloads über ihren gesamten Lebenszyklus hinweg zu sichern. Der Service kann die Verschlüsselung sowohl auf Betriebssystemebene als auch auf Datenebene bereitstellen. Dies bedeutet, dass alle Verzeichnisse, Ordner oder Dateien innerhalb einer Workload ver- und entschlüsselt werden können.

Sie können Instanzen bestellen, die den Service enthalten, oder diesen Service später zu Ihren vorhandenen Instanzen hinzufügen.

Weitere Informationen enthalten die folgenden Abschnitte:
* [Komponenten und Hinweise für HyTrust DataControl on IBM Cloud](../services/htdc_considerations.html)
* [HyTrust DataControl on IBM Cloud verwalten](../services/managinghtdc.html)

### IBM Spectrum Protect Plus on IBM Cloud

Das aktuelle Release installiert IBM Spectrum Protect&trade; Plus V10.1.1 als den standardmäßigen Sicherungsservice auf allen neu bereitgestellten Instanzen. Informationen zu den neuen Funktionen in IBM Spectrum Protect Plus V10.1.1 finden Sie unter [Updates für IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.1/spp/r_techchg_spp.html){:new_window}.

## Neue und aktualisierte Dokumentation

Eine neue developerWorks-Anleitung ist verfügbar, die Schritt für Schritt erläutert, wie Speicher zu IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} nach der Bereitstellung hinzugefügt werden kann. Weitere Informationen finden Sie unter [Speicher zu IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} nach der Bereitstellung hinzufügen](https://developer.ibm.com/recipes/tutorials/how-to-increase-vsnap-storage-for-ibm-spectrum-protect-plus-on-ibm-cloud-post-deployment/).

## Updates und Erweiterungen der Benutzerschnittstelle

Die Benutzerschnittstelle wurde aktualisiert und bietet die folgenden Erweiterungen:
* **Konsistenz**: Die Benutzerschnittstelle bietet nun eine konsistente Darstellung und Funktionsweise in Bezug auf andere Services in IBM Cloud.
* **Einfacher Zugriff**: Sie können nun auf die VMware-Angebote direkt über den **Katalog** von IBM Cloud zugreifen.
* **Optimiertes und vereinfachtes Bestellverfahren**: Sie können die Bestellung einer VMware-Instanz und die Bereitstellung der entsprechenden Add-on-Services nun über eine einzige Schnittstelle durchführen. Darüber hinaus werden die geschätzten Kosten berechnet und sofort in derselben Schnittstelle angezeigt, sodass Sie Ihre Konfiguration auf Basis Ihres Kostenplans anpassen können.
* Die BYOL-Option (BYOL = Bring Your Own License) beim Bestellen von Instanzen oder Hinzufügen von Clustern steht für Benutzer der Kategorie "Business Partner" nicht zur Verfügung.
* Verschiedene Fehlernachrichten und QuickInfos wurden erweitert, um Ihnen bei der Auswahl der geeigneten Einstellung in der Benutzerschnittstelle zu helfen.
