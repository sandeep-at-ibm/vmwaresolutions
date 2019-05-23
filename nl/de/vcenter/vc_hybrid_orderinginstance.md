---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-25"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter Server with Hybridity Bundle-Instanzen bestellen
{: #vc_hybrid_orderinginstance}

Um eine flexible und anpassbare virtualisierte VMware-Plattform bereitzustellen, die Ihren Workloadbedarf optimal erfüllt, bestellen Sie eine VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle-Instanz. Ihre Bestellung der vCenter Server with Hybridity Bundle-Instanz beinhaltet die Lizenzierung von VMware Hybrid Cloud Extension (HCX) und berechtigt Sie zur Verwendung des Service "VMware HCX on {{site.data.keyword.cloud_notm}}". Sie können auch Services hinzufügen, wie zum Beispiel [Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr) für die Disaster-Recovery.

## Voraussetzungen für die Bestellung von vCenter Server with Hybridity Bundle-Instanzen
{: #vc_hybrid_orderinginstance-req}

Stellen Sie sicher, dass Sie die folgenden Tasks ausgeführt haben:
*  Sie haben die Berechtigungsnachweise für die {{site.data.keyword.cloud_notm}}-Infrastruktur auf der Seite **Einstellungen** konfiguriert. Weitere Informationen finden Sie unter [Benutzerkonten und Einstellungen verwalten](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount).
*  Sie haben die Informationen in [Voraussetzungen und Planung für vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_planning) gelesen.
* Sie haben das Instanz- und Domänennamensformat geprüft. Der Domänenname und die Unterdomänenbezeichnung werden verwendet, um den Benutzernamen und die Servernamen der Instanz zu generieren.

Tabelle 1. Wertformat für Instanz- und Domänennamen

| Name        | Wertformat      |
  |:------------- |:------------- |
  | Domänenname | `<root_domain>` |  
  | Anmeldebenutzername für vCenter Server | `<user_id>@<root_domain>` (Microsoft Active Directory-Benutzer) oder `administrator@vsphere.local` |
  | vCenter Server (mit integriertem PSC) FQDN | `vcenter-<subdomain_label>.<subdomain_label>.<root_domain>`. Die maximale Länge beträgt 50 Zeichen. |
  | SSO-Standortname | `<subdomain_label>` |
  | Vollständig qualifizierter Name des ESXi-Servers | `<host_prefix><n>.<subdomain_label>.<root_domain>`. Dabei ist `<n>` die Folgenummer des ESXi-Servers. Die maximale Länge beträgt 50 Zeichen. |

Nehmen Sie keine Änderungen an Werten vor, die während der Bestellung oder Bereitstellung der Instanz festgelegt werden. Dies kann dazu führen, dass Ihre Instanz unbrauchbar wird. Beispielsweise, wenn der öffentliche Netzbetrieb beendet wird, Server sowie virtuelle Serverinstanzen (VSIs) mitten in einer Bereitstellung hinter eine Vyatta-Einheit versetzt werden oder wenn die Virtual Server-Instanz für IBM CloudBuilder gestoppt oder gelöscht wird.
{:important}

## Systemeinstellungen
{: #vc_hybrid_orderinginstance-sys-settings}

Sie müssen die folgenden Systemeinstellungen angeben, wenn Sie eine vCenter Server with Hybridity Bundle-Instanz bestellen.

### Instanzname
{: #vc_hybrid_orderinginstance-inst-name}

Der Instanzname muss die folgenden Anforderungen erfüllen:
* Es sind nur alphanumerische Zeichen und Bindestriche (-) zulässig.
* Der Instanzname muss mit einem alphabetischen Zeichen beginnen und mit einem alphanumerischen Zeichen enden.
* Die maximale Länge des Instanznamens beträgt 10 Zeichen.
* Der Instanzname muss innerhalb Ihres Kontos eindeutig sein.

### VMware vSphere-Lizenzen
{: #vc_hybrid_orderinginstance-vsphere-license}

Wählen Sie aus, ob vSphere Enterprise Plus 6.7u1 oder vSphere Enterprise Plus 6.5u2 bestellt werden soll.

vSphere Enterprise Plus 6.7u1 ist nur für Broadwell und Skylake {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} verfügbar.
{:note}

### Primär oder sekundär
{: #vc_hybrid_orderinginstance-primary-secondary}

Wählen Sie aus, ob Sie eine neue primäre oder sekundäre Instanz für eine bereits vorhandene primäre Instanz bestellen wollen.

## Lizenzierungseinstellungen
{: #vc_hybrid_orderinginstance-licensing-settings}

In die Bestellung Ihrer vCenter Server with Hybridity Bundle-Instanz sind folgende VMware-Lizenzen eingeschlossen. Sie müssen die Edition der NSX-Lizenz und der vSAN-Lizenz angeben.

* vCenter Server 6.5
* vSphere Enterprise Plus 6.5 oder 6.7
* NSX Service Providers 6.4 (Advanced Edition oder Enterprise Edition)
* vSAN 6.6 (Advanced Edition oder Enterprise Edition)

### Achtung
{: #vc_hybrid_orderinginstance-attention}

* vCenter Server with Hybridity Bundle-Instanzen bieten keine BYOL-Unterstützung (BYOL = Bring Your Own License; Verwendung der eigenen Lizenz).
* Die mindestens erforderlichen Lizenzeditionen sind in der Benutzerschnittstelle angegeben. Falls unterschiedliche Komponenteneditionen unterstützt werden, können Sie die gewünschte Edition auswählen.

## Einstellungen für Bare Metal Server
{: #vc_hybrid_orderinginstance-bare-metal-settings}

Die Bare Metal-Einstellungen sind von Ihrer Auswahl von {{site.data.keyword.CloudDataCent_notm}} und der Konfiguration des Bare Metal Server abhängig.

Für den ersten Cluster und die nach der Bereitstellung verfügbaren Cluster für vSAN-Konfigurationen sind vier ESXi-Server erforderlich. Alle ESXi-Server nutzen dieselbe Konfiguration gemeinsam. Nach der Bereitstellung können Sie vier weitere Cluster hinzufügen.

### Standort des Rechenzentrums
{: #vc_hybrid_orderinginstance-dc-location}

Wählen Sie das {{site.data.keyword.CloudDataCent_notm}} aus, das als Host für die Instanz verwendet werden soll.

### Skylake
{: #vc_hybrid_orderinginstance-skylake}

Wenn Sie **Skylake** auswählen, dann können Sie die Kombination aus CPU und RAM für den Bare Metal Server entsprechend Ihren Anforderungen auswählen.

Tabelle 2. Optionen für Skylake {{site.data.keyword.baremetal_short}}

| CPU-Modelloptionen        | RAM-Optionen       |
|:------------- |:------------- |
| Dual Intel Xeon Silver 4110-Prozessor / 16 Kerne insgesamt, 2,1 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon Gold 5120-Prozessor / 28 Kerne insgesamt, 2,2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon Gold 6140-Prozessor / 36 Kerne insgesamt, 2,3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |

### Broadwell
{: #vc_hybrid_orderinginstance-broadwell}

Wenn Sie **Broadwell** auswählen, dann können Sie die Kombination aus CPU und RAM für den Bare Metal Server entsprechend Ihren Anforderungen auswählen.

Tabelle 3. Optionen für Broadwell {{site.data.keyword.baremetal_short}}

| CPU-Modelloptionen        | RAM-Optionen       |
|:------------- |:------------- |
| Quad Intel Xeon E7-4820 v4 / 40 Kerne insgesamt, 2,0 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |
| Quad Intel Xeon E7-4850 v4 / 64 Kerne insgesamt, 2,1 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |

### Bare Metal Server-Anzahl
{: #vc_hybrid_orderinginstance-bare-metal-number}

* Alle Server, die Sie bestellen, haben die gleiche Konfiguration.
* Sie können zwischen 4 und 20 Server bestellen.

## Speichereinstellungen
{: #vc_hybrid_orderinginstance-storage-settings}

VMware vSAN 6.6 ist Bestandteil der Bestellung Ihrer vCenter Server with Hybridity Bundle-Instanz. Geben Sie die folgenden vSAN-Optionen an:
* **Plattentyp und Größe für vSAN-Kapazitätsplatten**: Wählen Sie die für die Kapazitätsplatten benötigte Option aus.
* **Anzahl der vSAN-Kapazitätsplatten**: Geben Sie die Anzahl der hinzuzufügenden Kapazitätsplatten an.
* Wenn Sie über den Grenzwert von zehn Stück hinaus Kapazitätsplatten hinzufügen möchten, müssen Sie das Feld für **Hohe Leistung mit Intel Optane** auswählen. Diese Option stellt zwei zusätzliche Kapazitätsplattenpositionen für eine Gesamtzahl von 12 Kapazitätsplatten bereit und ist für Workloads nützlich, die eine geringere Latenzzeit und einen höheren Durchsatz an E/A-Operationen pro Sekunde erfordern.

  Die Option **Hohe Leistung mit Intel Optane** ist nur für die Skylake-CPU-Modelle verfügbar.
  {:note}

* Überprüfen Sie die Werte für **Plattentyp für vSAN-Cacheplatten** und **Anzahl der vSAN-Cacheplatten**. Diese Werte hängen davon ab, ob Sie das Feld **Hohe Leistung mit Intel Optane** ausgewählt haben.

## Netzschnittstelleneinstellungen
{: #vc_hybrid_orderinginstance-network-interface-settings}

Sie müssen die folgenden Netzschnittstelleneinstellungen angeben, wenn Sie eine vCenter Server with Hybridity Bundle-Instanz bestellen.

### Hostnamenspräfix
{: #vc_hybrid_orderinginstance-host-name-prefix}

  Das Hostnamenspräfix muss die folgenden Anforderungen erfüllen:
  *  Es sind nur alphanumerische Zeichen und Bindestriche (-) zulässig.
  *  Das Hostnamenspräfix muss mit einem alphanumerischen Zeichen beginnen und enden.
  *  Die maximale Länge des Hostnamenspräfix beträgt 10 Zeichen.

### Unterdomänenbezeichnung
{: #vc_hybrid_orderinginstance-subdomain-label}

Die Unterdomänenbezeichnung muss die folgenden Anforderungen erfüllen:
*  Es sind nur alphanumerische Zeichen und Bindestriche (-) zulässig.
*  Die Unterdomänenbezeichnung muss mit einem alphabetischen Zeichen beginnen und mit einem alphanumerischen Zeichen enden.
*  Die maximale Länge der Unterdomänenbezeichnung beträgt 10 Zeichen.
*  Die Unterdomänenbezeichnung muss innerhalb Ihres Kontos eindeutig sein.

### Domänenname
{: #vc_hybrid_orderinginstance-domain-name}

Der Rootdomänenname muss die folgenden Anforderungen erfüllen:
* Der Domänenname muss aus zwei oder mehr Zeichenfolgen bestehen, die jeweils durch einen Punkt (.) voneinander getrennt sind.
* Die erste Zeichenfolge muss mit einem alphabetischen Zeichen beginnen und mit einem alphanumerischen Zeichen enden.
* Alle Zeichenfolgen mit Ausnahme der letzten darf nur alphanumerische Zeichen und Gedankenstriche (-) enthalten.
* Die letzte Zeichenfolge darf nur Buchstaben enthalten.
* Die Länge der letzten Zeichenfolge muss zwischen 2 und 24 Zeichen betragen.

Die maximale Länge des vollständig qualifizierten Domänennamens für Hosts und VMs beträgt 50 Zeichen. Domänennamen müssen diese maximale Länge zulassen.
{:note}

### Öffentliches oder privates Netz
{: #vc_hybrid_orderinginstance-public-private-network}

Die Einstellungen für die Aktivierung der Netzschnittstellenkarte (NIC - Network Interface Card) basieren darauf, ob Sie **Öffentliches und privates Netz** oder **Nur privates Netz** auswählen.

Wenn Sie die Option **Nur privates Netz** auswählen, gilt Folgendes:
* VMware NSX Edge Services Gateways (ESG) werden nicht bereitgestellt (weder die ESG für Management-Services noch die vom Kunden verwaltete ESG).
* Die folgenden Add-on-Services, für die öffentliche NICs erforderlich sind, sind nicht verfügbar:
  * F5 on {{site.data.keyword.cloud_notm}}
  * FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}
  * FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}

### Neue VLANs bestellen
{: #vc_hybrid_orderinginstance-new-vlans}

Wählen Sie **Neue VLANs bestellen** aus, um ein neues öffentliches VLAN und zwei neue private VLANs zu bestellen.

Für Ihre Instanzbestellung sind 1 öffentliches VLAN und 2 private VLANs erforderlich. Die zwei privaten VLANs werden in jedem Bare Metal Server zusammengelegt.

### Vorhandene VLANs auswählen
{: #vc_hybrid_orderinginstance-existing-vlans}

Abhängig vom ausgewählten {{site.data.keyword.CloudDataCent_notm}} sind möglicherweise vorhandene öffentliche und private VLANs verfügbar.

Für Ihre Instanzbestellung sind 1 öffentliches VLAN und 2 private VLANs erforderlich. Die zwei privaten VLANs werden in jedem Bare Metal Server zusammengelegt.

Wählen Sie **Vorhandene VLANs auswählen** aus, um vorhandene öffentliche und private VLANs wiederzuverwenden und eine Auswahl unter den verfügbaren VLANs und Teilnetzen zu treffen.

* Stellen Sie sicher, dass die Firewallkonfiguration bei den ausgewählten VLANs den Managementdatenverkehr nicht sperrt.
* Stellen Sie sicher, dass sich alle von Ihnen ausgewählten VLANs in demselben Pod befinden, da ESXi-Server nicht in VLANs mit heterogenen Pods bereitgestellt werden können.
{:important}

### DNS-Konfiguration
{: #vc_hybrid_orderinginstance-dns-config}

Wählen Sie die Konfiguration für DNS (Domain Name System) für Ihre Instanz aus:

* **Einzelne öffentliche Windows-VSI für Active Directory/DNS**: Eine einzelne Serverinstanz (VSI) von Microsoft Windows Server für Microsoft Active Directory (AD), die als DNS für die Instanz dient, auf der die Hosts und VMs registriert sind, wird bereitgestellt und kann zur Suche verwendet werden.
* **Zwei hoch verfügbare dedizierte Windows-Server-VMs auf dem Management-Cluster**: Es werden zwei Microsoft Windows-VMs bereitgestellt, die den Datenschutz und die Leistungsfähigkeit verbessern.

Sie müssen zwei Lizenzen für Microsoft Windows Server 2016 bereitstellen, wenn Sie Ihre Instanz für die Verwendung der beiden Microsoft Windows-VMs konfigurieren. Verwenden Sie die Lizenz für Microsoft Windows Server 2016 Standard Edition und/oder die Lizenz für Microsoft Windows Server 2016 Datacenter Edition.
{:important}

Jede Lizenz kann nur einem einzigen physischen Server zugeordnet werden und deckt bis zu zwei physische Prozessoren ab. Mit einer Standard Edition-Lizenz können zwei virtualisierte Microsoft Windows-VMs pro 2-Prozessor-Server ausgeführt werden. Daher sind zwei Lizenzen erforderlich, weil zwei Microsoft Windows-VMs in zwei unterschiedlichen Hosts bereitgestellt werden.

Sie haben 30 Tage Zeit, um die VMs zu aktivieren.

Weitere Informationen zur Bestellung von Lizenzen für Windows Server 2016 finden Sie unter [Erste Schritte mit Windows Server 2016](https://docs.microsoft.com/en-us/windows-server/get-started/server-basics){:new_window}.

## Serviceeinstellungen
{: #vc_hybrid_orderinginstance-addon-services}

Beim Bestellen einer vCenter Server with Hybridity Bundle-Instanz können Sie auch zusätzliche Services bestellen. Weitere Informationen zu den Services finden Sie unter [Verfügbare Services für vCenter Server with Hybridity Bundle-Instanzen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices#available-services-for-vcenter-server-with-hybridity-bundle-instances).

## Bestellübersicht
{: #vc_hybrid_orderinginstance-order-summary}

Auf Basis der für die Instanz und die Add-on-Services ausgewählten Konfiguration werden die geschätzten Kosten sofort generiert und im rechten Fenster im Abschnitt **Bestellübersicht** angezeigt. Klicken Sie unten im rechten Fenster auf **Preisdetails**, um ein PDF-Dokument zu generieren, das die Kostenschätzungsdetails enthält.

## Vorgehensweise zum Bestellen von vCenter Server with Hybridity Bundle-Instanzen
{: #vc_hybrid_orderinginstance-procedure}

1. Klicken Sie im {{site.data.keyword.cloud_notm}}-Katalog im linken Navigationsfenster auf **VMware** und klicken Sie anschließend im Abschnitt **Virtuelle Rechenzentren** auf **vCenter Server**.
2. Klicken Sie auf der Seite **VMware vCenter Server on IBM Cloud** auf die Karte **vCenter Server with Hybridity Bundle** und dann auf **Erstellen**.
3. Geben Sie auf der Seite **vCenter Server** den Instanznamen ein.
5. Wählen Sie die vSphere-Version aus.
4. Wählen Sie den Instanztyp aus:
   * Klicken Sie auf **Primäre Instanz**, um eine einzelne Instanz in der Umgebung bereitzustellen oder um die erste Instanz in einer Topologie mit mehreren Standorten bereitzustellen.
   * Klicken Sie auf **Sekundäre Instanz**, um die Instanz mit einer vorhandenen (primären) Instanz in der Umgebung zu verbinden, um eine hohe Verfügbarkeit zu erreichen, und führen Sie dann die folgenden Schritte aus:
     1. Wählen Sie die primäre Instanz aus, mit der die sekundäre Instanz verbunden werden soll.
     2. Geben Sie für primäre Instanzen ab Version 2.8 das Administratorkennwort für vCenter Server in der primären Instanz ein.
     3. Geben Sie für primäre Instanzen ab Version 2.7 das PSC-Administratorkennwort in der primären Instanz ein.
6. Wählen Sie die NSX-Lizenzedition und die vSAN-Lizenzedition aus.
7. Geben Sie die Bare Metal Server-Einstellungen an.
  1. Wählen Sie das {{site.data.keyword.CloudDataCent_notm}} als Host für die Instanz aus.
  2. Wählen Sie das CPU-Modell **Skylake** oder **Broadwell** und die Menge des **RAM** aus.
8. Führen Sie die Speicherkonfiguration durch. Geben Sie die Plattentypen für die Kapazitäts- und Cacheplatten sowie die Anzahl der Platten an. Falls Sie mehr Speicher benötigen, müssen Sie das Feld für **Hohe Leistung mit Intel Optane** auswählen.
9. Führen Sie die Netzschnittstellenkonfiguration durch.
  1. Geben Sie das Hostnamenspräfix für die bereitgestellte Instanz, die Unterdomänenbezeichnung und den Rootdomänennamen ein.
  2. Wählen Sie die Netzeinstellung für entweder **Öffentliches und privates Netz** oder **Nur privates Netz** aus.
  3. Wählen Sie die VLAN-Konfiguration aus.
     *  Falls Sie neue öffentliche und private VLANs bestellen wollen, klicken Sie auf **Neue VLANs bestellen**.
     *  Wenn Sie die vorhandenen öffentlichen und privaten VLANs wiederverwenden möchten, sofern diese verfügbar sind, dann klicken Sie auf **Vorhandene VLANs auswählen** und wählen Sie anschließend das öffentliche VLAN, das primäre Teilnetz, das private VLAN, das primäre private Teilnetz und das sekundäre private VLAN aus.
  4. Wählen Sie die DNS-Konfiguration aus.
10. Führen Sie die Konfiguration für den enthaltenen Service "HCX on {{site.data.keyword.cloud_notm}}" aus. Weitere Informationen zum Angeben von Einstellungen für den Service finden Sie im Abschnitt _VMware HCX on IBM Cloud - Konfiguration_ in [VMware HCX on IBM Cloud bestellen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_ordering#vmware-hcx-on-ibm-cloud-configuration).
11. Wählen Sie die Add-on-Services aus, die in der Instanz bereitgestellt werden sollen, indem Sie auf die entsprechende Servicekarte klicken. Wenn ein Service konfiguriert werden muss, dann geben Sie die servicespezifischen Einstellungen an und klicken Sie dann auf der Karte auf **Service hinzufügen**.  
Weitere Informationen zum Angeben von Einstellungen für einen Service finden Sie im entsprechenden Abschnitt zum Bestellen von Services.

12. Überprüfen Sie im Fenster **Bestellübersicht** die Instanzkonfiguration, bevor Sie die Bestellung aufgeben.
   1. Überprüfen Sie die Einstellungen für die Instanz.
   2. Überprüfen Sie die geschätzten Kosten der Instanz. Klicken Sie auf **Preisdetails**, um eine PDF-Datei mit der Zusammenfassung zu generieren. Ihre Bestellübersicht können Sie speichern oder drucken, indem Sie rechts oben im PDF-Fenster auf das Symbol **Drucken** bzw. **Herunterladen** klicken.
   3. Klicken Sie auf den Link bzw. die Links für die Bedingungen, die für Ihre Bestellung gelten, und vergewissern Sie sich, dass Sie mit diesen Bedingungen einverstanden sind, bevor Sie die Instanz bestellen.
   4. Klicken Sie auf **Bereitstellung**.

## Ergebnisse
{: #vc_hybrid_orderinginstance-results}

Die Bereitstellung der Instanz wird automatisch gestartet. Sie erhalten eine Bestätigung, dass die Bestellung bearbeitet wird, und Sie können den Status der Bereitstellung prüfen, indem Sie die Instanzdetails anzeigen.

Nachdem die Instanz erfolgreich bereitgestellt wurde, sind die Komponenten, die unter [Technische Spezifikationen für vCenter Server with Hybridity Bundle-Instanzen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_overview#specs) beschrieben sind, auf Ihrer virtuellen VMware-Plattform installiert. Die von Ihnen bestellten ESXi-Server werden standardmäßig als **cluster1** gruppiert. Wenn Sie Add-on-Services bestellt haben, wird die Bereitstellung der Services gestartet, nachdem Ihre Bestellung abgeschlossen ist.

Sobald die Instanz einsatzbereit ist, ändert sich der Status der Instanz in **Bereit** und Sie empfangen per E-Mail eine Benachrichtigung.

Wenn Sie eine sekundäre Instanz bestellen, kann VMware vSphere Web Client für die primäre Instanz (mit der sekundären Instanz verknüpft) erneut gestartet werden, nachdem die Bestellung der sekundären Instanz abgeschlossen ist.

## Nächste Schritte
{: #vc_hybrid_orderinginstance-next}

Sie können nun die bestellte vCenter Server with Hybridity Bundle-Instanz anzeigen und verwalten.

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
{: #vc_hybrid_orderinginstance-related}

* [Für ein {{site.data.keyword.cloud_notm}}-Konto registrieren](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-signing_softlayer_account)
* [vCenter Server with Hybridity Bundle-Instanzen anzeigen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_viewinginstances)
* [Konfiguration mit mehreren Standorten für vCenter Server with Hybridity Bundle-Instanzen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_multisite)
* [Cluster für vCenter Server with Hybridity Bundle-Instanzen hinzufügen und anzeigen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingviewingclusters)
* [Kapazität für vCenter Server with Hybridity Bundle-Instanzen erweitern und verringern](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservers)
* [Services für vCenter Server with Hybridity Bundle-Instanzen bestellen, anzeigen und entfernen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)
* [vCenter Server with Hybridity Bundle-Instanzen löschen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_deletinginstance)
