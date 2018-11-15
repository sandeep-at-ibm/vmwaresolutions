---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-29"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter Server-Instanzen bestellen

Um eine flexible und anpassbare virtualisierte VMware-Plattform bereitzustellen, die Ihren Workloadbedarf optimal erfüllt, bestellen Sie eine VMware vCenter Server-Instanz. Während der Erstbestellung können Sie auch Services hinzufügen, z. B. [Zerto on {{site.data.keyword.cloud}}](../services/addingzertodr.html) für die Disaster-Recovery.

## Voraussetzungen

Stellen Sie sicher, dass Sie die folgenden Tasks ausgeführt haben:
* Sie haben die Berechtigungsnachweise für die {{site.data.keyword.cloud_notm}}-Infrastruktur auf der Seite **Einstellungen** konfiguriert. Weitere Informationen finden Sie unter [Benutzerkonten und Einstellungen verwalten](../vmonic/useraccount.html).
* Sie haben die Informationen in [Voraussetzungen und Planung für vCenter Server-Instanzen](vc_planning.html) gelesen.
* Sie haben das Instanz- und Domänennamensformat geprüft. Der Domänenname und die Unterdomänenbezeichnung werden verwendet, um den Benutzernamen und die Servernamen der Instanz zu generieren.

Tabelle 1. Wertformat für Instanz- und Domänennamen

| Name        | Wertformat      |
  |:------------|:------------ |
  | Domänenname | `<root_domain>` |  
  | Anmeldebenutzername für vCenter Server | `<user_id>@<root_domain>` (Microsoft Active Directory-Benutzer) oder `administrator@vsphere.local` |
  | Vollständig qualifizierter Domänenname für vCenter Server | ` vcenter.<subdomain_label>.<root_domain>`. Die maximale Länge beträgt 50 Zeichen. |
  | SSO-Standortname | `<subdomain_label>` |
  | Vollständig qualifizierter Name des ESXi-Servers | `<host_prefix><n>.<subdomain_label>.<root_domain>`, hierbei steht `<n>` für die Folgenummer des ESXi-Servers. Die maximale Länge beträgt 50 Zeichen. |  
  | Vollständig qualifizierter Domänenname für PSC | `psc-<subdomain_label>.<subdomain_label>.<root_domain>`. Die maximale Länge beträgt 50 Zeichen. |

Nehmen Sie keine Änderungen an Werten vor, die während der Bestellung oder Bereitstellung der Instanz festgelegt werden. Dies kann dazu führen, dass Ihre Instanz unbrauchbar wird. Beispielsweise, wenn der öffentliche Netzbetrieb beendet wird, Server sowie virtuelle Serverinstanzen (VSIs) mitten in einer Bereitstellung hinter eine Vyatta-Einheit versetzt werden oder wenn die Virtual Server-Instanz für IBM CloudBuilder gestoppt oder gelöscht wird.
{:important}

## Systemeinstellungen

Sie müssen folgende Systemeinstellungen angeben, wenn Sie eine vCenter Server-Instanz bestellen.

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
* vCenter Server 6.5 – Standard Edition
* vSphere 6.5u1 – Enterprise Plus Edition
* NSX Service Providers 6.4 (Base, Advanced oder Enterprise Edition)

Für Benutzer der Kategorie "Business Partner" sind die vCenter Server-Lizenz (Standard Edition), die vSphere-Lizenz (Enterprise Plus Edition) und die NSX-Lizenz enthalten und werden in Ihrem Namen erworben. Für die NSX-Lizenz muss allerdings die Edition angegeben werden.

Für Nicht-Business-Partner-Benutzer können die von IBM bereitgestellten VMware-Lizenzen für diese Komponenten benutzt werden. Wählen Sie hierzu **In Kauf einbeziehen** aus. Alternativ hierzu können Sie auch eine eigene Lizenz (Bring Your Own License; BYOL) verwenden, indem Sie **Lizenz selbst bereitstellen** auswählen und die eigenen Lizenzschlüssel angeben.


