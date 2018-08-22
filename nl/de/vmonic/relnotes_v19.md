---

copyright:

  years:  2016, 2018

lastupdated: "2017-10-13"

---

# Releaseinformationen für V1.9

Dieses Release stellt neue Funktionen, Komponentenaktualisierungen, Verbesserungen des Bedienungskomforts und Fehlerkorrekturen zur Verfügung. Eine Liste mit den in den unterschiedlichen Releases behobenen Problemen, den bekannten Problemen beim Produkt sowie zusätzlichen Tipps für die Verwendung von {{site.data.keyword.vmwaresolutions_full}} finden Sie unter [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## VMware vSphere on IBM Cloud

In diesem Release wird das Produktangebot "VMware vSphere on {{site.data.keyword.cloud_notm}}" eingeführt, mit dem Sie Ihre eigene, von IBM gehostete virtuelle VMware-Umgebung erstellen können, indem Sie die VMware-kompatiblen Rechen-, Speicher- und Netzressourcen anpassen und bestellen, die auf ausgewählten VMware-Komponenten basieren. Da vSphere on {{site.data.keyword.cloud_notm}} weder Installation noch Konfiguration oder Inbetriebnahme der optionalen VMware-Komponenten automatisiert, besitzen Sie eine hohe Flexibilität hinsichtlich des Designs und der Architektur einer Umgebung, die optimal für Ihre Geschäftsanforderungen geeignet ist. Sie können am Anfang einen neuen vSphere-Cluster von ESXi-Servern erstellen oder einen vorhandenen vSphere-Cluster in einem {{site.data.keyword.CloudDataCent_notm}} (Rechenzentrum) skalieren.

Weitere Informationen enthalten die folgenden Abschnitte:
* [Neue vSphere-Cluster bestellen](../vsphere/vs_orderinginstances.html)
* [Vorhandene vSphere-Cluster skalieren](../vsphere/vs_scalingexistingclusters.html)

## NetApp ONTAP Select on IBM Cloud

In diesem Release wird das Produktangebot "NetApp ONTAP Select on {{site.data.keyword.cloud_notm}}" eingeführt, eine virtuelle Appliance für softwaredefinierten Speicher, die NetApp ONTAP Select als Service in den dedizierten {{site.data.keyword.baremetal_short}}-Instanzen der IBM Cloud implementiert. NetApp ONTAP Select on {{site.data.keyword.cloud_notm}} wird in Konfigurationen für hohe Leistung (alle mit SSD) und hohe Kapazität (alle mit SATA) angeboten.
Es dient als Host für Ihren Speicher in der dedizierten Infrastruktur und stellt NetApp-Funktionalität wie Deduplizierung, Komprimierung und Verschlüsselung für ruhende Daten bereit. Mithilfe dieses Produktangebots können Sie Speicherressourcen dynamisch und flexibel bereitstellen und gleichzeitig Ihre Daten durch die Verwendung von intelligenten Datenmanagementfunktionen wie den schnellen und effizienten NetApp Snapshot®-Kopien, FlexClone®-Kopien und SnapMirror®-Replikation schützen.

Weitere Informationen enthalten die folgenden Abschnitte:
* [Übersicht über NetApp ONTAP Select](../netapp/np_netappoverview.html)
* [NetApp ONTAP Select-Instanzen bestellen](../netapp/np_orderinginstances.html)

## Service "F5 on IBM Cloud"

Der Service "F5 BI-IP Virtual Edition (VE) on {{site.data.keyword.cloud_notm}}" ist jetzt für VMware Cloud Foundation- und für VMware vCenter Server-Instanzen verfügbar. Dieser stellt lokal und global einsetzbare intelligente Services für den L4-L7-Lastausgleich, einen stabilen Firewallschutz für Netze und Webanwendungen sowie einen sicheren und eingebundenen Anwendungszugriff zur Verfügung.
Sie können Instanzen bestellen, die den Service "F5 BIG-IP Virtual Edition (VE) on {{site.data.keyword.cloud_notm}}" enthalten, oder diesen Service später Ihren vorhandenen Instanzen über die Registerkarte **Services** auf der Detailseite mit den Instanzeigenschaften in der {{site.data.keyword.vmwaresolutions_short}}-Konsole hinzufügen. Je nach Bedarf stehen Ihnen drei Lizenzierungsoptionen für BIG-IP VE zur Auswahl.

Weitere Informationen enthalten die folgenden Abschnitte:
* [Hinweise zu F5 on {{site.data.keyword.cloud_notm}}](../services/f5_considerations.html)
* [F5 on {{site.data.keyword.cloud_notm}} verwalten](../services/managing_f5.html)

## Verwaltete Services aus IBM Integrated Managed Infrastructure

Für VMware Cloud Foundation-Instanzen sind jetzt verwaltete Services aus IBM Integrated Managed Infrastructure (IMI) verfügbar. IMI kann das Management der virtuellen VMware-Infrastruktur durch modulare Services vereinfachen und als einziger anerkannter Provider eingesetzt werden, um die Überwachung und das Management der virtuellen IT-Infrastrukturen zu vereinfachen. Sie können bestimmte Routineoperationen wie beispielsweise die Überwachung in IMI auslagern und sich hierdurch auf wichtigere Initiativen konzentrieren.

Auf der Seite **Einführung** können Sie jederzeit ein Beratungsgespräch und ein Angebot anfordern.
Weitere Informationen finden Sie unter [Verwaltete Services von IMI anfordern](../services/managing_imi.html#requesting-managed-services-from-imi).

## Einschränkungen bei Namen für vCenter Server- und NetApp ONTAP Select-Instanzen

Instanznamen, die bei der Bestellung von Instanzen in {{site.data.keyword.vmwaresolutions_short}} eingegeben werden, dürfen keine Sonderzeichen (z. B. Bindestriche) enthalten. Es sind nur alphanumerische Zeichen zulässig. Diese Einschränkung gilt nicht für Cloud Foundation-Instanzen.

Weitere Informationen enthalten die folgenden Abschnitte:
* [vCenter Server-Instanzen bestellen](../vcenter/vc_orderinginstance.html)
* [NetApp ONTAP Select-Instanzen bestellen](../netapp/np_orderinginstances.html)

## Updates für VMware Cloud Foundation-Instanzen

### CPU und Speicher von Instanzen anpassen

Neben den vordefinierten und getesteten Optionen "S (Klein)" und "Standard" gibt es eine vom Benutzer anpassbare Serveroption. Damit das Verhältnis von CPU zu RAM Ihrer Workloads besser auf die VMware-kompatible Hardware abgestimmt ist, können Sie nun die Gesamtzahl der Kerne in einem Dual-CPU-Server und die RAM-Menge unabhängig voneinander auswählen. Lokaler Speicher kann nicht angepasst werden.

Weitere Informationen finden Sie im Abschnitt [Cloud Foundation-Instanzen bestellen](../sddc/sd_orderinginstance.html).

## Updates für VMware vCenter Server-Instanzen

### Unterstützung für rechenzentrenübergreifende Cluster

Um die horizontale Skalierung Ihrer gehosteten VMware-Umgebung zu erhöhen, können Sie jetzt einen neuen Cluster in einem anderen Pod der {{site.data.keyword.cloud_notm}}-Infrastruktur (SoftLayer) oder einem anderen {{site.data.keyword.CloudDataCent_notm}} (Rechenzentrum) als dem ersten in der Instanz bereitgestellten Cluster erstellen.

Weitere Informationen finden Sie unter [Cluster für vCenter Server-Instanzen hinzufügen und anzeigen](../vcenter/vc_addingviewingclusters.html).

### Komponenten ändern

Bei diesem Release gibt es keine Auswirkungen auf Operationen in der {{site.data.keyword.vmwaresolutions_short}}-Konsole mehr, wenn der Administrator für das Single Sign-on bestimmte vCenter Server-Ressourcen in einem nativen VMware-Tool ändert. Beispielsweise können Sie jetzt die Namen von virtuellen VMware-Rechenzentren, Clustern, Switches, Portgruppen und Datenspeichern in VMware vSphere Web Client ändern, um Bereitstellungen an unternehmensweite oder individuelle Namenskonventionen anzupassen, ohne dass es zu nachgelagerten Auswirkungen auf die Operationen kommt, die von der {{site.data.keyword.vmwaresolutions_short}}-Konsole aus durchgeführt werden.

Weitere Informationen finden Sie im Abschnitt [Auswirkungen bei Änderungen für Komponenten von vCenter Server-Instanzen](../vcenter/vcenter_chg_impact.html).

### Zusätzliche RAM-Größen

Beim Bestellen von vCenter Server-Instanzen oder beim Hinzufügen von Clustern für vCenter Server-Instanzen können Sie nun unter mehr RAM-Größen wählen, damit das Verhältnis von CPU zu RAM der Workload besser auf die Hardware abgestimmt ist. Die folgenden Optionen sind bei der Konfigurationsoption **Angepasst** verfügbar, wenn Sie einen Server in der {{site.data.keyword.vmwaresolutions_short}}-Konsole bestellen: 64 GB, 128 GB, 256 GB, 384 GB, 512 GB, 768 GB und 1,5 TB.

Weitere Informationen finden Sie unter [vCenter Server-Instanzen bestellen](../vcenter/vc_orderinginstance.html).

### Versionsupdate für Network File System

Network File System (NFS) Version 4.1 ist nicht mehr als Speichereinstellung in der Benutzerschnittstelle verfügbar. Alle vCenter Server-Instanzen werden mit NFS V3 bereitgestellt. Obwohl NFS V3 eine ältere Protokollversion ist, ermöglicht es erweiterte Funktionen in VMware-Umgebungen mit Unterstützung für VMware Storage Distributed Resource Scheduler (SDRS) und Storage I/O Control (SIOC).

Weitere Informationen finden Sie unter [vCenter Server-Instanzen bestellen](../vcenter/vc_orderinginstance.html).

### Domänenname des Domänennamensservers einer einzelnen Site

Sie können jetzt den Domänennamen des Domänennamensservers (DNS) für eine vCenter Server-Instanz während einer Bestellung angeben. Eine Virtual Server-Instanz (VSI) von Microsoft Windows Server, die als DNS für die Instanz dient, auf der die Hosts und virtuellen Maschinen registriert sind, wird bereitgestellt und kann zur Suche verwendet werden. Microsoft Active Directory (AD) ist ebenfalls auf der Microsoft Windows-VSI eingerichtet und der DNS-Domänenname ist das Stammelement der AD-Domänengesamtstruktur. Diese Microsoft Windows-VSI ist nur in V1.9 und höher sichtbar.

Weitere Informationen enthalten die folgenden Abschnitte:
* [Übersicht über vCenter Server](../vcenter/vc_vcenterserveroverview.html)
* [vCenter Server-Instanzen anzeigen](../vcenter/vc_viewinginstances.html)

## Voraussetzungen für die automatische Installation von Updates für Windows Server

Microsoft Active Directory (AD) bzw. der Domänennamensserver (DNS) wird automatisch für das Herunterladen von Updates konfiguriert. Bei diesen Updates erfolgen Installation und Warmstart nicht automatisch. Sie müssen die Updates manuell installieren und den Warmstart zu einem geplanten Zeitpunkt ausführen, zu dem Unterbrechungen der laufenden Active Directory Server-Konfiguration und anderen Sicherungsjobs vermieden werden. Um Windows-Updates anzuwenden, installieren Sie die Updates manuell.

## Neue und aktualisierte Dokumentation

* Sie können sich darüber informieren, wie Sie Ihre privaten VCF-Instanzen mit mehreren Standorten schützen, während Sie Ihre VMware-Anwendungen auf die Verwendung von öffentlichen {{site.data.keyword.cloud_notm}}-Services erweitern. Weitere Informationen finden Sie auf der Seite [Securely connect your private VMware workloads in the {{site.data.keyword.cloud_notm}}](https://www.ibm.com/developerworks/library/se-securely-connect-private-vmware-workloads-ibm-cloud/index.html){:new_window}.
* Für die Konfiguration von Firewalls, die die gesamte Protokollkommunikation aus den virtuellen Maschinen für IBM CloudDriver und SDDC Manager zulassen, wird zusätzliche Dokumentation bereitgestellt. Weitere Informationen enthält der Abschnitt [Komponenten und Hinweise für Fortinet on {{site.data.keyword.cloud_notm}}](../services/fsa_considerations.html).
