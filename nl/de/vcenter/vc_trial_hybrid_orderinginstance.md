---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Single-node Trial for VMware vCenter Server on IBM Cloud-Instanzen bestellen und löschen

Single-node Trial for VMware vCenter Server on {{site.data.keyword.cloud}} ist eine gehostete private Single-Tenant-Cloud, die den VMware vSphere-Stack als Service bereitstellt. Während die vom Client verwaltete Umgebung in der Regel mit mindestens drei Knoten bereitgestellt wird, bietet diese Testversion für einen einzelnen Knoten eine kostengünstige Möglichkeit, die Vorteile einer Hybrid-Cloud-Implementierung zu nutzen.

Die Testversion eignet sich ideal für einen Konzeptnachweis, der zeigt, wie schnell eine automatisierte Erstbereitstellung mit den IBM Verfahren durchgeführt und wie komfortabel Workloads, die nicht zu Produktionszwecken dienen, in die Cloud verlagert werden können. Mit der VMware Hybrid Cloud Extension (HCX) können Sie Ihr lokales Rechenzentrumsnetz sicher in das {{site.data.keyword.CloudDataCent_notm}} erweitern, während die Netzkomplexität der Verbindungskonfiguration reduziert wird. HCX abstrahiert die zugrunde liegenden Netzressourcen, um Daten über das öffentliche Internet im Tunnelungsverfahren zu übertragen, sodass Sie die Workloads nahtlos bidirektional verschieben können, ohne den virtuellen Maschinen (VMs) neue IPs zuzuordnen. Bei HCX muss VMware NSX nicht lokal installiert sein und es besteht Abwärtskompatibilität mit älteren Versionen von vSphere.  

Die Testversion für Einzelknoten (Single-node Trial) dient nur für den Konzeptnachweis. Die Umgebung ist nicht für Workloads im Produktionsbetrieb geeignet. Managementfunktionen wie das Hinzufügen und Entfernen von Hosts und Clustern, das Bestellen zusätzlicher Add-on-Services und das Anwenden von Updates werden nicht unterstützt.
{:important}

Diese Testversion ist für eine Nutzung von bis zu 90 Tagen vorgesehen. Wenn Sie das Testen abschlossen haben, können Sie die Umgebung löschen und anschließend eine hoch verfügbare Umgebung einrichten, die Ihren Kapazitätsanforderungen entspricht.

Weitere Informationen zum Architekturdesign finden Sie unter [HCX on IBM Cloud-Architektur für Single-node Trial for vCenter Server on IBM Cloud](/docs/services/vmwaresolutions/archiref/trial/vc_trial_hcx_arch.html).

## Technische Spezifikationen für Single-node Trial for vCenter Server-Instanzen

Ihre Single-node Trial for vCenter Server-Instanz enthält die folgenden Komponenten:

Verfügbarkeit und Preisgestaltung standardisierter Hardwarekonfigurationen können abhängig vom {{site.data.keyword.CloudDataCent_notm}}, das für die Bereitstellung ausgewählt wird, variieren.
{:note}

### Bare Metal Server

Ein Dual Intel Xeon Gold 5120-Prozessor (28 Kerne, 2,20 GHz) mit 384 GB RAM.

### Netzspezifikationen für Instanzen von Single-node- Trial for vCenter-Server

