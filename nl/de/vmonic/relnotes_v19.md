---

copyright:

  years:  2016, 2017

lastupdated: "2017-10-13"

subcollection: vmware-solutions


---

# Releaseinformationen für V1.9
{: #relnotes_v19}

Dieses Release stellt neue Funktionen, Komponentenaktualisierungen, Verbesserungen des Bedienungskomforts und Fehlerkorrekturen zur Verfügung. Eine Liste mit den in den unterschiedlichen Releases behobenen Problemen, den bekannten Problemen beim Produkt sowie Tipps für die Verwendung von {{site.data.keyword.vmwaresolutions_full}} finden Sie unter [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## VMware vSphere on IBM Cloud
{: #relnotes_v19-vss}

In diesem Release wird das Produktangebot "VMware vSphere on {{site.data.keyword.cloud_notm}}" eingeführt. Dieses Angebot ermöglicht Ihnen, Ihre eigene, von IBM gehostete virtuelle VMware-Umgebung zu erstellen, indem Sie die VMware-kompatiblen Rechen-, Speicher- und Netzressourcen anpassen und bestellen, die auf ausgewählten VMware-Komponenten basieren. Da vSphere on {{site.data.keyword.cloud_notm}} weder Installation noch Konfiguration oder Öffnung der optionalen VMware-Komponenten automatisiert, besitzen Sie ein hohes Maß an Flexibilität hinsichtlich des Designs und der Architektur einer Umgebung, die optimal für Ihre Geschäftsanforderungen geeignet ist. Beginnen Sie mit der Erstellung eines neuen vSphere-Clusters von ESXi-Servern oder skalieren Sie einen vorhandenen vSphere-Cluster in einem {{site.data.keyword.CloudDataCent_notm}} (Rechenzentrum).

Weitere Informationen finden Sie in den folgenden Abschnitten:
* [Neue vSphere-Cluster bestellen](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)
* [Vorhandene vSphere-Cluster skalieren](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_scalingexistingclusters)

## NetApp ONTAP Select on IBM Cloud
{: #relnotes_v19-netapp}

In diesem Release wird das Produktangebot "NetApp ONTAP Select on {{site.data.keyword.cloud_notm}}" eingeführt, eine virtuelle Appliance für softwaredefinierten Speicher, die NetApp ONTAP Select als Service in den dedizierten {{site.data.keyword.baremetal_short}}-Instanzen der IBM Cloud implementiert. NetApp ONTAP Select on {{site.data.keyword.cloud_notm}} wird in Konfigurationen für hohe Leistung (alle mit SSD) und hohe Kapazität (alle mit SATA) angeboten.
Dieses Angebot dient als Host für Ihren Speicher in der dedizierten Infrastruktur und stellt NetApp-Funktionalität wie Deduplizierung, Komprimierung und Verschlüsselung für ruhende Daten bereit. Stellen Sie Speicherressourcen dynamisch und flexibel bereit und schützen Sie gleichzeitig Ihre Daten durch die Verwendung von intelligenten Datenmanagementfunktionen. Verwenden Sie beispielsweise die schnellen und effizienten NetApp Snapshot®-Kopien, FlexClone®-Kopien und die SnapMirror®-Replikation.

Weitere Informationen finden Sie in den folgenden Abschnitten:
* [Übersicht über NetApp ONTAP Select](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_netappoverview)
* [NetApp ONTAP Select-Instanzen bestellen](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_orderinginstances)

## Service "F5 on IBM Cloud"
{: #relnotes_v19-f5}

Der Service "F5 BI-IP Virtual Edition (VE) on {{site.data.keyword.cloud_notm}}" ist jetzt für VMware Cloud Foundation- und für VMware vCenter Server-Instanzen verfügbar. Dieser stellt lokal und global einsetzbare intelligente Services für den L4-L7-Lastausgleich, einen stabilen Firewallschutz für Netze und Webanwendungen sowie einen sicheren und eingebundenen Anwendungszugriff zur Verfügung.
Bestellen Sie Instanzen, die den Service "F5 BIG-IP Virtual Edition (VE) on {{site.data.keyword.cloud_notm}}" enthalten, oder fügen Sie diesen Service später Ihren vorhandenen Instanzen über die Registerkarte **Services** auf der Detailseite mit den Instanzeigenschaften in der {{site.data.keyword.vmwaresolutions_short}}-Konsole hinzu. Sie können je nach Bedarf eine der drei Lizenzierungsoptionen für BIG-IP VE auswählen.

Weitere Informationen finden Sie in den folgenden Abschnitten:
* [Hinweise zu F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_considerations)
* [F5 on {{site.data.keyword.cloud_notm}} verwalten](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_f5)

## Verwaltete Services aus IBM Integrated Managed Infrastructure
{: #relnotes_v19-imi}

Für VMware Cloud Foundation-Instanzen sind jetzt verwaltete Services aus IBM Integrated Managed Infrastructure (IMI) verfügbar. IMI kann das Management der virtuellen VMware-Infrastruktur durch modulare Services vereinfachen und als einziger anerkannter Provider eingesetzt werden, um die Überwachung und das Management der virtuellen IT-Infrastrukturen zu vereinfachen. Sie können bestimmte Routineoperationen wie beispielsweise die Überwachung in IMI auslagern und sich hierdurch auf wichtigere Initiativen konzentrieren.

Auf der Seite **Einführung** können Sie jederzeit ein Beratungsgespräch und eine Schätzung anfordern.
Weitere Informationen finden Sie unter [Verwaltete Services von IMI anfordern](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_imi#requesting-managed-services-from-imi).

## Einschränkungen bei Namen für vCenter Server- und NetApp ONTAP Select-Instanzen
{: #relnotes_v19-inst-name}

Instanznamen, die bei der Bestellung von Instanzen in {{site.data.keyword.vmwaresolutions_short}} eingegeben werden, dürfen keine Sonderzeichen (z. B. Bindestriche) enthalten. Es sind nur alphanumerische Zeichen zulässig. Diese Einschränkung gilt nicht für Cloud Foundation-Instanzen.

Weitere Informationen finden Sie in den folgenden Abschnitten:
* [vCenter Server-Instanzen bestellen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [NetApp ONTAP Select-Instanzen bestellen](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_orderinginstances)

## Updates für VMware Cloud Foundation-Instanzen
{: #relnotes_v19-vcf}

### CPU und Speicher von Instanzen anpassen
{: #relnotes_v19-custom-cpu}

Neben den vordefinierten und getesteten Optionen "S (Klein)" und "Standard" gibt es eine vom Benutzer anpassbare Serveroption. Damit das Verhältnis von CPU zu RAM Ihrer Workloads besser auf die VMware-kompatible Hardware abgestimmt ist, können Sie nun die Gesamtzahl der Kerne in einem Dual-CPU-Server und die RAM-Menge unabhängig voneinander auswählen. Lokaler Speicher kann nicht angepasst werden.

## Updates für VMware vCenter Server-Instanzen
{: #relnotes_v19-vcs}

### Unterstützung für rechenzentrenübergreifende Cluster
{: #relnotes_v19-cross-dc}

Um die horizontale Skalierung Ihrer gehosteten VMware-Umgebung zu erhöhen, können Sie jetzt einen neuen Cluster in einem anderen Pod der {{site.data.keyword.cloud_notm}}-Infrastruktur (SoftLayer) oder einem anderen {{site.data.keyword.CloudDataCent_notm}} (Rechenzentrum) als dem ersten in der Instanz bereitgestellten Cluster erstellen.

Weitere Informationen finden Sie unter [Cluster für vCenter Server-Instanzen hinzufügen, anzeigen und löschen](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingviewingclusters#vc_addingviewingclusters).

### Komponenten ändern
{: #relnotes_v19-change-comp}

Bei diesem Release gibt es keine Auswirkungen auf Operationen in der {{site.data.keyword.vmwaresolutions_short}}-Konsole mehr, wenn der Administrator für das Single Sign-on bestimmte vCenter Server-Ressourcen in einem nativen VMware-Tool ändert. Beispielsweise können Sie jetzt die Namen von virtuellen VMware-Rechenzentren, Clustern, Switches, Portgruppen und Datenspeichern in VMware vSphere Web Client ändern, um Bereitstellungen an unternehmensweite oder individuelle Namenskonventionen anzupassen, ohne dass es zu nachgelagerten Auswirkungen auf die Operationen kommt, die von der {{site.data.keyword.vmwaresolutions_short}}-Konsole aus durchgeführt werden.

Weitere Informationen finden Sie im Abschnitt [Auswirkungen bei Änderungen für Komponenten von vCenter Server-Instanzen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vcenter_chg_impact).

### Zusätzliche RAM-Größen
{: #relnotes_v19-ram-sizes}

Wenn Sie vCenter Server-Instanzen bestellen oder Cluster für vCenter Server-Instanzen hinzufügen, können Sie nun unter mehr RAM-Größen wählen, damit das Verhältnis von CPU zu RAM der Workload besser auf die Hardware abgestimmt ist. Die folgenden Optionen sind bei der Konfigurationsoption **Angepasst** verfügbar, wenn Sie einen Server in der {{site.data.keyword.vmwaresolutions_short}}-Konsole bestellen: 64 GB, 128 GB, 256 GB, 384 GB, 512 GB, 768 GB und 1,5 TB.

Weitere Informationen finden Sie unter [vCenter Server-Instanzen bestellen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance).

### Versionsupdate für Network File System

Network File System (NFS) Version 4.1 ist nicht mehr als Speichereinstellung in der Benutzerschnittstelle verfügbar. Alle vCenter Server-Instanzen werden mit NFS V3 bereitgestellt. Obwohl NFS V3 eine ältere Protokollversion ist, ermöglicht es erweiterte Funktionen in VMware-Umgebungen mit Unterstützung für VMware Storage Distributed Resource Scheduler (SDRS) und Storage I/O Control (SIOC).

Weitere Informationen finden Sie unter [vCenter Server-Instanzen bestellen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance).

### Domänenname des Domänennamensservers einer einzelnen Site
{: #relnotes_v19-single-site-dns}

Sie können jetzt den Domänennamen des Domänennamensservers (DNS) für eine vCenter Server-Instanz während einer Bestellung angeben. Eine Virtual Server-Instanz (VSI) von Microsoft Windows Server, die als DNS für die Instanz dient, auf der die Hosts und virtuellen Maschinen registriert sind, wird bereitgestellt und kann zur Suche verwendet werden. Microsoft Active Directory (AD) ist ebenfalls auf der Microsoft Windows-VSI eingerichtet und der DNS-Domänenname ist das Stammelement der AD-Domänengesamtstruktur. Diese Microsoft Windows-VSI ist nur in V1.9 und höher sichtbar.

Weitere Informationen finden Sie in den folgenden Abschnitten:
* [Übersicht über vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)
* [vCenter Server-Instanzen anzeigen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_viewinginstances)

## Voraussetzungen für die automatische Installation von Updates für Windows Server
{: #relnotes_v19-win-server}

Microsoft Active Directory (AD) bzw. der Domänennamensserver (DNS) wird automatisch ausschließlich für das Herunterladen der Updates konfiguriert. Bei diesen Updates erfolgen Installation und Neustart nicht automatisch. Sie müssen die Updates manuell installieren und den Neustart zu einem geplanten Zeitpunkt ausführen, zu dem Unterbrechungen der laufenden Active Directory Server-Konfiguration und anderen Sicherungsjobs vermieden werden. Um Windows-Updates anzuwenden, installieren Sie die Updates manuell.

## Neue und aktualisierte Dokumentation
{: #relnotes_v19-new-docs}

* Für die Konfiguration von Firewalls, die die gesamte Protokollkommunikation aus den virtuellen Maschinen für IBM CloudDriver und SDDC Manager zulassen, wird weitere Dokumentation bereitgestellt. Weitere Informationen enthält der Abschnitt [Komponenten und Hinweise für Fortinet on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_considerations).
