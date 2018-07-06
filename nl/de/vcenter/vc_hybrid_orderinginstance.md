---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-22"

---

# vCenter Server with Hybridity Bundle-Instanzen bestellen

Um eine flexible und anpassbare virtualisierte VMware-Plattform bereitzustellen, die Ihren Workloadbedarf optimal erfüllt, bestellen Sie eine VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle-Instanz. Ihre Bestellung der vCenter Server with Hybridity Bundle-Instanz beinhaltet die Lizenzierung von VMware Hybrid Cloud Extension (HCX) und berechtigt Sie zur Verwendung des Service "VMware HCX on IBM Cloud". Sie können auch Services hinzufügen, wie zum Beispiel [Zerto on {{site.data.keyword.cloud}}](../services/addingzertodr.html) für die Disaster-Recovery.

## Voraussetzungen

Stellen Sie sicher, dass Sie die folgenden Tasks ausgeführt haben:
*  Sie haben die Berechtigungsnachweise für die {{site.data.keyword.cloud_notm}}-Infrastruktur auf der Seite **Einstellungen** konfiguriert. Weitere Informationen finden Sie unter [Benutzerkonten und Einstellungen verwalten](../vmonic/useraccount.html).
*  Sie haben die Informationen in [Voraussetzungen und Planung für vCenter Server with Hybridity Bundle](vc_hybrid_planning.html) gelesen.
* Sie haben das Instanz- und Domänennamensformat geprüft. Der Domänenname und die Unterdomänenbezeichnung werden verwendet, um den Benutzernamen und die Servernamen der Instanz zu generieren.

Tabelle 1. Wertformat für Instanz- und Domänennamen

| Name        | Wertformat      |
  |:------------- |:------------- |
  | Domänenname | `<root_domain>` |  
  | Anmeldebenutzername für vCenter Server | `<user_id>@<root_domain>` (Microsoft Active Directory-Benutzer) oder `administrator@vsphere.local` |
  | Vollständig qualifizierter Domänennname für vCenter Server | ` vcenter.<subdomain_label>.<root_domain>`. Die maximale Länge beträgt 50 Zeichen. |
  | SSO-Standortname | `<subdomain_label>` |
  | Vollständig qualifizierter Name des ESXi-Servers | `<host_prefix><n>.<subdomain_label>.<root_domain>`, hierbei steht `<n>` für die Folgenummer des ESXi-Servers. Die maximale Länge beträgt 50 Zeichen. |  
  | Vollständig qualifizierter Domänenname für PSC | `psc-<subdomain_label>.<subdomain_label>.<root_domain>`. Die maximale Länge beträgt 50 Zeichen. |

**Wichtig**: Nehmen Sie keine Änderungen an Werten vor, die während der Bestellung und Instanzbereitstellung festgelegt werden. Dies kann dazu führen, dass Ihre Instanz unbrauchbar wird. Beispielsweise könnte der öffentliche Netzbetrieb beendet werden, Server sowie Virtual Server-Instanzen (VSIs) könnten mitten in einer Bereitstellung hinter eine Vyatta-Einheit versetzt werden oder die Virtual Server-Instanz für IBM CloudBuilder könnte gestoppt bzw. gelöscht werden.

## Systemeinstellungen

Sie müssen die folgenden Systemeinstellungen angeben, wenn Sie eine vCenter Server with Hybridity Bundle-Instanz bestellen.

### Instanzname

Der Instanzname muss die folgenden Anforderungen erfüllen:
* Es sind nur alphanumerische Zeichen und Bindestriche (-) zulässig.
* Der Instanzname muss mit einem alphanumerischen Zeichen beginnen und enden.
* Die maximale Länge des Instanznamens beträgt 10 Zeichen.
* Der Instanzname muss innerhalb Ihres Kontos eindeutig sein.

### Primär oder sekundär

Wählen Sie aus, ob Sie eine neue primäre oder sekundäre Instanz für eine bereits vorhandene primäre Instanz bestellen wollen.

