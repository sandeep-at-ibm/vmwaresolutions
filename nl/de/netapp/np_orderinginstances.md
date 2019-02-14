---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-25"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# NetApp ONTAP Select-Instanzen bestellen

Durch die Bestellung einer NetApp ONTAP Select-Instanz können Sie eine virtualisierte VMware-Plattform mit einer dedizierten und hoch verfügbaren Appliance für softwaredefinierten Speicher bereitstellen.

## Voraussetzungen

Stellen Sie sicher, dass Sie die folgenden Tasks ausgeführt haben:
*  Sie haben die Berechtigungsnachweise für die {{site.data.keyword.cloud}}-Infrastruktur auf der Seite **Einstellungen** konfiguriert. Weitere Informationen finden Sie unter [Benutzerkonten und Einstellungen verwalten](/docs/services/vmwaresolutions/vmonic/useraccount.html).
*  Sie haben sich mit den Voraussetzungen und Hinweisen im Abschnitt [Voraussetzungen und Planung für NetApp ONTAP Select-Instanzen](/docs/services/vmwaresolutions/netapp/np_planning.html) vertraut gemacht.

Nehmen Sie keine Änderungen an Werten vor, die während der Bestellung oder Bereitstellung der Instanz festgelegt werden. Dies kann dazu führen, dass Ihre Instanz unbrauchbar wird. Beispielsweise, wenn der öffentliche Netzbetrieb beendet wird, Server sowie virtuelle Serverinstanzen (VSIs) mitten in einer Bereitstellung hinter eine Vyatta-Einheit versetzt werden oder wenn die Virtual Server-Instanz für IBM CloudBuilder gestoppt oder gelöscht wird.
{:important}

## Systemeinstellungen

Wenn Sie eine NetApp ONTAP Select-Instanz bestellen, müssen Sie die folgenden Basiseinstellungen angeben.

### Instanzname

Der Instanzname muss die folgenden Anforderungen erfüllen:
* Es sind nur alphanumerische Zeichen und Bindestriche (-) zulässig.
* Der Instanzname muss mit einem alphabetischen Zeichen beginnen und mit einem alphanumerischen Zeichen enden. 
* Die maximale Länge des Instanznamens beträgt 10 Zeichen.
* Der Instanzname muss innerhalb Ihres Kontos eindeutig sein.

## Netzschnittstelleneinstellungen

Sie müssen die folgenden Netzschnittstelleneinstellungen angeben, wenn Sie eine NetApp ONTAP Select-Instanz bestellen.

### Hostnamenspräfix

Das Hostnamenspräfix muss die folgenden Anforderungen erfüllen:
*  Es sind nur alphanumerische Zeichen und Bindestriche (-) zulässig.
*  Das Hostnamenspräfix muss mit einem alphanumerischen Zeichen beginnen und enden.
*  Die maximale Länge des Hostnamenspräfix beträgt 10 Zeichen.

### Unterdomänenbezeichnung

Die Unterdomänenbezeichnung muss die folgenden Anforderungen erfüllen:
*  Es sind nur alphanumerische Zeichen und Bindestriche (-) zulässig.
*  Die Unterdomänenbezeichnung muss mit einem alphabetischen Zeichen beginnen und mit einem alphanumerischen Zeichen enden. 
*  Die maximale Länge der Unterdomänenbezeichnung beträgt 10 Zeichen.
*  Die Unterdomänenbezeichnung muss innerhalb Ihres Kontos eindeutig sein.

### Domänenname

Der Rootdomänenname muss die folgenden Anforderungen erfüllen:
* Der Domänenname muss aus zwei oder mehr Zeichenfolgen bestehen, die jeweils durch einen Punkt (.) voneinander getrennt sind.
* Die erste Zeichenfolge muss mit einem alphabetischen Zeichen beginnen und mit einem alphanumerischen Zeichen enden.
* In allen Zeichenfolgen mit Ausnahme der letzten dürfen nur alphanumerische Zeichen und Gedankenstriche (-) enthalten sein.
* In der letzten Zeichenfolge dürfen nur Buchstaben enthalten sein.
* Die Länge der letzten Zeichenfolge muss zwischen 2 und 24 Zeichen betragen.

