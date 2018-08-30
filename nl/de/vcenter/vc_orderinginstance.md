---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-15"

---

# vCenter Server-Instanzen bestellen

Um eine flexible und anpassbare virtualisierte VMware-Plattform bereitzustellen, die Ihren Workloadbedarf optimal erfüllt, bestellen Sie eine VMware vCenter Server-Instanz. Während der Erstbestellung können Sie auch Services hinzufügen, z. B. [Zerto on {{site.data.keyword.cloud}}](../services/addingzertodr.html) für die Disaster-Recovery.

## Voraussetzungen

Stellen Sie sicher, dass Sie die folgenden Tasks ausgeführt haben:
* Sie haben die Berechtigungsnachweise für die {{site.data.keyword.cloud_notm}}-Infrastruktur auf der Seite **Einstellungen** konfiguriert. Weitere Informationen finden Sie unter [Benutzerkonten und Einstellungen verwalten](../vmonic/useraccount.html).
* Sie haben die Informationen in [Voraussetzungen und Planung für vCenter Server-Instanzen](vc_planning.html) gelesen.
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

Sie müssen die folgenden Systemeinstellungen angeben, wenn Sie eine vCenter Server-Instanz bestellen.

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
* VMware vSphere Enterprise Plus 6.5u1
* VMware vCenter Server 6.5
* VMware NSX Service Providers Edition (Base, Advanced oder Enterprise) 6.4

Für Benutzer der Kategorie "Business Partner" sind die vCenter Server-Lizenz (Standard Edition), die vSphere-Lizenz (Enterprise Plus Edition) und die NSX-Lizenz enthalten und werden in Ihrem Namen erworben. Für die NSX-Lizenz muss allerdings die Edition angegeben werden.

Für Nicht-Business-Partner-Benutzer können die von IBM bereitgestellten VMware-Lizenzen für diese Komponenten benutzt werden. Wählen Sie hierzu **In Kauf einbeziehen** aus. Alternativ hierzu können Sie auch eine eigene Lizenz (Bring Your Own License; BYOL) verwenden, indem Sie **Lizenz selbst bereitstellen** auswählen und die eigenen Lizenzschlüssel angeben.

**Achtung**:
* Es ist eine Lizenz mit mindestens 8 CPUs erforderlich, die für 4 Server mit 2 CPUs pro Server verwendet wird. Die Lizenzauswahl für jede VMware-Komponente gilt für die Basisinstanz und für alle ESXi-Server, die Sie später zur Instanz hinzufügen. Sie müssen daher sicherstellen, dass Ihre Lizenz eine zukünftige Kapazitätserweiterung in Ihrer Infrastruktur unterstützt.
* Die mindestens erforderlichen Lizenzeditionen sind in der Benutzerschnittstelle angegeben. Falls unterschiedliche Komponenteneditionen unterstützt werden, können Sie die gewünschte Edition auswählen. Es liegt in Ihrer Verantwortung, zu gewährleisten, dass der bereitgestellte Lizenzschlüssel für jede ausgewählte VMware-Komponente korrekt ist.
* Für vSphere wird zum Zeitpunkt der Bestellung eine Lizenzgebühr berechnet, anschließend wird die Lizenzgebühr dann aber Ihrem Konto gutgeschrieben.
* Sie können alle Lizenzen ändern, die Sie mit VMware vSphere Web Client bereitgestellt haben, nachdem die Bereitstellung der Instanz abgeschlossen ist.
* Die Unterstützung für die VMware-Komponenten, für die Sie Lizenzen bereitstellen, wird von VMware und nicht vom IBM Support zur Verfügung gestellt.

## Einstellungen für Bare Metal Server

Die Bare Metal-Einstellungen sind von Ihrer Rechenzentrumsauswahl und davon abhängig, ob Sie eine vorkonfigurierte oder angepasste Konfiguration auswählen.

### Standort des Rechenzentrums

Wählen Sie das {{site.data.keyword.CloudDataCent_notm}} aus, das als Host für die Instanz verwendet werden soll.

### Vorkonfiguriert

Wenn Sie **Vorkonfiguriert** auswählen, dann können Sie die CPU- oder RAM-Einstellungen nicht ändern.

