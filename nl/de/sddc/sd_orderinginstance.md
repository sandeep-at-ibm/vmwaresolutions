---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-15"

---

# Cloud Foundation-Instanzen bestellen

Durch die Bestellung einer VMware Cloud Foundation-Instanz können Sie eine einheitliche Plattform für SDDC (Software-Defined Data Center, softwaredefiniertes Rechenzentrum) mit einer Standardkonfiguration für Rechenressourcen, Speicher und Netz bereitstellen. Während der Erstbestellung können Sie auch Services hinzufügen, z. B. [Zerto on {{site.data.keyword.cloud}}](../services/addingzertodr.html) für die Disaster-Recovery.

## Voraussetzungen

Stellen Sie sicher, dass Sie die folgenden Tasks ausgeführt haben:
*  Sie haben die Berechtigungsnachweise für die {{site.data.keyword.cloud_notm}}-Infrastruktur auf der Seite **Einstellungen** konfiguriert. Weitere Informationen finden Sie unter [Benutzerkonten und Einstellungen verwalten](../vmonic/useraccount.html).
*  Sie haben sich mit den Voraussetzungen und Hinweisen im Abschnitt [Voraussetzungen und Planung für Cloud Foundation-Instanzen](sd_planning.html) vertraut gemacht.

**Wichtig:** Nehmen Sie keine Änderungen an Werten vor, die während der Bestellung und Instanzbereitstellung festgelegt werden. Dies kann dazu führen, dass Ihre Instanz unbrauchbar wird. Ändern Sie darüber hinaus nach der Bereitstellung der Instanz weder den Instanznamen, noch den Rootdomänennamen, die Unterdomänenbezeichnung oder das Hostnamenspräfix.

## Systemeinstellungen

Sie müssen die folgenden Systemeinstellungen angeben, wenn Sie eine Cloud Foundation-Instanz bestellen.

### Instanzname

Der Instanzname muss die folgenden Anforderungen erfüllen:
* Es sind nur alphanumerische Zeichen und Bindestriche (-) zulässig.
* Der Instanzname muss mit einem alphanumerischen Zeichen beginnen und enden.
* Die maximale Länge des Instanznamens beträgt 10 Zeichen.
* Der Instanzname muss innerhalb Ihres Kontos eindeutig sein.

### Primär oder sekundär

Wählen Sie aus, ob Sie eine neue primäre oder sekundäre Instanz für eine bereits vorhandene primäre Instanz bestellen wollen.

## Lizenzierungseinstellungen

Geben Sie die Lizenzierungsoptionen für die folgenden VMware-Komponenten in der Instanz an:  
* vCenter Server-Lizenz - Standard
* vSphere-Lizenz - Enterprise Plus
* NSX-Lizenz - Enterprise
* vSAN-Lizenz (Auswahl der Advanced Edition oder Enterprise Edition)

Für Benutzer der Kategorie "Business Partner" sind die vCenter Server-Lizenz (Standard Edition), die vSphere-Lizenz (Enterprise Plus Edition), die NSX-Lizenz und die vSAN-Lizenz enthalten und werden in Ihrem Namen erworben. Für die vSAN-Lizenz muss allerdings die Edition angegeben werden.

Für Nicht-Business-Partner-Benutzer können die von IBM bereitgestellten VMware-Lizenzen für diese Komponenten benutzt werden. Wählen Sie hierzu **In Kauf einbeziehen** aus. Alternativ hierzu können Sie auch eine eigene Lizenz (Bring Your Own License; BYOL) verwenden, indem Sie **Lizenz selbst bereitstellen** auswählen und die eigenen Lizenzschlüssel angeben.

## Einstellungen für Bare Metal Server

### Standort des Rechenzentrums

Wählen Sie das {{site.data.keyword.CloudDataCent_notm}} aus, das als Host für die Instanz verwendet werden soll.

### Vorkonfiguriert

