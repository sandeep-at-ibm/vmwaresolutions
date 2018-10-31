---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-01"

---

# Releaseinformationen für V2.6

Dieses Release stellt neue Funktionen, Komponentenaktualisierungen, Verbesserungen des Bedienungskomforts und Fehlerkorrekturen zur Verfügung. Eine Liste mit den in den unterschiedlichen Releases behobenen Problemen, den bekannten Problemen beim Produkt sowie Tipps für die Verwendung von {{site.data.keyword.vmwaresolutions_full}} finden Sie unter [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Korrektur für Spectre und Meltdown

{{site.data.keyword.vmwaresolutions_short}} hat als Reaktion auf Sicherheitslücken, die "Spectre" und "Meltdown" betreffen, Patches aus VMware freigegeben (CVE-2017-5753, CVE-2017-5715 und CVE-2017-5754).

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

Weitere Informationen enthält der Abschnitt [Gegenmaßnahmen für Sicherheitslücken "Spectre" und "Meltdown"](../vmonic/trbl_fix_spectre.html).

## Option "Hohe Leistung mit Intel Optane"

Dieses Release stellt die Option bereit, einen leistungsfähigen Cache für den vSAN-Speicher hinzuzufügen, wenn Sie eine neue Instanz bestellen oder wenn Sie nach der ersten Bereitstellung einen neuen vSAN-Cluster hinzufügen.

Diese Option ermöglicht Ihnen, die Anzahl der Speicherkapazitätsplatten von acht auf maximal zehn zu erhöhen.

Die Option "Hohe Leistung mit Intel Optane" steht nur für angepasste Konfigurationen mit Dual Intel Xeon Gold 5120-Prozessor bzw. Dual Intel Xeon Gold 6140-Prozessor zur Verfügung.

Weitere Informationen finden Sie in dem für Ihre Instanz oder Ihren Clustertyp entsprechenden Abschnitt zum Bestellen.

## Öffentliches oder privates Netz aktivieren

Sie können nun vCenter Server- und vCenter Server with Hybridity Bundle-Instanzen sowie VMware vSphere-Cluster bereitstellen, die eine für das öffentliche und private Netz aktivierte Schnittstellenkarte (NIC – Network Interface Card) oder eine nur für das private Netz aktivierte NIC haben. Diese Option ist auch verfügbar, wenn Sie Ihrer vCenter Server- bzw. vCenter Server with Hybridity Bundle-Instanz einen neuen Cluster hinzufügen.

Einige Add-on-Services benötigen öffentliche NICs und sind nicht verfügbar, wenn Sie das ausschließlich private Netz auswählen.

Weitere Informationen finden Sie unter _Netzschnittstelleneinstellungen_ in den folgenden Abschnitten:

* [vCenter Server-Instanzen bestellen](../vcenter/vc_orderinginstance.html#network-interface-settings)
* [vCenter Server with Hybridity Bundle-Instanzen bestellen](../vcenter/vc_hybrid_orderinginstance.html#network-interface-settings)
* [Neue vSphere-Cluster bestellen](../vsphere/vs_orderinginstances.html#network-interface-settings)

## ESXi-Server löschen

Sie können nun aus Ihrer vCenter Server-, vCenter Server with Hybridity Bundle- oder Ihrer Cloud Foundation-Instanz beliebige ESXi-Server löschen, wenn Sie die Mindestvoraussetzungen für Ihre Instanz erfüllen.

Weitere Informationen zu Voraussetzungen für ESXi-Server finden Sie in den folgenden Abschnitten:

* [Kapazität für vCenter Server-Instanzen erweitern und verringern](../vcenter/vc_addingremovingservers.html)
* [Kapazität für vCenter Server with Hybridity Bundle-Instanzen erweitern und verringern](../vcenter/vc_hybrid_addingremovingservers.html)
* [Kapazität für Cloud Foundation-Instanzen erweitern und verringern](../sddc/sd_addingremovingservers.html)

## Updates für VMware vCenter Server-Instanzen

Mit diesem Release werden die folgenden Upgrades und Verbesserungen angewendet:

* vSphere ESXi 6.5 Update 2c
* vCenter Server Appliance 6.5 Update 2c
* Platform Services Controller 6.5 Update 2c
* NSX for vSphere 6.4.1

## Updates für VMware vCenter Server with Hybridity Bundle-Instanzen

### Hybridity Bundle aus einer vCenter Server-Instanz entfernen

Sie können nun die Lizenz für Hybridity Bundle aus Ihrer vCenter Server-Instanz entfernen. Dazu müssen Sie die Schlüssel der VMware NSX- und VMware vSAN-Mietlizenzen in VMware vSphere Web Client durch Schlüssel eigener Lizenzen (BYOL – Bring Your Own License) ersetzen und ein Support-Ticket öffnen, um die Gebühren für die Mietlizenzen zu stornieren.

Weitere Informationen finden Sie in [Hybridity Bundle aus einer vCenter Server-Instanz entfernen](../vcenter/vc_hybrid_deletingbundle.html).

### Verfügbarkeit von vCenter Server with Hybridity Bundle

Business Partner können nun vCenter Server with Hybridity Bundle-Instanzen bestellen. Business Partner können für eine vorhandene vCenter Server-Instanz kein Upgrade auf eine vCenter Server with Hybridity Bundle-Instanz durchführen und sie können das Hybridity Bundle nicht aus einer vCenter Server with Hybridity Bundle-Instanz entfernen.

Weitere Informationen finden Sie in den folgenden Abschnitten:

* [Übersicht über vCenter Server with Hybridity Bundle](../vcenter/vc_hybrid_overview.html)
* [vCenter Server with Hybridity Bundle-Instanzen bestellen](../vcenter/vc_hybrid_orderinginstance.html)

## Updates für VMware Cloud Foundation-Instanzen

Mit diesem Release werden die folgenden Upgrades und Verbesserungen angewendet:

* vSphere ESXi 6.5 Update 2c
* vCenter Server Appliance 6.5 Update 2c
* Platform Services Controller 6.5 Update 2c
* NSX for vSphere 6.4.1

## Updates für Add-on-Services

### HyTrust KeyControl on IBM Cloud

Der Service "HyTrust KeyControl on {{site.data.keyword.cloud_notm}}" ist nun für VMware Cloud Foundation-Instanzen und VMware vCenter Server-Instanzen verfügbar, auf denen vSphere 6.5 ausgeführt wird und die in V2.5 oder höheren Releases bereitgestellt wurden oder für die ein Upgrade auf diese Releases durchgeführt wurde. Der Service vereinfacht das Management verschlüsselter Workloads durch Automatisierung und Vereinfachung des Lebenszyklus von Verschlüsselungsschlüsseln. Der Service kann mithilfe der FIPS 140-2-konformen Verschlüsselung ohne großen Aufwand skalierbare Verschlüsselungsschlüssel verwalten. Mithilfe dieses Service können Sie die Verschlüsselungsschlüssel aller virtuellen Maschinen und verschlüsselten Datenspeicher verwalten; darüber hinaus können Sie ihn skalieren, um in großen Bereitstellungen Tausende verschlüsselter Workloads zu unterstützen.

Sie können Instanzen bestellen, die den Service enthalten, oder diesen Service später zu Ihren vorhandenen Instanzen hinzufügen.

Weitere Informationen finden Sie in den folgenden Abschnitten:
* [Komponenten und Hinweise für HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](../services/htkc_considerations.html)
* [HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](../services/managinghtkc.html)

### HyTrust CloudControl on IBM Cloud

Das aktuelle Release installiert HyTrust CloudControl 5.4 auf allen neu bereitgestellten Instanzen. Weitere Informationen zu den neuen Funktionen in HyTrust CloudControl 5.4 finden Sie im [Satz mit der Onlinedokumentation für HyTrust CloudControl v 5.4](https://docs.hytrust.com/CloudControl/5.4.0/Online/index.html).

### HyTrust DataControl on IBM Cloud

Das aktuelle Release installiert HyTrust DataControl 4.2 auf allen neu bereitgestellten Instanzen. Weitere Informationen zu den neuen Funktionen in HyTrust DataControl 4.2 finden Sie in [Neuerungen in HyTrust DataControl 4.x](https://docs.hytrust.com/DataControl/4.2/Admin_Guide-4.2/Content/Books/aaCommon/New-Changed-4x.htm).

### Veeam on IBM Cloud-Unterstützung für vSphere ESXi V6.5 Update 2c

Ab Version 2.6 werden neue Instanzen und neue Hosts mithilfe von vSphere ESXi V6.5 Update 2c bereitgestellt. Wenn Sie Veeam Backup and Replication verwenden, empfiehlt Veeam die Durchführung eines Updates für Ihre Veeam on {{site.data.keyword.cloud_notm}}-Instanz auf Version 9.5u3a oder höher, um sicherzustellen, dass Sie die beste Kompatibilität mit vSphere ESXi 6.5 Update 2c erzielen.

Es wird empfohlen, für vorhandene Cloud Foundation-Instanzen, in denen Veeam on {{site.data.keyword.cloud_notm}} installiert ist, ebenfalls eine Aktualisierung auf Version 9.5u3a oder höher durchzuführen.

Weitere Informationen zu Veeam on {{site.data.keyword.cloud_notm}} finden Sie in [Übersicht über Veeam on {{site.data.keyword.cloud_notm}}](../services/veeam_considerations.html).

### VMware HCX on IBM Cloud

Das aktuelle Release installiert VMware HCX 3.5.1 auf allen neu bereitgestellten Instanzen. Weitere Informationen zu den neuen Funktionen in HCX 3.5.1 finden Sie in der [Dokumentation zu VMware NSX Hybrid Connect](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/index.html).

### Zerto on IBM Cloud-Unterstützung für vSphere ESXi V6.5 Update 2c

Wenn Sie vorhandene Hosts auf vSphere ESXi V6.5 Update 2 aktualisieren und zuvor Zerto on {{site.data.keyword.cloud_notm}} installiert haben, kann die Zerto Virtual Replication-Konsole unter Umständen die Warnung `Unsupported ESX Version` unter dem Status 'Zerto Virtual Replication Appliances (VRAs)' anzeigen.

Weitere Informationen zum Beheben dieser Warnung finden Sie in den folgenden Abschnitten:

* [Zerto Virtual Replication Interoperability Matrix](http://s3.amazonaws.com/zertodownload_docs/6.0_Latest/Zerto%20Virtual%20Replication%20Operability%20Matrix.pdf)
* [Updating a ZVM to Support Zerto-Approved Host Releases Prior to a Full ZVR Update](https://www.zerto.com/myzerto/knowledge-base/updating-a-zvm-to-support-zerto-approved-host-releases-prior-to-a-full-zvr-update/)

## Neue und aktualisierte Dokumentation

### Referenzdokumentation zur Architektur
Das {{site.data.keyword.vmwaresolutions_short}}-Architekturdokument wurde aktualisiert, um wichtige Hinweise für das Verständnis Ihrer Verantwortlichkeiten hinsichtlich der Verwaltung und des Betriebs Ihrer VMware-Instanz zu verstehen.

Weitere Informationen finden Sie in [Nach der Bereitstellung zu beachtende Aspekte für Ihre VMware-Instanz](../archiref/solution/solution_considerations.html).

## Updates und Erweiterungen der Benutzerschnittstelle

Die Benutzerschnittstelle wurde aktualisiert und bietet die folgenden Erweiterungen:

* Es sind verschiedene Fehlernachrichten und QuickInfos verfügbar, die Sie bei der Auswahl der geeigneten Einstellung in der Benutzerschnittstelle unterstützen.