Die maximale Länge des vollständig qualifizierten Domänennamens für Hosts und VMs beträgt 50 Zeichen. Domänennamen müssen diese maximale Länge zulassen.
{:note}

## Lizenzierungseinstellungen

Sie müssen vier NetApp-Lizenzdateien hochladen, jeweils eine für jede der vier {{site.data.keyword.baremetal_short}}-Instanzen. Wenden Sie sich an Ihr NetApp-Vertriebsteam, um die entsprechende Lizenzierung für Ihre Hochleistungs- oder Hochkapazitätsbereitstellung zu erhalten.

## Einstellungen für Bare Metal Server

### Standort des Rechenzentrums

Sie müssen das {{site.data.keyword.CloudDataCent_notm}} (Rechenzentrum) auswählen, das als Host für die Instanz verwendet werden soll.

### Bare Metal Server-Konfiguration

Wählen Sie eine Ihren Anforderungen entsprechende Bare Metal Server-Konfiguration aus:
* **Hohe Leistung (M = Mittel)** - Premium-Lizenz / Dual Intel Xeon E5-2650 V4 (24 Kerne insgesamt, 2,2 GHz) / 128 GB RAM / Kapazität von 22 1,9-TB-SSD-Laufwerken pro Knoten / Effektive Kapazität eines Clusters mit 4 Knoten - 59 TB
* **Hohe Leistung (groß)** - Premium-Lizenz / Dual Intel Xeon E5-2650 V4 (24 Kerne insgesamt, 2,2 GHz) / 128 GB RAM / Kapazität von 22 3,8-TB-SSD-Laufwerken pro Knoten / Effektive Kapazität eines Clusters mit 4 Knoten - 118 TB
* **Hohe Kapazität** - Standard-Lizenz / Dual Intel Xeon E5-2650 V4 (24 Kerne insgesamt, 2,2 GHz) / 64 GB RAM / Kapazität von 34 4-TB-SATA-Laufwerken pro Knoten / Effektive Kapazität eines Clusters mit 4 Knoten - 190 TB

3,8-TB-Solid-State-Platten (SSD) werden unterstützt, wenn sie in einem {{site.data.keyword.CloudDataCent_notm}} allgemein verfügbar gemacht werden.
{:note}

### Bare Metal Server-Anzahl

Die Anzahl der ESXi-Server einer NetApp ONTAP Select-Instanz ist standardmäßig 4. Dieser Wert kann nicht geändert werden. Alle ESXi-Server verfügen über dieselbe Konfiguration.

## Vorgehensweise zum Bestellen von NetApp ONTAP Select-Instanzen

1. Klicken Sie im {{site.data.keyword.cloud_notm}}-Katalog im linken Navigationsfenster auf **VMware** und anschließend im Abschnitt **Virtuelle Rechenzentren** auf **NetApp ONTAP Select**.
2. Klicken Sie auf der Seite **NetApp ONTAP Select** auf **Erstellen**.
3. Geben Sie auf der Seite **NetApp ONTAP** den Instanznamen ein.
4. Füllen Sie die Netzschnittstelleneinstellungen aus. Geben Sie dazu Werte für **Hostnamenspräfix**, für **Unterdomänenbezeichnung** und für **Domänenname** ein.
5. Füllen Sie die Lizenzierungseinstellungen aus. Klicken Sie dazu auf **Lizenzdateien hinzufügen**, um vier NetApp-Lizenzdateien hochzuladen, die von den vier {{site.data.keyword.baremetal_short}}-Instanzen benötigt werden.
6. Geben Sie die Bare Metal Server-Einstellungen an:
   1. Wählen Sie das {{site.data.keyword.CloudDataCent_notm}} als Host für die Instanz aus.
   2. Wählen Sie die Bare Metal Server-Konfiguration aus.