## Lizenzierungseinstellungen

Die Bestellung der vCenter Server with Hybridity Bundle-Instanz enthält die folgenden Lizenzen. Für die NSX-Lizenzeditionen müssen Sie entweder **Advanced** oder **Enterprise** angeben.

* VMware vCenter Server 6.5
* VMware vSphere Enterprise Plus 6.5u1
* VMware NSX Service Providers Edition (Advanced oder Enterprise) 6.3
* VMware vSAN 6.6-Lizenzedition (Advanced oder Enterprise)

**Achtung:**
* vCenter Server with Hybridity Bundle-Instanzen bieten keine BYOL-Unterstützung (BYOL = Bring Your Own License; Verwendung der eigenen Lizenz).
* Die mindestens erforderlichen Lizenzeditionen sind in der Benutzerschnittstelle angegeben. Falls unterschiedliche Komponenteneditionen unterstützt werden, können Sie die gewünschte Edition auswählen.

## Einstellungen für Bare Metal Server

Die Bare Metal-Einstellungen sind von Ihrer {{site.data.keyword.CloudDataCent_notm}}-Konfiguration und der angepassten Konfiguration abhängig.

Für den ersten Cluster und die nach der Bereitstellung verfügbaren Cluster für vSAN-Konfigurationen sind vier ESXi-Server erforderlich. Alle ESXi-Server nutzen dieselbe Konfiguration gemeinsam. Nach der Bereitstellung können Sie vier weitere Cluster hinzufügen.

### Standort des Rechenzentrums

Wählen Sie das {{site.data.keyword.CloudDataCent_notm}} aus, das als Host für die Instanz verwendet werden soll.

### Angepasst

Geben Sie das CPU-Modell und die Menge des RAM für den angepassten Bare Metal Server an.

Tabelle 2. Optionen für angepasste {{site.data.keyword.baremetal_short}}-Instanzen

| CPU-Optionen        | RAM-Optionen       |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4 / 16 Kerne insgesamt, 2,1 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2650 v4 / 24 Kerne insgesamt, 2,2 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2690 v4 / 28 Kerne insgesamt, 2,6 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon Silver 4110-Prozessor / 16 Kerne insgesamt, 2,1 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon Gold 5120-Prozessor / 28 Kerne insgesamt, 2,2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon Gold 6140-Prozessor / 36 Kerne insgesamt, 2,3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
### Bare Metal Server-Anzahl

Standardmäßig werden vier ESXi-Server ausgewählt. Diese Einstellung kann nicht geändert werden.

## Speichereinstellungen

VMware vSAN 6.6 ist Bestandteil der Bestellung Ihrer vCenter Server with Hybridity Bundle-Instanz. Sie müssen die folgenden Speichereinstellungen angeben, wenn Sie die Instanz bestellen:

* **Plattentyp und -größe für vSAN-Kapazitätsplatten**: Wählen Sie die Kapazität aus, die Ihrem Bedarf an gemeinsam genutzten Speicher entspricht.
* **Anzahl der vSAN-Kapazitätsplatten**: Wählen Sie die Anzahl der Platten für den gemeinsam genutzten vSAN-Speicher aus, die Sie hinzufügen wollen. Die Plattenanzahl muss 2, 4, 6 oder 8 sein.

## Netzschnittstelleneinstellungen

Sie müssen die folgenden Netzschnittstelleneinstellungen angeben, wenn Sie eine vCenter Server with Hybridity Bundle-Instanz bestellen.

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

### Neue VLANs bestellen

Wählen Sie **Neue VLANs bestellen** aus, um ein neues öffentliches VLAN und zwei neue private VLANs zu bestellen.

Für Ihre Instanzbestellung sind 1 öffentliches VLAN und 2 private VLANs erforderlich. Die zwei privaten VLANs werden in jedem Bare Metal Server zusammengelegt.

### Vorhandene VLANs auswählen

Abhängig vom ausgewählten {{site.data.keyword.CloudDataCent_notm}} sind möglicherweise vorhandene öffentliche und private VLANs verfügbar.