**Achtung:**
* Es ist eine Lizenz mit mindestens acht CPUs erforderlich, die für vier Server mit zwei CPUs pro Server verwendet wird. Die Lizenzauswahl für jede VMware-Komponente gilt für die Basisinstanz und für alle ESXi-Server, die Sie später zur Instanz hinzufügen. Stellen Sie sicher, dass Ihre Lizenz eine zukünftige Kapazitätserweiterung in Ihrer Infrastruktur unterstützt.
* Die mindestens erforderlichen Lizenzeditionen sind in der Benutzerschnittstelle angegeben. Falls unterschiedliche Komponenteneditionen unterstützt werden, können Sie die gewünschte Edition auswählen. Es liegt in Ihrer Verantwortung, zu gewährleisten, dass der bereitgestellte Lizenzschlüssel für jede ausgewählte VMware-Komponente korrekt ist.
* Für vSphere wird zum Zeitpunkt der Bestellung eine Lizenzgebühr berechnet, anschließend wird die Lizenzgebühr dann aber Ihrem Konto gutgeschrieben.
* Sie können alle Lizenzen ändern, die Sie mit VMware vSphere Web Client bereitgestellt haben, nachdem die Bereitstellung der Instanz abgeschlossen ist.
* Die Unterstützung für die VMware-Komponenten, für die Sie Lizenzen bereitgestellt haben, wird von VMware und nicht vom IBM Support zur Verfügung gestellt.
{:important}

## Einstellungen für Bare Metal Server

Die Bare Metal-Einstellungen sind von Ihrer Rechenzentrumsauswahl und der Konfiguration des Bare Metal Servers abhängig. 

### Standort des Rechenzentrums

Wählen Sie das {{site.data.keyword.CloudDataCent_notm}} aus, das als Host für die Instanz verwendet werden soll.

### Skylake

Wenn Sie **Skylake** auswählen, dann können Sie die Kombination aus CPU und RAM für den Bare Metal Server entsprechend Ihren Anforderungen auswählen.

Tabelle 2. Optionen für Skylake {{site.data.keyword.baremetal_short}}

| CPU-Modelloptionen        | RAM-Optionen       |
|:------------- |:------------- |
| Dual Intel Xeon Silver 4110-Prozessor / 16 Kerne insgesamt, 2,1 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon Gold 5120-Prozessor / 28 Kerne insgesamt, 2,2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon Gold 6140-Prozessor / 36 Kerne insgesamt, 2,3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |

### SAP-zertifiziert

Wenn Sie **SAP-zertifiziert** auswählen, dann können Sie die CPU- oder RAM-Einstellungen nicht ändern.

Wählen Sie gemäß Ihren Anforderungen eine Bare Metal Server-Konfiguration aus:
  * Dual Intel Xeon Gold 6140-Prozessor / 36 Kerne insgesamt, 2,3 GHzDual / 192 GB RAM
  * Dual Intel Xeon Gold 6140-Prozessor / 36 Kerne insgesamt, 2,3 GHzDual / 384 GB RAM
  * Dual Intel Xeon Gold 6140-Prozessor / 36 Kerne insgesamt, 2,3 GHzDual / 768 GB RAM

### Broadwell

Wenn Sie **Broadwell** auswählen, dann können Sie die Kombination aus CPU und RAM für den Bare Metal Server entsprechend Ihren Anforderungen auswählen.

Tabelle 3. Optionen für Broadwell {{site.data.keyword.baremetal_short}}

| CPU-Modelloptionen        | RAM-Optionen       |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4 / 16 Kerne insgesamt, 2,1 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2650 v4 / 24 Kerne insgesamt, 2,2 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2690 v4 / 28 Kerne insgesamt, 2,6 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |

### Vorkonfiguriert

Wenn Sie **Vorkonfiguriert** auswählen, dann können Sie die CPU- oder RAM-Einstellungen nicht ändern.

Wählen Sie gemäß Ihren Anforderungen eine Bare Metal Server-Konfiguration aus:
  * S (Klein): Dual Intel Xeon E5-2620 v4 / 16 Kerne insgesamt, 2,1 GHz / 128 GB RAM / 2 Laufwerke
  * M (Mittel): Dual Intel Xeon E5-2650 v4 / 24 Kerne insgesamt, 2,2 GHz / 256 GB RAM / 2 Laufwerke
  * L (Groß): Dual Intel Xeon E5-2690 v4 / 28 Kerne insgesamt, 2,6 GHz / 512 GB RAM / 2 Laufwerke

### Bare Metal Server-Anzahl

