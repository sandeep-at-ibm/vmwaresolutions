---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-14"

---

# VMware Federal-Instanzen bestellen

Um eine flexible und anpassbare virtualisierte VMware-Plattform bereitzustellen, die Ihren Workloadbedarf optimal erfüllt, bestellen Sie eine VMware Federal-Instanz, die es Ihnen ermöglicht, die offene Managementverbindung zu trennen und Ihre bereitgestellte Instanz zu schützen.

**Hinweis:** VMware Federal on {{site.data.keyword.cloud}} wird gegenwärtig nur von vCenter Server-Instanzen unterstützt.

## Voraussetzungen

Stellen Sie sicher, dass Sie die folgenden Tasks ausgeführt haben:
* Sie haben die Berechtigungsnachweise für die {{site.data.keyword.cloud_notm}}-Infrastruktur auf der Seite **Einstellungen** konfiguriert. Weitere Informationen finden Sie unter [Benutzerkonten und Einstellungen verwalten](../vmonic/useraccount.html).
* Sie haben die Informationen in [Voraussetzungen und Planung für VMware Federal-Instanzen](vc_fed_planning.html) gelesen.
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

Sie müssen die folgenden Systemeinstellungen angeben, wenn Sie eine VMware Federal-Instanz bestellen.

### Instanzname

Der Instanzname muss die folgenden Anforderungen erfüllen:
* Es sind nur alphanumerische Zeichen und Bindestriche (-) zulässig.
* Der Instanzname muss mit einem alphanumerischen Zeichen beginnen und enden.
* Die maximale Länge des Instanznamens beträgt 10 Zeichen.
* Der Instanzname muss innerhalb Ihres Kontos eindeutig sein.

### Primär oder sekundär

Bestellen Sie eine neue primäre Instanz. Die Bereitstellung einer sekundären Instanz für die Hochverfügbarkeit wird gegenwärtig nicht unterstützt.

## Lizenzierungseinstellungen

Von IBM bereitgestellte VMware-Lizenzen für folgende Ressourcen:

* VMware vCenter Server 6.5
* VMware vSphere Enterprise Plus 6.5u1
* VMware NSX Service Providers Edition (Base, Advanced oder Enterprise) 6.4
* (Für vSAN-Cluster) VMware vSAN Advanced oder Enterprise 6.6

**Achtung:**

* Die mindestens erforderlichen Lizenzeditionen sind in der Benutzerschnittstelle angegeben. Falls unterschiedliche Komponenteneditionen unterstützt werden, können Sie die gewünschte Edition auswählen. Es liegt in Ihrer Verantwortung, zu gewährleisten, dass der bereitgestellte Lizenzschlüssel für jede ausgewählte VMware-Komponente korrekt ist.
* Für vSphere wird zum Zeitpunkt der Bestellung eine Lizenzgebühr berechnet, anschließend wird die Lizenzgebühr dann aber Ihrem Konto gutgeschrieben.

## Einstellungen für Bare Metal Server

Die Bare-Metal-Einstellungen sind von Ihrer angepassten Konfiguration abhängig. Die Option zum Auswählen einer vordefinierten Konfiguration wird gegenwärtig nicht unterstützt.

### Standort des Rechenzentrums

Wählen Sie das {{site.data.keyword.CloudDataCent_notm}} aus, das als Host für die Instanz verwendet werden soll.

### Angepasst

Geben Sie das CPU-Modell und den RAM (Arbeitsspeicher) für den Bare Metal Server an.

Tabelle 2. Optionen für angepasste {{site.data.keyword.baremetal_short}}-Instanzen

| CPU-Modelloptionen        | RAM-Optionen       |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4 / 16 Kerne insgesamt, 2,1 GHz | 64 GB, 128 GB, 256 GB, 512 GB |
| Dual Intel Xeon E5-2650 v4 / 24 Kerne insgesamt, 2,2 GHz | 64 GB, 128 GB, 256 GB, 512 GB |
| Dual Intel Xeon E5-2690 v4 / 28 Kerne insgesamt, 2,6 GHz | 64 GB, 128 GB, 256 GB, 512 GB |
| Dual Intel Xeon Silver 4110-Prozessor / 16 Kerne insgesamt, 2,1 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon Gold 5120-Prozessor / 28 Kerne insgesamt, 2,2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon Gold 6140-Prozessor / 36 Kerne insgesamt, 2,3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |

### Bare Metal Server-Anzahl

Sie können die Anzahl der ESXi-Server im Bereich von 2 bis 20 konfigurieren.