7. Überprüfen Sie im Fenster **Bestellübersicht** die Instanzkonfiguration, bevor Sie die Bestellung aufgeben.
    1. Überprüfen Sie die Einstellungen für die Instanz.
    2. Überprüfen Sie die geschätzten Kosten der Instanz. Klicken Sie auf **Preisdetails**, um eine PDF-Datei mit der Zusammenfassung zu generieren. Ihre Bestellübersicht können Sie speichern oder drucken, indem Sie im PDF-Fenster auf das Symbol **Drucken** bzw. **Herunterladen** klicken.
    3. Vergewissern Sie sich, dass das zu belastende Konto korrekt ist und wählen Sie dann das Kontrollkästchen **Ich habe zur Kenntnis genommen, dass das im Folgenden aufgeführte Konto belastet wird** aus.
    4. Klicken Sie auf den Link bzw. die Links für die Bedingungen, die für Ihre Bestellung gelten. Vergewissern Sie sich, dass Sie mit diesen Bedingungen einverstanden sind, und wählen Sie dann das Kontrollkästchen **Ich habe die im Folgenden aufgeführten Vereinbarungen zu dem Service eines anderen Anbieters gelesen und diesen zugestimmt** aus.
    5. Klicken Sie auf **Bereitstellung**.

## Ergebnisse

Die Bereitstellung der Instanz wird automatisch gestartet. Sie erhalten eine Bestätigung, dass die Bestellung bearbeitet wird, und Sie können den Status der Bereitstellung prüfen, indem Sie die Instanzdetails anzeigen.

Nachdem die Instanz erfolgreich bereitgestellt wurde, sind die Komponenten, die unter [Technische Spezifikationen für NetApp ONTAP Select-Instanzen](/docs/services/vmwaresolutions/netapp/np_netappoverview.html#technical-specifications-for-netapp-ontap-select-instances) beschrieben sind, auf Ihrer virtuellen VMware-Plattform installiert.

Sobald die Instanz einsatzbereit ist, ändert sich der Status der Instanz in **Bereit** und Sie empfangen per E-Mail eine Benachrichtigung.

## Nächste Schritte

Sie können Ihre bestellte NetApp ONTAP Select-Instanz jetzt anzeigen und verwalten.

Sie dürfen die {{site.data.keyword.vmwaresolutions_short}}-Komponenten, die in Ihrem {{site.data.keyword.cloud_notm}}-Konto erstellt werden, nur über die {{site.data.keyword.vmwaresolutions_short}}-Konsole und nicht im {{site.data.keyword.slportal}} oder über ein anderes Verfahren außerhalb der Konsole verwalten. Wenn Sie diese Komponenten außerhalb der {{site.data.keyword.vmwaresolutions_short}}-Konsole ändern, werden die Änderungen nicht mit der Konsole synchronisiert.
{:important}

**VORSICHT:** Wenn Sie {{site.data.keyword.vmwaresolutions_short}}-Komponenten (die in Ihrem {{site.data.keyword.cloud_notm}}-Konto installiert wurden, als Sie die Instanz bestellt haben) außerhalb der {{site.data.keyword.vmwaresolutions_short}}-Konsole verwalten, kann dies zur Instabilität Ihrer Umgebung führen. Zu diesen Managementaktivitäten gehören:
*  Komponenten hinzufügen, ändern, zurückgeben oder entfernen
*  Komponenten ausschalten

   Ausgenommen von diesen Aktivitäten ist unter anderem das Management der gemeinsam genutzten Dateiressourcen für gemeinsam genutzten Speicher im {{site.data.keyword.slportal}}. Hierzu gehört das Bestellen, Löschen (mit möglicher Auswirkung auf angehängte Datenspeicher), Berechtigen und Anhängen von gemeinsam genutzten Dateiressourcen für gemeinsam genutzten Speicher.

### Zugehörige Links

* [NetApp ONTAP Select-Instanzen anzeigen](/docs/services/vmwaresolutions/netapp/np_viewinginstances.html)
* [NetApp ONTAP Select-Instanzen löschen](/docs/services/vmwaresolutions/netapp/np_deletinginstance.html)
* [NetApp ONTAP Documentation Center](http://docs.netapp.com/ontap-9/index.jsp?topic=%2Fcom.netapp.doc.exp-clus-peer%2Fhome.html)
* [Dedizierten Speicher für NetApp ONTAP Select-Bereitstellungen zuordnen](https://developer.ibm.com/recipes/tutorials/steps-to-attach-dedicated-storage-to-existing-ic4v-deployments-on-ibm-cloud/)