Für den ersten Cluster in der Instanz können Sie die Anzahl der ESXi-Server wie folgt konfigurieren:
* Falls Sie **Skylake** oder **Broadwell** ausgewählt haben, können Sie die Anzahl der ESXi-Server im Bereich von 2 bis 20 konfigurieren.
* Falls Sie **Vorkonfiguriert** ausgewählt haben, können Sie die Anzahl der ESXi-Server im Bereich von 2 bis 10 konfigurieren.

Alle ESXi-Server nutzen die festgelegte Konfiguration gemeinsam. Nach der Erstbereitstellung können Sie vier weitere Cluster hinzufügen. Wenn Sie die Konfiguration **Skylake** oder **Broadwell** für VMware vSAN ausgewählt haben, werden sowohl für den ersten Cluster als auch für die Cluster nach der Bereitstellung 4 ESXi-Server benötigt. Weitere Informationen zum Minimum von ESXi-Servern finden Sie im Abschnitt [Ist eine Serverinstanz mit zwei Knoten hoch verfügbar?](../vmonic/faq.html#is-a-two-node-vcenter-server-instance-highly-available-)

## Speichereinstellungen

Die Speichereinstellungen sind von der Auswahl der Bare Metal Server-Konfiguration und des Speichertyps abhängig.

### vSAN-Speicher

vSAN ist nur für die Bare-Metal-Konfigurationen des Typs **Skylake** oder **Broadwell**verfügbar. Geben Sie die folgenden vSAN-Optionen an:
* **Plattentyp und Größe für vSAN-Kapazitätsplatten**: Wählen Sie die für die Kapazitätsplatten benötigte Option aus.
* **Anzahl der vSAN-Kapazitätsplatten**: Geben Sie die Anzahl der hinzuzufügenden Kapazitätsplatten an.
* Wenn Sie über den Grenzwert von acht Stück hinaus Kapazitätsplatten hinzufügen möchten, müssen Sie das Feld für **Hohe Leistung mit Intel Optane** auswählen. Diese Option stellt zwei zusätzliche Kapazitätsplattenpositionen für eine Gesamtzahl von 10 Kapazitätsplatten bereit und ist für Workloads nützlich, die eine geringere Latenzzeit und einen höheren Durchsatz an E/A-Operationen pro Sekunde erfordern. Die Option **Hohe Leistung mit Intel Optane** steht nur für die Dualprozessoren Intel Xeon Gold 5120 und 6140 zur Verfügung.
* Überprüfen Sie die Werte für **Plattentyp für vSAN-Cacheplatten** und **Anzahl der vSAN-Cacheplatten**. Diese Werte hängen davon ab, ob Sie das Feld **Hohe Leistung mit Intel Optane** ausgewählt haben.
* **vSAN-Lizenz**: Verwenden Sie die von IBM bereitgestellte VMware-Lizenz für die vSAN-Komponente, indem Sie **In Kauf einbeziehen** auswählen, oder verwenden Sie eine eigene Lizenz (Bring Your Own License, BYOL), indem Sie **Lizenz selbst bereitstellen** auswählen und Ihren eigenen Lizenzschlüssel eingeben.

### NFS-Speicher

Wenn Sie **NFS-Speicher** auswählen, können Sie gemeinsam genutzten Speicher auf Dateiebene für Ihre Instanz hinzufügen, wobei für alle gemeinsam genutzten Ressourcen dieselben Einstellungen verwendet werden; alternativ können Sie für die einzelnen gemeinsam genutzten Dateiressourcen jeweils unterschiedliche Konfigurationseinstellungen angeben. Geben Sie die folgenden NFS-Optionen an:

Die Anzahl der gemeinsam genutzten Dateiressourcen muss zwischen 1 und 32 liegen.
{:note}

* **Gemeinsam genutzte Ressourcen einzeln konfigurieren**: Wählen Sie diese Option aus, um für jede einzelne gemeinsam genutzte Dateiressource unterschiedliche Konfigurationseinstellungen anzugeben.
* **Anzahl der gemeinsam genutzten Ressourcen**: Geben Sie bei Verwendung derselben Konfigurationseinstellung für alle gemeinsam genutzten Dateiressourcen die Anzahl der gemeinsam genutzten Dateiressourcen für den gemeinsam genutzten NFS-Speicher an, die Sie hinzufügen möchten.
* **Größe**: Wählen Sie die Kapazität aus, die Ihrem Bedarf an gemeinsam genutzten Speicher entspricht.
* **Leistung**: Wählen Sie basierend auf Ihren Workloadanforderungen die pro GB geltende Anzahl von E/A-Operationen pro Sekunde aus.
* **NFS hinzufügen**: Wählen Sie diese Option aus, um einzelne gemeinsam genutzte Dateiressourcen hinzuzufügen, für die unterschiedliche Konfigurationseinstellungen verwendet werden.

Tabelle 4. Optionen für die NFS-Leistungsstufe

| Option        | Details       |
  |:------------- |:------------- |
  | 2 IOPS/GB | Diese Option ist für die meisten allgemeinen Workloads geeignet. Anwendungsbeispiele sind das Hosting von kompakten Datenbanken, die Sicherung von Webanwendungen oder Plattenimages von virtuellen Maschinen für einen Hypervisor. |
  | 4 IOPS/GB | Diese Option ist für Workloads mit höherer Intensität geeignet, die zu einem bestimmten Zeitpunkt einen hohen Prozentsatz an aktiven Daten aufweisen. Anwendungsbeispiele sind transaktionsorientierte Datenbanken. |
  | 10 IOPS/GB | Diese Option ist für die aufwändigsten Workloadtypen wie beispielsweise die Analyse gedacht. Anwendungsbeispiele sind Hochtransaktionsdatenbanken und andere leistungskritische Datenbanken. Diese Leistungsstufe ist auf eine maximale Kapazität von 4 TB pro gemeinsam genutzte Dateiressource begrenzt. |

## Netzschnittstelleneinstellungen

Sie müssen folgende Netzschnittstelleneinstellungen angeben, wenn Sie eine vCenter Server-Instanz bestellen.

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

Die maximale Länge des vollständig qualifizierten Domänennamens (FQDN = Fully Qualified Domain Name) für Hosts und VMs beträgt 50 Zeichen. Domänennamen müssen diese maximale Länge zulassen.
{:note}

### Öffentliches oder privates Netz

Die Einstellungen für die Aktivierung der Netzschnittstellenkarte (NIC – Network Interface Card) basieren darauf, ob Sie **Öffentliches und privates Netz** oder **Nur privates Netz** auswählen. Die folgenden Add-on-Services benötigen öffentliche NICs und sind nicht verfügbar, wenn Sie die private Option auswählen:

* F5 on {{site.data.keyword.cloud_notm}}
* FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}
* FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}
* Zerto on {{site.data.keyword.cloud_notm}}