Wenn Sie **Vorkonfiguriert** auswählen, dann können Sie die CPU- oder RAM-Einstellungen nicht ändern.

Wählen Sie gemäß Ihren Anforderungen eine Bare Metal Server-Konfiguration aus:
  * S (Klein): Dual Intel Xeon E5-2650 v4 / 24 Kerne insgesamt, 2,2 GHz / 128 GB RAM / 12 Laufwerke
  * L (Groß): Dual Intel Xeon E5-2690 v4 / 28 Kerne insgesamt, 2,6 GHz / 512 GB RAM / 12 Laufwerke

### Angepasst

Wenn Sie **Angepasst** auswählen, dann können Sie die Kombination aus CPU und RAM entsprechend Ihren Anforderungen auswählen.

Wählen Sie das CPU-Modell und den RAM (Arbeitsspeicher) für den Bare Metal Server aus.

Tabelle 1. Optionen für angepasste {{site.data.keyword.baremetal_short}}-Instanzen

| CPU-Modelloptionen        | RAM-Optionen       |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4 / 16 Kerne insgesamt, 2,1 GHz | 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2650 v4 / 24 Kerne insgesamt, 2,2 GHz | 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2690 v4 / 28 Kerne insgesamt, 2,6 GHz | 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon Silver 4110-Prozessor / 16 Kerne insgesamt, 2,1 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon Gold 5120-Prozessor / 28 Kerne insgesamt, 2,2 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon Gold 6140-Prozessor / 36 Kerne insgesamt, 2,3 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |

### Bare Metal Server-Anzahl

Eine Cloud Foundation-Instanz besteht in der Erstbereitstellung aus vier Bare Metal Server-Instanzen. Sie können die Anzahl der Bare Metal Server-Instanzen nicht ändern, wenn Sie die Bestellung aufgeben.

## Speichereinstellungen

Die Cloud Foundation-Instanzen unterstützen nur den vSAN-Speicher.
* Wenn Sie für die Bare Metal Server-Konfiguration die Option **Vorkonfiguriert** auswählen, dann sind die Speichereinstellungen standardisiert und können nicht geändert werden:
  * Für die Bare Metal Server-Konfiguration vom Typ **S (Klein)** werden 2 SSD-SED-Plattenlaufwerke mit jeweils 1,9 TB bestellt.
  * Für die Bare Metal Server-Konfiguration vom Typ **L (Groß)** werden 4 SSD-SED-Plattenlaufwerke mit jeweils 3,8 TB bestellt.
* Wenn Sie für die Bare Metal Server-Konfiguration die Option **Angepasst** auswählen, können Sie den VMware vSAN-Speicher für Ihre Instanz anpassen, indem Sie die folgenden Einstellungen unter **vSAN-Speicher** angeben:
  * **Plattentyp und -größe für vSAN-Kapazitätsplatten**: Wählen Sie die Kapazität aus, die Ihrem Bedarf an gemeinsam genutzten Speicher entspricht.
  * **Anzahl der vSAN-Kapazitätsplatten**: Geben Sie die Anzahl der Platten für den gemeinsam genutzten vSAN-Speicher an, die Sie hinzufügen wollen. Die Plattenanzahl muss 2, 4, 6 oder 8 sein.

## Netzschnittstelleneinstellungen

Sie müssen die folgenden Netzschnittstelleneinstellungen angeben, wenn Sie eine Cloud Foundation-Instanz bestellen.

### Hostnamenspräfix

Das Hostnamenspräfix muss die folgenden Anforderungen erfüllen:
*  Es sind nur alphanumerische Zeichen und Bindestriche (-) zulässig.
*  Das Hostnamenspräfix muss mit einem alphanumerischen Zeichen beginnen und enden.
*  Die maximale Länge des Hostnamenspräfix beträgt 10 Zeichen.

### Unterdomänenbezeichnung

