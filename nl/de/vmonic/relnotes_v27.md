---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-29"

---

# Releaseinformationen für V2.7

Dieses Release stellt neue Funktionen, Komponentenaktualisierungen, Verbesserungen des Bedienungskomforts und Fehlerkorrekturen zur Verfügung. Eine Liste mit den in den unterschiedlichen Releases behobenen Problemen, den bekannten Problemen beim Produkt sowie Tipps für die Verwendung von {{site.data.keyword.vmwaresolutions_full}} finden Sie unter [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Unterstützung SAP-zertifizierter 6140-Server

Ab dem Release von V2.7 sind die folgenden neuen {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short_sing}}-CPU-Modelle für die Bereitstellung für VMware vCenter Server auf {{site.data.keyword.cloud_notm}}- und VMware vSphere on {{site.data.keyword.cloud_notm}}-Instanzen und -Clustern verfügbar:
* Dual Intel Xeon Gold 6140-Prozessor / 36 Kerne insgesamt, 2,3 GHzDual / 192 GB RAM
* Dual Intel Xeon Gold 6140-Prozessor / 36 Kerne insgesamt, 2,2 GHzDual / 384 GB RAM
* Dual Intel Xeon Gold 6140-Prozessor / 36 Kerne insgesamt, 2,3 GHzDual / 768 GB RAM

Weitere Informationen enthält der Abschnitt *{{site.data.keyword.baremetal_short_sing}}-Einstellungen* unter:
* [vCenter Server-Instanzen bestellen](../vcenter/vc_orderinginstance.html#bare-metal-server-settings)
* [Neue vSphere-Cluster bestellen](../vsphere/vs_orderinginstances.html#bare-metal-server-settings)

## Updates für Add-on-Services

### IBM Cloud Private Hosted

Der Service "{{site.data.keyword.cloud_notm}} Private Hosted" ist nun für VMware vCenter Server with Hybridity Bundle-Instanzen zusätzlich zu VMware vCenter Server-Instanzen verfügbar, die in V2.5 oder höheren Releases bereitgestellt werden bzw. für die ein Upgrade auf eine entsprechende Version durchgeführt wurde. Sie können jetzt eine vCenter Server-Instanz oder vCenter Server with Hybridity Bundle-Instanz mit integriertem Service bestellen oder den Service nach der Erstbereitstellung zu einer vorhandenen vCenter Server-Instanz oder einer vCenter Server with Hybridity Bundle-Instanz hinzufügen.

Weitere Informationen finden Sie in den folgenden Abschnitten:
* [ Übersicht über {{site.data.keyword.cloud_notm}} Private Hosted](../services/icp_overview.html)
* [{{site.data.keyword.cloud_notm}} Private Hosted bestellen](../services/icp_ordering.html)

### Mission Critical VMware on IBM Cloud

Der Service "Mission Critical VMware on {{site.data.keyword.cloud_notm}}" ist nun für Instanzen verfügbar, die in V2.7 oder höheren Releases bereitgestellt werden bzw. für die ein Upgrade auf eine entsprechende Version durchgeführt wurde.

Mission Critical VMware on {{site.data.keyword.cloud_notm}} bietet eine Cloudarchitektur mit mehreren Zonen, die Unternehmen dabei unterstützt, Ausfallzeiten für Cloudanwendungen zu verhindern und Failover-Funktionen in einer Cloudregion zu automatisieren. Mit dieser Cloudarchitektur können Sie eine höhere Verfügbarkeit und Failover-Erfolgsquote erzielen, als es bei den meisten VMware-Clients mit lokalen Umgebungen oder konkurrierenden Cloudplattformen möglich ist.

Weitere Informationen enthält der Abschnitt [Übersicht über Mission Critical VMware on {{site.data.keyword.cloud_notm}}](../services/mcv_overview.html).

### F5 on IBM Cloud

Wenn Sie jetzt den Service "F5 on {{site.data.keyword.cloud_notm}}" bestellen, können Sie auswählen, ob F5 die Lizenz über ein öffentliches Netz oder über ein privates Netz mit einem Proxy-Server anwenden soll. Weitere Informationen finden Sie unter [F5 on {{site.data.keyword.cloud_notm}} bestellen](../services/f5_ordering.html).

### FortiGate Virtual Appliance on IBM Cloud

Im 3. Quartal 2018 hat Fortinet Änderungen an seinen Abonnementpaketen (Subscription Bundles) vorgenommen. Weitere Informationen finden Sie unter [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} bestellen](../services/fortinetvm_ordering.html).

Für den Service "FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}", der in Cloud Foundation-Instanzen und vCenter Server-Instanzen mit V2.7 und höher bereitgestellt wird, wird FortiOS 6.0.3 zur Verfügung gestellt.

Wenn Sie darüber hinaus den Service "FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}" bestellen, können Sie auswählen, ob FortiGate die Lizenz- und Sicherheitsupdates über ein öffentliches Netz oder über ein privates Netz mit einem Proxy-Server anwenden soll. Weitere Informationen finden Sie unter [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} bestellen](../services/fortinetvm_ordering.html).