Für Ihre Instanzbestellung sind 1 öffentliches VLAN und 2 private VLANs erforderlich. Die zwei privaten VLANs werden in jedem Bare Metal Server zusammengelegt.

Wählen Sie **Vorhandene VLANs auswählen** aus, um vorhandene öffentliche und private VLANs wiederzuverwenden und eine Auswahl unter den verfügbaren VLANs und Teilnetzen zu treffen.

**Wichtig:**
* Stellen Sie sicher, dass die Firewallkonfiguration bei den ausgewählten VLANs den Managementdatenverkehr nicht blockiert.
* Stellen Sie sicher, dass sich alle von Ihnen ausgewählten VLANs in demselben Pod befinden, da ESXi-Server nicht in VLANs mit heterogenen Pods bereitgestellt werden können.

### DNS-Konfiguration

Wählen Sie die Konfiguration für DNS (Domain Name System) für Ihre Instanz aus:

* **Einzelne öffentliche Windows-VSI für Active Directory/DNS**: Eine einzelne Serverinstanz (VSI) von Microsoft Windows Server für Microsoft Active Directory (AD), die als DNS für die Instanz dient, auf der die Hosts und VMs registriert sind, wird bereitgestellt und kann zur Suche verwendet werden.
* **Zwei hoch verfügbare dedizierte Windows-Server-VMs auf dem Management-Cluster**: Es werden zwei Microsoft Windows-VMs bereitgestellt, die den Datenschutz und die Leistungsfähigkeit verbessern.

**Wichtig:** Sie müssen zwei Lizenzen für Microsoft Windows Server 2012 R2 bereitstellen, wenn Sie Ihre Instanz für die Verwendung der beiden Microsoft Windows-VMs konfigurieren. Verwenden Sie die Lizenz für Microsoft Windows Server 2012 R2 Standard Edition und/oder die Lizenz für Microsoft Windows Server 2012 R2 Datacenter Edition.

Jede Lizenz kann nur einem einzigen physischen Server zugeordnet werden und deckt bis zu zwei physische Prozessoren ab. Mit einer Standard Edition-Lizenz können zwei virtualisierte Microsoft Windows-VMs pro 2-Prozessor-Server ausgeführt werden. Daher sind zwei Lizenzen erforderlich, weil zwei Microsoft Windows-VMs in zwei unterschiedlichen Hosts bereitgestellt werden.

Sie haben 30 Tage Zeit, um die VMs zu aktivieren.

