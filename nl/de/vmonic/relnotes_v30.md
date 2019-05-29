---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-03"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Releaseinformationen für Version 3.0
{: #relnotes_v30}

Dieses Release stellt neue Funktionen, Komponentenaktualisierungen, Verbesserungen des Bedienungskomforts und Fehlerkorrekturen zur Verfügung. Eine Liste mit den in den unterschiedlichen Releases behobenen Problemen, den bekannten Problemen beim Produkt sowie Tipps für die Verwendung von {{site.data.keyword.vmwaresolutions_full}} finden Sie unter [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Ende der Unterstützung für VMware Cloud Foundation on IBM Cloud
{: #relnotes_v30-vcf-eos}

Um unsere Angebote für ein besseres Kundenerlebnis zu konsolidieren, umfasst die {{site.data.keyword.vmwaresolutions_short}}-Plattform ab dem 13. Mai 2019 keine VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} mehr.

In Zukunft werden alle Kunden auf VMware vCenter Server on {{site.data.keyword.cloud_notm}} verwiesen, unsere Flagschiff-VMware-Lösung für SDDC (Software-Defined Data Center, softwaredefiniertes Rechenzentrum) für {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}.

Vorhandene Kunden, die VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} verwenden, werden bei der Konvertierung in VMware vCenter Server on {{site.data.keyword.cloud_notm}} bis zum Enddatum des Unterstützungszeitraums am 13. Mai 2019 unterstützt.

Nach dem 13. Mai werden die Managementfunktionen für VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} so lange von der {{site.data.keyword.vmwaresolutions_short}}-Konsole eingefroren, bis sie in VMware vCenter Server on {{site.data.keyword.cloud_notm}} konvertiert wurden. Kunden, die sich dafür entschieden haben, dass ihre VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}-Instanz nicht auf VMware vCenter Server on {{site.data.keyword.cloud_notm}} migriert bzw. konvertiert werden soll, können über die Konsole der {{site.data.keyword.cloud_notm}}-Infrastruktur auf ihre Instanzen zugreifen.