### Updates für Servicekomponente "Zerto on IBM Cloud"

Für den Service "Zerto on {{site.data.keyword.cloud_notm}}", der in Cloud Foundation-Instanzen und vCenter Server-Instanzen mit V2.7 und höher bereitgestellt wird, wird nun Zerto Virtual Replication 6.0 Update 3 zur Verfügung gestellt. Weitere Informationen enthält der Abschnitt [Übersicht über Zerto on {{site.data.keyword.cloud_notm}}](../services/addingzertodr.html).

### Integration von KMIP for VMware on IBM Cloud mit IBM Cloud Activity Tracker

Neben VMware-Instanzereignissen sind jetzt auch Ereignisse für Ihre KMIP for VMware on {{site.data.keyword.cloud_notm}}-Instanz, wie z. B. Schlüsselerstellung, Schlüssellöschung und Schlüsselzugriff, in Ihre {{site.data.keyword.cloud_notm}} Activity Tracker-Instanz integriert. Weitere Informationen zu KMIP for VMware on {{site.data.keyword.cloud_notm}} enthält der Abschnitt [Übersicht über KMIP for VMware on {{site.data.keyword.cloud_notm}}](../services/kmip_considerations.html).

## Neue und aktualisierte Dokumentation

### Referenzdokumentation zur Architektur

Die folgenden technischen Dokumente stehen nun im Abschnitt *Referenz* der Benutzerdokumentation zur Verfügung:

* [NSX Edge Services Gateway-Lösungsarchitektur](../archiref/nsx/nsx_overview.html)
* [VMware Update Manager - Leitfaden](../archiref/vum/vum-intro.html)
* [vCenter Server Networking - Leitfaden](../archiref/vcsnsxt/vcsnsxt-intro.html)
* [vCenter Server and {{site.data.keyword.cloud_notm}} Private - Leitfaden](../archiref/vcsicp/vcsicp-intro.html)
* [vCenter Server and IBM Kubernetes Service - Leitfaden](../archiref/vcsiks/vcsiks-intro.html)
* [VMware and Skate Advisor Concept Car - Leitfaden](../archiref/vcscar/vcscar-intro.html)
* [VMware: Die Modernisierung der Anwendung 'Stock Trader'](../archiref/vcscontent/vcscontent-modjourney.html)

Manche Referenzdokumente zur Architektur sind nur in Englisch verfügbar.

## Updates und Erweiterungen der Benutzerschnittstelle

Die Benutzerschnittstelle wurde aktualisiert und bietet die folgenden Erweiterungen:

* Die ursprüngliche Registerkarte **Angepasst**, in der Sie das CPU-Modell und das RAM für {{site.data.keyword.baremetal_short_sing}}-Einstellungen angeben, wenn Sie Instanzen bestellen, wurde in die Registerkarte **Skylake** und die Registerkarte **Broadwell** entsprechend dem Servertyp aufgeteilt, um die Serverauswahl zu vereinfachen.
* Die Spalte **Typ** ist jetzt in der Tabelle **vCenter Server-Instanzen** auf der Seite **Bereitgestellte Instanzen** enthalten, um vCenter Server-, vCenter Server with Hybridity Bundle- und vCenter Limited Test Drive-Instanzen anzugeben.
* Es sind verschiedene Fehlernachrichten und QuickInfos verfügbar, die Sie bei der Auswahl der geeigneten Einstellung in der Benutzerschnittstelle unterstützen.