### VLANs

Die Netzeinstellungen basieren auf Ihrer Auswahl von entweder **Neue VLANs bestellen** oder **Vorhandene VLANs auswählen**.

Für Ihre Instanzbestellung sind 1 öffentliches VLAN und 2 private VLANs erforderlich. Die zwei privaten VLANs werden in jedem Bare Metal Server zusammengelegt.

#### Neue VLANs bestellen
Wählen Sie diese Option aus, um ein neues öffentliches VLANs und zwei neue private VLANs zu bestellen.

#### Vorhandene VLANs auswählen
Abhängig vom ausgewählten {{site.data.keyword.CloudDataCent_notm}} sind möglicherweise vorhandene öffentliche und private VLANs verfügbar.

Wenn Sie vorhandene öffentliche und private VLANs wiederverwenden wollen, dann geben Sie die VLANs und Teilnetze an:
* **Öffentliches VLAN** - Wird für den Zugriff auf öffentliche Netze verwendet.
* **Privates VLAN** - Wird für die Konnektivität zwischen den Rechenzentren und Services in {{site.data.keyword.cloud_notm}} verwendet.
* **Sekundäres privates VLAN** - Wird für VMware-Funktionen wie z. B. vSAN verwendet.
* **Primäres Teilnetz** - Wird physischen Hosts für den Zugriff auf öffentliche Netze zugewiesen.
* **Primäres privates Teilnetz** - Wird physischen Hosts für den Managementdatenverkehr zugewiesen.

* Stellen Sie sicher, dass die Firewallkonfiguration bei den ausgewählten VLANs den Managementdatenverkehr nicht blockiert.
* Stellen Sie sicher, dass sich alle von Ihnen ausgewählten VLANs in demselben Pod befinden. ESXi-Server können nicht in VLANs mit unterschiedlichen Pods bereitgestellt werden.
{:important}

### DNS-Konfiguration

