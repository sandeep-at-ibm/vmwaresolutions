---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-20"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter Server with NSX-T-Instanzen bestellen
{: #vc_nsx-t_orderinginstance}

Bestellen Sie eine VMware vCenter Server with NSX-T-Instanz, um eine flexible und anpassbare virtualisierte VMware-Plattform bereitzustellen, die Ihre Workloadanforderungen optimal erfüllt.

## Voraussetzungen
{: #vc_nsx-t_orderinginstance-req}

Stellen Sie sicher, dass Sie die folgenden Tasks ausgeführt haben:
* Sie haben die Berechtigungsnachweise für die {{site.data.keyword.cloud_notm}}-Infrastruktur auf der Seite **Einstellungen** konfiguriert. Weitere Informationen finden Sie unter [Benutzerkonten und Einstellungen verwalten](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount).
* Sie haben die Informationen in [Voraussetzungen und Planung für vCenter Server-Instanzen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning) gelesen.
* Sie haben das Instanz- und Domänennamensformat geprüft. Der Domänenname und die Unterdomänenbezeichnung werden verwendet, um den Benutzernamen und die Servernamen der Instanz zu generieren.

Tabelle 1. Wertformat für Instanz- und Domänennamen

| Name        | Wertformat      |
  |:------------|:------------ |
  | Domänenname | `<root_domain>` |  
  | Anmeldebenutzername für vCenter Server | `<user_id>@<root_domain>` (Microsoft Active Directory-Benutzer) oder `administrator@vsphere.local` |
  | vCenter Server (mit integriertem PSC) FQDN | `vcenter-<subdomain_label>.<subdomain_label>.<root_domain>`. Die maximale Länge beträgt 50 Zeichen. |
  | SSO-Standortname | `<subdomain_label>` |
  | Vollständig qualifizierter Name des ESXi-Servers | `<host_prefix><n>.<subdomain_label>.<root_domain>`, hierbei steht `<n>` für die Folgenummer des ESXi-Servers. Die maximale Länge beträgt 50 Zeichen. |

Nehmen Sie keine Änderungen an Werten vor, die während der Bestellung oder Bereitstellung der Instanz festgelegt werden. Dies kann dazu führen, dass Ihre Instanz unbrauchbar wird. Beispielsweise, wenn der öffentliche Netzbetrieb beendet wird, Server sowie virtuelle Serverinstanzen (VSIs) mitten in einer Bereitstellung hinter eine Vyatta-Einheit versetzt werden oder wenn die Virtual Server-Instanz für IBM CloudBuilder gestoppt oder gelöscht wird.
{:important}

## Systemeinstellungen
{: #vc_nsx-t_orderinginstance-sys-settings}

Sie müssen folgende Systemeinstellungen angeben, wenn Sie eine vCenter Server-Instanz bestellen.

### Instanzname
{: #vc_nsx-t_orderinginstance-inst-name}

Der Instanzname muss die folgenden Anforderungen erfüllen:
* Es sind nur alphanumerische Zeichen und Bindestriche (-) zulässig.
* Der Instanzname muss mit einem alphabetischen Zeichen beginnen und mit einem alphanumerischen Zeichen enden.
* Die maximale Länge des Instanznamens beträgt 10 Zeichen.
* Der Instanzname muss innerhalb Ihres Kontos eindeutig sein.

### VMware vSphere-Lizenzen
{: ##vc_nsx-t_orderinginstance-vsphere-license}

Die vSphere Enterprise Plus 6.7u1-Lizenz ist standardmäßig ausgewählt.

### Primär oder sekundär
{: #vc_nsx-t_orderinginstance-primary-secondary}

Wählen Sie aus, ob Sie eine neue primäre oder sekundäre Instanz für eine bereits vorhandene primäre Instanz bestellen wollen.

## Lizenzierungseinstellungen
{: #vc_nsx-t_orderinginstance-licensing-settings}

Geben Sie die Lizenzierungsoptionen für die folgenden VMware-Komponenten in der Instanz an:
* vCenter Server 6.5
* vSphere Enterprise Plus 6.7
* NSX-T 2.4 (Base, Advanced oder Enterprise Edition)

Für Benutzer der Kategorie "Business Partner" sind die vCenter Server-Lizenz (Standard Edition), die vSphere-Lizenz (Enterprise Plus Edition) und die NSX-Lizenz enthalten und werden in Ihrem Namen erworben. Für die NSX-Lizenz muss allerdings die Edition angegeben werden.

Für Nicht-Business-Partner-Benutzer können die von IBM bereitgestellten VMware-Lizenzen für diese Komponenten benutzt werden. Wählen Sie hierzu **In Kauf einbeziehen** aus. Alternativ hierzu können Sie auch eine eigene Lizenz (Bring Your Own License; BYOL) verwenden, indem Sie **Lizenz selbst bereitstellen** auswählen und die eigenen Lizenzschlüssel angeben.

### Hinweise zur Lizenzierung
{: #vc_nsx-t_orderinginstance-licensing-notes}

* Es ist eine Lizenz mit mindestens acht CPUs erforderlich, die für vier Server mit zwei CPUs pro Server verwendet wird. Die Lizenzauswahl für jede VMware-Komponente gilt für die Basisinstanz und für alle ESXi-Server, die Sie später zur Instanz hinzufügen. Stellen Sie sicher, dass Ihre Lizenz eine zukünftige Kapazitätserweiterung in Ihrer Infrastruktur unterstützt.
* Die mindestens erforderlichen Lizenzeditionen sind in der Benutzerschnittstelle angegeben. Falls unterschiedliche Komponenteneditionen unterstützt werden, können Sie die gewünschte Edition auswählen. Es liegt in Ihrer Verantwortung, zu gewährleisten, dass der bereitgestellte Lizenzschlüssel für jede ausgewählte VMware-Komponente korrekt ist.
* Für vSphere wird zum Zeitpunkt der Bestellung eine Lizenzgebühr berechnet, anschließend wird die Lizenzgebühr dann aber Ihrem Konto gutgeschrieben.
* Sie können alle Lizenzen ändern, die Sie mit VMware vSphere Web Client bereitgestellt haben, nachdem die Bereitstellung der Instanz abgeschlossen ist.
* Die Unterstützung für die VMware-Komponenten, für die Sie Lizenzen bereitgestellt haben, wird von VMware und nicht vom IBM Support zur Verfügung gestellt.

## Einstellungen für Bare Metal Server
{: #vc_nsx-t_orderinginstance-bare-metal-settings}

Die Bare Metal-Einstellungen sind von Ihrer Rechenzentrumsauswahl und der Konfiguration des Bare Metal Servers abhängig.

### Standort des Rechenzentrums
{: #vc_nsx-t_orderinginstance-dc-location}

Wählen Sie das {{site.data.keyword.CloudDataCent_notm}} aus, das als Host für die Instanz verwendet werden soll.

### Skylake
{: #vc_nsx-t_orderinginstance-skylake}

Wenn Sie **Skylake** auswählen, dann können Sie die Kombination aus CPU und RAM für den Bare Metal Server entsprechend Ihren Anforderungen auswählen.

Tabelle 2. Optionen für Skylake {{site.data.keyword.baremetal_short}}

| CPU-Modelloptionen        | RAM-Optionen       |
|:------------- |:------------- |
| Dual Intel Xeon Silver 4110-Prozessor / 16 Kerne insgesamt, 2,1 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon Gold 5120-Prozessor / 28 Kerne insgesamt, 2,2 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon Gold 6140-Prozessor / 36 Kerne insgesamt, 2,3 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |

### Broadwell
{: #vc_nsx-t_orderinginstance-broadwell}

Wenn Sie **Broadwell** auswählen, dann können Sie die Kombination aus CPU und RAM für den Bare Metal Server entsprechend Ihren Anforderungen auswählen.

Tabelle 3. Optionen für Broadwell {{site.data.keyword.baremetal_short}}

| CPU-Modelloptionen        | RAM-Optionen       |
|:------------- |:------------- |
| Quad Intel Xeon E7-4820 v4 / 40 Kerne insgesamt, 2,0 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |
| Quad Intel Xeon E7-4850 v4 / 64 Kerne insgesamt, 2,1 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |

### Bare Metal Server-Anzahl
{: #vc_nsx-t_orderinginstance-bare-metal-number}

Für den ersten Cluster in der Instanz können Sie die Anzahl der ESXi-Server im Bereich von 3 bis 20 konfigurieren. Alle ESXi-Server nutzen die festgelegte Konfiguration gemeinsam.

Nach der Erstbereitstellung können Sie vier weitere Cluster hinzufügen. Wenn Sie die Konfiguration **Skylake** oder **Broadwell** für VMware vSAN ausgewählt haben, werden sowohl für den ersten Cluster als auch für die Cluster nach der Bereitstellung 4 ESXi-Server benötigt. Weitere Informationen zum Minimum von ESXi-Servern finden Sie im Abschnitt [Ist eine Serverinstanz mit zwei Knoten hoch verfügbar?](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq#is-a-two-node-vcenter-server-instance-highly-available-)

## Speichereinstellungen
{: #vc_nsx-t_orderinginstance-storage-settings}

Die Speichereinstellungen sind von der Auswahl der Bare Metal Server-Konfiguration und des Speichertyps abhängig.

Für bereitgestellte Instanzen können Sie gemeinsam genutzte NFS-Speicherressourcen zu einem vorhandenen NFS- oder vSAN-Cluster hinzufügen. Weitere Informationen finden Sie im Abschnitt *NFS-Speicher zu vCenter Server-Instanzen hinzufügen* in [Kapazität für vCenter Server-Instanzen erweitern und verringern](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers#adding-nfs-storage-to-vcenter-server-instances).
{:note}

### vSAN-Speicher
{: #vc_nsx-t_orderinginstance-vsan-storage}

vSAN ist nur für die Bare-Metal-Konfigurationen des Typs **Skylake** oder **Broadwell**verfügbar. Geben Sie die folgenden vSAN-Optionen an:
* **Plattentyp und Größe für vSAN-Kapazitätsplatten**: Wählen Sie die für die Kapazitätsplatten benötigte Option aus.
* **Anzahl der vSAN-Kapazitätsplatten**: Geben Sie die Anzahl der hinzuzufügenden Kapazitätsplatten an.
* Wenn Sie über den Grenzwert von acht Stück hinaus Kapazitätsplatten hinzufügen möchten, müssen Sie das Feld für **Hohe Leistung mit Intel Optane** auswählen. Diese Option stellt zwei zusätzliche Kapazitätsplattenpositionen für eine Gesamtzahl von 10 Kapazitätsplatten bereit und ist für Workloads nützlich, die eine geringere Latenzzeit und einen höheren Durchsatz an E/A-Operationen pro Sekunde erfordern.

  Die Option **High-Performance Intel Optane** ist nur für die Skylake-CPU-Modelle Dual Intel Xeon Gold 5120 und Dual Intel Xeon Gold 6140 verfügbar.
  {:note}

* Überprüfen Sie die Werte für **Plattentyp für vSAN-Cacheplatten** und **Anzahl der vSAN-Cacheplatten**. Diese Werte hängen davon ab, ob Sie das Feld **Hohe Leistung mit Intel Optane** ausgewählt haben.
* **vSAN-Lizenz**: Verwenden Sie die von IBM bereitgestellte VMware-Lizenz für die vSAN-Komponente, indem Sie **In Kauf einbeziehen** auswählen, oder verwenden Sie eine eigene Lizenz (Bring Your Own License, BYOL), indem Sie **Lizenz selbst bereitstellen** auswählen und Ihren eigenen Lizenzschlüssel eingeben.

### NFS-Speicher
{: #vc_nsx-t_orderinginstance-nfs-storage}

Wenn Sie **NFS-Speicher** auswählen, können Sie gemeinsam genutzten Speicher auf Dateiebene für Ihre Instanz hinzufügen, wobei für alle gemeinsam genutzten Ressourcen dieselben Einstellungen verwendet werden; alternativ können Sie für die einzelnen gemeinsam genutzten Dateiressourcen jeweils unterschiedliche Konfigurationseinstellungen angeben. Geben Sie die folgenden NFS-Optionen an:

Die Anzahl der gemeinsam genutzten Dateiressourcen muss zwischen 1 und 32 liegen.
{:note}

* **Gemeinsam genutzte Ressourcen einzeln konfigurieren**: Wählen Sie diese Option aus, um für jede einzelne gemeinsam genutzte Dateiressource unterschiedliche Konfigurationseinstellungen anzugeben.
* **Anzahl der gemeinsam genutzten Ressourcen**: Geben Sie bei Verwendung derselben Konfigurationseinstellung für alle gemeinsam genutzten Dateiressourcen die Anzahl der gemeinsam genutzten Dateiressourcen für den gemeinsam genutzten NFS-Speicher an, die Sie hinzufügen möchten.
* **Leistung**: Wählen Sie basierend auf Ihren Workloadanforderungen die pro GB geltende Anzahl von E/A-Operationen pro Sekunde aus.
* **Größe (GB)**: Wählen Sie die Kapazität aus, die Ihrem Bedarf an gemeinsam genutzten Speicher entspricht.
* **Gemeinsam genutzten Speicher hinzufügen**: Wählen Sie diese Option aus, um einzelne gemeinsam genutzte Dateiressourcen mit anderen Konfigurationseinstellungen hinzuzufügen.

Tabelle 4. Optionen für die NFS-Leistungsstufe

| Option        | Details       |
  |:------------- |:------------- |
  | 0,25 IOPS/GB | Diese Option ist für Workloads vorgesehen, die nicht häufig verwendet werden. Zu den Beispielanwendungen gehören: durch Vaulting geschützte Daten, das Hosting großer Datenbanken mit übernommenen Daten oder Images von virtuellen Platten des virtuellen Speichersystems als Sicherung. |
  | 2 IOPS/GB | Diese Option ist für die meisten allgemeinen Workloads geeignet. Anwendungsbeispiele sind das Hosting von kompakten Datenbanken, die Sicherung von Webanwendungen oder Plattenimages von virtuellen Maschinen für einen Hypervisor. |
  | 4 IOPS/GB | Diese Option ist für Workloads mit höherer Intensität geeignet, die zu einem bestimmten Zeitpunkt einen hohen Prozentsatz an aktiven Daten aufweisen. Anwendungsbeispiele sind transaktionsorientierte Datenbanken. |
  | 10 IOPS/GB | Diese Option ist für die aufwändigsten Workloadtypen wie beispielsweise die Analyse gedacht. Anwendungsbeispiele sind Hochtransaktionsdatenbanken und andere leistungskritische Datenbanken. Diese Leistungsstufe ist auf eine maximale Kapazität von 4 TB pro gemeinsam genutzte Dateiressource begrenzt. |

## Netzschnittstelleneinstellungen
{: #vc_nsx-t_orderinginstance-network-interface-settings}

Sie müssen folgende Netzschnittstelleneinstellungen angeben, wenn Sie eine vCenter Server-Instanz bestellen.

### Hostnamenspräfix
{: #vc_nsx-t_orderinginstance-host-name-prefix}

Das Hostnamenspräfix muss die folgenden Anforderungen erfüllen:
*  Es sind nur alphanumerische Zeichen und Bindestriche (-) zulässig.
*  Das Hostnamenspräfix muss mit einem alphanumerischen Zeichen beginnen und enden.
*  Die maximale Länge des Hostnamenspräfix beträgt 10 Zeichen.

### Unterdomänenbezeichnung
{: #vc_nsx-t_orderinginstance-subdomain-label}

Die Unterdomänenbezeichnung muss die folgenden Anforderungen erfüllen:
*  Es sind nur alphanumerische Zeichen und Bindestriche (-) zulässig.
*  Die Unterdomänenbezeichnung muss mit einem alphabetischen Zeichen beginnen und mit einem alphanumerischen Zeichen enden.
*  Die maximale Länge der Unterdomänenbezeichnung beträgt 10 Zeichen.
*  Die Unterdomänenbezeichnung muss innerhalb Ihres Kontos eindeutig sein.

### Domänenname
{: #vc_nsx-t_orderinginstance-domain-name}

Der Rootdomänenname muss die folgenden Anforderungen erfüllen:
* Der Domänenname muss aus zwei oder mehr Zeichenfolgen bestehen, die jeweils durch einen Punkt (.) voneinander getrennt sind.
* Die erste Zeichenfolge muss mit einem alphabetischen Zeichen beginnen und mit einem alphanumerischen Zeichen enden.
* Alle Zeichenfolgen mit Ausnahme der letzten darf nur alphanumerische Zeichen und Gedankenstriche (-) enthalten.
* Die letzte Zeichenfolge darf nur Buchstaben enthalten.
* Die Länge der letzten Zeichenfolge muss zwischen 2 und 24 Zeichen betragen.

Die maximale Länge des vollständig qualifizierten Domänennamens (FQDN = Fully Qualified Domain Name) für Hosts und VMs beträgt 50 Zeichen. Domänennamen müssen diese maximale Länge zulassen.
{:note}

### Öffentliches oder privates Netz
{: #vc_nsx-t_orderinginstance-public-private-network}

Die Einstellungen für die Aktivierung der Netzschnittstellenkarte (NIC - Network Interface Card) basieren darauf, ob Sie **Öffentliches und privates Netz** oder **Nur privates Netz** auswählen.

### VLANs
{: #vc_nsx-t_orderinginstance-vlans}

Die Netzeinstellungen basieren auf Ihrer Auswahl von entweder **Neue VLANs bestellen** oder **Vorhandene VLANs auswählen**.

Für Ihre Instanzbestellung sind 1 öffentliches VLAN und 2 private VLANs erforderlich. Die zwei privaten VLANs werden in jedem Bare Metal Server zusammengelegt.

#### Neue VLANs bestellen
{: #vc_nsx-t_orderinginstance-new-vlans}

Wählen Sie diese Option aus, um ein neues öffentliches VLANs und zwei neue private VLANs zu bestellen.

#### Vorhandene VLANs auswählen
{: #vc_nsx-t_orderinginstance-existing-vlans}

Abhängig vom ausgewählten {{site.data.keyword.CloudDataCent_notm}} sind möglicherweise vorhandene öffentliche und private VLANs verfügbar.

Wenn Sie vorhandene öffentliche und private VLANs wiederverwenden wollen, dann geben Sie die VLANs und Teilnetze an:
* **Öffentliches VLAN** - Wird für den Zugriff auf öffentliche Netze verwendet.
* **Privates VLAN** - Wird für die Konnektivität zwischen den Rechenzentren und Services in {{site.data.keyword.cloud_notm}} verwendet.
* **Sekundäres privates VLAN** - Wird für VMware-Funktionen wie z. B. vSAN verwendet.
* **Primäres Teilnetz** - Wird physischen Hosts für den Zugriff auf öffentliche Netze zugewiesen.
* **Primäres privates Teilnetz** - Wird physischen Hosts für den Managementdatenverkehr zugewiesen.

Stellen Sie sicher, dass die Firewallkonfiguration bei den ausgewählten VLANs den Managementdatenverkehr nicht sperrt. Stellen Sie außerdem sicher, dass sich alle von Ihnen ausgewählten VLANs in demselben Pod befinden. ESXi-Server können nicht in VLANs mit unterschiedlichen Pods bereitgestellt werden.
{:important}

### DNS-Konfiguration
{: #vc_nsx-t_orderinginstance-dns-config}

Wählen Sie die Konfiguration für DNS (Domain Name System) für Ihre Instanz aus:

* **Einzelne öffentliche Windows-VSI für Active Directory/DNS**: Eine einzelne Serverinstanz (VSI) von Microsoft Windows Server für Microsoft Active Directory (AD), die als DNS für die Instanz dient, auf der die Hosts und VMs registriert sind, wird bereitgestellt und kann zur Suche verwendet werden. Diese Option wurde standardmäßig für Instanzen von V1.9 und höher bereitgestellt.
* **Zwei hoch verfügbare dedizierte Windows-Server-VMs auf dem Management-Cluster**: Es werden zwei Microsoft Windows-VMs bereitgestellt, die den Datenschutz und die Leistungsfähigkeit verbessern.

Sie müssen zwei Lizenzen für Microsoft Windows Server 2012 R2 bereitstellen, wenn Sie Ihre Instanz für die Verwendung der beiden Microsoft Windows-VMs konfigurieren. Verwenden Sie die Lizenz für Microsoft Windows Server 2012 R2 Standard Edition und/oder die Lizenz für Microsoft Windows Server 2012 R2 Datacenter Edition.
{:important}

Jede Lizenz kann nur einem einzigen physischen Server zugeordnet werden und deckt bis zu zwei physische Prozessoren ab. Mit einer Standard Edition-Lizenz können zwei virtualisierte Microsoft Windows-VMs pro 2-Prozessor-Server ausgeführt werden. Daher sind zwei Lizenzen erforderlich, weil zwei Microsoft Windows-VMs in zwei unterschiedlichen Hosts bereitgestellt werden.

Sie haben 30 Tage Zeit, um die VMs zu aktivieren.

Weitere Informationen zur Windows-Lizenzierung finden Sie auf der Seite mit der [Dokumentation zu Windows Server 2012 R2](https://www.microsoft.com/en-us/licensing/product-licensing/windows-server-2012-r2.aspx#tab=2).

## Bestellübersicht
{: #vc_nsx-t_orderinginstance-order-summary}

Auf Basis der für die Instanz ausgewählten Konfiguration werden die geschätzten Kosten sofort generiert und im rechten Fenster im Abschnitt **Bestellübersicht** angezeigt. Klicken Sie unten im rechten Fenster auf **Preisdetails**, um ein PDF-Dokument zu generieren, das die Kostenschätzungsdetails enthält.

## Vorgehensweise zum Bestellen von vCenter Server-Instanzen
{: #vc_nsx-t_orderinginstance-procedure}

1. Klicken Sie im {{site.data.keyword.cloud_notm}}-Katalog im linken Navigationsfenster auf **VMware** und klicken Sie anschließend im Abschnitt **Virtuelle Rechenzentren** auf **vCenter Server**.
2. Klicken Sie auf der Seite **VMware vCenter Server on IBM Cloud** auf die Karte **vCenter Server** und dann auf **Erstellen**.
3. Geben Sie auf der Seite **vCenter Server** den Instanznamen ein.
4. Wählen Sie den Instanztyp aus:
   * Klicken Sie auf **Primäre Instanz**, um eine einzelne Instanz in der Umgebung bereitzustellen oder um die erste Instanz in einer Topologie mit mehreren Standorten bereitzustellen.
   * Klicken Sie auf **Sekundäre Instanz**, um die Instanz mit einer vorhandenen (primären) Instanz in der Umgebung zu verbinden, um eine hohe Verfügbarkeit zu erreichen, und führen Sie dann die folgenden Schritte aus:
     1. Wählen Sie die primäre Instanz aus, mit der die sekundäre Instanz verbunden werden soll.
     2. Geben Sie für primäre Instanzen ab Version 2.8 das Administratorkennwort für vCenter Server in der primären Instanz ein.
     3. Geben Sie für primäre Instanzen der Version 2.5, 2.6 oder 2.7 das PSC-Administratorkennwort in der primären Instanz ein.
     4. Überprüfen Sie für primäre Instanzen bis Version 2.4, ob der vorgegebene Wert für das PSC-Administratorkennwort der primären Instanz korrekt ist.
6. Geben Sie die Lizenzeinstellungen für die Instanzkomponenten ein.
   *  Zur Verwendung der von IBM bereitgestellten Lizenzen müssen Sie **In Kauf einbeziehen** und bei Bedarf die Lizenzedition auswählen.
   *  Zur Verwendung einer eigenen Lizenz müssen Sie **Lizenz selbst bereitstellen** auswählen und den Lizenzschlüssel eingeben.
7. Geben Sie die Bare Metal Server-Einstellungen an.
    1. Wählen Sie das {{site.data.keyword.CloudDataCent_notm}} als Host für die Instanz aus.
    2. Wählen Sie die Bare-Metal-Serverkonfiguration aus und geben Sie anschließend das CPU-Modell und die RAM-Größe an.
    3. Geben Sie die Anzahl der {{site.data.keyword.baremetal_short}}-Instanzen an. Wenn vSAN als Speicherlösung verwendet werden soll, sind mindestens vier {{site.data.keyword.baremetal_short}}-Instanzen erforderlich.  
8. Führen Sie die Speicherkonfiguration durch.
  * Wenn Sie **vSAN-Speicher** auswählen, geben Sie die Plattentypen für die Kapazitäts- und Cacheplatten, die Anzahl der Platten und die vSAN-Lizenzedition an. Falls Sie mehr Speicher benötigen, müssen Sie das Feld für **Hohe Leistung mit Intel Optane** auswählen.
  * Wenn Sie **NFS-Speicher** auswählen und für alle gemeinsam genutzten Dateiressourcen dieselben Einstellungen konfigurieren möchten, geben Sie die **Anzahl der gemeinsam genutzten Ressourcen**, die **Leistung**und die **Größe (GB)** an.
  * Wenn Sie **NFS-Speicher** auswählen und alle gemeinsam genutzten Dateiressourcen einzeln hinzufügen und konfigurieren möchten, wählen Sie **Gemeinsam genutzte Ressourcen einzeln konfigurieren** aus. Klicken Sie anschließend auf das Symbol **+** neben der Bezeichnung **Gemeinsam genutzten Speicher hinzufügen** und wählen Sie für jede Dateifreigabe die Optionen **Leistung** und **Größe (GB)** aus. Sie müssen mindestens eine gemeinsam genutzte Dateiressource auswählen.
9. Geben Sie die Netzschnittstelleneinstellungen an.
   1. Geben Sie das Hostnamenspräfix, die Unterdomänenbezeichnung und den Rootdomänennamen ein. Für eine sekundäre Instanz wird der Domänenname automatisch ergänzt.
   2. Wählen Sie die Netzeinstellung für entweder **Öffentliches und privates Netz** oder **Nur privates Netz** aus.
   3. Wählen Sie die VLAN-Einstellungen aus:
      * Falls Sie neue öffentliche und private VLANs bestellen wollen, klicken Sie auf **Neue VLANs bestellen**.
      * Wenn Sie die vorhandenen öffentlichen und privaten VLANs wiederverwenden möchten, sofern diese verfügbar sind, dann klicken Sie auf **Vorhandene VLANs auswählen** und geben Sie die VLANs und Teilnetze an.
   4. Geben Sie die DNS-Konfiguration an.

11. Überprüfen Sie im Fenster **Bestellübersicht** die Instanzkonfiguration, bevor Sie die Bestellung aufgeben.
   1. Überprüfen Sie die Einstellungen für die Instanz.
   2. Überprüfen Sie die geschätzten Kosten der Instanz. Klicken Sie auf **Preisdetails**, um eine PDF-Datei mit der Zusammenfassung zu generieren. Ihre Bestellübersicht können Sie speichern oder drucken, indem Sie rechts oben im PDF-Fenster auf das Symbol **Drucken** bzw. **Herunterladen** klicken.
   3. Klicken Sie auf den Link bzw. die Links für die Bedingungen, die für Ihre Bestellung gelten, und vergewissern Sie sich, dass Sie mit diesen Bedingungen einverstanden sind, bevor Sie die Instanz bestellen.
   4. Klicken Sie auf **Bereitstellung**.

## Ergebnisse nach dem Bestellen von vCenter Server with NSX-T-Instanzen
{: #vc_nsx-t_orderinginstance-results}

Die Bereitstellung der Instanz wird automatisch gestartet. Sie erhalten eine Bestätigung, dass die Bestellung bearbeitet wird, und Sie können den Status der Bereitstellung prüfen, indem Sie die Instanzdetails anzeigen.

Nachdem die Instanz erfolgreich bereitgestellt wurde, sind die Komponenten, die unter [Technische Spezifikationen für vCenter Server with NSX-T-Instanzen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_overview-specs) beschrieben sind, auf Ihrer virtuellen VMware-Plattform installiert. Die von Ihnen bestellten ESXi-Server werden standardmäßig als **cluster1** gruppiert.

Sobald die Instanz einsatzbereit ist, ändert sich der Status der Instanz in **Bereit** und Sie empfangen per E-Mail eine Benachrichtigung.

Wenn Sie eine sekundäre Instanz bestellen, kann VMware vSphere Web Client für die primäre Instanz (mit der sekundären Instanz verknüpft) erneut gestartet werden, nachdem die Bestellung der sekundären Instanz abgeschlossen ist.

## Nächste Schritte
{: #vc_nsx-t_orderinginstance-next}

Sie können nun die bestellte vCenter Server with NSX-T-Instanz anzeigen und verwalten. Weitere Informationen zum Anzeigen der Instanz finden Sie unter [vCenter Server-Instanzen anzeigen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_viewinginstances).

Sie dürfen die {{site.data.keyword.vmwaresolutions_short}}-Komponenten, die in Ihrem {{site.data.keyword.cloud_notm}}-Konto erstellt werden, nur über die {{site.data.keyword.vmwaresolutions_short}}-Konsole und nicht im {{site.data.keyword.slportal}} oder über ein anderes Verfahren außerhalb der Konsole verwalten.
Wenn Sie diese Komponenten außerhalb der {{site.data.keyword.vmwaresolutions_short}}-Konsole ändern, werden die Änderungen nicht mit der Konsole synchronisiert.
{:important}

**VORSICHT:** Wenn Sie {{site.data.keyword.vmwaresolutions_short}}-Komponenten (die in Ihrem {{site.data.keyword.cloud_notm}}-Konto installiert wurden, als Sie die Instanz bestellt haben) außerhalb der {{site.data.keyword.vmwaresolutions_short}}-Konsole verwalten, kann dies zur Instabilität Ihrer Umgebung führen. Zu diesen Managementaktivitäten gehören:
*  Komponenten hinzufügen, ändern, zurückgeben oder entfernen
*  Instanzkapazität durch das Hinzufügen oder Entfernen von ESXi-Servern erweitern oder verringern
*  Komponenten ausschalten
*  Services erneut starten

   Ausgenommen von diesen Aktivitäten ist unter anderem das Management der gemeinsam genutzten Dateiressourcen für gemeinsam genutzten Speicher im {{site.data.keyword.slportal}}. Hierzu gehört das Bestellen, Löschen (mit möglicher Auswirkung auf angehängte Datenspeicher), Berechtigen und Anhängen von gemeinsam genutzten Dateiressourcen für gemeinsam genutzten Speicher.

## Zugehörige Links
{: #vc_nsx-t_orderinginstance-related}

* [Für ein {{site.data.keyword.cloud_notm}}-Konto registrieren](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-signing_softlayer_account)
* [vCenter Server-Instanzen anzeigen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_viewinginstances)
* [Konfiguration mit mehreren Standorten für vCenter Server-Instanzen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_multisite)
* [Cluster für vCenter Server with NSX-T-Instanzen hinzufügen, anzeigen und löschen](/docs/services/vmwaresolutions/vcenter?topic=vc_nsx-t_deletinginstance)
* [Kapazität für vCenter Server with NSX-T-Instanzen erweitern und verringern](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_addingremovingservers)
* [vCenter Server with NSX-T-Instanzen löschen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_deletinginstance)
