---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-29"

keywords: NetApp order instance, order NetApp ONTAP, order NetApp

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# NetApp ONTAP Select-Instanzen bestellen
{: #np_orderinginstances}

Durch die Bestellung einer NetApp ONTAP Select-Instanz können Sie eine virtualisierte VMware-Plattform mit einer dedizierten und hoch verfügbaren Appliance für softwaredefinierten Speicher bereitstellen.

## Voraussetzungen
{: #np_orderinginstances-req}

Stellen Sie sicher, dass Sie die folgenden Tasks ausgeführt haben:
*  Sie haben die Berechtigungsnachweise für die {{site.data.keyword.cloud}}-Infrastruktur auf der Seite **Einstellungen** konfiguriert. Weitere Informationen finden Sie unter [Benutzerkonten und Einstellungen verwalten](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount).
*  Sie haben sich mit den Voraussetzungen und Hinweisen im Abschnitt [Voraussetzungen und Planung für NetApp ONTAP Select-Instanzen](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_planning) vertraut gemacht.

Nehmen Sie keine Änderungen an Werten vor, die während der Bestellung oder Bereitstellung der Instanz festgelegt werden. Dies kann dazu führen, dass Ihre Instanz unbrauchbar wird. Beispielsweise, wenn der öffentliche Netzbetrieb beendet wird, Server sowie virtuelle Serverinstanzen (VSIs) mitten in einer Bereitstellung hinter eine Vyatta-Einheit versetzt werden oder wenn die Virtual Server-Instanz für IBM CloudBuilder gestoppt oder gelöscht wird.
{:important}

## Systemeinstellungen
{: #np_orderinginstances-sys-settings}

Wenn Sie eine NetApp ONTAP Select-Instanz bestellen, müssen Sie die folgenden Basiseinstellungen angeben.

### Instanzname
{: #np_orderinginstances-instance-name}

Der Instanzname muss die folgenden Anforderungen erfüllen:
* Es sind nur Kleinbuchstaben, Ziffern und Gedankenstriche (-) zulässig.
* Der Instanzname muss mit einem Kleinbuchstaben beginnen.
* Der Instanzname muss entweder auf einen Kleinbuchstaben oder auf eine Ziffer enden.
* Die maximale Länge des Instanznamens beträgt 10 Zeichen.
* Der Instanzname muss innerhalb Ihres Kontos eindeutig sein.

## Netzschnittstelleneinstellungen
{: #np_orderinginstances-network-interface-settings}

Sie müssen die folgenden Netzschnittstelleneinstellungen angeben, wenn Sie eine NetApp ONTAP Select-Instanz bestellen.

### Hostnamenspräfix
{: #np_orderinginstances-host-name-prefix}

Das Hostnamenspräfix muss die folgenden Anforderungen erfüllen:
* Es sind nur Kleinbuchstaben, Ziffern und Gedankenstriche (-) zulässig.
* Das Hostnamen-Präfix muss mit einem Kleinbuchstaben beginnen.
* Das Hostnamen-Präfix muss entweder auf einen Kleinbuchstaben oder auf eine Ziffer enden.
* Die maximale Länge des Hostnamenspräfix beträgt 10 Zeichen.

### Unterdomänenbezeichnung
{: #np_orderinginstances-subdomain-label}

Die Unterdomänenbezeichnung muss die folgenden Anforderungen erfüllen:
* Es sind nur Kleinbuchstaben, Ziffern und Gedankenstriche (-) zulässig.
* Die Unterdomänenbezeichnung muss mit einem Kleinbuchstaben beginnen.
* Die Unterdomänenbezeichnung muss entweder auf einen Kleinbuchstaben oder auf eine Ziffer enden.
* Die maximale Länge der Unterdomänenbezeichnung beträgt 10 Zeichen.

### Domänenname
{: #np_orderinginstances-domain-name}

Der Rootdomänenname muss die folgenden Anforderungen erfüllen:
* Der Domänenname muss aus zwei oder mehr Zeichenfolgen bestehen, die jeweils durch einen Punkt (.) voneinander getrennt sind.
* Die erste Zeichenfolge muss mit einem Kleinbuchstaben beginnen.
* Die erste Zeichenfolge muss entweder auf einen Kleinbuchstaben oder auf eine Ziffer enden.
* Alle Zeichenfolgen mit Ausnahme der letzten dürfen nur Kleinbuchstaben, Ziffern und Gedankenstriche (-) enthalten.
* Die letzte Zeichenfolge darf nur Kleinbuchstaben enthalten.
* Die Länge der letzten Zeichenfolge muss zwischen 2 und 24 Zeichen betragen.

Die maximale Länge des vollständig qualifizierten Domänennamens für Hosts und VMs beträgt 50 Zeichen. Domänennamen müssen diese maximale Länge zulassen.
{:note}

## Lizenzierungseinstellungen
{: #np_orderinginstances-licensing-settings}

Sie müssen vier NetApp-Lizenzdateien hochladen, jeweils eine für jede der vier {{site.data.keyword.baremetal_short}}-Instanzen. Wenden Sie sich an Ihr NetApp-Vertriebsteam, um die entsprechende Lizenzierung für Ihre Hochleistungs- oder Hochkapazitätsbereitstellung zu erhalten.

## Einstellungen für Bare Metal Server
{: #np_orderinginstances-bare-metal-settings}

### Standort des Rechenzentrums
{: #np_orderinginstances-dc-location}

Sie müssen das {{site.data.keyword.CloudDataCent_notm}} (Rechenzentrum) auswählen, das als Host für die Instanz verwendet werden soll.

### Bare Metal Server-Konfiguration
{: #np_orderinginstances-bare-metal-config}

Wählen Sie eine Ihren Anforderungen entsprechende Bare Metal Server-Konfiguration aus:
* **Hohe Leistung (M = Mittel)** - Premium-Lizenz / Dual Intel Xeon E5-2650 V4 (24 Kerne insgesamt, 2,2 GHz) / 128 GB RAM / Kapazität von 22 1,9-TB-SSD-Laufwerken pro Knoten / Effektive Kapazität eines Clusters mit 4 Knoten - 59 TB
* **Hohe Leistung (groß)** - Premium-Lizenz / Dual Intel Xeon E5-2650 V4 (24 Kerne insgesamt, 2,2 GHz) / 128 GB RAM / Kapazität von 22 3,8-TB-SSD-Laufwerken pro Knoten / Effektive Kapazität eines Clusters mit 4 Knoten - 118 TB
* **Hohe Kapazität** - Standard-Lizenz / Dual Intel Xeon E5-2650 V4 (24 Kerne insgesamt, 2,2 GHz) / 64 GB RAM / Kapazität von 34 4-TB-SATA-Laufwerken pro Knoten / Effektive Kapazität eines Clusters mit 4 Knoten - 190 TB

3,8-TB-Solid-State-Platten (SSD) werden unterstützt, wenn sie in einem {{site.data.keyword.CloudDataCent_notm}} allgemein verfügbar gemacht werden.
{:note}

### Bare Metal Server-Anzahl
{: #np_orderinginstances-bare-metal-number}

Die Anzahl der ESXi-Server einer NetApp ONTAP Select-Instanz ist standardmäßig vier. Dieser Wert kann nicht geändert werden. Alle ESXi-Server verfügen über dieselbe Konfiguration.

## Bestellübersicht
{: #np_orderinginstances-order-summary}

Auf Basis der ausgewählten Konfiguration werden die geschätzten Kosten sofort generiert und im rechten Fenster **Bestellübersicht** angezeigt.  Klicken Sie auf **Preisdetails**, um ein PDF-Dokument mit der Kostenübersicht für die {{site.data.keyword.vmwaresolutions_short}}-Ressourcen zu generieren.

Sie können die bereitgestellten Ressourcen auch durch Klicken auf **Zur Schätzung hinzufügen** zum {{site.data.keyword.cloud_notm}}-Schätztool hinzufügen. Dies ist nützlich, wenn Sie die Kosten für die ausgewählten {{site.data.keyword.vmwaresolutions_short}}-Ressourcen zusammen mit anderen {{site.data.keyword.cloud_notm}}-Ressourcen schätzen möchten, die Sie für den Kauf in Betracht ziehen könnten.

## Vorgehensweise zum Bestellen von NetApp ONTAP Select-Instanzen
{: #ordering-netapp-ontap-select-instances}

1. Klicken Sie im {{site.data.keyword.cloud_notm}}-Katalog im linken Navigationsfenster auf das Symbol **VMware** und anschließend im Abschnitt **Virtuelle VMware-Rechenzentren** auf die Karte **NetApp ONTAP Select**.
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

## Ergebnisse nach Bestellen der NetApp ONTAP-Instanzen
{: #np_orderinginstances-results}

* Die Bereitstellung der Instanz beginnt automatisch und Sie erhalten eine Bestätigung, dass die Bestellung bearbeitet wird. Sie können den Bereitstellungsstatus, einschließlich aller Probleme, die eventuell Ihre Aufmerksamkeit erfordern, durch Anzeigen des Abschnitts **Bereitstellungsverlauf** der Instanzdetails überprüfen.
* Nachdem die Instanz erfolgreich bereitgestellt wurde, sind die Komponenten, die unter [Technische Spezifikationen für NetApp ONTAP Select-Instanzen](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_netappoverview#specs) beschrieben sind, auf Ihrer virtuellen VMware-Plattform installiert.
* Sobald die Instanz einsatzbereit ist, ändert sich der Status der Instanz in **Bereit** und Sie empfangen per E-Mail eine Benachrichtigung.

## Nächste Schritte
{: #np_orderinginstances-next}

Sie können Ihre bestellte NetApp ONTAP Select-Instanz jetzt anzeigen und verwalten.

Sie dürfen die {{site.data.keyword.vmwaresolutions_short}}-Komponenten, die in Ihrem {{site.data.keyword.cloud_notm}}-Konto erstellt werden, nur über die {{site.data.keyword.vmwaresolutions_short}}-Konsole und nicht im {{site.data.keyword.slportal}} oder über ein anderes Verfahren außerhalb der Konsole verwalten. Wenn Sie diese Komponenten außerhalb der {{site.data.keyword.vmwaresolutions_short}}-Konsole ändern, werden die Änderungen nicht mit der Konsole synchronisiert.
{:important}

**VORSICHT:** Wenn Sie {{site.data.keyword.vmwaresolutions_short}}-Komponenten (die in Ihrem {{site.data.keyword.cloud_notm}}-Konto installiert wurden, als Sie die Instanz bestellt haben) außerhalb der {{site.data.keyword.vmwaresolutions_short}}-Konsole verwalten, kann dies zur Instabilität Ihrer Umgebung führen. Zu diesen Managementaktivitäten gehören:
*  Komponenten hinzufügen, ändern, zurückgeben oder entfernen
*  Komponenten ausschalten

   Ausgenommen von diesen Aktivitäten ist unter anderem das Management der gemeinsam genutzten Dateiressourcen für gemeinsam genutzten Speicher im {{site.data.keyword.slportal}}. Hierzu gehört das Bestellen, Löschen (mit möglicher Auswirkung auf angehängte Datenspeicher), Berechtigen und Anhängen von gemeinsam genutzten Dateiressourcen für gemeinsam genutzten Speicher.

## Zugehörige Links
{: #np_orderinginstances-related}

* [NetApp ONTAP Select-Instanzen anzeigen](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_viewinginstances)
* [NetApp ONTAP Select-Instanzen löschen](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_deletinginstance)
* [NetApp ONTAP Documentation Center](http://docs.netapp.com/ontap-9/index.jsp?topic=%2Fcom.netapp.doc.exp-clus-peer%2Fhome.html){: external}
* [Dedizierten Speicher für NetApp ONTAP Select-Bereitstellungen zuordnen](https://developer.ibm.com/recipes/tutorials/steps-to-attach-dedicated-storage-to-existing-ic4v-deployments-on-ibm-cloud/){: external}
