---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-26"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Single-node Trial for VMware vCenter Server on IBM Cloud-Instanzen bestellen und löschen

Single-node Trial for VMware vCenter Server on {{site.data.keyword.cloud}} ist eine gehostete private Single-Tenant-Cloud, die den VMware vSphere-Stack als Service bereitstellt. Während die vom Client verwaltete Umgebung in der Regel mit mindestens drei Knoten bereitgestellt wird, bietet diese Testversion für einen einzelnen Knoten eine kostengünstige Möglichkeit, die Vorteile einer Hybrid-Cloud-Implementierung zu nutzen.

Die Testversion eignet sich ideal für einen Konzeptnachweis, der zeigt, wie schnell eine automatisierte Erstbereitstellung mit den IBM Verfahren durchgeführt und wie komfortabel Workloads, die nicht zu Produktionszwecken dienen, in die Cloud verlagert werden können. Mit der VMware Hybrid Cloud Extension (HCX) können Sie Ihr lokales Rechenzentrumsnetz sicher in das {{site.data.keyword.CloudDataCent_notm}} erweitern, während die Netzkomplexität der Verbindungskonfiguration reduziert wird. HCX abstrahiert die zugrunde liegenden Netzressourcen, um Daten über das öffentliche Internet im Tunnelungsverfahren zu übertragen, sodass Sie die Workloads nahtlos bidirektional verschieben können, ohne den virtuellen Maschinen (VMs) neue IPs zuzuordnen. Bei HCX muss VMware NSX nicht lokal installiert sein und es besteht Abwärtskompatibilität mit älteren Versionen von vSphere.  

Die Testversion für Einzelknoten (Single-node Trial) dient nur für den Konzeptnachweis. Die Umgebung ist nicht für Workloads im Produktionsbetrieb geeignet. Managementfunktionen wie das Hinzufügen und Entfernen von Hosts und Clustern, das Bestellen zusätzlicher Add-on-Services und das Anwenden von Updates werden nicht unterstützt.
{:important}

Diese Testversion ist für eine Nutzung von bis zu 90 Tagen vorgesehen. Wenn Sie das Testen abschlossen haben, können Sie die Umgebung löschen und anschließend eine hoch verfügbare Umgebung einrichten, die Ihren Kapazitätsanforderungen entspricht. Weitere Informationen finden Sie unter [vCenter Server with Hybridity Bundle-Instanzen bestellen](vc_hybrid_orderinginstance.html).

## Technische Spezifikationen für Single-node Trial for vCenter Server-Instanzen

Ihre Single-node Trial for vCenter Server-Instanz enthält die folgenden Komponenten:

Verfügbarkeit und Preisgestaltung standardisierter Hardwarekonfigurationen können abhängig vom {{site.data.keyword.CloudDataCent_notm}}, das für die Bereitstellung ausgewählt wird, variieren.
{:note}

### Bare Metal Server

Ein Dual Intel Xeon Gold 5120-Prozessor (28 Kerne, 2,20 GHz) mit 384 GB RAM.

### Netzbetrieb