Weitere Informationen zum Bestellen der Windows-Lizenzierung finden Sie auf der Seite [Windows Server 2012 R2 documentation](https://www.microsoft.com/en-us/licensing/product-licensing/windows-server-2012-r2.aspx#tab=2).

## Serviceeinstellungen

Beim Bestellen einer vCenter Server with Hybridity Bundle-Instanz können Sie auch zusätzliche Services bestellen. Weitere Informationen zu den Services finden Sie unter [Verfügbare Services für vCenter Server with Hybridity Bundle-Instanzen](vc_hybrid_addingremovingservices.html#available-services-for-vcenter-server-with-hybridity-bundle-instances).

## Bestellübersicht

Auf Basis der für die Instanz und die Add-on-Services ausgewählten Konfiguration werden die geschätzten Kosten sofort generiert und im rechten Fenster im Abschnitt **Bestellübersicht** angezeigt. Klicken Sie unten im rechten Fenster auf **Preisdetails**, um ein PDF-Dokument zu generieren, das die Kostenschätzungsdetails enthält.

## Vorgehensweise

1. Klicken Sie im IBM Cloud-Katalog im linken Navigationsfenster auf **VMware** und anschließend im Abschnitt **Virtuelle Rechenzentren** auf **vCenter Server**.
2. Klicken Sie auf der Seite **VMware vCenter Server on IBM Cloud** auf die Karte **vCenter Server with Hybridity Bundle** und dann auf **Erstellen**.
3. Geben Sie auf der Seite **vCenter Server** den Instanznamen ein.
4. Wählen Sie den Instanztyp aus:
   * Klicken Sie auf **Primäre Instanz**, um eine einzelne Instanz in der Umgebung bereitzustellen oder um die erste Instanz in einer Topologie mit mehreren Standorten bereitzustellen.
   * Klicken Sie auf **Sekundäre Instanz**, um die Instanz mit einer vorhandenen (primären) Instanz in der Umgebung zu verbinden, um eine hohe Verfügbarkeit zu erreichen, und führen Sie dann die folgenden Schritte aus:
     1. Wählen Sie die primäre Instanz aus, mit der die sekundäre Instanz verbunden werden soll.
     2. Geben Sie das PSC-Administratorkennwort für die primäre Instanz ein.
5. Wählen Sie die NSX-Lizenzedition und die vSAN-Lizenzedition aus.
6. Geben Sie die Bare Metal Server-Einstellungen an.
  1. Wählen Sie das {{site.data.keyword.CloudDataCent_notm}} als Host für die Instanz aus.
  2. Wählen Sie das CPU-Modell **Angepasst** und die Menge des **RAM** aus.

  **Hinweis:** Die **Anzahl der Bare Metal Server** ist standardmäßig auf vier gesetzt und kann nicht geändert werden.

7. Führen Sie die Speicherkonfiguration durch.
  1. Wählen Sie **Plattentyp und -größe für vSAN-Kapazitätsplatten** aus.
  2. Wählen Sie **Anzahl der vSAN-Kapazitätsplatten** aus.
8. Führen Sie die Netzschnittstellenkonfiguration durch.
  1. Geben Sie das Hostnamenspräfix, die Unterdomänenbezeichnung und den Rootdomänennamen ein.
  2. Wählen Sie die VLAN-Konfiguration aus.
     *  Falls Sie neue öffentliche und private VLANs bestellen wollen, klicken Sie auf **Neue VLANs bestellen**.
     *  Wenn Sie die vorhandenen öffentlichen und privaten VLANs wiederverwenden möchten, sofern diese verfügbar sind, dann klicken Sie auf **Vorhandene VLANs auswählen** und wählen Sie anschließend das öffentliche VLAN, das primäre Teilnetz, das private VLAN, das primäre private Teilnetz und das sekundäre private VLAN aus.
  3. Wählen Sie die DNS-Konfiguration aus.
9. Wählen Sie die Add-on-Services aus, die in der Instanz bereitgestellt werden sollen, indem Sie auf die entsprechende Servicekarte klicken. Wenn ein Service konfiguriert werden muss, dann geben Sie die servicespezifischen Einstellungen an und klicken Sie dann auf der Karte auf **Service hinzufügen**.  
Informationen zum Angeben von Einstellungen für einen Service finden Sie im entsprechenden Abschnitt zum Bestellen von Services.

8. Überprüfen Sie im Fenster **Bestellübersicht** die Instanzkonfiguration, bevor Sie die Bestellung aufgeben.
   1. Überprüfen Sie die Einstellungen für die Instanz.
   2. Überprüfen Sie die geschätzten Kosten der Instanz. Klicken Sie auf **Preisdetails**, um eine PDF-Datei mit der Zusammenfassung zu generieren. Ihre Bestellübersicht können Sie speichern oder drucken, indem Sie rechts oben im PDF-Fenster auf das Symbol **Drucken** bzw. **Herunterladen** klicken.
   3. Klicken Sie auf den Link bzw. die Links für die Bedingungen, die für Ihre Bestellung gelten, und vergewissern Sie sich, dass Sie mit diesen Bedingungen einverstanden sind, bevor Sie die Instanz bestellen.
   4. Klicken Sie auf **Bereitstellung**.

## Ergebnisse

Die Bereitstellung der Instanz wird automatisch gestartet. Sie erhalten eine Bestätigung, dass die Bestellung bearbeitet wird, und Sie können den Status der Bereitstellung prüfen, indem Sie die Instanzdetails anzeigen.

Nachdem die Instanz erfolgreich bereitgestellt wurde, sind die Komponenten, die im Abschnitt _Technische Spezifikationen für vCenter Server with Hybridity Bundle_ im [Überblick zu vCenter Server with Hybridity Bundle](vc_hybrid_overview.html) beschrieben werden, auf Ihre virtuelle VMware-Plattform installiert. Die von Ihnen bestellten ESXi-Server werden standardmäßig als **cluster1** gruppiert. Wenn Sie zusätzliche Services bestellt haben, wird die Bereitstellung der Services gestartet, nachdem Ihre Bestellung abgeschlossen ist.

Sobald die Instanz einsatzbereit ist, ändert sich der Status der Instanz in **Bereit** und Sie empfangen per E-Mail eine Benachrichtigung.

Wenn Sie eine sekundäre Instanz bestellen, kann VMware vSphere Web Client für die primäre Instanz (mit der sekundären Instanz verknüpft) erneut gestartet werden, nachdem die Bestellung der sekundären Instanz abgeschlossen ist.

## Nächste Schritte

Sie können nun die bestellte vCenter Server with Hybridity Bundle-Instanz anzeigen und verwalten.

**Wichtig**: Sie dürfen die {{site.data.keyword.vmwaresolutions_short}}-Komponenten, die in Ihrem {{site.data.keyword.cloud_notm}}-Konto erstellt werden, nur über die {{site.data.keyword.vmwaresolutions_short}}-Konsole und nicht im {{site.data.keyword.slportal}} oder über ein anderes Verfahren außerhalb der Konsole verwalten.
Wenn Sie diese Komponenten außerhalb der {{site.data.keyword.vmwaresolutions_short}}-Konsole ändern, werden die Änderungen nicht mit der Konsole synchronisiert.

**VORSICHT**: Wenn Sie {{site.data.keyword.vmwaresolutions_short}}-Komponenten (die in Ihrem {{site.data.keyword.cloud_notm}}-Konto installiert wurden, als Sie die Instanz bestellt haben) außerhalb der {{site.data.keyword.vmwaresolutions_short}}-Konsole verwalten, kann dies zur Instabilität Ihrer Umgebung führen. Zu diesen Managementaktivitäten gehören:
*  Komponenten hinzufügen, ändern, zurückgeben oder entfernen
*  Instanzkapazität durch das Hinzufügen oder Entfernen von ESXi-Servern erweitern oder verringern
*  Komponenten ausschalten
*  Services erneut starten

   Ausgenommen von diesen Aktivitäten ist unter anderem das Management der Dateifreigaben für gemeinsam genutzten Speicher im {{site.data.keyword.slportal}}. Hierzu gehört das Bestellen, Löschen (mit möglicher Auswirkung auf angehängte Datenspeicher), Berechtigen und Anhängen von Dateifreigaben für gemeinsam genutzten Speicher.

## Zugehörige Links

* [Für ein {{site.data.keyword.cloud_notm}}-Konto registrieren](../vmonic/signing_softlayer_account.html)
* [vCenter Server with Hybridity Bundle-Instanzen anzeigen](vc_hybrid_viewinginstances.html)
* [Konfiguration mit mehreren Standorten für vCenter Server with Hybridity Bundle-Instanzen](vc_hybrid_multisite.html)
* [Cluster für vCenter Server with Hybridity Bundle-Instanzen hinzufügen und anzeigen](vc_hybrid_addingviewingclusters.html)
* [Kapazität für vCenter Server with Hybridity Bundle-Instanzen erweitern und verringern](vc_hybrid_addingremovingservers.html)
* [Services für vCenter Server with Hybridity Bundle-Instanzen bestellen, anzeigen und entfernen](vc_hybrid_addingremovingservices.html)
* [vCenter Server with Hybridity Bundle-Instanzen löschen](vc_hybrid_deletinginstance.html)
