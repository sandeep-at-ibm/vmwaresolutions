---

copyright:

  years:  2016, 2018

lastupdated: "2018-12-14"

---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Releaseinformationen für V2.7
{: #relnotes_v27}

Dieses Release stellt neue Funktionen, Komponentenaktualisierungen, Verbesserungen des Bedienungskomforts und Fehlerkorrekturen zur Verfügung. Eine Liste mit den in den unterschiedlichen Releases behobenen Problemen, den bekannten Problemen beim Produkt sowie Tipps für die Verwendung von {{site.data.keyword.vmwaresolutions_full}} finden Sie unter [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Unterstützung SAP-zertifizierter 6140-Server

Ab dem Release von V2.7 sind die folgenden neuen {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short_sing}}-CPU-Modelle für die Bereitstellung für VMware vCenter Server auf {{site.data.keyword.cloud_notm}}- und VMware vSphere on {{site.data.keyword.cloud_notm}}-Instanzen und -Clustern verfügbar:
* Dual Intel Xeon Gold 6140-Prozessor / 36 Kerne insgesamt, 2,3 GHzDual / 192 GB RAM
* Dual Intel Xeon Gold 6140-Prozessor / 36 Kerne insgesamt, 2,2 GHzDual / 384 GB RAM
* Dual Intel Xeon Gold 6140-Prozessor / 36 Kerne insgesamt, 2,3 GHzDual / 768 GB RAM

Weitere Informationen enthält der Abschnitt *{{site.data.keyword.baremetal_short_sing}}-Einstellungen* unter:
* [vCenter Server-Instanzen bestellen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance#bare-metal-server-settings)
* [Neue vSphere-Cluster bestellen](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances#bare-metal-server-settings)

## Updates für Add-on-Services

### IBM Cloud Private Hosted

Der Service "{{site.data.keyword.cloud_notm}} Private Hosted" ist nun für VMware vCenter Server with Hybridity Bundle-Instanzen zusätzlich zu VMware vCenter Server-Instanzen verfügbar, die in V2.5 oder höheren Releases bereitgestellt werden bzw. für die ein Upgrade auf eine entsprechende Version durchgeführt wurde. Sie können jetzt eine vCenter Server-Instanz oder vCenter Server with Hybridity Bundle-Instanz mit integriertem Service bestellen. Sie können den Service auch nach der Erstbereitstellung zu einer vorhandenen vCenter Server-Instanz oder einer vCenter Server with Hybridity Bundle-Instanz hinzufügen.

Weitere Informationen finden Sie in den folgenden Abschnitten:
* [{{site.data.keyword.cloud_notm}} Private Hosted - Übersicht](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_overview)
* [{{site.data.keyword.cloud_notm}} Private Hosted bestellen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_ordering)

### Mission Critical VMware on IBM Cloud

Der Service "Mission Critical VMware on {{site.data.keyword.cloud_notm}}" ist nun für Instanzen verfügbar, die in V2.7 oder höheren Releases bereitgestellt werden bzw. für die ein Upgrade auf eine entsprechende Version durchgeführt wurde.

Mission Critical VMware on {{site.data.keyword.cloud_notm}} bietet eine Cloudarchitektur mit mehreren Zonen, die Unternehmen dabei unterstützt, Ausfallzeiten für Cloudanwendungen zu verhindern und Failover-Funktionen in einer Cloudregion zu automatisieren. Mit dieser Cloudarchitektur können Sie eine höhere Verfügbarkeit und Failover-Erfolgsquote erzielen, als es bei den meisten VMware-Clients mit lokalen Umgebungen oder konkurrierenden Cloudplattformen möglich ist.

Weitere Informationen enthält der Abschnitt [Mission Critical VMware on {{site.data.keyword.cloud_notm}} - Übersicht](/docs/services/vmwaresolutions/services?topic=vmware-solutions-mcv_overview).

### F5 on IBM Cloud

Wenn Sie jetzt den Service "F5 on {{site.data.keyword.cloud_notm}}" bestellen, können Sie auswählen, ob F5 die Lizenz über ein öffentliches Netz oder über ein privates Netz mit einem Proxy-Server anwenden soll. Weitere Informationen enthält der Abschnitt [F5 on {{site.data.keyword.cloud_notm}} bestellen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_ordering). 

### FortiGate Virtual Appliance on IBM Cloud

Im 3. Quartal 2018 hat Fortinet Änderungen an seinen Abonnementpaketen (Subscription Bundles) vorgenommen. Weitere Informationen enthält der Abschnitt [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} bestellen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_ordering). 

Für den Service "FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}", der in Cloud Foundation-Instanzen und vCenter Server-Instanzen mit V2.7 und höher bereitgestellt wird, wird FortiOS 6.0.3 zur Verfügung gestellt.

Wenn Sie FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} bestellen, können Sie auswählen, ob FortiGuard Lizenz- und Sicherheitsupdates über ein öffentliches Netz oder über ein privates Netz mit einem Proxy-Server anwenden soll. Weitere Informationen enthält der Abschnitt [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} bestellen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_ordering). 