Wählen Sie die Konfiguration für DNS (Domain Name System) für Ihre Instanz aus:

* **Einzelne öffentliche Windows-VSI für Active Directory/DNS**: Eine einzelne Serverinstanz (VSI) von Microsoft Windows Server für Microsoft Active Directory (AD), die als DNS für die Instanz dient, auf der die Hosts und VMs registriert sind, wird bereitgestellt und kann zur Suche verwendet werden. Diese Option wurde standardmäßig für Instanzen von V1.9 und höher bereitgestellt.
* **Zwei hoch verfügbare dedizierte Windows-Server-VMs auf dem Management-Cluster**: Es werden zwei Microsoft Windows-VMs bereitgestellt, die den Datenschutz und die Leistungsfähigkeit verbessern.

Sie müssen zwei Lizenzen für Microsoft Windows Server 2012 R2 bereitstellen, wenn Sie Ihre Instanz für die Verwendung der beiden Microsoft Windows-VMs konfigurieren. Verwenden Sie die Lizenz für Microsoft Windows Server 2012 R2 Standard Edition und/oder die Lizenz für Microsoft Windows Server 2012 R2 Datacenter Edition.
{:important}

Jede Lizenz kann nur einem einzigen physischen Server zugeordnet werden und deckt bis zu zwei physische Prozessoren ab. Mit einer Standard Edition-Lizenz können zwei virtualisierte Microsoft Windows-VMs pro 2-Prozessor-Server ausgeführt werden. Daher sind zwei Lizenzen erforderlich, weil zwei Microsoft Windows-VMs in zwei unterschiedlichen Hosts bereitgestellt werden.

Sie haben 30 Tage Zeit, um die VMs zu aktivieren.