Die folgenden Netzkomponenten werden bestellt:
*  10-Gbps-Uplinks für öffentliche und private Netze
*  3 VLANs (virtuelle LANs): 1 öffentliches VLAN und 2 private VLANs
*  1 VXLAN (Virtual eXtensible LAN) mit einem verteilten logischen Router (Distributed Logical Router, DLR) für die potenzielle Ost-West-Kommunikation zwischen lokalen Workloads, die mit Netzen der Schicht 2 (L2) verbunden sind. Das VXLAN wird als Muster für die Routingtopologie bereitgestellt, das Sie ändern, als Ausgangspunkt für Erstellungen verwenden oder entfernen können. Sie können außerdem Sicherheitszonen hinzufügen, indem Sie zusätzliche VXLANs an neue logische Schnittstellen im DLR anhängen.
*  2 VMware NSX Edge Services Gateways:
  * 1 sicheres VMware NSX Edge Services Gateway (ESG) für Management-Services für abgehenden HTTPS-Managementdatenverkehr, das von IBM im Rahmen der Managementnetztypologie bereitgestellt wird. Dieses ESG wird von den IBM Management-VMs für die Kommunikation mit bestimmten externen IBM Managementkomponenten verwendet, die mit der Automatisierung zusammenhängen.

    Dieses ESG ist für Sie weder zugänglich, noch können Sie es verwenden. Falls Sie es ändern, sind Sie möglicherweise nicht in der Lage, die Single-node Trial for vCenter Server-Instanz über die {{site.data.keyword.vmwaresolutions_short}}-Konsole zu verwalten. Beachten Sie außerdem, dass die Verwendung einer Firewall oder die Inaktivierung der ESG-Kommunikation mit den externen IBM Managementkomponenten dazu führt, dass {{site.data.keyword.vmwaresolutions_short}} unbrauchbar wird.
    {:important}
  * 1 sicheres vom Kunden verwaltetes VMware NSX Edge Services Gateway für eingehenden und abgehenden HTTPS-Workloaddatenverkehr, das von IBM als Vorlage bereitgestellt wird und von Ihnen geändert werden kann, um den VPN-Zugriff oder den öffentlichen Zugriff zu ermöglichen.

### Virtual Server-Instanzen

Die folgenden VSIs (Virtual Server-Instanzen) werden bestellt:

* Eine VSI für IBM CloudBuilder, die nach vollständiger Bereitstellung der Instanz abgebrochen wird.
* Eine VSI von Microsoft Windows Server für Microsoft Active Directory (AD) wird bereitgestellt und kann zur Suche verwendet werden. Die Virtual Server-Instanz (VSI) dient als DNS für die Instanz, auf der die Hosts und VMs registriert sind.

### Von IBM bereitgestellte Lizenzen und Gebühren

Ihre Bestellung der Single-node Trial for vCenter Server-Instanz enthält die folgenden Lizenzen:

* VMware vSphere Enterprise Plus 6.5
* VMware vCenter Server 6.5
* VMware NSX Service Providers Advanced Edition 6.4

Single-node Trial for vCenter Server-Instanzen bieten keine BYOL-Unterstützung (BYOL = Bring Your Own License; d. h. Verwendung der eigenen Lizenz).
{:note}

## Technische Spezifikationen für VMware HCX on IBM Cloud

Single-node Trial for vCenter Server enthält HCX on {{site.data.keyword.cloud_notm}}. Mit dem Service "HCX on {{site.data.keyword.cloud_notm}}" werden die folgenden Komponenten bestellt und einbezogen.

Lokale HCX-Instanzen schließen nur Lizenzierung und Aktivierung ein.
{:note}

### Ein Aktiv/Passiv-Paar von VMware NSX Edge Services Gateways für das HCX-Management

* CPU: 6 vCPU
* RAM: 8 GB
* Festplatte: 3 GB VMDK

### HCX-Management-Appliance - virtuelle Maschine

* CPU: 4 vCPU
* RAM: 12 GB
* Festplatte: 60 GB VMDK

Weitere HCX-Appliances werden bei der Konfiguration wie für die L2-Konnektivität, die WAN-Optimierung und Gateway-Verbindungen erforderlich bereitgestellt.

### Netzspezifikationen für den Service "HCX on IBM Cloud"

* 1 öffentliches portierbares Teilnetz mit 16 IP-Adressen
* 2 private portierbare Teilnetze mit 64 IP-Adressen
* 8 IP-Adressen aus dem privaten portierbaren vMotion-Teilnetz

## Voraussetzungen und Planung für die Bestellung von Single-node Trial for vCenter Server-Instanzen