Wählen Sie gemäß Ihren Anforderungen eine Bare Metal Server-Konfiguration aus:
  * S (Klein): Dual Intel Xeon E5-2620 v4 / 16 Kerne insgesamt, 2,1 GHz / 128 GB RAM / 2 Laufwerke
  * M (Mittel): Dual Intel Xeon E5-2650 v4 / 24 Kerne insgesamt, 2,2 GHz / 256 GB RAM / 2 Laufwerke
  * L (Groß): Dual Intel Xeon E5-2690 v4 / 28 Kerne insgesamt, 2,6 GHz / 512 GB RAM / 2 Laufwerke

### Angepasst

Wenn Sie **Angepasst** auswählen, dann können Sie die Kombination aus CPU und RAM entsprechend Ihren Anforderungen auswählen.

Wählen Sie das CPU-Modell und den RAM (Arbeitsspeicher) für den Bare Metal Server aus.

Tabelle 2. Optionen für angepasste {{site.data.keyword.baremetal_short}}-Instanzen

| CPU-Modelloptionen        | RAM-Optionen       |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4 / 16 Kerne insgesamt, 2,1 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2650 v4 / 24 Kerne insgesamt, 2,2 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2690 v4 / 28 Kerne insgesamt, 2,6 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon Silver 4110-Prozessor / 16 Kerne insgesamt, 2,1 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon Gold 5120-Prozessor / 28 Kerne insgesamt, 2,2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon Gold 6140-Prozessor / 36 Kerne insgesamt, 2,3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |

### Bare Metal Server-Anzahl

Für den ersten Cluster in der Instanz können Sie die Anzahl der ESXi-Server wie folgt konfigurieren:
* Falls Sie **Vorkonfiguriert** ausgewählt haben, können Sie die Anzahl der ESXi-Server im Bereich von 2 bis 10 konfigurieren.
* Falls Sie **Angepasst** ausgewählt haben, können Sie die Anzahl der ESXi-Server im Bereich von 2 bis 20 konfigurieren.