Alle ESXi-Server nutzen dieselbe Konfiguration gemeinsam. Nach der Bereitstellung können Sie vier weitere Cluster hinzufügen. Für die vSAN-Speichereinstellungen werden für den ersten Cluster und die Cluster nach der Bereitstellung 4 ESXi-Server benötigt. Weitere Informationen zum Minimum von ESXi-Servern finden Sie im Abschnitt [Ist eine Serverinstanz mit zwei Knoten hoch verfügbar?](../vmonic/faq.html#is-a-two-node-vcenter-server-instance-highly-available-)

## Speichereinstellungen

Die Speichereinstellungen sind von der Auswahl der Bare Metal Server-Konfiguration und des Speichertyps abhängig.

### vSAN-Speicher

Geben Sie für vSAN die folgenden Speicheroptionen an:

* **Plattentyp und -größe für vSAN-Kapazitätsplatten**: Wählen Sie die Kapazität aus, die Ihrem Bedarf an gemeinsam genutzten Speicher entspricht.
* **Anzahl der vSAN-Kapazitätsplatten**: Wählen Sie die Anzahl der Platten für den gemeinsam genutzten vSAN-Speicher aus, die Sie hinzufügen wollen. Die Plattenanzahl muss 2, 4, 6 oder 8 sein.
* Wählen Sie die VMware vSAN 6.6-Lizenzedition (Advanced oder Enterprise) aus.

### NFS-Speicher

Wenn Sie **NFS-Speicher** auswählen, können Sie gemeinsam genutzten Speicher auf Dateiebene für Ihre Instanz hinzufügen, wobei für alle Dateifreigaben dieselben Einstellungen verwendet werden. Alternativ können Sie für die einzelnen Dateifreigaben jeweils unterschiedliche Konfigurationseinstellungen angeben. Geben Sie die folgenden NFS-Optionen an:

**Hinweis:** Die Anzahl der Dateifreigaben muss zwischen 1 und 32 liegen.

* **Dateifreigaben einzeln konfigurieren**: Wählen Sie diese Option aus, um für jede einzelne Dateifreigabe unterschiedliche Konfigurationseinstellungen anzugeben.
* **Anzahl der Dateifreigaben**: Geben Sie bei Verwendung derselben Konfigurationseinstellung für jede Dateifreigabe die Anzahl der Dateifreigaben für den gemeinsam genutzten NFS-Speicher an, die Sie hinzufügen möchten.
* **Größe**: Wählen Sie die Kapazität aus, die Ihrem Bedarf an gemeinsam genutzten Speicher entspricht.
* **Leistung**: Wählen Sie basierend auf Ihren Workloadanforderungen die E/A-Operationen pro Sekunde (Input/output Operations Per Second, IOPS) pro GB aus.
* **NFS hinzufügen**: Wählen Sie diese Option aus, um einzelne Dateifreigaben hinzuzufügen, für die unterschiedliche Konfigurationseinstellungen verwendet werden.

Tabelle 3. Optionen für die NFS-Leistungsstufe

| Option        | Details       |
  |:------------- |:------------- |
  | 2 IOPS/GB | Diese Option ist für die meisten allgemeinen Workloads geeignet. Anwendungsbeispiele sind das Hosting von kompakten Datenbanken, die Sicherung von Webanwendungen oder Plattenimages von virtuellen Maschinen für einen Hypervisor. |
  | 4 IOPS/GB | Diese Option ist für Workloads mit höherer Intensität geeignet, die zu einem bestimmten Zeitpunkt einen hohen Prozentsatz an aktiven Daten aufweisen. Anwendungsbeispiele sind transaktionsorientierte Datenbanken. |
  | 10 IOPS/GB | Diese Option ist für die aufwändigsten Workloadtypen wie beispielsweise die Analyse gedacht. Anwendungsbeispiele sind Hochtransaktionsdatenbanken und andere leistungskritische Datenbanken. Diese Leistungsstufe ist auf eine maximale Kapazität von 4 TB pro Dateifreigabe begrenzt. |

## Netzschnittstelleneinstellungen

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

**Hinweis:** Die maximale Länge des vollständig qualifizierten Domänennamens (FQDN = Fully Qualified Domain Name) für Hosts und VMs beträgt 50 Zeichen. Domänennamen müssen diese maximale Länge zulassen.

### DNS-Konfiguration

Wählen Sie die Konfiguration für DNS (Domain Name System) für Ihre Instanz aus:

* **Einzelne öffentliche Windows-VSI für Active Directory/DNS**: Eine einzelne virtuelle Serverinstanz (VSI) von Microsoft Windows Server für Microsoft Active Directory (AD), die als DNS für die Instanz dient, auf der die Hosts und virtuellen Maschinen registriert sind, wird bereitgestellt und kann zur Suche verwendet werden.
* **Zwei hoch verfügbare dedizierte Windows-Server-VMs auf dem Management-Cluster**: Für V2.3 und zukünftige Releases werden zwei virtuelle Microsoft Windows-Maschinen bereitgestellt, die Datenschutz und Leistungsfähigkeit verbessern.

**Wichtig:** Sie müssen zwei Lizenzen für Microsoft Windows Server 2012 R2 bereitstellen, wenn Sie Ihre Instanz für die Verwendung der beiden virtuellen Microsoft Windows-Maschinen konfigurieren. Verwenden Sie die Lizenz für Microsoft Windows Server 2012 R2 Standard Edition und/oder die Lizenz für Microsoft Windows Server 2012 R2 Datacenter Edition.

Derzeit kann jede Lizenz nur einem einzigen physischen Server zugeordnet werden und deckt bis zu zwei physische Prozessoren ab. Eine Standard Edition-Lizenz ist in der Lage, zwei virtualisierte virtuelle Microsoft Windows-Maschinen pro 2-Prozessor-Server auszuführen. Die beiden Lizenzen sind deshalb erforderlich, weil zwei virtuelle Microsoft Windows-Maschinen in zwei unterschiedlichen Hosts bereitgestellt werden.

Sie haben 30 Tage Zeit, um die virtuellen Maschinen zu aktivieren.

Weitere Informationen zum Bestellen der Windows-Lizenzierung finden Sie auf der Seite [Windows Server 2012 R2 documentation](https://www.microsoft.com/en-us/licensing/product-licensing/windows-server-2012-r2.aspx#tab=2).

## Bestellübersicht

Auf Basis der für die Instanz ausgewählten Konfiguration werden die geschätzten Kosten sofort generiert und im rechten Fenster im Abschnitt **Bestellübersicht** angezeigt. Klicken Sie unten im rechten Fenster auf **Preisdetails**, um ein PDF-Dokument zu generieren, das die Kostenschätzungsdetails enthält.

## Vorgehensweise

1. Klicken Sie im {{site.data.keyword.cloud_notm}}-Katalog im linken Navigationsfenster auf **VMware** und anschließend im Abschnitt **Virtuelle Rechenzentren** auf **vCenter Server**.
2. Klicken Sie auf der Seite **VMware vCenter Server on IBM Cloud** auf die Karte **vCenter Server** und dann auf **Erstellen**.
3. Geben Sie auf der Seite **vCenter Server** den Instanznamen ein.
4. Klicken Sie auf **Primäre Instanz**, um eine einzelne Instanz in der Umgebung bereitzustellen.
5. Geben Sie die VMware NSX-Lizenzedition an.
6. Führen Sie die Bare Metal Server-Konfiguration durch:
  1. Wählen Sie das {{site.data.keyword.CloudDataCent_notm}} als Host für die Instanz aus.
  2. Wählen Sie das CPU-Modell **Angepasst** und die Menge des **RAM** aus.
7. Führen Sie die Speicherkonfiguration durch.
  * Wenn Sie **vSAN-Speicher** ausgewählt haben, geben Sie **Plattentyp und -größe für vSAN-Kapazitätsplatten** und **Anzahl der vSAN-Kapazitätsplatten** sowie die Methode an, mit der die **vSAN-Lizenz** bereitgestellt werden soll.
  * Wenn Sie **NFS-Speicher** ausgewählt haben und für alle Dateifreigaben dieselben Einstellungen hinzufügen und konfigurieren wollen, geben Sie die **Anzahl der Dateifreigaben**, **Größe** und **Leistung** an.
  * Wenn Sie **NFS-Speicher** ausgewählt haben und Dateifreigaben einzeln hinzufügen und bearbeiten möchten, wählen Sie **Dateifreigaben einzeln konfigurieren** aus, klicken Sie neben der Bezeichnung **NFS hinzufügen** auf das Symbol **+** und wählen Sie dann für jede Dateifreigabe jeweils **Größe** und **Leistung** aus. Sie müssen mindestens eine Dateifreigabe auswählen.
8. Führen Sie die Netzschnittstellenkonfiguration durch.
   1. Geben Sie das Hostnamenspräfix, die Unterdomänenbezeichnung und den Rootdomänennamen ein.
   2. Wählen Sie die DNS-Konfiguration aus.
9. Überprüfen Sie im Fenster **Bestellübersicht** die Instanzkonfiguration, bevor Sie die Bestellung aufgeben.
   1. Überprüfen Sie die Einstellungen für die Instanz.
   2. Klicken Sie auf den Link bzw. die Links für die Bedingungen, die für Ihre Bestellung gelten, und vergewissern Sie sich, dass Sie mit diesen Bedingungen einverstanden sind, bevor Sie die Instanz bestellen.
   3. Prüfen Sie die geschätzten Kosten für die Instanz, indem Sie unter **Kosten berechnen** auf den Link für die Kosten klicken. Ihre Bestellübersicht können Sie speichern oder drucken, indem Sie rechts oben im PDF-Fenster auf das Symbol **Drucken** bzw. **Herunterladen** klicken.
   4. Klicken Sie auf **Bereitstellung**.

## Ergebnisse

Die Bereitstellung der Instanz wird automatisch gestartet. Sie erhalten eine Bestätigung, dass die Bestellung bearbeitet wird, und Sie können den Status der Bereitstellung prüfen, indem Sie die Instanzdetails anzeigen.

Nachdem die Instanz erfolgreich bereitgestellt wurde, sind die Komponenten, die unter [Technische Spezifikationen für VMware Federal on {{site.data.keyword.cloud_notm}}-Instanzen](vc_fed_overview.html#technical-specifications-for-vmware-federal-on-ibm-cloud-instances) beschrieben sind, auf Ihrer virtuellen VMware-Plattform installiert. Die von Ihnen bestellten ESXi-Server werden standardmäßig als **cluster1** gruppiert.

Sobald die Instanz einsatzbereit ist, ändert sich der Status der Instanz in **Bereit** und Sie empfangen per E-Mail eine Benachrichtigung.

## Nächste Schritte

Sie können nun die bestellte VMware Federal-Instanz anzeigen, verwalten und schützen.

**Wichtig:** Sie dürfen die {{site.data.keyword.vmwaresolutions_short}}-Komponenten, die in Ihrem {{site.data.keyword.cloud_notm}}-Konto erstellt werden, nur über die {{site.data.keyword.vmwaresolutions_short}}-Konsole und nicht im {{site.data.keyword.slportal}} oder über ein anderes Verfahren außerhalb der Konsole verwalten.
Wenn Sie diese Komponenten außerhalb der {{site.data.keyword.vmwaresolutions_short}}-Konsole ändern, werden die Änderungen nicht mit der Konsole synchronisiert.

**VORSICHT:** Wenn Sie {{site.data.keyword.vmwaresolutions_short}}-Komponenten (die in Ihrem {{site.data.keyword.cloud_notm}}-Konto installiert wurden, als Sie die Instanz bestellt haben) außerhalb der {{site.data.keyword.vmwaresolutions_short}}-Konsole verwalten, kann dies zur Instabilität Ihrer Umgebung führen. Zu diesen Managementaktivitäten gehören:
*  Komponenten hinzufügen, ändern, zurückgeben oder entfernen
*  Instanzkapazität durch das Entfernen von ESXi-Servern erweitern oder verringern
*  Komponenten ausschalten

   Ausgenommen von diesen Aktivitäten ist unter anderem das Management der Dateifreigaben für gemeinsam genutzten Speicher im {{site.data.keyword.slportal}}. Hierzu gehört das Bestellen, Löschen (mit möglicher Auswirkung auf angehängte Datenspeicher), Berechtigen und Anhängen von Dateifreigaben für gemeinsam genutzten Speicher.

### Zugehörige Links

* [Für ein {{site.data.keyword.cloud_notm}}-Konto registrieren](../vmonic/signing_softlayer_account.html)
* [VMware Federal-Instanzen anzeigen](vc_fed_viewinginstance.html)
* [Kapazität für VMware Federal-Instanzen erweitern und verringern](vc_fed_addingremovingservers.html)
* [Cluster für VMware Federal-Instanzen hinzufügen, anzeigen und löschen](fed_addviewdeleteclusters.html)
* [VMware Federal-Instanzen schützen](vc_fed_securinginstance.html)
* [VMware Federal-Instanzen löschen](vc_fed_deletinginstance.html)
* [Kontaktaufnahme mit dem IBM Support](../vmonic/trbl_support.html)