Überprüfen Sie die folgenden Voraussetzungen und führen Sie die folgenden Tasks aus:
* Voraussetzungen für lokale HCX-Instanzen:
 * Erfordert VMware vSphere und vCenter 5.5 oder höher.
 * Die vSphere-Umgebung muss über verteilte Switches für die VMx verfügen, die zu {{site.data.keyword.cloud_notm}} migriert wird.
 * HCX Manager Virtual Appliance muss in einem privaten Netzwerk in der lokalen Umgebung bereitgestellt werden können und auf das öffentliche Internet zugreifen dürfen.
 * Um {{site.data.keyword.vmwaresolutions_short}} für die Bestellung von Instanzen verwenden zu können, müssen Sie ein Konto für die {{site.data.keyword.cloud_notm}}-Infrastruktur (SoftLayer) besitzen. Die Kosten der Komponenten, die in Ihren Instanzen bestellt werden, werden diesem {{site.data.keyword.cloud_notm}}-Konto in Rechnung gestellt.
 *  Konfigurieren Sie die Berechtigungsnachweise für die {{site.data.keyword.cloud_notm}}-Infrastruktur auf der Seite **Einstellungen**. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Einstellungen**.
 * Machen Sie sich mit den Anforderungen für die Instanznamen vertraut:
    * Es sind nur alphanumerische Zeichen und Bindestriche (-) zulässig.
    * Der Instanzname muss mit einem alphanumerischen Zeichen beginnen und enden.
    * Die maximale Länge des Instanznamens beträgt 10 Zeichen.
    * Der Instanzname muss innerhalb Ihres Kontos eindeutig sein.

## Vorgehensweise zum Bestellen von Single-node Trial for vCenter Server-Instanzen

1. Klicken Sie auf der Seite **Single-node Trial for VMware vCenter Server on {{site.data.keyword.cloud_notm}}** auf **Weiter**.
2. Führen Sie auf der Seite **Single-node Trial for VMware vCenter Server** die entsprechenden Schritte aus, um ein {{site.data.keyword.cloud_notm}}-Infrastrukturkonto anzufordern oder um Ihren bestehenden **Benutzernamen** und den **API-Schlüssel** anzugeben, und klicken Sie auf **Abrufen**.

 Dieser Abschnitt ist ausgeblendet, wenn der API-Schlüssel bereits vorhanden ist.
 {:note}
3. Geben Sie den Instanznamen ein.
4. Wählen Sie das {{site.data.keyword.CloudDataCent_notm}} als Host für die Instanz aus.  

 Standardmäßig ist DAL09 {{site.data.keyword.CloudDataCent_notm}} bereits ausgewählt. Wählen Sie bei Bedarf einen anderen Standort für das {{site.data.keyword.CloudDataCent_notm}} aus.
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
   * Zwei private portierbare Teilnetze für das HCX-Management.
   * Ein öffentliches portierbares Teilnetz für die Aktivierung und Wartung mit VMware. Dieses Teilnetz wird auch für HCX-Verbindungen verwendet.

   Die IP-Adresse in den für HCX bestellten Teilnetzen sollten durch die Automatisierung von VMware on {{site.data.keyword.cloud_notm}} verwaltet werden. Diese IP-Adressen können nicht zu VMware-Ressourcen wie VMs und NSX-Edges zugeordnet werden, die von Ihnen erstellt worden sind. Wenn Sie zusätzliche IP-Adressen für Ihre VMware-Artefakte benötigen, müssen Sie Ihre eigenen Teilnetze aus {{site.data.keyword.cloud_notm}} bestellen.
   {:important}
3. Es werden drei Ressourcenpools und VM-Ordner für HCX erstellt. Diese werden für die HCX-Verbindungen, die lokalen HCX-Komponenten sowie die fernen HCX-Komponenten benötigt.
4. Ein Paar von VMware NSX Edge Services Gateways (ESGs) für den HCX-Managementdatenverkehr wird bereitgestellt und konfiguriert:
   * Öffentliche und private Uplink-Schnittstellen werden unter Verwendung der bestellten Teilnetze konfiguriert.
   * Die ESGs werden als ein Paar sehr großer Edge-Appliances mit aktivierter Hochverfügbarkeit konfiguriert.
   * Die Firewallregeln und die Regeln für die Netzadressumsetzung (NAT-Regeln) werden konfiguriert, damit eingehender und abgehender HTTPS-Datenverkehr an den und vom HCX-Manager zulässig ist.
   * Die Regeln für den Lastausgleich und Ressourcenpools werden konfiguriert. Diese Regeln und Ressourcenpools werden verwendet, um den HCX-bezogenen eingehenden Datenverkehr an die entsprechenden virtuellen Appliances von HCX Manager und vCenter Server (mit Embedded Platform Services Controller) weiterzuleiten.
   * Ein SSL-Zertifikat zum Verschlüsseln des HCX-bezogenen eingehenden HTTPS-Datenverkehrs, der über die ESGs eintrifft, wird angewendet.

   Die HCX-Management-Edge ist für den HCX-Managementdatenverkehr zwischen den lokalen HCX-Komponenten und den cloudseitigen HCX-Komponenten dediziert. Die HCX-Management-Edge darf weder geändert noch für HCX-Netzerweiterungen verwendet werden. Erstellen Sie für Netzerweiterungen stattdessen separate Edges. Außerdem kann die Verwendung einer Firewall oder die Inaktivierung der HCX-Edge-Kommunikation mit den privaten IBM Managementkomponenten oder dem öffentlichen Internet die HCX-Funktionalität beeinträchtigen.
   {:important}