Weitere Informationen zur Windows-Lizenzierung finden Sie auf der Seite [Windows Server 2012 R2 documentation](https://www.microsoft.com/en-us/licensing/product-licensing/windows-server-2012-r2.aspx#tab=2).

## Serviceeinstellungen

Beim Bestellen einer vCenter Server-Instanz können Sie auch Add-on-Services bestellen. Weitere Informationen zu den Services finden Sie unter [Verfügbare Services für vCenter Server-Instanzen](vc_addingremovingservices.html#available-services-for-vcenter-server-instances).

## Bestellübersicht

Auf Basis der für die Instanz und die Add-on-Services ausgewählten Konfiguration werden die geschätzten Kosten sofort generiert und im rechten Fenster im Abschnitt **Bestellübersicht** angezeigt. Klicken Sie unten im rechten Fenster auf **Preisdetails**, um ein PDF-Dokument zu generieren, das die Kostenschätzungsdetails enthält.

## Vorgehensweise zum Bestellen von vCenter Server-Instanzen

1. Klicken Sie im {{site.data.keyword.cloud_notm}}-Katalog im linken Navigationsfenster auf **VMware** und klicken Sie anschließend im Abschnitt **Virtuelle Rechenzentren** auf **vCenter Server**.
2. Klicken Sie auf der Seite **VMware vCenter Server on IBM Cloud** auf die Karte **vCenter Server** und dann auf **Erstellen**.
3. Geben Sie auf der Seite **vCenter Server** den Instanznamen ein.
4. Wählen Sie den Instanztyp aus:
   * Klicken Sie auf **Primäre Instanz**, um eine einzelne Instanz in der Umgebung bereitzustellen oder um die erste Instanz in einer Topologie mit mehreren Standorten bereitzustellen.
   * Klicken Sie auf **Sekundäre Instanz**, um die Instanz mit einer vorhandenen (primären) Instanz in der Umgebung zu verbinden, um eine hohe Verfügbarkeit zu erreichen, und führen Sie dann die folgenden Schritte aus:
     1. Wählen Sie die primäre Instanz aus, mit der die sekundäre Instanz verbunden werden soll.
     2. Geben Sie für primäre Instanzen ab Version 2.5 den Wert für ****das Administratorkennwort für PSC in der primären Instanz ein.
     3. Überprüfen Sie für primäre Instanzen der Version 2.4 oder früher, dass der in das Feld ****für das Administratorkennwort für PSC in der primären Instanz voreingetragene Wert korrekt ist.
5. Geben Sie die Lizenzeinstellungen für die Instanzkomponenten ein.
   *  Zur Verwendung der von IBM bereitgestellten Lizenzen müssen Sie **In Kauf einbeziehen** und bei Bedarf die Lizenzedition auswählen.
   *  Zur Verwendung einer eigenen Lizenz müssen Sie **Lizenz selbst bereitstellen** auswählen und den Lizenzschlüssel eingeben.
6. Geben Sie die Bare Metal Server-Einstellungen an.
    1. Wählen Sie das {{site.data.keyword.CloudDataCent_notm}} als Host für die Instanz aus.
    2. Wählen Sie die Bare Metal Server-Konfiguration aus.
       * Wenn Sie **Skylake** oder **Broadwell** auswählen, dann müssen Sie das CPU-Modell und die RAM-Größe angeben.
       * Wenn Sie **SAP-zertifiziert** auswählen, müssen Sie das CPU-Modell wählen.
       * Wenn Sie **Vorkonfiguriert** auswählen, dann können Sie zwischen der Konfiguration **S (Klein)**, der Konfiguration **M (Mittel)** und der Konfiguration **L (Groß)** wählen.
    3. Geben Sie die Anzahl der {{site.data.keyword.baremetal_short}}-Instanzen an. Wenn vSAN als Speicherlösung verwendet werden soll, sind mindestens vier {{site.data.keyword.baremetal_short}}-Instanzen erforderlich.  
7. Führen Sie die Speicherkonfiguration durch.
  * Wenn Sie **vSAN-Speicher** auswählen, geben Sie die Plattentypen für die Kapazitäts- und Cacheplatten, die Anzahl der Platten und die vSAN-Lizenzedition an. Falls Sie mehr Speicher benötigen, müssen Sie das Feld für **Hohe Leistung mit Intel Optane** auswählen.
  * Wenn Sie **NFS-Speicher** auswählen und für alle gemeinsam genutzten Dateiressourcen dieselben Einstellungen hinzufügen und konfigurieren wollen, geben Sie die **Anzahl der gemeinsam genutzten Ressourcen**, **Größe** und **Leistung** an.
  * Wenn Sie **NFS-Speicher** auswählen und alle gemeinsam genutzten Dateiressourcen einzeln hinzufügen und konfigurieren möchten, wählen Sie **Gemeinsam genutzte Ressourcen einzeln konfigurieren** aus. Klicken Sie anschließend auf das Symbol **+** neben der Bezeichnung **NFS hinzufügen** und wählen Sie für jede gemeinsam genutzte Dateiressource die **Größe** und die **Leistung** aus. Sie müssen mindestens eine gemeinsam genutzte Dateiressource auswählen.
8. Geben Sie die Netzschnittstelleneinstellungen an.
   1. Geben Sie das Hostnamenspräfix, die Unterdomänenbezeichnung und den Rootdomänennamen ein. Für eine sekundäre Instanz wird der Domänenname automatisch ergänzt.
   2. Wählen Sie die Netzeinstellung für entweder **Öffentliches und privates Netz** oder **Nur privates Netz** aus.
   3. Wählen Sie die VLAN-Einstellungen aus:
      * Falls Sie neue öffentliche und private VLANs bestellen wollen, klicken Sie auf **Neue VLANs bestellen**.
      * Wenn Sie die vorhandenen öffentlichen und privaten VLANs wiederverwenden möchten, sofern diese verfügbar sind, dann klicken Sie auf **Vorhandene VLANs auswählen** und geben Sie die VLANs und Teilnetze an.
   4. Geben Sie die DNS-Konfiguration an.

9. Wählen Sie die Add-on-Services aus, die in der Instanz bereitgestellt werden sollen, indem Sie auf die entsprechende Servicekarte klicken. Wenn ein Service konfiguriert werden muss, dann geben Sie die servicespezifischen Einstellungen an und klicken Sie dann auf der Karte auf **Service hinzufügen**.
Weitere Informationen zum Angeben von Einstellungen für einen Service finden Sie im entsprechenden Abschnitt zum Bestellen von Services.

10. Überprüfen Sie im Fenster **Bestellübersicht** die Instanzkonfiguration, bevor Sie die Bestellung aufgeben.
   1. Überprüfen Sie die Einstellungen für die Instanz.
   2. Überprüfen Sie die geschätzten Kosten der Instanz. Klicken Sie auf **Preisdetails**, um eine PDF-Datei mit der Zusammenfassung zu generieren. Ihre Bestellübersicht können Sie speichern oder drucken, indem Sie rechts oben im PDF-Fenster auf das Symbol **Drucken** bzw. **Herunterladen** klicken.
   3. Klicken Sie auf den Link bzw. die Links für die Bedingungen, die für Ihre Bestellung gelten, und vergewissern Sie sich, dass Sie mit diesen Bedingungen einverstanden sind, bevor Sie die Instanz bestellen.
   4. Klicken Sie auf **Bereitstellung**.

## Ergebnisse

Die Bereitstellung der Instanz wird automatisch gestartet. Sie erhalten eine Bestätigung, dass die Bestellung bearbeitet wird, und Sie können den Status der Bereitstellung prüfen, indem Sie die Instanzdetails anzeigen.

Nachdem die Instanz erfolgreich bereitgestellt wurde, sind die Komponenten, die unter [Technische Spezifikationen für vCenter Server-Instanzen](vc_vcenterserveroverview.html#technical-specifications-for-vcenter-server-instances) beschrieben sind, auf Ihrer virtuellen VMware-Plattform installiert. Die von Ihnen bestellten ESXi-Server werden standardmäßig als **cluster1** gruppiert. Wenn Sie Add-on-Services bestellt haben, wird die Bereitstellung der Services gestartet, nachdem Ihre Bestellung abgeschlossen ist.

Sobald die Instanz einsatzbereit ist, ändert sich der Status der Instanz in **Bereit** und Sie empfangen per E-Mail eine Benachrichtigung.

Wenn Sie eine sekundäre Instanz bestellen, kann VMware vSphere Web Client für die primäre Instanz (mit der sekundären Instanz verknüpft) erneut gestartet werden, nachdem die Bestellung der sekundären Instanz abgeschlossen ist.

## Nächste Schritte

Sie können nun die bestellte vCenter Server-Instanz anzeigen und verwalten.

Sie dürfen die {{site.data.keyword.vmwaresolutions_short}}-Komponenten, die in Ihrem {{site.data.keyword.cloud_notm}}-Konto erstellt werden, nur über die {{site.data.keyword.vmwaresolutions_short}}-Konsole und nicht im {{site.data.keyword.slportal}} oder über ein anderes Verfahren außerhalb der Konsole verwalten. Wenn Sie diese Komponenten außerhalb der {{site.data.keyword.vmwaresolutions_short}}-Konsole ändern, werden die Änderungen nicht mit der Konsole synchronisiert.
{:important}

**VORSICHT:** Wenn Sie {{site.data.keyword.vmwaresolutions_short}}-Komponenten (die in Ihrem {{site.data.keyword.cloud_notm}}-Konto installiert wurden, als Sie die Instanz bestellt haben) außerhalb der {{site.data.keyword.vmwaresolutions_short}}-Konsole verwalten, kann dies zur Instabilität Ihrer Umgebung führen. Zu diesen Managementaktivitäten gehören:
*  Komponenten hinzufügen, ändern, zurückgeben oder entfernen
*  Instanzkapazität durch das Hinzufügen oder Entfernen von ESXi-Servern erweitern oder verringern
*  Komponenten ausschalten
*  Services erneut starten

   Ausgenommen von diesen Aktivitäten ist unter anderem das Management der gemeinsam genutzten Dateiressourcen für gemeinsam genutzten Speicher im {{site.data.keyword.slportal}}. Hierzu gehört das Bestellen, Löschen (mit möglicher Auswirkung auf angehängte Datenspeicher), Berechtigen und Anhängen von gemeinsam genutzten Dateiressourcen für gemeinsam genutzten Speicher.

### Zugehörige Links

* [Für ein {{site.data.keyword.cloud_notm}}-Konto registrieren](../vmonic/signing_softlayer_account.html)
* [vCenter Server-Instanzen anzeigen](vc_viewinginstances.html)
* [Konfiguration mit mehreren Standorten für vCenter Server-Instanzen](vc_multisite.html)
* [Cluster für vCenter Server-Instanzen hinzufügen, anzeigen und löschen](vc_addingviewingclusters.html)
* [Kapazität für vCenter Server-Instanzen erweitern und verringern](vc_addingremovingservers.html)
* [Services für vCenter Server-Instanzen bestellen, anzeigen und entfernen](vc_addingremovingservices.html)
* [vCenter Server-Instanzen löschen](vc_deletinginstance.html)