### Updates für Servicekomponente "Zerto on IBM Cloud"

Für den Service "Zerto on {{site.data.keyword.cloud_notm}}", der in Cloud Foundation-Instanzen und vCenter Server-Instanzen mit V2.7 und höher bereitgestellt wird, wird nun Zerto Virtual Replication 6.0 Update 3 zur Verfügung gestellt. Weitere Informationen enthält der Abschnitt [Zerto on {{site.data.keyword.cloud_notm}} - Übersicht](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr).

### Integration von KMIP for VMware on IBM Cloud mit IBM Cloud Activity Tracker

Neben VMware-Instanzereignissen sind jetzt auch Ereignisse für die KMIP for VMware on {{site.data.keyword.cloud_notm}}-Instanz, wie z. B. Schlüsselerstellung, Schlüssellöschung und Schlüsselzugriff, in Ihre {{site.data.keyword.cloud_notm}} Activity Tracker-Instanz integriert. Weitere Informationen zu KMIP for VMware on {{site.data.keyword.cloud_notm}} enthält der Abschnitt [KMIP for VMware on {{site.data.keyword.cloud_notm}} - Übersicht](/docs/services/vmwaresolutions/services/kmip_considerations.html).

### KMIP for VMware on IBM Cloud - nicht mehr verwendet

(Aktualisiert am 14. Dezember 2018) Die aktuelle Version von KMIP for VMware on {{site.data.keyword.cloud_notm}} wird nicht weiter unterstützt. Weitere Informationen finden Sie unter [Kontaktaufnahme mit dem IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support).
{:deprecated}

## Neue und aktualisierte Dokumentation

### Referenzdokumentation zur Architektur

Die folgenden technischen Dokumente stehen nun im Abschnitt *Referenz* der Benutzerdokumentation zur Verfügung:

* [NSX Edge Services Gateway-Lösungsarchitektur](/docs/services/vmwaresolutions/archiref/nsx?topic=vmware-solutions-nsx_overview)
* [VMware Update Manager - Leitfaden](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-intro)
* [vCenter Server-Netzbetrieb - Leitfaden](/docs/services/vmwaresolutions/archiref/vcsnsxt?topic=vmware-solutions-vcsnsxt-intro)
* [vCenter Server and {{site.data.keyword.cloud_notm}} Private - Leitfaden](/docs/services/vmwaresolutions/archiref/vcsicp?topic=vmware-solutions-vcsicp-intro)
* [vCenter Server and IBM Kubernetes Service - Leitfaden](/docs/services/vmwaresolutions/archiref/vcsiks?topic=vmware-solutions-vcsiks-intro)
* [VMware und Concept Car "Skate Advisor" - Leitfaden](/docs/services/vmwaresolutions/archiref/vcscar?topic=vmware-solutions-vcscar-intro)
* [VMware - Modernisierung der Anwendung "Stock Trader"](/docs/services/vmwaresolutions/archiref/vcscontent?topic=vmware-solutions-vcscontent-modjourney)

## Updates und Erweiterungen der Benutzerschnittstelle

Die Benutzerschnittstelle wurde aktualisiert und bietet die folgenden Erweiterungen:

* Die Registerkarte **Angepasst**, in der Sie das CPU-Modell und das RAM für {{site.data.keyword.baremetal_short_sing}}-Einstellungen angeben, wenn Sie Instanzen bestellen, wird in die Registerkarte **Skylake** und die Registerkarte **Broadwell** entsprechend dem Servertyp aufgeteilt, um Sie bei der Serverauswahl zu unterstützen.
* Die Optionen für **Vorkonfiguriert** für Bare-Metal-Serverkonfigurationen sind nicht mehr verfügbar.
* Die Spalte **Typ** ist jetzt in der Tabelle **vCenter Server-Instanzen** auf der Seite **Bereitgestellte Instanzen** enthalten, um vCenter Server-, vCenter Server with Hybridity Bundle- und vCenter Limited Test Drive-Instanzen anzugeben.
* Es sind verschiedene Fehlernachrichten und QuickInfos verfügbar, die Sie bei der Auswahl der geeigneten Einstellung in der Benutzerschnittstelle unterstützen.