Alle ESXi-Server nutzen dieselbe Konfiguration gemeinsam. Nach der Erstbereitstellung können Sie vier weitere Cluster hinzufügen. Wenn Sie die Konfiguration **Angepasst** für vSAN ausgewählt haben, werden sowohl für den ersten Cluster als auch für die Cluster nach der Bereitstellung 4 ESXi-Server benötigt. Weitere Informationen zum Minimum von ESXi-Servern finden Sie im Abschnitt [Ist eine Serverinstanz mit zwei Knoten hoch verfügbar?](../vmonic/faq.html#is-a-two-node-vcenter-server-instance-highly-available-)

## Speichereinstellungen

Die Speichereinstellungen sind von der Auswahl der Bare Metal Server-Konfiguration und des Speichertyps abhängig.

### vSAN-Speicher

vSAN ist nur verfügbar, wenn Sie die Bare-Metal-Konfiguration **Angepasst** auswählen. Geben Sie die folgenden vSAN-Optionen an:

* **Anzahl der vSAN-Kapazitätsplatten**: Geben Sie die Anzahl der Platten für den gemeinsam genutzten vSAN-Speicher an, die Sie hinzufügen wollen. Die Plattenanzahl muss 2, 4, 6 oder 8 sein.
* **Plattentyp und -größe für vSAN-Kapazitätsplatten**: Wählen Sie die Kapazität aus, die Ihrem Bedarf an gemeinsam genutzten Speicher entspricht.
* **vSAN-Lizenz**: Verwenden Sie die von IBM bereitgestellte VMware-Lizenz für die vSAN-Komponente, indem Sie **In Kauf einbeziehen** auswählen, oder verwenden Sie eine eigene Lizenz (Bring Your Own License, BYOL), indem Sie **Lizenz selbst bereitstellen** auswählen und Ihren eigenen Lizenzschlüssel eingeben.

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

Sie müssen die folgenden Netzschnittstelleneinstellungen angeben, wenn Sie eine vCenter Server-Instanz bestellen.

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
* **Primäres privates Teilnetz** - Wird physischen Hosts für den Managementdatenverkehr zugewiesen.

**Wichtig:**
* Stellen Sie sicher, dass die Firewallkonfiguration bei den ausgewählten VLANs den Managementdatenverkehr nicht blockiert.
* Stellen Sie sicher, dass sich alle von Ihnen ausgewählten VLANs in demselben Pod befinden, da ESXi-Server nicht in VLANs mit heterogenen Pods bereitgestellt werden können.

### DNS-Konfiguration

Wählen Sie die Konfiguration für DNS (Domain Name System) für Ihre Instanz aus:

* **Einzelne öffentliche Windows-VSI für Active Directory/DNS**: Eine einzelne Serverinstanz (VSI) von Microsoft Windows Server für Microsoft Active Directory (AD), die als DNS für die Instanz dient, auf der die Hosts und VMs registriert sind, wird bereitgestellt und kann zur Suche verwendet werden. Diese Option wurde standardmäßig für Instanzen von V1.9 und höher bereitgestellt.
* **Zwei hoch verfügbare dedizierte Windows-Server-VMs auf dem Management-Cluster**: Es werden zwei Microsoft Windows-VMs bereitgestellt, die den Datenschutz und die Leistungsfähigkeit verbessern.

**Wichtig:** Sie müssen zwei Lizenzen für Microsoft Windows Server 2012 R2 bereitstellen, wenn Sie Ihre Instanz für die Verwendung der beiden Microsoft Windows-VMs konfigurieren. Verwenden Sie die Lizenz für Microsoft Windows Server 2012 R2 Standard Edition und/oder die Lizenz für Microsoft Windows Server 2012 R2 Datacenter Edition.

Jede Lizenz kann nur einem einzigen physischen Server zugeordnet werden und deckt bis zu zwei physische Prozessoren ab. Eine Standard Edition-Lizenz ist in der Lage, zwei virtualisierte Microsoft Windows-VMs pro 2-Prozessor-Server auszuführen. Daher sind zwei Lizenzen erforderlich, weil zwei Microsoft Windows-VMs in zwei unterschiedlichen Hosts bereitgestellt werden.

Sie haben 30 Tage Zeit, um die VMs zu aktivieren.

Weitere Informationen zur Windows-Lizenzierung finden Sie auf der Seite [Windows Server 2012 R2 documentation](https://www.microsoft.com/en-us/licensing/product-licensing/windows-server-2012-r2.aspx#tab=2).

## Serviceeinstellungen

Beim Bestellen einer vCenter Server-Instanz können Sie auch zusätzliche Services bestellen. Weitere Informationen zu den Services finden Sie unter [Verfügbare Services für vCenter Server-Instanzen](vc_addingremovingservices.html#available-services-for-vcenter-server-instances).

## Bestellübersicht

Auf Basis der für die Instanz und die Add-on-Services ausgewählten Konfiguration werden die geschätzten Kosten sofort generiert und im rechten Fenster im Abschnitt **Bestellübersicht** angezeigt. Klicken Sie unten im rechten Fenster auf **Preisdetails**, um ein PDF-Dokument zu generieren, das die Kostenschätzungsdetails enthält.

## Vorgehensweise

1. Klicken Sie im {{site.data.keyword.cloud_notm}}-Katalog im linken Navigationsfenster auf **VMware** und anschließend im Abschnitt **Virtuelle Rechenzentren** auf **vCenter Server**.
2. Klicken Sie auf der Seite **VMware vCenter Server on IBM Cloud** auf die Karte **vCenter Server** und dann auf **Erstellen**.
3. Geben Sie auf der Seite **vCenter Server** den Instanznamen ein.
4. Wählen Sie den Instanztyp aus:
   * Klicken Sie auf **Primäre Instanz**, um eine einzelne Instanz in der Umgebung bereitzustellen oder um die erste Instanz in einer Topologie mit mehreren Standorten bereitzustellen.
   * Klicken Sie auf **Sekundäre Instanz**, um die Instanz mit einer vorhandenen (primären) Instanz in der Umgebung zu verbinden, um eine hohe Verfügbarkeit zu erreichen, und führen Sie dann die folgenden Schritte aus:
     1. Wählen Sie die primäre Instanz aus, mit der die sekundäre Instanz verbunden werden soll.
     2. Wenn für die primäre Instanz, die Sie ausgewählt haben, ein Upgrade auf das Release der Version 2.5 durchgeführt wurde oder die primäre Instanz in Version 2.4 und früheren Releases bereitgestellt oder aktualisiert wurde, überprüfen Sie das voreingetragene **** Administratorkennwort für die PSC in der primären Instanz, um sicherzustellen, dass es korrekt ist.
     
        **Hinweis:** Das Feld für **** das Administratorkennwort für PSC in der primären Instanz ist nicht für primäre Instanzen verfügbar, die in Version 2.5 oder höheren Releases bereitgestellt werden.     
5. Geben Sie die Lizenzeinstellungen für die Instanzkomponenten ein.  
   *  Zur Verwendung der von IBM bereitgestellten Lizenzen müssen Sie **In Kauf einbeziehen** und bei Bedarf die Lizenzedition auswählen.
   *  Zur Verwendung einer eigenen Lizenz müssen Sie **Lizenz selbst bereitstellen** auswählen und den Lizenzschlüssel eingeben.
6. Geben Sie die Bare Metal Server-Einstellungen an.
    1. Wählen Sie das {{site.data.keyword.CloudDataCent_notm}} als Host für die Instanz aus.
    2. Wählen Sie die Bare Metal Server-Konfiguration aus.
       * Wenn Sie **Vorkonfiguriert** auswählen, dann können Sie zwischen der Konfiguration **S (Klein)**, der Konfiguration **M (Mittel)** und der Konfiguration **L (Groß)** wählen.
       * Wenn Sie **Angepasst** auswählen, dann müssen Sie das CPU-Modell und die RAM-Größe angeben.
    3. Geben Sie die Anzahl der {{site.data.keyword.baremetal_short}}-Instanzen an. Wenn Sie vSAN als Speicherlösung verwenden möchten, beachten Sie, dass mindestens 4 {{site.data.keyword.baremetal_short}}-Instanzen erforderlich sind.  

7. Geben Sie die Speichereinstellungen an:
  * Wenn Sie **vSAN-Speicher** ausgewählt haben, geben Sie **Plattentyp und -größe für vSAN-Kapazitätsplatten** und **Anzahl der vSAN-Kapazitätsplatten** sowie die Methode an, mit der die **vSAN-Lizenz** bereitgestellt werden soll.
  * Wenn Sie **NFS-Speicher** ausgewählt haben und für alle Dateifreigaben dieselben Einstellungen hinzufügen und konfigurieren wollen, geben Sie die **Anzahl der Dateifreigaben**, **Größe** und **Leistung** an.
  * Wenn Sie **NFS-Speicher** ausgewählt haben und Dateifreigaben einzeln hinzufügen und bearbeiten möchten, wählen Sie **Dateifreigaben einzeln konfigurieren** aus, klicken Sie neben der Bezeichnung **NFS hinzufügen** auf das Symbol **+** und wählen Sie dann für jede Dateifreigabe jeweils **Größe** und **Leistung** aus. Sie müssen mindestens eine Dateifreigabe auswählen.

8. Geben Sie die Netzschnittstelleneinstellungen an.
   1. Geben Sie das Hostnamenspräfix, die Unterdomänenbezeichnung und den Rootdomänennamen ein. Für eine sekundäre Instanz wird der Domänenname automatisch eingetragen.
   2. Wählen Sie die VLAN-Einstellungen aus:
      * Falls Sie neue öffentliche und private VLANs bestellen wollen, klicken Sie auf **Neue VLANs bestellen**.
      * Wenn Sie die vorhandenen öffentlichen und privaten VLANs wiederverwenden möchten, sofern diese verfügbar sind, dann klicken Sie auf **Vorhandene VLANs auswählen** und geben Sie die VLANs und Teilnetze an.
   3. Geben Sie die DNS-Konfiguration an.

9. Wählen Sie die Add-on-Services aus, die in der Instanz bereitgestellt werden sollen, indem Sie auf die entsprechende Servicekarte klicken. Wenn ein Service konfiguriert werden muss, dann geben Sie die servicespezifischen Einstellungen an und klicken Sie dann auf der Karte auf **Service hinzufügen**.
Informationen zum Angeben von Einstellungen für einen Service finden Sie im entsprechenden Abschnitt zum Bestellen von Services.

10. Überprüfen Sie im Fenster **Bestellübersicht** die Instanzkonfiguration, bevor Sie die Bestellung aufgeben.
   1. Überprüfen Sie die Einstellungen für die Instanz.
   2. Überprüfen Sie die geschätzten Kosten der Instanz. Klicken Sie auf **Preisdetails**, um eine PDF-Datei mit der Zusammenfassung zu generieren. Ihre Bestellübersicht können Sie speichern oder drucken, indem Sie rechts oben im PDF-Fenster auf das Symbol **Drucken** bzw. **Herunterladen** klicken.
   3. Klicken Sie auf den Link bzw. die Links für die Bedingungen, die für Ihre Bestellung gelten, und vergewissern Sie sich, dass Sie mit diesen Bedingungen einverstanden sind, bevor Sie die Instanz bestellen.
   4. Klicken Sie auf **Bereitstellung**.

## Ergebnisse

Die Bereitstellung der Instanz wird automatisch gestartet. Sie erhalten eine Bestätigung, dass die Bestellung bearbeitet wird, und Sie können den Status der Bereitstellung prüfen, indem Sie die Instanzdetails anzeigen.

Nachdem die Instanz erfolgreich bereitgestellt wurde, sind die Komponenten, die unter [Technische Spezifikationen für vCenter Server-Instanzen](vc_vcenterserveroverview.html#technical-specifications-for-vcenter-server-instances) beschrieben sind, auf Ihrer virtuellen VMware-Plattform installiert. Die von Ihnen bestellten ESXi-Server werden standardmäßig als **cluster1** gruppiert. Wenn Sie zusätzliche Services bestellt haben, wird die Bereitstellung der Services gestartet, nachdem Ihre Bestellung abgeschlossen ist.

Sobald die Instanz einsatzbereit ist, ändert sich der Status der Instanz in **Bereit** und Sie empfangen per E-Mail eine Benachrichtigung.

Wenn Sie eine sekundäre Instanz bestellen, kann VMware vSphere Web Client für die primäre Instanz (mit der sekundären Instanz verknüpft) erneut gestartet werden, nachdem die Bestellung der sekundären Instanz abgeschlossen ist.

## Nächste Schritte

Sie können nun die bestellte vCenter Server-Instanz anzeigen und verwalten.

**Wichtig**: Sie dürfen die {{site.data.keyword.vmwaresolutions_short}}-Komponenten, die in Ihrem {{site.data.keyword.cloud_notm}}-Konto erstellt werden, nur über die {{site.data.keyword.vmwaresolutions_short}}-Konsole und nicht im {{site.data.keyword.slportal}} oder über ein anderes Verfahren außerhalb der Konsole verwalten.
Wenn Sie diese Komponenten außerhalb der {{site.data.keyword.vmwaresolutions_short}}-Konsole ändern, werden die Änderungen nicht mit der Konsole synchronisiert.

**VORSICHT**: Wenn Sie {{site.data.keyword.vmwaresolutions_short}}-Komponenten (die in Ihrem {{site.data.keyword.cloud_notm}}-Konto installiert wurden, als Sie die Instanz bestellt haben) außerhalb der {{site.data.keyword.vmwaresolutions_short}}-Konsole verwalten, kann dies zur Instabilität Ihrer Umgebung führen. Zu diesen Managementaktivitäten gehören:
*  Komponenten hinzufügen, ändern, zurückgeben oder entfernen
*  Instanzkapazität durch das Hinzufügen oder Entfernen von ESXi-Servern erweitern oder verringern
*  Komponenten ausschalten
*  Services erneut starten

   Ausgenommen von diesen Aktivitäten ist unter anderem das Management der Dateifreigaben für gemeinsam genutzten Speicher im {{site.data.keyword.slportal}}. Hierzu gehört das Bestellen, Löschen (mit möglicher Auswirkung auf angehängte Datenspeicher), Berechtigen und Anhängen von Dateifreigaben für gemeinsam genutzten Speicher.

### Zugehörige Links

* [Für ein {{site.data.keyword.cloud_notm}}-Konto registrieren](../vmonic/signing_softlayer_account.html)
* [vCenter Server-Instanzen anzeigen](vc_viewinginstances.html)
* [Konfiguration mit mehreren Standorten für vCenter Server-Instanzen](vc_multisite.html)
* [Cluster für vCenter Server-Instanzen hinzufügen, anzeigen und löschen](vc_addingviewingclusters.html)
* [Kapazität für vCenter Server-Instanzen erweitern und verringern](vc_addingremovingservers.html)
* [Services für vCenter Server-Instanzen bestellen, anzeigen und entfernen](vc_addingremovingservices.html)
* [vCenter Server-Instanzen löschen](vc_deletinginstance.html)