5. Der HCX-Manager on {{site.data.keyword.cloud_notm}} wird bereitgestellt, aktiviert und konfiguriert:
   * Der HCX-Manager wird bei vCenter Server registriert.
   * Der HCX-Manager, vCenter Server (mit integriertem Platform Services Controller) und NSX-Manager sind konfiguriert.
   * Das HCX-Produktpaket wird konfiguriert.
   * Lokale und ferne HCX-Bereitstellungscontainer werden konfiguriert.
6. Der Hostname und die IP-Adresse des HCX-Managers werden beim DNS-Server von VMware vCenter Server on {{site.data.keyword.cloud_notm}} registriert.

#### Instanzdetails anzeigen

Sie können den Status der Bereitstellung prüfen, indem Sie die Instanzdetails anzeigen. Klicken Sie im linken Navigationsfenster auf **Bereitgestellte Instanzen** und suchen Sie die Tabelle **vCenter Server-Instanzen** oder **Lokale HCX-Instanzen**, um Informationen zu den bestellten Instanzen anzuzeigen.

Wenn die Instanz erfolgreich bereitgestellt wurde, werden die in den Abschnitten *Technische Spezifikationen* dieses Themas beschriebenen Komponenten auf Ihrer virtuellen VMware-Plattform installiert und der Aktivierungsschlüssel für den lokalen HCX on {{site.data.keyword.cloud_notm}}-Service in der Tabelle **Lokale HCX-Instanzen** aufgeführt.

Der Status der Instanz ändert sich in **Bereit** und Sie erhalten eine Benachrichtigung per E-Mail.

### Nächste Schritte

Installieren Sie den lokalen HCX Enterprise Manager und konfigurieren Sie die Verbindung zu Ihrer HCX on {{site.data.keyword.cloud_notm}}-Instanz.

1. Suchen Sie den lokalen Aktivierungsschlüssel auf der Seite **Bereitgestellte Instanzen**.
  1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Bereitgestellte Instanzen**.
  2. Suchen Sie in der Tabelle **vCenter Server-Instanzen** in der Spalte **Typ** nach der vCenter Server Single-node Trial-Instanz und notieren Sie den Instanznamen.
  3. Blättern Sie zur Tabelle **Lokale HCX-Instanzen** und suchen Sie in der Spalte **Name** nach der Instanz mit demselben Namen wie die bestellte Einzelknoteninstanz mit dem Suffix *-OnPrem*.
  4. Notieren Sie den Schlüssel im Feld **Aktivierungsschlüssel**.