Die folgenden Netzkomponenten werden bestellt:
*  10-Gbps-Uplinks für öffentliche und private Netze
*  3 VLANs (virtuelle LANs): 1 öffentliches VLAN und 2 private VLANs
*  1 VXLAN (Virtual eXtensible LAN) mit einem verteilten logischen Router (Distributed Logical Router, DLR) für die potenzielle Ost-West-Kommunikation zwischen lokalen Workloads, die mit Netzen der Schicht 2 (L2) verbunden sind. Das VXLAN wird als Muster für die Routingtopologie bereitgestellt, das Sie ändern, als Ausgangspunkt für Erstellungen verwenden oder entfernen können. Sie können außerdem Sicherheitszonen hinzufügen, indem Sie zusätzliche VXLANs an neue logische Schnittstellen im DLR anhängen.
*  2 VMware NSX Edge Services Gateways:
  * 1 sicheres VMware NSX Edge Services Gateway (ESG) für Management-Services für abgehenden HTTPS-Managementdatenverkehr, das von IBM im Rahmen der Managementnetztypologie bereitgestellt wird. Dieses ESG wird von den IBM Management-VMs für die Kommunikation mit bestimmten externen IBM Managementkomponenten verwendet, die mit der Automatisierung zusammenhängen. Weitere Informationen finden Sie unter [Netz zur Verwendung des vom Kunden verwalteten ESG konfigurieren](../vcenter/vc_esg_config.html#configuring-your-network-to-use-the-customer-managed-nsx-esg-with-your-vms).

    Dieses ESG ist für Sie weder zugänglich, noch können Sie es verwenden. Wenn Sie es ändern, sind Sie möglicherweise nicht mehr in der Lage, die vCenter Server with Hybridity Bundle-Instanz über die {{site.data.keyword.vmwaresolutions_short}}-Konsole zu verwalten. Beachten Sie außerdem, dass die Verwendung einer Firewall oder die Inaktivierung der ESG-Kommunikation mit den externen IBM Managementkomponenten dazu führt, dass {{site.data.keyword.vmwaresolutions_short}} unbrauchbar wird.
    {:important}
  * 1 sicheres vom Kunden verwaltetes VMware NSX Edge Services Gateway für eingehenden und abgehenden HTTPS-Workloaddatenverkehr, das von IBM als Vorlage bereitgestellt wird und von Ihnen geändert werden kann, um den VPN-Zugriff oder den öffentlichen Zugriff zu ermöglichen. Weitere Informationen finden Sie im Abschnitt [Stellt das vom Kunden verwaltete NSX Edge ein Sicherheitsrisiko dar?](../vmonic/faq.html#does-the-customer-managed-nsx-edge-pose-a-security-risk-)

Weitere Informationen zu Netzkomponenten, die bei der Bereitstellung des Service "HCX on {{site.data.keyword.cloud_notm}}" bestellt werden, finden Sie im Abschnitt [Übersicht über HCX on {{site.data.keyword.cloud_notm}}](../services/hcx_considerations.html).

### Virtual Server-Instanzen

Die folgenden VSIs (Virtual Server-Instanzen) werden bestellt:

* Eine VSI für IBM CloudBuilder, der nach vollständiger Bereitstellung der Instanz beendet wird.
* Eine VSI von Microsoft Windows Server für Microsoft Active Directory (AD) wird bereitgestellt und kann zur Suche verwendet werden. Die Virtual Server-Instanz (VSI) dient als DNS für die Instanz, auf der die Hosts und virtuellen Maschinen registriert sind.

### Von IBM bereitgestellte Lizenzen und Gebühren

Ihre Bestellung der Single-node Trial for vCenter Server-Instanz enthält die folgenden Lizenzen:

* VMware vSphere Enterprise Plus 6.5u1
* VMware vCenter Server 6.5
* VMware NSX Service Providers Advanced Edition 6.4

Single-node Trial for vCenter Server-Instanzen bieten keine BYOL-Unterstützung (BYOL = Bring Your Own License; d. h. Verwendung der eigenen Lizenz).
{:note}

Es können zusätzliche Support- und Servicegebühren anfallen.

## Technische Spezifikationen für HCX on IBM Cloud

Weitere Informationen zu technischen Spezifikationen und Hinweise zu HCX on {{site.data.keyword.cloud_notm}} finden Sie im Abschnitt [Übersicht über VMware HCX on IBM Cloud](../services/hcx_considerations.html).

## Voraussetzungen und Planung für die Bestellung von Single-node Trial for vCenter Server-Instanzen

Sie müssen die folgenden Tasks ausführen:
* Das {{site.data.keyword.cloud_notm}}-Konto, das Sie verwenden, muss bestimmte Voraussetzungen erfüllen. Weitere Informationen finden Sie unter [Voraussetzungen für das {{site.data.keyword.cloud_notm}}-Konto](../vmonic/slaccountrequirement.html).
*  Konfigurieren Sie die Berechtigungsnachweise für die {{site.data.keyword.cloud_notm}}-Infrastruktur auf der Seite **Einstellungen**. Weitere Informationen finden Sie unter [Benutzerkonten und Einstellungen verwalten](../vmonic/useraccount.html).
* Machen Sie sich mit den Anforderungen für die Instanznamen vertraut:  
 * Es sind nur alphanumerische Zeichen und Bindestriche (-) zulässig.
 * Der Instanzname muss mit einem alphanumerischen Zeichen beginnen und enden.
 * Die maximale Länge des Instanznamens beträgt 10 Zeichen.
 * Der Instanzname muss innerhalb Ihres Kontos eindeutig sein.
* Prüfen Sie, welche {{site.data.keyword.CloudDataCents_notm}} die Anforderungen der physischen Infrastruktur erfüllen. Weitere Informationen finden Sie im Abschnitt *Verfügbarkeit des {{site.data.keyword.CloudDataCent_notm}}s* unter [Voraussetzungen und Planung für vCenter Server with Hybridity Bundle-Instanzen](../vcenter/vc_hybrid_planning.html#ibm-cloud-data-center-availability).
<!--* Ensure the that you meet the following prerequisites for the on-premises HCX instance:
 * VMware vSphere and vCenter 5.5 or higher
 * The VMware HCX Manager must reside in the same security zone as the on-premises vSphere environment
 * The VMware HCX Manager must be able to reach the public Internet to update firewall rules to allow outbound traffic
 * The vSphere environment must have distributed switches-->

## Vorgehensweise zum Bestellen von Single-node Trial for vCenter Server-Instanzen

1. Klicken Sie auf der Seite **Single-node Trial for VMware vCenter Server on {{site.data.keyword.cloud_notm}}** auf die Karte **vCenter Server** und dann auf **Fortsetzen**.
2. Führen Sie auf der Seite **Single-node Trial for VMware vCenter Server** die entsprechenden Schritte aus, um ein {{site.data.keyword.cloud_notm}}-Infrastrukturkonto anzufordern oder um Ihren bestehenden **Benutzernamen** und den **API-Schlüssel** anzugeben, und klicken Sie auf **Abrufen**.
3. Geben Sie den Instanznamen ein.
4. Wählen Sie das {{site.data.keyword.CloudDataCent_notm}} als Host für die Instanz aus.  

 Das {{site.data.keyword.CloudDataCent_notm}} ist bereits ausgewählt. Wählen Sie bei Bedarf einen anderen Standort für das {{site.data.keyword.CloudDataCent_notm}} aus.
{:note}
5. Überprüfen Sie im Fenster **Bestellübersicht** die Instanzkonfiguration, bevor Sie die Bestellung aufgeben.
   1. Überprüfen Sie die Einstellungen für die Instanz.
   2. Überprüfen Sie die geschätzten Kosten der Instanz. Klicken Sie auf **Preisdetails**, um eine PDF-Datei mit der Zusammenfassung zu generieren. Ihre Bestellübersicht können Sie speichern oder drucken, indem Sie rechts oben im PDF-Fenster auf das Symbol **Drucken** bzw. **Herunterladen** klicken.
   3. Klicken Sie auf den Link bzw. die Links für die Bedingungen, die für Ihre Bestellung gelten, und vergewissern Sie sich, dass Sie mit diesen Bedingungen einverstanden sind, bevor Sie die Instanz bestellen.
   4. Klicken Sie auf **Bereitstellung**.

### Ergebnisse

Die Bereitstellung der Instanz wird automatisch gestartet und der Aktivierungsschlüssel für den lokalen HCX on {{site.data.keyword.cloud_notm}}-Service wird bestellt.

#### Bereitstellungsprozess für HCX on IBM Cloud

Die Bereitstellung von HCX on {{site.data.keyword.cloud_notm}} ist automatisiert. Die folgenden Schritte werden durch den {{site.data.keyword.vmwaresolutions_short}}-Automatisierungsprozess ausgeführt:
1. Über die {{site.data.keyword.cloud_notm}}-Infrastruktur werden drei Teilnetze für HCX bestellt:
   * Ein privates portierbares Teilnetz für das HCX-Management.
   * Ein privates portierbares Teilnetz für HCX-Verbindungen. Dieses Teilnetz wird bei Auswahl der Option **Privates Netz** für den **HCX-Verbindungstyp** verwendet.
   * Ein öffentliches portierbares Teilnetz für die Aktivierung und Wartung mit VMware. Bei Auswahl der Option **Öffentliches Netz** für den **HCX-Verbindungstyp** wird dieses Teilnetz auch für HCX-Verbindungen verwendet.

   Die IP-Adresse in den für HCX bestellten Teilnetzen sollten durch die Automatisierung von VMware on {{site.data.keyword.cloud_notm}} verwaltet werden. Diese IP-Adressen können nicht zu VMware-Ressourcen wie VMs und NSX-Edges zugeordnet werden, die von Ihnen erstellt worden sind. Wenn Sie zusätzliche IP-Adressen für Ihre VMware-Artefakte benötigen, müssen Sie Ihre eigenen Teilnetze aus {{site.data.keyword.cloud_notm}} bestellen.
   {:important}
2. Wenn für **HCX-Verbindungstyp** die Option **Privates Netz** ausgewählt wurde, wird auf dem privaten verteilten virtuellen Switch (Distributed Virtual Switch, DVS) eine Portgruppe namens **SDDC-DPortGroup-HCX-Private** erstellt.
3. Es wird ein HCX-Aktivierungsschlüssel von VMware bestellt.
4. Es werden drei Ressourcenpools und VM-Ordner für HCX erstellt. Diese werden für die HCX-Verbindungen, die lokalen HCX-Komponenten sowie die fernen HCX-Komponenten benötigt.
5. Ein Paar von VMware NSX Edge Services Gateways (ESGs) für den HCX-Managementdatenverkehr wird bereitgestellt und konfiguriert:
   * Öffentliche und private Uplink-Schnittstellen werden unter Verwendung der bestellten Teilnetze konfiguriert.
   * Die ESGs werden als ein Paar sehr großer Edge-Appliances mit aktivierter Hochverfügbarkeit konfiguriert.
   * Die Firewallregeln und die Regeln für die Netzadressumsetzung (NAT-Regeln) werden konfiguriert, damit eingehender und abgehender HTTPS-Datenverkehr an den und vom HCX-Manager zulässig ist.
   * Die Regeln für den Lastausgleich und Ressourcenpools werden konfiguriert. Diese Regeln und Ressourcenpools werden für die Weiterleitung des HCX-bezogenen eingehenden Datenverkehrs an die entsprechenden virtuellen Appliances für den HCX-Manager, für vCenter Server und für Platform Services Controller (PSC) verwendet.
   * Ein SSL-Zertifikat zum Verschlüsseln des HCX-bezogenen eingehenden HTTPS-Datenverkehrs, der über die ESGs eintrifft, wird angewendet.

   Die HCX-Management-Edge ist für den HCX-Managementdatenverkehr zwischen den lokalen HCX-Komponenten und den cloudseitigen HCX-Komponenten dediziert. Die HCX-Management-Edge darf weder geändert noch für HCX-Netzerweiterungen verwendet werden. Erstellen Sie für Netzerweiterungen stattdessen separate Edges. Außerdem kann die Verwendung einer Firewall oder die Inaktivierung der HCX-Edge-Kommunikation mit den privaten IBM Managementkomponenten oder dem öffentlichen Internet die HCX-Funktionalität beeinträchtigen.
   {:important}

6. Der HCX-Manager on {{site.data.keyword.cloud_notm}} wird bereitgestellt, aktiviert und konfiguriert:
   * Der HCX-Manager wird bei vCenter Server registriert.
   * Der HCX-Manager, vCenter Server, PSC und der NSX-Manager werden konfiguriert.
   * Das HCX-Produktpaket wird konfiguriert.
   * Lokale und ferne HCX-Bereitstellungscontainer werden konfiguriert.
7. Der Hostname und die IP-Adresse des HCX-Managers werden beim DNS-Server von VMware vCenter Server on {{site.data.keyword.cloud_notm}} registriert.

#### Instanzdetails anzeigen

Sie können den Status der Bereitstellung prüfen, indem Sie die Instanzdetails anzeigen. Informationen zum Anzeigen von Instanzdetails finden Sie unter:

* [vCenter Server-Instanzen anzeigen](vc_viewinginstances.html)
* [Lokale VMware HCX on IBM Cloud-Instanzen anzeigen](../services/standalone_viewingserviceinstances.html)

Wenn die Instanz erfolgreich bereitgestellt wurde, werden die Komponenten, die in den Abschnitten *Technische Spezifikationen* dieses Themas beschrieben werden, auf Ihrer virtuellen VMware-Plattform installiert und der Aktivierungsschlüssel des lokalen HCX on {{site.data.keyword.cloud_notm}}-Service steht auf der {{site.data.keyword.cloud_notm}}-Detailseite zur Verfügung.

Der Status der Instanz ändert sich in **Bereit** und Sie erhalten eine Benachrichtigung per E-Mail.

### Nächste Schritte

Konfigurieren Sie den HCX on {{site.data.keyword.cloud_notm}}-Service und installieren Sie den lokalen Aktivierungsschlüssel.

1. Suchen Sie den lokalen Aktivierungsschlüssel auf der Seite **Bereitgestellte Instanzen**.
  1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Bereitgestellte Instanzen**.
  2. Suchen Sie in der Tabelle **vCenter Server-Instanzen** in der Spalte **Typ** nach der Single-node Trial-Instanz und notieren Sie den Instanznamen.
  3. Blättern Sie zur Tabelle **Lokale HCX-Instanzen** und suchen Sie in der Spalte **Name** nach der Instanz, die denselben Namen wie die Einzelknoteninstanz hat.
  4. Notieren Sie den Schlüssel im Feld **Aktivierungsschlüssel**.
2. Wechseln Sie zu [VMware HCX](https://hcx.vmware.com/#/vm-documentation), verwenden Sie den Aktivierungsschlüssel, um die lokale VMware HCX on {{site.data.keyword.cloud_notm}}-Instanz zu installieren, und schließen Sie den Installationsprozess ab. Weitere Informationen finden Sie unter *Prozedur in Kürze verfügbar*.

Sie dürfen die {{site.data.keyword.vmwaresolutions_short}}-Infrastrukturkomponenten, die in Ihrem {{site.data.keyword.cloud_notm}}-Konto erstellt werden, nur über die {{site.data.keyword.vmwaresolutions_short}}-Konsole und nicht im {{site.data.keyword.slportal}} oder über ein anderes Verfahren außerhalb der Konsole verwalten. Wenn Sie diese Komponenten außerhalb der {{site.data.keyword.vmwaresolutions_short}}-Konsole ändern, werden die Änderungen nicht mit der Konsole synchronisiert. Dies kann die Stabilität Ihrer Umgebung beeinträchtigen.
{:important}

## Vorgehensweise zum Löschen von Single-node Trial for vCenter Server-Instanzen

Zum Freigeben der Komponenten, die Sie in einer Single-node Trial for vCenter Server-Instanz bestellt haben, löschen Sie die Instanz.

Weitere Informationen finden Sie unter [vCenter Server-Instanzen löschen](vc_deletinginstance.html).

### Zugehörige Links

* [Für ein {{site.data.keyword.cloud_notm}}-Konto registrieren](../vmonic/signing_softlayer_account.html)
* [Glossar der HCX-Begriffe](../services/hcx_glossary.html)
* [Dokumentation zu VMware Hybrid Cloud Extension](https://hcx.vmware.com/#/vm-documentation)
* [Übersicht über vCenter Server with Hybridity Bundle](vc_hybrid_overview.html)
* [Hinweise zum Netzbetrieb für vCenter Server with Hybridity Bundle-Instanzen](vc_hybrid_networkingonvcenterserver.html)
* [vCenter Server with Hybridity Bundle-Instanzen bestellen](vc_hybrid_orderinginstance.html)
