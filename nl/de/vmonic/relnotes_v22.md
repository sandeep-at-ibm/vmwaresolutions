---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-19"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Releaseinformationen für V2.2
{: #relnotes_v22}

Dieses Release stellt neue Funktionen, Komponentenaktualisierungen, Verbesserungen des Bedienungskomforts und Fehlerkorrekturen zur Verfügung. Eine Liste mit den in den unterschiedlichen Releases behobenen Problemen, den bekannten Problemen beim Produkt sowie Tipps für die Verwendung von {{site.data.keyword.vmwaresolutions_full}} finden Sie unter [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Korrektur für Spectre und Meltdown

{{site.data.keyword.vmwaresolutions_short}} hat als Reaktion auf Sicherheitslücken, die unter den Begriffen "Spectre" und "Meltdown" bekannt sind, Patches aus VMware freigegeben (CVE-2017-5753, CVE-2017-5715 und CVE-2017-5754).

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

Weitere Informationen enthält der Abschnitt [Gegenmaßnahmen für Sicherheitslücken "Spectre" und "Meltdown"](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_fix_spectre).

## Upgrade der virtuellen Maschine für IBM CloudDriver

Während des Upgradeprozesses für V2.2 wird die virtuelle Maschine für IBM CloudDriver mit CentOS Linux Release 7.4.1708 erneut bereitgestellt. Alle neu bereitgestellten Instanzen enthalten ebenfalls CentOS Linux Release 7.4.1708 für IBM CloudDriver.

**Wichtig:**

* Falls Sie eine Sicherungslösung verwenden, die die virtuelle Maschine für IBM CloudDriver referenziert, müssen Sie nach dem Upgrade auf V2.2 sicherstellen, dass die Sicherungslösung die neue virtuelle Maschine für IBM CloudDriver referenziert.
* Denken Sie vor dem Upgrade auf V2.2 daran, die herkömmliche virtuelle Serverinstanz (VSI) für Veeam durch den Service "Veeam on {{site.data.keyword.cloud_notm}}" zu ersetzen. Das herkömmliche Veeam wird in V2.2 und künftigen Releases nicht mehr unterstützt; die dem herkömmlichen Veeam zugeordneten Sicherungen von Managementkomponenten sind daher nicht für eine Wiederherstellung verfügbar.

Weitere Informationen zur Verwendung des Service "Veeam on {{site.data.keyword.cloud_notm}}" enthalten die folgenden Abschnitte:
* [Komponenten und Hinweise für Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_considerations)
* [Veeam on {{site.data.keyword.cloud_notm}} verwalten](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingveeam)

## Erweiterte Konfigurationseinstellungen für ESXi-Server

Bei V2.2 oder höheren Releases werden neue Instanzen mit einer neuen Gruppe von erweiterten Konfigurationseinstellungen für ESXi-Server bestellt.
Bei Instanzen, für die ausgehend von einem Vorgängerrelease ein Upgrade auf V2.2 oder höher durchgeführt wurde, machen einige Einstellungen einen Neustart der ESXi-Server erforderlich. Deshalb wird hier nur ein Teil der Konfigurationseinstellungen automatisch angewendet.

Es wird empfohlen, die verbleibenden Konfigurationseinstellungen auf die neuen Werte zu setzen, um eine instanzübergreifende Konsistenz zu erreichen und eine adäquate Unterstützung für die Speichererweiterung zu ermöglichen. IBM plant, Tests ausschließlich mit diesen neuen Einstellungen für alle künftigen Releases von {{site.data.keyword.cloud_notm}} for VMware Solutions vorzunehmen.

Weitere Informationen finden Sie unter _Erweiterte Konfigurationseinstellungen für ESXi-Server_ in den folgenden Abschnitten:
* [vCenter Server-Teileliste](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom#advanced-configuration-settings-for-esxi-servers)
* [Cloud Foundation-Teileliste](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_bom#advanced-configuration-settings-for-esxi-servers)

## Unterstützung von bis zu 51 ESXi-Servern für ersten Cluster und bis zu 59 ESXi-Servern für zusätzliche Cluster

Bei V2.2 und höheren Releases können Sie jetzt die Anzahl der ESXi-Server für den ersten Cluster auf maximal 51 und für zusätzliche Cluster auf bis zu 59 erhöhen.

Bei Instanzen, die in V2.1 oder früheren Releases bereitgestellt wurden, müssen Sie die erforderliche vSAN-Unterstützung aktivieren, um die Clustergröße auf über 32 zu erhöhen. Weitere Informationen zu Schritten zum Erhöhen der Anzahl von ESXi-Servern finden Sie unter _Wie viele ESXi-Server kann ich zu einem Cluster hinzufügen?_ im Abschnitt [Häufig gestellte Fragen zu ESXi-Servern](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq_esxi#how-many-esxi-servers-can-i-add-to-a-cluster-).
{:important}

## Weitere Netzkonfigurationsoptionen für vCenter Server- und Cloud Foundation-Instanzen

Bei Bestellungen von vCenter Server- und Cloud Foundation-Instanzen können Sie nun vorhandene private und öffentliche VLANs für Ihre Netzkonfiguration wiederverwenden. Wenn keine vorhandenen VLANs verfügbar sind, können Sie ein neues öffentliches und zwei private VLANs bestellen.

Wichtige Hinweise, die Sie vor der Auswahl vorhandener VLANs lesen sollten, enthalten die Abschnitte zu den *Netzschnittstelleneinstellungen* in:
* [vCenter Server-Instanzen bestellen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [Cloud Foundation-Instanzen bestellen](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_orderinginstance)

## Updates für VMware vCenter Server-Instanzen

### Updates bei Konfigurationseinstellungen für NSX-Komponenten und -Portgruppen

Mit dem aktuellen Release wird das Update der Komponente "VMware NSX for vSphere 6.3.5" angewendet. Weitere Informationen zu Komponenten finden Sie unter [vCenter Server-Teileliste](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom).

Für VMware vCenter Server-Instanzen, die in V2.2 oder höheren Releases bereitgestellt werden, haben sich die Konfigurationseinstellungen für NSX und Portgruppe geändert. Weitere Informationen finden Sie im Abschnitt *Konfigurationseinstellungen für NSX und Portgruppe* in der [Softwareteileliste von vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom#nsx-and-port-group-configuration-settings).

### Neue Option für DNS-Konfiguration

Sie können jetzt die Bereitstellung einer einzigen Virtual Server-Instanz (VSI) von Microsoft Windows für Microsoft Active Directory (AD) oder aber zwei virtuelle Microsoft Windows-Maschinen für die Hochverfügbarkeit im Management-Cluster auswählen. Bei Releases vor V2.2 wurde die einzelne Microsoft Windows-VSI für Microsoft AD standardmäßig automatisch bereitgestellt. Die neue Option zur Auswahl von zwei virtuellen Microsoft Windows-Maschinen bietet mehr Datenschutz und die Möglichkeit, die virtuellen Maschinen, die den Veeam-Service verwenden, zu sichern und wiederherzustellen.

Sie müssen zwei Lizenzen für Microsoft Windows Server 2012 R2 bereitstellen, wenn Sie Ihre Instanz für die Verwendung der beiden virtuellen Microsoft Windows-Maschinen konfigurieren. Verwenden Sie die Lizenz für Microsoft Windows Server 2012 R2 Standard Edition und/oder die Lizenz für Microsoft Windows Server 2012 R2 Datacenter Edition. Sie haben 30 Tage Zeit, um die virtuellen Maschinen zu aktivieren.
{:note}

Weitere Informationen finden Sie unter *Systemeinstellungen* im Abschnitt [vCenter Server-Instanzen bestellen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance#system-settings).

### Größere Anzahl von Clustern pro Instanz

Sie können jetzt bis zu 10 Cluster zu VMware vCenter Server-Instanzen hinzufügen, die in V2.2 oder höher bereitgestellt werden bzw. für die ein Upgrade auf eine entsprechende Version durchgeführt wurde. Weitere Informationen finden Sie unter [Cluster für vCenter Server-Instanzen hinzufügen und anzeigen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-adding-and-viewing-clusters-for-vcenter-server-instances).

## Updates für VMware vSphere-Cluster

### Komponentenlizenzpakete für Kunden des Typs "Business Partner" verfügbar

Benutzer der Kategorie "Business Partner" können bei der Bestellung eines neuen vSphere-Clusters jetzt unter vier Komponentenlizenzpaketen wählen. Zur Auswahl stehen die Pakete "Standard with Management", "Advanced", "Advanced with Networking" oder "Advanced with Networking and Management". Sie können auch zusätzliche VMware-Komponenten in Ihre Bestellung aufnehmen. Die Option zur Verwendung Ihrer eigenen Lizenz (BYOL) ist jedoch nicht verfügbar.

Weitere Informationen finden Sie unter *Lizenzierungseinstellungen* im Abschnitt [Neue vSphere-Cluster bestellen](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances).

## Updates für NetApp ONTAP Select-Instanzen

Im aktuellen Release wird das Update von NetApp ONTAP Select 9.3 angewendet.

### Höhere Anzahl von SATA-Laufwerken für IBM Cloud Bare Metal Server-Systeme mit hoher Kapazität

Für {{site.data.keyword.baremetal_short}}-Systeme mit hoher Kapazität und NetApp ONTAP Select sind jetzt 34 SATA-Laufwerke verfügbar. Weitere Informationen enthält der Abschnitt [Technische Spezifikationen für NetApp ONTAP Select-Instanzen](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_netappoverview#technical-specifications-for-netapp-ontap-select-instances).

## Updates für Add-on-Services

### Erhöhte Bandbreitenoption für F5 on IBM Cloud

Bei der Installation des Service "F5 on {{site.data.keyword.cloud_notm}}" für Cloud Foundation- und vCenter Server-Instanzen können Sie jetzt eine maximale Bandbreite von 10 Gb/s auswählen. Weitere Informationen finden Sie unter [Hinweise zu F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_considerations).

### KMIP for VMware on IBM Cloud

Sie können jetzt eine Cloud Foundation- oder vCenter Server-Instanz mit integriertem Service "KMIP for VMware on {{site.data.keyword.cloud_notm}}" bestellen oder den Service nach der Erstbereitstellung zu einer vorhandenen Cloud Foundation- oder vCenter Server-Instanz hinzufügen.

Dieser Service stellt täglich rund um die Uhr einen hoch verfügbaren Service für das Management von Verschlüsselungsschlüsseln bereit, die von VMware in der {{site.data.keyword.cloud_notm}} verwendet werden. Dieser Service bietet Laufzeitfunktionalität, mit der Kunden die Verschlüsselungsschlüssel erstellen, abrufen, aktivieren, widerrufen und löschen können. Dieser Service stellt darüber hinaus Managementfunktionen zum Verwalten der Zuordnungen zwischen den Clientberechtigungsnachweisen und den Verschlüsselungsschlüsseln bereit.

Weitere Informationen finden Sie unter [Hinweise zu KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/kmip_considerations.html).

### IBM Spectrum Protect Plus on IBM Cloud

Der Service "IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}}" ist nun für Instanzen verfügbar, die in V2.2 oder höheren Releases bereitgestellt werden bzw. für die ein Upgrade auf eine entsprechende Version durchgeführt wurde.

Dieser Service bietet eine effiziente und skalierbare Datensicherungs-, Datenwiederverwendungs- und Datenwiederherstellungslösung für virtuelle Umgebungen. Er kann als eigenständige Lösung implementiert oder in Ihre IBM Spectrum Protect&trade; Plus-Umgebung integriert werden, um Kopien für die Langzeitspeicherung und Datengovernance auszulagern.

Der Service "IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}" stellt Datenschutz nur für die Workload-VMs bereit.

Weitere Informationen finden Sie in [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} verwalten](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingspp). 

### Verwaltete Services

Verwaltete Services für Veeam on {{site.data.keyword.cloud_notm}} und für Zerto on {{site.data.keyword.cloud_notm}} sind jetzt für VMware vCenter Server- und VMware Cloud Foundation-Instanzen verfügbar. Fordern Sie diese verwalteten Services an, wenn Sie eine eigene komplexe Lösung und Umgebung nicht selbst verwalten möchten.

Der Service "Veeam on {{site.data.keyword.cloud_notm}}" wird nahtlos in Ihre VMware-Hypervisoren integriert und fördert so die Hochverfügbarkeit in Ihrem Unternehmen. Eine vollständig verwaltete Sicherungsumgebung sowohl mit Veeam-Sicherungssoftware als auch IBM Resiliency Backup as a Service kann bereitgestellt werden.

Der Service "Zerto on {{site.data.keyword.cloud_notm}}" stellt Replikations- und Disaster-Recovery-Funktionen bereit, die in die Bereitstellungsangebote integriert werden können, um Daten in Ihrer virtuellen VMware-Umgebung in {{site.data.keyword.cloud_notm}} zu schützen und wiederherzustellen. Hiermit kann eine vollständig verwaltete Disaster-Recovery-Umgebung sowohl mit Disaster-Recovery-Software von Zerto als auch IBM Resiliency Services bereitgestellt werden.

Sie können verwaltete Services für Ihre Instanzen auf der Seite **Einführung** anfordern, indem Sie entweder eine neue Instanzbestellung aufgeben oder den Service zu einer vorhandenen Instanz hinzufügen.

Weitere Informationen finden Sie in den folgenden Abschnitten:
* [Services für Veeam on {{site.data.keyword.cloud_notm}} anfordern](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_veeam_services)
* [Services für Zerto on {{site.data.keyword.cloud_notm}} anfordern](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_zerto_services)

## Neue und aktualisierte Dokumentation

* In der Dokumentation ist jetzt eine Vergleichstabelle mit den unterstützten Funktionen für Cloud Foundation- und vCenter Server-Instanzen sowie VMware vSphere-Clustern verfügbar. Sie können auf einen Blick die Unterschiede zwischen den Funktionen erkennen, die von den einzelnen Instanztypen zur Verfügung gestellt werden. Weitere Informationen finden Sie im [Angebotsvergleichsdiagramm](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-inst_comp_chart).

* Die Dokumentation für Cloud Foundation-, vCenter Server- und VMware vSphere-Cluster umfasst jetzt eine Teileliste für VLANs und Software.

  Weitere Informationen finden Sie in den folgenden Abschnitten:

  * [vCenter Server-Teileliste](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)
  * [Cloud Foundation-Teileliste](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_bom)
  * [VMware vSphere-Teileliste](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_bom)

## Updates und Erweiterungen der Benutzerschnittstelle

In der gesamten Benutzerschnittstelle wurden Verbesserungen vorgenommen:

* Wenn Sie eine Instanz bestellen, werden alle Hardwareoptionen jetzt nach Standort gefiltert und die nicht verfügbaren Optionen im inaktivierten Status angezeigt.
* Die **{{site.data.keyword.baremetal_short}}**-Konfiguration wird nun bei der Bestellung eines vSphere-Clusters basierend auf den vorhandenen Konfigurationen automatisch ausgefüllt. Sie können die Konfiguration Ihrem Bedarf entsprechend aktualisieren.
* Es sind verschiedene Fehlernachrichten und QuickInfos verfügbar, die Sie bei der Auswahl der geeigneten Einstellung in der Benutzerschnittstelle unterstützen.