Die Unterdomänenbezeichnung muss die folgenden Anforderungen erfüllen:
*  Es sind nur alphanumerische Zeichen und Bindestriche (-) zulässig.
*  Die Unterdomänenbezeichnung muss mit einem alphanumerischen Zeichen beginnen und enden.
*  Die maximale Länge der Unterdomänenbezeichnung beträgt 10 Zeichen.
*  Die Unterdomänenbezeichnung muss innerhalb Ihres Kontos eindeutig sein.

### Domänenname

Der Rootdomänenname muss die folgenden Anforderungen erfüllen:
* Der Domänenname muss aus zwei oder mehr Zeichenfolgen bestehen, die jeweils durch einen Punkt (.) voneinander getrennt sind.
* Die erste Zeichenfolge muss mit einem alphabetischen Zeichen beginnen und mit einem alphanumerischen Zeichen enden.
* Alle Zeichenfolgen mit Ausnahme der letzten darf nur alphanumerische Zeichen und Gedankenstriche (-) enthalten.
* Die letzte Zeichenfolge darf nur Buchstaben enthalten.
* Die Länge der letzten Zeichenfolge muss zwischen 2 und 24 Zeichen betragen.

**Hinweis:** Die maximale Länge des vollständig qualifizierten Domänennamens für Hosts und VMs beträgt 50 Zeichen. Domänennamen müssen diese maximale Länge zulassen.

### Wertformat für Netzeinstellungen

Der Domänenname und die Unterdomänenbezeichnung werden verwendet, um den Benutzernamen und die Servernamen der Instanz zu generieren. Diese Informationen sind in der folgenden Tabelle dargestellt.

Tabelle 2. Wertformat für Benutzernamen, Domänennamen und Servernamen