2. Rufen Sie die HCX Enterprise Manager Open Virtual Appliance (OVA) von der HCX on {{site.data.keyword.cloud_notm}} HCX Manager-Konsole ab.
  1. Stellen Sie eine Verbindung mit der HCX-Cloudkonsole her.
    1. Klicken Sie in der Tabelle **vCenter Server-Instanzen** auf die Single-node Trial-Instanz, um die Instanzdetails anzuzeigen.
    2. Suchen Sie unter **Zugriffsinformationen** die vCenter-Berechtigungsnachweise und notieren Sie sie.
    3. Klicken Sie im linken Navigationsfenster auf **Services**.
    4. Klicken Sie auf der Seite **Services** auf **HCX on IBM Cloud**.
    5. Suchen Sie auf der Detailseite von **HCX on IBM Cloud** die **HCX-Cloud-IP** und notieren Sie sie.
    6. Stellen Sie sicher, dass Sie mit dem VPN verbunden sind, um auf Ihr {{site.data.keyword.cloud_notm}} Private-Netz zuzugreifen.
    7. Klicken Sie auf **HCX-Cloudkonsole anzeigen**.
  2. Führen Sie in der **HCX-Cloudkonsole** die folgenden Schritte aus:
      1. Klicken Sie auf die Registerkarte **Verwaltung**.
      2. Klicken Sie auf der Registerkarte **Systemupdates** auf **DOWNLOAD-LINK ANFORDERN**.
      3. Klicken Sie auf **LINK KOPIEREN** und verwenden Sie anschließend diesen Link, um HCX Enterprise Client in eine lokale Umgebung herunterzuladen, die Zugriff auf Ihre lokale vSphere-Umgebung besitzt.
3. Stellen Sie HCX Enterprise Client in VMware vSphere Web Client als virtuelle Appliance für den HCX-Manager (kurz "HCX-Manager") in Ihrer lokalen Umgebung bereit. Weitere Informationen hierzu finden Sie im Abschnitt [HCX Enterprise Manager OVA installieren](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-C61E107C-1F5F-4615-9BA9-351900CDB69E.html).

    Sie müssen den lokalen HCX-Manager in einem privaten Netz bereitstellen und ihm den Zugriff auf das öffentliche Netz ermöglichen. Sie können NSX Edge, Vyatta oder ähnliche Gateways verwenden, um dem lokalen HCX-Manager den Internetzugriff zu ermöglichen. Falls für den Zugriff auf das private Netz und auf das öffentliche Netz verschiedene Gateways verwendet werden, empfiehlt es sich, das Standardgateway für den Zugriff auf das öffentliche Netz zu verwenden und mit der lokalen **Administratorkonsole für den HCX-Manager** eine statische Route für den Zugriff auf das private Netz zu erstellen.  
    {:note}
4. Verwenden Sie den in Schritt 1 notierten lokalen Aktivierungsschlüssel, um die lokale virtuelle HCX Enterprise Manager-Maschine zu aktivieren.
  1. Melden Sie sich bei der lokalen virtuellen HCX Enterprise Manager-Maschine mit den Berechtigungsnachweisen an, die bei der Bereitstellung von OVA angegeben wurden.
  2. Geben Sie den Aktivierungsschlüssel ein, wenn Sie dazu aufgefordert werden.

  Weitere Informationen finden Sie in der Veröffentlichung zur [HCX-Aktivierung und Erstkonfiguration](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-6A4740C1-2225-444C-8ADC-CBE54F181536.html).
  {:note}
