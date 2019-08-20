---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-25"

keywords: single-node trial, migration app modernization, order migration app modernization

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Single-node Trial für Migration und App-Modernisierung bestellen, anzeigen und löschen
{: #cloud_modern_bundle_orderinginstance}

Überprüfen Sie die Planungsvoraussetzungen, bevor Sie eine Single-node Trial-Instanz für Migration und Anwendungsmodernisierung bestellen.

## Voraussetzungen und Planung für die Bestellung von Single-node Trial-Instanzen für Migration und Anwendungsmodernisierung
{: #cloud_modern_bundle_orderinginstance-req}

Überprüfen Sie die folgenden Voraussetzungen und führen Sie die folgenden Tasks aus.

### Voraussetzungen für lokale HCX-Instanzen
{: #cloud_modern_bundle_orderinginstance-hcx-req}

* Erfordert VMware vSphere und vCenter 5.5 oder höher.
* Die vSphere-Umgebung muss über verteilte Switches für die VMs verfügen, die zu {{site.data.keyword.cloud_notm}} migriert werden.
* HCX Manager Virtual Appliance muss in einem privaten Netz in der lokalen Umgebung bereitgestellt werden können und auf das öffentliche Internet zugreifen dürfen.

### IBM Cloud-Infrastrukturkonto
{: #cloud_modern_bundle_orderinginstance-account-req}

* Um {{site.data.keyword.vmwaresolutions_short}} für die Bestellung von Instanzen verwenden zu können, müssen Sie ein Konto für die {{site.data.keyword.cloud_notm}}-Infrastruktur besitzen. Die Kosten der Komponenten, die in Ihren Instanzen bestellt werden, werden diesem {{site.data.keyword.cloud_notm}}-Konto in Rechnung gestellt.
*  Konfigurieren Sie die Berechtigungsnachweise für die {{site.data.keyword.cloud_notm}}-Infrastruktur auf der Seite **Einstellungen**. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Einstellungen**.

### Voraussetzungen für Instanznamen
{: #cloud_modern_bundle_orderinginstance-inst-name-req}

Der Instanzname muss die folgenden Anforderungen erfüllen:
* Es sind nur Kleinbuchstaben, Ziffern und Gedankenstriche (-) zulässig.
* Der Instanzname muss mit einem Kleinbuchstaben beginnen.
* Der Instanzname muss entweder auf einen Kleinbuchstaben oder auf eine Ziffer enden.
* Die maximale Länge des Instanznamens beträgt 10 Zeichen.
* Der Instanzname muss innerhalb Ihres Kontos eindeutig sein.

## Vorgehensweise zum Bestellen von Single-node Trial-Instanzen für Migration und Anwendungsmodernisierung
{: #cloud_modern_bundle_orderinginstance-procedure}

1. Klicken Sie im {{site.data.keyword.cloud_notm}}-Katalog im linken Navigationsfenster auf das Symbol **VMware** und anschließend im Abschnitt **Virtuelle VMware-Rechenzentren** auf die Karte **Single-node Trial für Migration und Anwendungsmodernisierung**.
2. Klicken Sie auf der Seite **Single-node Trial für Migration und Anwendungsmodernisierung** auf **Weiter**.
3. Führen Sie die Schritte aus, um ein {{site.data.keyword.cloud_notm}}-Infrastrukturkonto anzufordern, oder geben Sie Ihren vorhandenen **Benutzernamen** und **API-Schlüssel** an. Klicken Sie anschließend auf **Abrufen**.

 Wenn der API-Schlüssel vorhanden ist, ist dieser Abschnitt ausgeblendet.
 {:note}
4. Geben Sie den Instanznamen ein.
5. Wählen Sie das {{site.data.keyword.CloudDataCent_notm}} als Host für die Instanz aus.  

 Standardmäßig ist DAL09 {{site.data.keyword.CloudDataCent_notm}} vorausgewählt. Wählen Sie bei Bedarf einen anderen Standort für das {{site.data.keyword.CloudDataCent_notm}} aus.
 {:note}
6. Überprüfen Sie im Fenster **Bestellübersicht** die Instanzkonfiguration, bevor Sie die Bestellung aufgeben.
   1. Überprüfen Sie die Einstellungen für die Instanz.
   2. Überprüfen Sie die geschätzten Kosten der Instanz. Klicken Sie auf **Preisdetails**, um eine PDF-Datei mit der Zusammenfassung zu generieren. Ihre Bestellübersicht können Sie speichern oder drucken, indem Sie rechts oben im PDF-Fenster auf das Symbol **Drucken** bzw. **Herunterladen** klicken.
   3. Klicken Sie auf den Link bzw. die Links für die Bedingungen, die für Ihre Bestellung gelten, und vergewissern Sie sich, dass Sie mit diesen Bedingungen einverstanden sind, bevor Sie die Instanz bestellen.
   4. Klicken Sie auf **Bereitstellung**.

### Ergebnisse nach dem Bestellen von Single-node Trial-Instanzen für Migration und Anwendungsmodernisierung
{: #cloud_modern_bundle_orderinginstance-results}

* Die Bereitstellung der Instanz wird automatisch gestartet und der Aktivierungsschlüssel für den lokalen HCX on {{site.data.keyword.cloud_notm}}-Service wird bestellt.
* Sie können den Bereitstellungsstatus, einschließlich aller Probleme, die eventuell Ihre Aufmerksamkeit erfordern, durch Anzeigen des Abschnitts **Bereitstellungsverlauf** der Instanzdetails überprüfen.
* Nachdem die Instanz erfolgreich bereitgestellt wurde, sind die Komponenten installiert, die unter [Technische Spezifikationen für Single-node Trial-Instanzen für Migration und Anwendungsmodernisierung](/docs/services/vmwaresolutions/services?topic=vmware-solutions-cloud_modern_bundle_overview#cloud_modern_bundle_overview-tech-specs) beschrieben werden.
* Sobald die Instanz einsatzbereit ist, ändert sich der Status der Instanz in **Bereit** und Sie empfangen per E-Mail eine Benachrichtigung.

#### Bereitstellungsprozess für HCX on IBM Cloud
{: #cloud_modern_bundle_orderinginstance-hcx-deploy-process}

Die Bereitstellung von HCX on {{site.data.keyword.cloud_notm}} ist automatisiert. Die folgenden Schritte werden durch den {{site.data.keyword.vmwaresolutions_short}}-Automatisierungsprozess ausgeführt:
1. Über die {{site.data.keyword.cloud_notm}}-Infrastruktur werden drei Teilnetze für HCX bestellt:
   * Zwei private portierbare Teilnetze für das HCX-Management.
   * Ein öffentliches portierbares Teilnetz für die Aktivierung und Wartung mit VMware. Dieses Teilnetz wird auch für HCX-Verbindungen verwendet.

   Die IP-Adresse in den für HCX bestellten Teilnetzen sollten durch die Automatisierung von VMware on {{site.data.keyword.cloud_notm}} verwaltet werden. Diese IP-Adressen können nicht zu VMware-Ressourcen wie VMs und NSX-Edges zugeordnet werden, die von Ihnen erstellt worden sind. Wenn Sie weitere IP-Adressen für Ihre VMware-Artefakte benötigen, müssen Sie Ihre eigenen Teilnetze aus {{site.data.keyword.cloud_notm}} bestellen.
   {:important}
3. Es werden drei Ressourcenpools und VM-Ordner für HCX erstellt. Diese werden für die HCX-Verbindungen, die lokalen HCX-Komponenten sowie die fernen HCX-Komponenten benötigt.
4. Ein Paar von VMware NSX Edge Services Gateways (ESGs) für den HCX-Managementdatenverkehr wird bereitgestellt und konfiguriert:
   * Öffentliche und private Uplink-Schnittstellen werden unter Verwendung der bestellten Teilnetze konfiguriert.
   * Die ESGs werden als ein Paar sehr großer Edge-Appliances mit aktivierter Hochverfügbarkeit konfiguriert.
   * Die Firewallregeln und die Regeln für die Netzadressumsetzung (NAT-Regeln) werden konfiguriert, damit eingehender und abgehender HTTPS-Datenverkehr an den und vom HCX-Manager zulässig ist.
   * Die Regeln für den Lastausgleich und Ressourcenpools werden konfiguriert. Diese Regeln und Ressourcenpools werden verwendet, um den HCX-bezogenen eingehenden Datenverkehr an die entsprechenden virtuellen Appliances von HCX Manager und vCenter Server (mit Embedded Platform Services Controller) weiterzuleiten.
   * Ein SSL-Zertifikat zum Verschlüsseln des HCX-bezogenen eingehenden HTTPS-Datenverkehrs, der über die ESGs eintrifft, wird angewendet.

   Die HCX-Management-Edge ist für den HCX-Managementdatenverkehr zwischen den lokalen HCX-Komponenten und den cloudseitigen HCX-Komponenten dediziert. Das HCX-Management-Edge darf weder geändert noch für HCX-Netzerweiterungen verwendet werden. Erstellen Sie für Netzerweiterungen stattdessen separate Edges. Außerdem kann die Verwendung einer Firewall oder die Inaktivierung der HCX-Edge-Kommunikation mit den privaten IBM Managementkomponenten oder dem öffentlichen Internet die HCX-Funktionalität beeinträchtigen.
   {:important}

5. Der HCX-Manager on {{site.data.keyword.cloud_notm}} wird bereitgestellt, aktiviert und konfiguriert:
   * Der HCX-Manager wird bei vCenter Server registriert.
   * Der HCX-Manager, vCenter Server (mit integriertem Platform Services Controller) und NSX-Manager sind konfiguriert.
   * Das HCX-Produktpaket wird konfiguriert.
   * Lokale und ferne HCX-Bereitstellungscontainer werden konfiguriert.
6. Der Hostname und die IP-Adresse des HCX-Managers werden beim DNS-Server von VMware vCenter Server on {{site.data.keyword.cloud_notm}} registriert.

#### Instanzdetails anzeigen
{: #cloud_modern_bundle_orderinginstance-view-inst-details}

Sie können den Status der Bereitstellung prüfen, indem Sie die Instanzdetails anzeigen. Klicken Sie im linken Navigationsfenster auf **Ressourcen** und suchen Sie die Tabelle **vCenter Server-Instanzen** oder **Lokale HCX-Instanzen**, um Informationen zu den bestellten Instanzen anzuzeigen.

Wenn die Instanz erfolgreich bereitgestellt wurde, werden die in den Abschnitten *Technische Spezifikationen* dieses Themas beschriebenen Komponenten auf Ihrer virtuellen VMware-Plattform installiert und der Aktivierungsschlüssel für den lokalen HCX on {{site.data.keyword.cloud_notm}}-Service in der Tabelle **Lokale HCX-Instanzen** aufgeführt.

Der Status der Instanz ändert sich in **Bereit** und Sie erhalten eine Benachrichtigung per E-Mail.

### Nächste Schritte
{: #cloud_modern_bundle_orderinginstance-next}

Installieren Sie den lokalen HCX Enterprise Manager und konfigurieren Sie die Verbindung zu Ihrer HCX on {{site.data.keyword.cloud_notm}}-Instanz.

1. Suchen Sie den lokalen Aktivierungsschlüssel auf der Seite **Ressourcen**.
  1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Ressourcen**.
  2. Zeigen Sie in der Tabelle **vCenter Server-Instanzen** die Spalte **Typ** an, um die Single-node Trial-Instanz für Migration und Anwendungsmodernisierung zu finden, und notieren Sie sich den Instanznamen.
  3. Blättern Sie zur Tabelle **Lokale HCX-Instanzen** und suchen Sie in der Spalte **Name** nach der Instanz mit demselben Namen wie die bestellte Einzelknoteninstanz mit dem Suffix *-OnPrem*.
  4. Notieren Sie den Schlüssel im Feld **Aktivierungsschlüssel**.
2. Rufen Sie die HCX Enterprise Manager Open Virtual Appliance (OVA) von der HCX on {{site.data.keyword.cloud_notm}} HCX Manager-Konsole ab.
  1. Stellen Sie eine Verbindung mit der HCX-Cloudkonsole her.
    1. Klicken Sie in der Tabelle **vCenter Server-Instanzen** auf die Single-node Trial-Instanz für Migration und Anwendungsmodernisierung, um die Instanzdetails anzuzeigen.
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
3. Stellen Sie HCX Enterprise Client in VMware vSphere Web Client als virtuelle Appliance für den HCX-Manager (kurz "HCX-Manager") in Ihrer lokalen Umgebung bereit. Folgen Sie den Anweisungen im [Benutzerhandbuch von VMware HCX](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-BFD7E194-CFE5-4259-B74B-991B26A51758.html){:external}.

    Sie müssen den lokalen HCX-Manager in einem privaten Netz bereitstellen und ihm den Zugriff auf das öffentliche Netz ermöglichen. Sie können NSX Edge, Vyatta oder ähnliche Gateways verwenden, um dem lokalen HCX-Manager den Internetzugriff zu ermöglichen. Falls für den Zugriff auf das private Netz und auf das öffentliche Netz verschiedene Gateways verwendet werden, empfiehlt es sich, das Standardgateway für den Zugriff auf das öffentliche Netz zu verwenden und mit der lokalen **Administratorkonsole für den HCX-Manager** eine statische Route für den Zugriff auf das private Netz zu erstellen.  
    {:note}
4. Verwenden Sie den in Schritt 1 notierten lokalen Aktivierungsschlüssel, um die lokale virtuelle HCX Enterprise Manager-Maschine zu aktivieren.
  1. Melden Sie sich bei der lokalen virtuellen HCX Enterprise Manager-Maschine mit den Berechtigungsnachweisen an, die bei der Bereitstellung von OVA angegeben wurden.
  2. Geben Sie den Aktivierungsschlüssel ein, wenn Sie dazu aufgefordert werden.

  Folgen Sie den Anweisungen im [Benutzerhandbuch von VMware HCX](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-BFD7E194-CFE5-4259-B74B-991B26A51758.html){:external}.

5. Ein selbst signiertes SSL-Zertifikat wurde vom HCX on {{site.data.keyword.cloud_notm}}-Service generiert. Sie müssen das Zertifikat in den lokalen HCX-Manager importieren, indem Sie die folgenden Schritte ausführen:
    1. Klicken Sie in der lokalen **Administratorkonsole für den HCX-Manager** auf die Registerkarte **Verwaltung**.
    2. Klicken Sie im linken Navigationsfenster auf **Anerkanntes CA-Zertifikat** und dann rechts auf **IMPORTIEREN**.
    3. Klicken Sie auf **URL** und geben Sie dann die URL des Zertifikats ein, das Sie anwenden möchten. Dies ist die **HCX-Cloud-IP** (``https://<cloud-side public IP>``), die Sie auf der Seite mit den Details für den Service "HCX on {{site.data.keyword.cloud_notm}}" in der {{site.data.keyword.vmwaresolutions_short}}-Konsole finden.
    4. Klicken Sie auf **ANWENDEN**.
6. Fahren Sie mit der Erstkonfiguration fort und erstellen Sie die Verbindung. Folgen Sie den Anweisungen im [Benutzerhandbuch von VMware HCX](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-BFD7E194-CFE5-4259-B74B-991B26A51758.html){:external}.
7. Erweitern Sie Netze in VMware HCX von lokal auf {{site.data.keyword.cloud_notm}}. Folgen Sie den Anweisungen im [Benutzerhandbuch von VMware HCX](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-BFD7E194-CFE5-4259-B74B-991B26A51758.html){:external}.
8. Migrieren Sie virtuelle Maschinen (VMs) zwischen lokalen Umgebungen und {{site.data.keyword.cloud_notm}}-Umgebungen. Folgen Sie den Anweisungen im [Benutzerhandbuch von VMware HCX](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-BFD7E194-CFE5-4259-B74B-991B26A51758.html){:external}.

Sie dürfen die {{site.data.keyword.vmwaresolutions_short}}-Infrastrukturkomponenten, die in Ihrem {{site.data.keyword.cloud_notm}}-Konto erstellt werden, nur über die {{site.data.keyword.vmwaresolutions_short}}-Konsole und nicht im {{site.data.keyword.slportal}} oder über ein anderes Verfahren außerhalb der Konsole verwalten.
Wenn Sie diese Komponenten außerhalb der {{site.data.keyword.vmwaresolutions_short}}-Konsole ändern, werden die Änderungen nicht mit der Konsole synchronisiert. Dies kann die Stabilität Ihrer Umgebung beeinträchtigen.
{:important}

## Vorgehensweise zum Löschen von Single-node Trial-Instanzen für Migration und Anwendungsmodernisierung
{: #cloud_modern_bundle_orderinginstance-deleting-procedure}

Wenn Sie eine Single-node Trial-Instanz für Migration und Anwendungsmodernisierung löschen, werden die folgenden Komponenten nacheinander freigegeben:

1. Alle bereitgestellten Services
3. VMware-Produktlizenzen
4. ESXi-Server
5. Teilnetze
6. VLANs

Aufgrund von Ressourcenabhängigkeiten werden die Komponenten in Ihrer Instanz nicht sofort freigegeben, wenn Sie die Instanz löschen. Beispielsweise können die Teilnetze und VLANs erst gelöscht werden, nachdem die ESXi-Server vollständig von der {{site.data.keyword.cloud_notm}}-Infrastruktur zurückgefordert wurden, was am Ende des Abrechnungszyklus für die {{site.data.keyword.cloud_notm}}-Infrastruktur erfolgt. Am Ende des Abrechnungszyklus für die {{site.data.keyword.cloud_notm}}-Infrastruktur, der normalerweise 30 Tage beträgt, werden die Teilnetze und VLANs gelöscht und die Instanzlöschung ist abgeschlossen.

Die gelöschten Instanzen werden Ihnen bis zum Ende des Abrechnungszyklus für die {{site.data.keyword.cloud_notm}}-Infrastruktur berechnet.
{:note}

Führen Sie folgende Schritte aus, um eine Single-node Trial-Instanz für Migration und Anwendungsmodernisierung zu löschen:

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Ressourcen**.
2. Suchen Sie in der Tabelle **vCenter Server-Instanzen** nach der Instanz, die Sie löschen wollen.
3. Klicken Sie in der Spalte **Aktionen** auf das Symbol "Löschen".
   Der Status der Instanz ändert sich in **Wird gelöscht**. Nachdem die Instanz erfolgreich gelöscht wurde, werden die Komponenten der Instanz freigegeben und der Status der Instanz ändert sich in **Gelöscht**.
4. Wenn Sie den Instanzdatensatz aus der {{site.data.keyword.vmwaresolutions_short}}-Konsole entfernen möchten, führen Sie die folgenden Schritte aus:
   1. Klicken Sie in der Spalte **Aktionen** erneut auf das Symbol "Löschen".
   2. Klicken Sie im Fenster **Instanz löschen** auf **OK**.

## Zugehörige Links
{: #cloud_modern_bundle_orderinginstance-related}

* [vCenter Server and {{site.data.keyword.cloud_notm}} Private - Leitfaden](/docs/services/vmwaresolutions/archiref/vcsicp?topic=vmware-solutions-vcsicp-intro)
* [Ticket für {{site.data.keyword.cloud_notm}} Private öffnen](https://www.ibm.com/mysupport/s/?language=en_US){:external}
* [VMware HCX-Ressourcen](https://hcx.vmware.com/#/docs){:external}
* [Benutzerhandbuch zu VMware HCX](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-BFD7E194-CFE5-4259-B74B-991B26A51758.html){:external}
* [Virtuelle Server stornieren](/docs/vsi?topic=virtual-servers-managing-virtual-servers#cancel)