| Name        | Wertformat      |
  |:------------- |:------------- |
  | Domänenname | `<root_domain>` |  
  | Vollständig qualifizierter Name des ESXi-Servers | `<host_prefix><n>.<subdomain_label>.<root_domain>`, hierbei steht `<n>` für die Folgenummer des ESXi-Servers. Die maximale Länge beträgt 50 Zeichen. |   
  | Anmeldebenutzername für vCenter Server | `<user_id>@<root_domain>` (Microsoft Active Directory-Benutzer) oder `administrator@vsphere.local` |
  | Vollständig qualifizierter Domänennname für vCenter Server | `vcenter-1.<subdomain_label>.<root_domain>`. Die maximale Länge beträgt 50 Zeichen. |  
  | Vollständig qualifizierter Domänenname für SDDC Manager | `sddcmanager.<subdomain_label>.<root_domain>`. Die maximale Länge beträgt 50 Zeichen. |
  | SSO-Standortname | `<subdomain_label>`
  | Vollständig qualifizierter Domänenname für PSC | `PSC-<subdomain_label>.<subdomain_label>.<root_domain>`. Die maximale Länge beträgt 50 Zeichen. |  

  Der vollständig qualifizierte Domänenname für SDDC Manager kann nicht öffentlich auflösbar sein. Andernfalls schlägt die Konfiguration der Cloud-Foundation-Instanz möglicherweise fehl und kann nicht wiederhergestellt werden. Prüfen Sie vor Angabe eines Domänennamens die Informationen unter [Hinweise zur Auswahl eines Rootdomänennamens](../vmonic/trbl_limitations.html#considerations-when-choosing-a-root-domain-name-for-cloud-foundation-instances).

### VLANs

Die Netzeinstellungen basieren auf Ihrer Auswahl von entweder **Neue VLANs bestellen** oder **Vorhandene VLANs auswählen**.

Für Ihre Instanzbestellung sind 1 öffentliches VLAN und 2 private VLANs erforderlich. Die zwei privaten VLANs werden in jedem Bare Metal Server zusammengelegt.

**Neue VLANs bestellen**  
Wählen Sie diese Option aus, um ein neues öffentliches VLANs und zwei neue private VLANs zu bestellen.

**Vorhandene VLANs auswählen**  
Abhängig vom ausgewählten {{site.data.keyword.CloudDataCent_notm}} sind möglicherweise vorhandene öffentliche und private VLANs verfügbar.

Wenn Sie vorhandene öffentliche und private VLANs wiederverwenden wollen, dann geben Sie die VLANs und Teilnetze an:
  * **Öffentliches VLAN** - Wird für den Zugriff auf öffentliche Netze verwendet.
  * **Privates VLAN** - Wird für die Konnektivität zwischen den Rechenzentren und Services in {{site.data.keyword.cloud_notm}} verwendet.
  * **Sekundäres privates VLAN** - Wird für VMware-Funktionen wie z. B. vSAN verwendet.
  * **Primäres Teilnetz** - Wird physischen Hosts für den Zugriff auf öffentliche Netze zugewiesen.
  * **Privates primäres Teilnetz** - Wird physischen Hosts für den Managementdatenverkehr zugewiesen.

**Wichtig:**
* Stellen Sie sicher, dass die Firewallkonfiguration bei den ausgewählten VLANs den Managementdatenverkehr nicht blockiert.
* Stellen Sie sicher, dass sich alle von Ihnen ausgewählten VLANs in demselben Pod befinden, da ESXi-Server nicht in VLANs mit heterogenen Pods bereitgestellt werden können.

## Services

Beim Bestellen einer Cloud Foundation-Instanz können Sie auch zusätzliche Services bestellen. Weitere Informationen zu den verfügbaren Services finden Sie unter [Services für Cloud Foundation-Instanzen](sd_planning.html#services-for-cloud-foundation-instances).

## Bestellübersicht

Auf Basis der für die Instanz und die Add-on-Services ausgewählten Konfiguration werden die geschätzten Kosten sofort generiert und im rechten Fenster angezeigt. Klicken Sie unten im rechten Fenster auf **Preisdetails**, um ein PDF-Dokument zu generieren, das die Kostenschätzungsdetails enthält.

## Vorgehensweise

1. Klicken Sie im {{site.data.keyword.cloud_notm}}-Katalog im linken Navigationsfenster auf **VMware** und anschließend im Abschnitt **Virtuelle Rechenzentren** auf **Cloud Foundation**.
2. Klicken Sie auf der Seite **VMware Cloud Foundation on IBM Cloud** auf **Erstellen**.
3. Geben Sie auf der Seite **Cloud Foundation** den Instanznamen ein.
4. Wählen Sie den Instanztyp aus:
   * Klicken Sie auf **Primäre Instanz**, um eine einzelne Instanz in der Umgebung bereitzustellen oder um die erste Instanz in einer Topologie mit mehreren Standorten bereitzustellen.
   * Klicken Sie auf **Sekundäre Instanz**, um die Instanz mit einer vorhandenen (primären) Instanz in der Umgebung zu verbinden, um eine hohe Verfügbarkeit zu erreichen, und führen Sie dann die folgenden Schritte aus:
     1. Wählen Sie die primäre Instanz aus, mit der die sekundäre Instanz verbunden werden soll.
     2. Wenn für die primäre Instanz, die Sie ausgewählt haben, ein Upgrade auf das Release der Version 2.5 durchgeführt wurde oder die primäre Instanz in Version 2.4 und früheren Releases bereitgestellt oder aktualisiert wurde, überprüfen Sie das voreingetragene **** Administratorkennwort für die PSC in der primären Instanz, um sicherzustellen, dass es korrekt ist.
     
         **Hinweis:** Das Feld für **** das Administratorkennwort für PSC in der primären Instanz ist nicht für primäre Instanzen verfügbar, die in Version 2.5 oder höheren Releases bereitgestellt werden.     
5. Geben Sie die Lizenzeinstellungen für die Instanzkomponenten ein:
   *  Zur Verwendung der von IBM bereitgestellten Lizenzen müssen Sie **In Kauf einbeziehen** auswählen.
   *  Zur Verwendung einer eigenen Lizenz müssen Sie **Lizenz selbst bereitstellen** auswählen und den Lizenzschlüssel eingeben.  
6. Geben Sie die Bare Metal Server-Einstellungen an:
   1. Wählen Sie das {{site.data.keyword.CloudDataCent_notm}} als Host für die Instanz aus.
   2. Wählen Sie die Bare Metal Server-Konfiguration aus.
      * Wenn Sie **Vorkonfiguriert** auswählen, dann können Sie zwischen der Konfiguration **S (Klein)** und der Konfiguration **L (Groß)** wählen.
      * Wenn Sie **Angepasst** auswählen, dann müssen Sie das CPU-Modell und die RAM-Größe angeben.
7. Geben Sie die Speichereinstellungen an:
   * Wenn Sie für die Bare-Metal-Konfiguration die Option **Vorkonfiguriert** ausgewählt haben, ist zu beachten, dass die Speichereinstellungen für die standardisierten Bare Metal Server-Konfigurationen **S (Klein)** und **L (Groß)** nicht geändert werden können.
   * Wenn Sie für die Bare-Metal-Konfiguration die Option **Angepasst** ausgewählt haben, geben Sie **Plattentyp und -größe für vSAN-Kapazitätsplatten** und **Anzahl der vSAN-Kapazitätsplatten** an.
8. Geben Sie die Netzschnittstelleneinstellungen an:
   1. Geben Sie das Hostnamenspräfix, die Unterdomänenbezeichnung und den Rootdomänennamen ein. Für eine sekundäre Instanz wird der Domänenname automatisch eingetragen.
   2. Wählen Sie die VLAN-Einstellungen aus:
      * Falls Sie neue öffentliche und private VLANs bestellen wollen, klicken Sie auf **Neue VLANs bestellen**.
      * Wenn Sie die vorhandenen öffentlichen und privaten VLANs wiederverwenden möchten, sofern diese verfügbar sind, dann klicken Sie auf **Vorhandene VLANs auswählen** und geben Sie die VLANs und Teilnetze an.

9. Wählen Sie die Add-on-Services aus, die in der Instanz bereitgestellt werden sollen, indem Sie auf die entsprechende Servicekarte klicken. Wenn ein Service konfiguriert werden muss, dann geben Sie die servicespezifischen Einstellungen an und klicken Sie dann im Popup-Konfigurationsfenster auf **Service hinzufügen**. Informationen zum Angeben von Einstellungen für einen Service finden Sie im entsprechenden Abschnitt zum Bestellen von Services.

10. Überprüfen Sie im Fenster **Bestellübersicht** die Instanzkonfiguration, bevor Sie die Bestellung aufgeben.
    1. Überprüfen Sie die Einstellungen für die Instanz.
    2. Überprüfen Sie die geschätzten Kosten der Instanz. Klicken Sie auf **Preisdetails**, um eine PDF-Datei mit der Zusammenfassung zu generieren. Ihre Bestellübersicht können Sie speichern oder drucken, indem Sie rechts oben im PDF-Fenster auf das Symbol **Drucken** bzw. **Herunterladen** klicken.
    3. Vergewissern Sie sich, dass das zu belastende Konto korrekt ist und wählen Sie dann das Kontrollkästchen **Ich habe zur Kenntnis genommen, dass das im Folgenden aufgeführte Konto belastet wird** aus.
    4. Klicken Sie auf den Link bzw. die Links für die Bedingungen, die für Ihre Bestellung gelten. Vergewissern Sie sich, dass Sie mit diesen Bedingungen einverstanden sind, und wählen Sie dann das Kontrollkästchen **Ich habe die im Folgenden aufgeführten Vereinbarungen zu dem Service eines anderen Anbieters gelesen und diesen zugestimmt** aus.
    5. Klicken Sie auf **Bereitstellung**.

## Ergebnisse

Die Bereitstellung der Instanz wird automatisch gestartet. Sie erhalten eine Bestätigung, dass die Bestellung bearbeitet wird, und Sie können den Status der Bereitstellung prüfen, indem Sie die Instanzdetails anzeigen.

Nachdem die Instanz erfolgreich bereitgestellt wurde, sind die Komponenten, die unter [Technische Spezifikationen für Cloud Foundation-Instanzen](../sddc/sd_cloudfoundationoverview.html#technical-specifications-for-cloud-foundation-instances) beschrieben sind, auf Ihrer virtuellen VMware-Plattform installiert. Die von Ihnen bestellten ESXi-Server werden standardmäßig als **SDDC-Cluster** gruppiert. Wenn Sie zusätzliche Services bestellt haben, wird die Bereitstellung der Services gestartet, nachdem Ihre Bestellung abgeschlossen ist.

Sobald die Instanz einsatzbereit ist, ändert sich der Status der Instanz in **Bereit** und Sie empfangen per E-Mail eine Benachrichtigung.

Wenn Sie eine sekundäre Instanz bestellen, kann VMware vSphere Web Client für die primäre Instanz (mit der sekundären Instanz verknüpft) erneut gestartet werden, nachdem die Bestellung der sekundären Instanz abgeschlossen ist.

## Nächste Schritte

Sie können nun die bestellte Cloud Foundation-Instanz anzeigen und verwalten.

**Wichtig**: Sie dürfen die {{site.data.keyword.vmwaresolutions_short}}-Komponenten, die in Ihrem {{site.data.keyword.cloud_notm}}-Konto erstellt werden, nur über die {{site.data.keyword.vmwaresolutions_short}}-Konsole und nicht im {{site.data.keyword.slportal}} oder über ein anderes Verfahren außerhalb der Konsole verwalten. Wenn Sie diese Komponenten außerhalb der {{site.data.keyword.vmwaresolutions_short}}-Konsole ändern, werden die Änderungen nicht mit der Konsole synchronisiert.

**VORSICHT**: Wenn Sie {{site.data.keyword.vmwaresolutions_short}}-Komponenten (die in Ihrem {{site.data.keyword.cloud_notm}}-Konto installiert wurden, als Sie die Instanz bestellt haben) außerhalb der {{site.data.keyword.vmwaresolutions_short}}-Konsole verwalten, kann dies zur Instabilität Ihrer Umgebung führen. Zu diesen Managementaktivitäten gehören:

*  Komponenten hinzufügen, ändern, zurückgeben oder entfernen
*  Instanzkapazität durch das Hinzufügen oder Entfernen von ESXi-Servern erweitern oder verringern
*  Komponenten ausschalten
*  Services erneut starten

   Ausgenommen von diesen Aktivitäten ist unter anderem das Management der Dateifreigaben für gemeinsam genutzten Speicher im {{site.data.keyword.slportal}}. Hierzu gehört das Bestellen, Löschen (mit möglicher Auswirkung auf angehängte Datenspeicher), Berechtigen und Anhängen von Dateifreigaben für gemeinsam genutzten Speicher.

### Zugehörige Links

* [Für ein {{site.data.keyword.cloud_notm}}-Konto registrieren](../vmonic/signing_softlayer_account.html)
* [Cloud Foundation-Instanzen anzeigen](sd_viewinginstances.html)
* [Cluster für Cloud Foundation-Instanzen hinzufügen, anzeigen und löschen](sd_addingviewingclusters.html)
* [Kapazität für Cloud Foundation-Instanzen erweitern und verringern](sd_addingremovingservers.html)
* [Services für Cloud Foundation-Instanzen bestellen, anzeigen und entfernen](sd_addingremovingservices.html)
* [Cloud Foundation-Instanzen löschen](sd_deletinginstance.html)
* [Häufig gestellte Fragen zu eigenen Lizenzen (BYOL)](../vmonic/faq_byol.html)