5. Ein selbst signiertes SSL-Zertifikat wurde vom HCX on {{site.data.keyword.cloud_notm}}-Service generiert. Sie müssen das Zertifikat in den lokalen HCX-Manager importieren, indem Sie die folgenden Schritte ausführen:
    1. Klicken Sie in der lokalen **Administratorkonsole für den HCX-Manager** auf die Registerkarte **Verwaltung**.
    2. Klicken Sie im linken Navigationsfenster auf **Anerkanntes CA-Zertifikat** und dann rechts auf **IMPORTIEREN**.
    3. Klicken Sie auf **URL** und geben Sie dann die URL des Zertifikats ein, das Sie anwenden möchten, also die **HCX-Cloud-IP** (``https://<cloud-side public IP>``), die auf der Seite mit den Details für den Service "HCX on {{site.data.keyword.cloud_notm}}" in der {{site.data.keyword.vmwaresolutions_short}}-Konsole zu finden ist.
    4. Klicken Sie auf **ANWENDEN**.
6. Fahren Sie mit der Erstkonfiguration fort und erstellen Sie die Verbindung. Weitere Informationen hierzu finden Sie im Abschnitt zur [Installation und Konfiguration von VMware HCX Enterprise](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-A26BFB16-FA94-426F-8E18-15BAD4BF840E.html).
7. Erweitern Sie Netze in VMware HCX von lokal auf {{site.data.keyword.cloud_notm}}. Weitere Informationen hierzu finden Sie im Abschnitt zum [Erweitern von Netzen mit VMware HCX](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-DD9C3316-D01C-4088-B3EA-84ADB9FED573.html?hWord=N4IghgNiBcIKIA8AuBTAdgEwJZoOYAI0UkB3AewCcBrAZxAF8g).
8. Migrieren Sie virtuelle Maschinen (VMs) zwischen lokalen Umgebungen und {{site.data.keyword.cloud_notm}}-Umgebungen. Weitere Informationen finden Sie im Abschnitt zur [Migration virtueller Maschinen mit VMware HCX](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-D0CD0CC6-3802-42C9-9718-6DA5FEC246C6.html?hWord=N4IghgNiBcILIEsDmAnMAXBA7JACAagiugK6S5xgDGAFtgKYDOuA7gujQXC2CvbgAkAwgA0QAXyA).

Sie dürfen die {{site.data.keyword.vmwaresolutions_short}}-Infrastrukturkomponenten, die in Ihrem {{site.data.keyword.cloud_notm}}-Konto erstellt werden, nur über die {{site.data.keyword.vmwaresolutions_short}}-Konsole und nicht im {{site.data.keyword.slportal}} oder über ein anderes Verfahren außerhalb der Konsole verwalten.
Wenn Sie diese Komponenten außerhalb der {{site.data.keyword.vmwaresolutions_short}}-Konsole ändern, werden die Änderungen nicht mit der Konsole synchronisiert. Dies kann die Stabilität Ihrer Umgebung beeinträchtigen.
{:important}

## Vorgehensweise zum Löschen von Single-node Trial for vCenter Server-Instanzen

Wenn Sie eine Instanz von Single-node Trial for vCenter Server löschen, werden die folgenden Komponenten nacheinander freigegeben:

1. Alle bereitgestellten Services
3. VMware-Produktlizenzen
4. ESXi-Server
5. Teilnetze
6. VLANs

Aufgrund von Ressourcenabhängigkeiten werden die Komponenten in Ihrer Instanz nicht sofort freigegeben, wenn Sie die Instanz löschen. Beispielsweise können die Teilnetze und VLANs erst gelöscht werden, nachdem die ESXi-Server vollständig von der {{site.data.keyword.cloud_notm}}-Infrastruktur zurückgefordert wurden, was am Ende des Abrechnungszyklus für die {{site.data.keyword.cloud_notm}}-Infrastruktur erfolgt. Am Ende des Abrechnungszyklus für die {{site.data.keyword.cloud_notm}}-Infrastruktur, der normalerweise 30 Tage beträgt, werden die Teilnetze und VLANs gelöscht und die Instanzlöschung ist abgeschlossen.

Die gelöschten Instanzen werden Ihnen bis zum Ende des Abrechnungszyklus für die {{site.data.keyword.cloud_notm}}-Infrastruktur berechnet.
{:note}

Führen Sie folgende Schritte aus, um eine Instanz von Single-node Trial for vCenter Server zu löschen:

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Bereitgestellte Instanzen**.
2. Suchen Sie in der Tabelle **vCenter Server-Instanzen** nach der Instanz, die Sie löschen wollen.
3. Klicken Sie in der Spalte **Aktionen** auf das Symbol "Löschen".
   Der Status der Instanz ändert sich in **Wird gelöscht**. Nachdem die Instanz erfolgreich gelöscht wurde, werden die Komponenten der Instanz freigegeben und der Status der Instanz ändert sich in **Gelöscht**.
4. Wenn Sie den Instanzdatensatz aus der {{site.data.keyword.vmwaresolutions_short}}-Konsole entfernen möchten, führen Sie die folgenden Schritte aus:
   1. Klicken Sie in der Spalte **Aktionen** erneut auf das Symbol "Löschen".
   2. Klicken Sie im Fenster **Instanz löschen** auf **OK**.

### Zugehörige Links

* [HCX on IBM Cloud-Architekturdesign für Single-node Trial for vCenter Server on IBM Cloud](/docs/services/vmwaresolutions/archiref/trial/vc_trial_hcx_arch.html)
* [Dokumentation zu VMware Hybrid Cloud Extension](https://hcx.vmware.com/#/vm-documentation)
* [HCX OVA anfordern](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-B0471D10-6EB0-4587-9205-11BF0C78EC1C.html)