## Entfernte Unterstützung für Broadwell 2-CPU-Server
{: #relnotes_v30-broadwell}

Ab dem Release V3.0 sind Broadwell 2-CPU-Server nicht mehr für die Bereitstellung neuer vCenter Server-, vCenter Server with Hybridity Bundle-, vCenter Server with NSX-T- und vSphere on {{site.data.keyword.cloud_notm}}-Instanzen und -Cluster verfügbar. Sie können jedoch weiterhin Server zu vorhandenen Clustern hinzufügen.

## Erweiterungen der Netzdateisystemoperation
{: #relnotes_v30-nfs}

Ab dem Release V3.0 können Sie gleichzeitig NFS-Speicher und ESXi-Server zu Clustern hinzufügen, die sich im Status **Bereit** befinden, bzw. daraus entfernen. Sie können z. B. einen ESXi-Server in einem Cluster hinzufügen oder entfernen und einen NFS-Speicher in einem weiteren Cluster hinzufügen oder entfernen. Dies gilt für alle vCenter Server-Instanzen und vCenter Server with NSX-T-Instanzen.

## Updates für VMware vCenter Server-Instanzen
{: #relnotes_v30-vcs}

Mit diesem Release werden die folgenden Upgrades und Verbesserungen angewendet:

* vSphere ESXi 6.7 Update 1 (Build 6.7.0-13004448)
* vSphere ESXi 6.5 Update 2 (Build 6.5.0-13004031)
* vCenter Server Appliance 6.7 Update 1b (Build 6.7.0-11727113)
* Platform Services Controller 6.7 Update 1b (Build 6.7.0-11727113) 

Weitere Informationen Sie in der [vCenter Server-Teileliste](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom).

Windows-Software, die für Microsoft Active Directory-Services (AD) und DNS-Services (Domain Name System) bestellt wird, wird für beide Konfigurationsoptionen auf Windows Server 2016 aktualisiert: die VSIs (Virtual Server Instances) und die beiden hoch verfügbaren Windows-VMs. Weitere Informationen zum Auswählen Ihrer VMware-Komponenten finden Sie im Abschnitt [Software-BOM für vCenter-Serverinstanzen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_bom#vc_bom-software).

### Erweiterungen für vSAN-Speicher
{: #relnotes_v30-vcs-vsan}

* Wenn Sie vSAN-Speicher verwenden, können Sie jetzt bei Bedarf mehr als vier Bare-Metal-Server bestellen. Dies gilt für alle vCenter Server-, vCenter Server with Hybridity- und vCenter Server with NSX-T-Instanzen.
* Ab Release V3.0 wird ein M.2-Solid-State-Laufwerk mit der vSAN-Speicherinstanz bestellt. Wenn Sie die Option **Hohe Leistung mit Intel Optane** auswählen, können Sie bis zu 10 Kapazitätsplatten oder insgesamt 12 Kapazitätsplatten bestellen.

Weitere Informationen finden Sie im Abschnitt *Speichereinstellungen* in:
* [vCenter Server-Instanzen bestellen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_orderinginstance#vc_orderinginstance-storage-settings)
* [vCenter Server with Hybridity Bundle-Instanzen bestellen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_hybrid_orderinginstance#vc_hybrid_orderinginstance-storage-settings)
* [vCenter Server with NSX-T-Instanzen bestellen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_nsx-t_orderinginstance#vc_nsx-t_orderinginstance-storage-settings)

## Updates für Add-on-Services
{: #relnotes_v30-services}

### HyTrust CloudControl on IBM Cloud
{: #relnotes_v30-services-htcc}

Im aktuellen Release wird HyTrust CloudControl 5.5 auf allen neu bereitgestellten Instanzen installiert. Weitere Informationen zu den neuen Funktionen in HyTrust CloudControl 5.5 finden Sie in der Veröffentlichung mit den [Neuerungen in HyTrust CloudControl Version 5.5](https://docs.hytrust.com/CloudControl/5.5.0/Online/Content/HTCC_Admin_Guide/_FrontMatter/Whats-New.html){:new_window}.

### HyTrust DataControl on IBM Cloud
{: #relnotes_v30-services-htdc}

Das aktuelle Release installiert HyTrust DataControl 4.3 auf allen neu bereitgestellten Instanzen. Weitere Informationen zu den neuen Funktionen in HyTrust DataControl 4.3 finden Sie in der Veröffentlichung mit den [Neuerungen in HyTrust DataControl 4.3](https://docs.hytrust.com/DataControl/4.3/Online/Content/Books/aaCommon/New-Changed-4x.html){:new_window}.

### HyTrust KeyControl on IBM Cloud
{: #relnotes_v30-services-htkc}

Das aktuelle Release installiert HyTrust KeyControl 4.3 auf allen neu bereitgestellten Instanzen. Weitere Informationen zu den neuen Funktionen in HyTrust KeyControl 4.3 finden Sie in der Veröffentlichung mit den [Neuerungen in HyTrust KeyControl 4.3](https://docs.hytrust.com/DataControl/4.3/Online/Content/Books/aaCommon/New-Changed-4x.html){:new_window}.

### IBM Cloud Private Hosted
{: #relnotes_v30-services-icp}

Im Rahmen des aktuellen Release wird {{site.data.keyword.cloud_notm}} Private Hosted 3.1.2 gemeinsam mit {{site.data.keyword.cloud_notm}} Automation Manager 3.1.2 auf allen neu bereitgestellten Instanzen installiert.

Weitere Informationen zu den neuen Funktionen in {{site.data.keyword.cloud_notm}} Private Version 3.1.2 finden Sie im Abschnitt [Neuerungen in {{site.data.keyword.cloud_notm}} Private Version 3.1.2](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_3.1.2/getting_started/whats_new.html){:new_window}.
Weitere Informationen zu den neuen Funktionen in {{site.data.keyword.cloud_notm}} Automation Manager 3.1.2 finden Sie im Abschnitt [Neuerungen in {{site.data.keyword.cloud_notm}} Automation Manager 3.1.2](https://www.ibm.com/support/knowledgecenter/en/SS2L37_3.1.2.0/cam_whatisnew.html){:new_window}.

### KMIP for VMware on IBM Cloud
{: #relnotes_v30-services-kmip}

Zwei neue Endpunkte sind jetzt in London und USA (Osten) für den KMIP for VMware on {{site.data.keyword.cloud_notm}}-Service verfügbar. Weitere Informationen enthält der Abschnitt zur [Konfiguration des Service "KMIP for VMware on {{site.data.keyword.cloud_notm}}"](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_ordering-config#kmip_standalone_ordering-config).

### IBM Spectrum Protect Plus on IBM Cloud
{: #relnotes_v30-services-spp}

Das aktuelle Release installiert IBM Spectrum Protect™ Plus V10.1.3 auf allen neu bereitgestellten Instanzen. Weitere Informationen zu den neuen Funktionen in IBM Spectrum Protect Plus V10.1.3 finden Sie unter [Updates für IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.3/spp/r_techchg_spp.html){:new_window}.

### Zerto on IBM Cloud
{: #relnotes_v30-services-zerto}

Sie können Zerto on {{site.data.keyword.cloud_notm}} nur für rein private Instanzen hinzufügen. Wenn Sie Zerto auf solchen Instanzen installieren möchten, müssen Sie Ihren eigenen Proxy-Server einrichten und zudem die Call-Home-Funktion für Zerto konfigurieren. Weitere Informationen dazu finden Sie im Abschnitt zum [Bestellen von Zerto on {{site.data.keyword.cloud_notm}} für rein private Instanzen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-zerto_ordering#zerto_ordering-private-only).

## Neue und aktualisierte Dokumentation

* In der Dokumentation finden Sie jetzt unterstützende Schritte für das Upgrade von {{site.data.keyword.vmwaresolutions_short}}-Komponenten auf VMware vSphere 6.7. Dieses Upgrade ist erforderlich, wenn Sie weiterhin von der {{site.data.keyword.vmwaresolutions_short}}-Automatisierung profitieren möchten. Weitere Informationen finden Sie im Abschnitt [Upgrade von vCenter Server vSphere-Software von VMware vSphere 6.5 auf Version 6.7 durchführen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_vsphere_upgrade#vc_vsphere_upgrade).
* Es ist jetzt eine Referenzdokumentation verfügbar, um Ihnen Benutzer-IDs zur Verfügung zu stellen, die {{site.data.keyword.vmwaresolutions_short}} für die Verwendung im Rahmen der {{site.data.keyword.cloud_notm}}-Automatisierung verwaltet. In den Systemprotokollen für Ihre Instanz können Sie zudem dort möglicherweise enthaltene Nachrichten überprüfen. Weitere Informationen finden Sie im Abschnitt zu den [IBM Benutzer-IDs](/docs/services/vmwaresolutions?topic=vmware-solutions-audit_user_ids) und zu den [Instanzprotokollnachrichten](/docs/services/vmwaresolutions?topic=vmware-solutions-audit_messages).
* Die Berechtigung **Warmstart/Steuerung** wurde der Tabelle hinzugefügt, in der die erforderlichen Berechtigungen für das IBM Cloud-Infrastrukturkonto beschrieben werden. Weitere Informationen finden Sie unter [Berechtigungen für das {{site.data.keyword.cloud_notm}}-Infrastrukturkonto](/docs/services/vmwaresolutions/services?topic=vmware-solutions-slaccountrequirement#slaccountrequirement-permissions).
* Für die folgenden APIs ist eine neue Referenzdokumentation verfügbar. Weitere Informationen finden Sie in [API-Referenz](https://cloud.ibm.com/apidocs/vmware-solutions){:new_window}.
  * Auflisten aller Protokollnachrichten für eine angegebene VMware vCenter Server-Instanz
  * Hinzufügen von gemeinsam genutztem Speicher zu einem angegebenen Cluster
  * Löschen von NFS-Speicher aus einem angegebenen Cluster

## Updates und Erweiterungen der Benutzerschnittstelle
{: #relnotes_v30-ui}

Die Benutzerschnittstelle wurde aktualisiert und bietet die folgenden Erweiterungen:

* Es sind verschiedene Fehlernachrichten und QuickInfos verfügbar, die Sie bei der Auswahl der geeigneten Einstellung in der Benutzerschnittstelle unterstützen.
