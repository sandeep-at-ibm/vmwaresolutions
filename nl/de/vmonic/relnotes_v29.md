---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-25"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Releaseinformationen für Version 2.9
{: #relnotes_v29}

Dieses Release stellt neue Funktionen, Komponentenaktualisierungen, Verbesserungen des Bedienungskomforts und Fehlerkorrekturen zur Verfügung. Eine Liste mit den in den unterschiedlichen Releases behobenen Problemen, den bekannten Problemen beim Produkt sowie Tipps für die Verwendung von {{site.data.keyword.vmwaresolutions_full}} finden Sie unter [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## VMware vCenter Server on IBM Cloud with NSX-T
{: #relnotes_v29-vcs-nsx-t}

In diesem Release wird das Angebot VMware vCenter Server on {{site.data.keyword.cloud_notm}} with NSX-T für den Konzeptnachweis oder Sandboxtests eingeführt. vCenter Server with NSX-T ist eine privat gehostete Cloud, die Ihnen den Test der VMware-Netzwerkplattform der nächsten Generation, NSX-T, ermöglicht.

Weitere Informationen finden Sie in den folgenden Abschnitten:

* [Übersicht über vCenter Server with NSX-T](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_overview)
* [vCenter Server with NSX-T-Instanzen bestellen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_orderinginstance)

## Ende der Unterstützung für VMware Cloud Foundation on IBM Cloud
{: #relnotes_v29-vcf-eos}

Um unsere Angebote für ein besseres Kundenerlebnis zu konsolidieren, bietet {{site.data.keyword.cloud_notm}} ab dem 13. Mai 2019 keine Unterstützung mehr für VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}.
 
In Zukunft werden alle Kunden auf VMware vCenter Server on {{site.data.keyword.cloud_notm}} verwiesen; ein Angebot, das mehr Flexibilität in Bezug auf Speicher- und Lizenzoptionen bietet.
Vorhandene Kunden, die VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} verwenden, werden bei der Migration auf VMware vCenter Server on {{site.data.keyword.cloud_notm}} bis zum Enddatum des Unterstützungszeitraums am 13. Mai 2019 unterstützt.

Nach dem 13. Mai werden die Managementfunktionen für VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} aus der {{site.data.keyword.vmwaresolutions_short}}-Konsole entfernt. Auf Instanzen, die nicht auf VMware vCenter Server on {{site.data.keyword.cloud_notm}} migriert wurden, kann über die IBM Cloud-Infrastrukturkonsole zugegriffen werden.

Kunden werden vom {{site.data.keyword.cloud_notm}}-Support vor dem 25. März 2019 kontaktiert, um die Migration von VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} zu starten. Weitere Informationen zu Migrationsoptionen für vorhandene Kunden finden Sie auf der [Wikiseite für {{site.data.keyword.vmwaresolutions_short}}](https://w3-connections.ibm.com/wikis/home?lang=en-us#!/wiki/Wf58c4c538dbf_45b4_b7a7_5003d0ceb79b/page/IBM%20Cloud%20for%20VMware%20Solutions){:new_window}.
 
Kunden können ihre vorhandene VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}-Instanz in der [{{site.data.keyword.vmwaresolutions_short}}-Konsole](https://cloud.ibm.com/infrastructure/vmware-solutions/console/gettingstarted) anzeigen.

## Unterstützung für VMware vSphere 6.7 Update 1
{: #relnotes_v29-vsphere}

Sie haben nun die Möglichkeit, VMware vSphere Version 6.7 Update 1 mit Ihren VMware vCenter Server-, VMware vCenter Server with Hybridity Bundle- und VMware vSphere on {{site.data.keyword.cloud_notm}}-Instanzen zu bestellen.

Darüber hinaus werden jetzt Single-node Trial-Instanzen für Migration und Anwendungsmodernisierung mit vSphere Enterprise Plus 6.7u1 bestellt.

vSphere Enterprise Plus 6.7u1 ist nur für Broadwell und Skylake {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} verfügbar.

Weitere Informationen finden Sie in den Abschnitten zu den _Lizenzeinstellungen_ unter:

* [vCenter Server-Instanzen bestellen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [vCenter Server with Hybridity Bundle-Instanzen bestellen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance)
* [Neue vSphere-Cluster bestellen](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)

## Ende der Unterstützung für VLAN-Spanning
{: #relnotes_v29-vlan}

Ab August 2019 wird VLAN-Spanning nicht mehr von {{site.data.keyword.vmwaresolutions_short}} unterstützt. Bis Ende Juli 2019 müssen Sie Ihr {{site.data.keyword.cloud_notm}}-Infrastrukturkonto in ein VRF-Konto (Virtual Routing and Forwarding) konvertieren und Serviceendpunkte für Ihr Konto aktivieren.

Weitere Informationen finden Sie in den folgenden Abschnitten:

* [Virtual Routing and Forwarding (VRF) on IBM Cloud - Übersicht](/docs/infrastructure/direct-link?topic=direct-link-overview-of-virtual-routing-and-forwarding-vrf-on-ibm-cloud)
* [Konto für die Verwendung von Serviceendpunkten aktivieren](/docs/services/service-endpoint?topic=service-endpoint-getting-started#cs_cli_install_steps)

## Unterstützung für Anwendungsprogrammierschnittstellen
{: #relnotes_v29-api}

Anwendungsprogrammierschnittstellen (APIs) sind jetzt verfügbar, um Instanzen bereitzustellen, Instanzen zu löschen und ESXi-Server und Cluster hinzuzufügen und zu entfernen.

Zudem ist die REST-API-Dokumentation im Abschnitt *Referenz* der Benutzerdokumentation verfügbar. Weitere Informationen finden Sie unter [{{site.data.keyword.vmwaresolutions_short}}-API](https://cloud.ibm.com/apidocs/vmware-solutions).

## Updates für VMware vCenter Server-Instanzen
{: #relnotes_v29-vcs}

Mit diesem Release werden die folgenden Upgrades und Verbesserungen angewendet:

* vSphere ESXi 6.7 Update 1 (Build 6.7.0-11675023)
* vSphere ESXi 6.5 Update 2 (Build 6.5.0-11925212)
* vSphere 6.7 Distributed vSwitch 6.6.0
* vSphere 6.5 Distributed vSwitch 6.5.0
* vCenter Server Appliance 6.7 U1 (Build 6.7.0-10244745)
* vSAN 6.7.0 U1
* NSX for vSphere 6.4.4 (Build 11197766)
* NSX-T for vSphere 2.4

Weitere Informationen zum Auswählen Ihrer VMware-Komponenten finden Sie unter [vCenter Server-Teileliste](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom).

### Updates für Rechenzentren
{: #relnotes_v29-dc}

Die folgenden neuen Rechenzentren sind für die Bereitstellung verfügbar: **FRA-05 - Frankfurt** und **LON-05 - London**. Weitere Informationen finden Sie unter [Voraussetzungen und Planung für vCenter Server-Instanzen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning).

### Erweiterungen für ESXi-Server
{: #relnotes_v29-vcs-esxi}

* Das SSH-Protokoll (Secure Shell) wird jetzt vor der Instanzbereitstellung für ESXi-Server inaktiviert. Wenn Sie SSH aktivieren möchten, lesen Sie die Informationen im Abschnitt [SSH über den vSphere-Web-Client aktivieren](https://pubs.vmware.com/vsphere-6-5/index.jsp?topic=%2Fcom.vmware.vcli.getstart.doc%2FGUID-C3A44A30-EEA5-4359-A248-D13927A94CCE.html).
* Ab Release V2.9 sind die folgenden ESXi-Serveroperationen verfügbar:

   * Einem vorhandenen Cluster neue ESXi-Server hinzufügen, während die Server sich im Wartungsmodus befinden. Virtuelle Maschinen werden erst dann auf die neuen Server migriert, wenn Sie den Wartungsmodus für die Server beenden.
   * ESXi-Server für mehre Cluster in Ihrer Instanz gleichzeitig hinzufügen oder entfernen.

Weitere Informationen finden Sie unter [Kapazität für vCenter Server-Instanzen erweitern und verringern](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers).

### Speichergröße für Network File System
{: #relnotes_v29-vcs-nfs}

Bei Bestellungen von vCenter Server-Instanzen können Sie jetzt bis zu 24 TB gemeinsam genutzten NFS-Speicher (Network File System) für die Leistungsstufen 0,25, 2 und 4 IOPS/GB hinzufügen.

Die Leistungsstufe 10 IOPS/GB ist weiterhin auf eine maximale Kapazität von 4 TB pro gemeinsam genutzter Dateiressource begrenzt.
{:note}

## Updates für Add-on-Services
{: #relnotes_v29-services}

### Caveonix RiskForesight on IBM Cloud
{: #relnotes_v29-services-caveonix}

Der Service "Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}" ist jetzt für VMware vCenter Server-Instanzen verfügbar, die in V2.9 oder höheren Releases bereitgestellt oder auf diese Versionen aktualisiert werden. Dieser Service kann Sie durch proaktive Überwachung und automatisierte Abwehrkontrollen bei der Verwaltung von Cyber- und Konformitätsrisiken unterstützen, um vor Bedrohungen zu schützen und die Branchenvorschriften oder Regierungsverordnungen zu erfüllen.

Sie können vCenter Server-Instanzen mit dem Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}-Service bestellen oder diesen Service zu einem späteren Zeitpunkt Ihren vorhandenen vCenter Server-Instanzen über die Registerkarte **Services** auf der Seite mit den Instanzdetails hinzufügen.

Sie können auch eine eigenständige Caveonix RiskForesight-Lizenz bestellen, ohne sie einer VMware-Instanz für die Lizenzierung und Aktivierung Ihrer lokalen Workloads zuzuordnen.

Weitere Informationen finden Sie in den folgenden Abschnitten:
* [Hinweise zu Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_considerations)
* [Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} bestellen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_ordering)
* [Hinweise zu Caveonix-Lizenzen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_license_considerations)
* [Caveonix-Lizenzen bestellen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_license_ordering)

### F5 on IBM Cloud
{: #relnotes_v29-services-f5}

Im aktuellen Release wird F5-BigIP VE V14.1.0.2 auf allen neu bereitgestellten Instanzen installiert. Weitere Informationen zu neuen Funktionen in F5-BigIP VE V14.1.0.2 finden Sie unter [Release Note: BIG-IP 14.1.0 New and Installation](https://support.f5.com/kb/en-us/products/big-ip_ltm/releasenotes/product/relnote-bigip-14-1-0.html){:new_window}.

### HyTrust CloudControl on IBM Cloud
{: #relnotes_v29-services-htcc}

Im aktuellen Release wird HyTrust CloudControl 5.4.2 auf allen neu bereitgestellten Instanzen installiert. Weitere Informationen zu neuen Funktionen in HyTrust CloudControl 5.4.2 finden Sie unter [HyTrust CloudControl Release Notes Version 5.4.2](https://docs.hytrust.com/CloudControl/5.4.2/Online/index.html#HTCC_Admin_Guide/_FrontMatter/Whats-New.html%3FTocPath%3D_____2){:new_window}.

### KMIP for VMware on IBM Cloud
{: #relnotes_v29-services-kmip}

Zwei neue Endpunkte sind jetzt in Sydney für den KMIP for VMware on {{site.data.keyword.cloud_notm}}-Service verfügbar. Weitere Informationen enthält der Abschnitt zur [Konfiguration des Service "KMIP for VMware on {{site.data.keyword.cloud_notm}}"](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_ordering#kmip_standalone_ordering-config).

(Aktualisiert am 09. April 2019) Bisher hat KMIP for VMware on {{site.data.keyword.cloud_notm}} IBM Key Protect for {{site.data.keyword.cloud_notm}} verwendet, um Verschlüsselungsschlüssel zu erstellen, zu verschlüsseln und zu entschlüsseln. Ab Version 2.9 kann KMIP for VMware on {{site.data.keyword.cloud_notm}} auch {{site.data.keyword.cloud_notm}} Hyper Protect Crypto Services, eine vollständige Gruppe von Verschlüsselungs- und Schlüsselverwaltungsservices, verwenden, um Verschlüsselungsschlüssel zu verwalten, die von VMware in {{site.data.keyword.cloud_notm}} verwendet werden. Weitere Informationen finden Sie in der [Übersicht zu KMIP for VMware on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations) und im Abschnitt zu [{{site.data.keyword.cloud_notm}} Hyper Protect Crypto Services](/docs/services/hs-crypto?topic=hs-crypto-get-started).

### Veeam on IBM Cloud
{: #relnotes_v29-services-veeam}

Im aktuellen Release wird Veeam Backup and Replication 9.5 Update 4 auf allen neu bereitgestellten Instanzen installiert. Weitere Informationen zu den neuen Funktionen in Veeam 9.5u4 finden Sie unter [Release information for Veeam Backup and Replication 9.5 Update 4](https://www.veeam.com/kb2878){:new_window}.

### Zerto on IBM Cloud
{: #relnotes_v29-services-zerto}

Im aktuellen Release wird Zerto Virtual Replication 6.5 Update 3 auf allen neu bereitgestellten Instanzen installiert. Weitere Informationen zu den neuen Funktionen in Zerto Virtual Replication 6.5 Update 3 finden Sie unter [Release notes for Zerto Virtual Replication V6.5 Update 3](http://s3.amazonaws.com/zertodownload_docs/Latest/Zerto%20Virtual%20Replication%20Release%20Notes.pdf){:new_window}.

## Updates und Erweiterungen der Benutzerschnittstelle
{: #relnotes_v29-ui}

Die Benutzerschnittstelle wurde aktualisiert und bietet die folgenden Erweiterungen:

* Auf der Seite **Infrastruktur** enthält die neue Tabelle **Netzschnittstelle** Details zu VLAN, Teilnetz und IP-Adressen für Ihren Cluster.
* Es sind verschiedene Fehlernachrichten und QuickInfos verfügbar, die Sie bei der Auswahl der geeigneten Einstellung in der Benutzerschnittstelle unterstützen.
