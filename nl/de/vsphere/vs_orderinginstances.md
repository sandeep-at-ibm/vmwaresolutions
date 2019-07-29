---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-18"

keywords: vSphere order cluster, order vSphere, order vSphere cluster

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Neue vSphere-Cluster bestellen
{: #vs_orderinginstances}

Zur Bereitstellung einer hochanpassungsfähigen virtualisierten VMware-Plattform müssen Sie einen VMware vSphere on {{site.data.keyword.cloud}}-Cluster bestellen. In diesem Abschnitt ist beschrieben, wie Sie einen neuen vSphere-Cluster definieren.

In dieser Prozedur werden Sie durch die Auswahl von VMware-Komponenten, {{site.data.keyword.cloud_notm}} Bare Metal Server-Einstellungen, Speichereinstellungen und Optionen für den Netzbetrieb geführt, um einen neuen Cluster zu erstellen. Nachdem Sie die Bestellung aufgegeben haben, wird die Clusterkonfiguration gespeichert, damit Sie den Cluster später ausgehend von dieser Konfiguration wie benötigt skalieren können. Nach der Bestellung können Sie den VMware-Cluster manuell gemäß Ihren Anforderungen konfigurieren.

## Voraussetzungen
{: #vs_orderinginstances-req}

Stellen Sie sicher, dass Sie die folgenden Tasks ausgeführt haben:
*  Sie haben die Berechtigungsnachweise für die {{site.data.keyword.cloud_notm}}-Infrastruktur auf der Seite **Einstellungen** konfiguriert. Weitere Informationen finden Sie unter [Benutzerkonten und Einstellungen verwalten](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount).
*  Sie haben sich mit den Voraussetzungen und Hinweisen im Abschnitt [Voraussetzungen und Planung für vSphere-Cluster](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_planning) vertraut gemacht.

## Systemeinstellungen
{: #vs_orderinginstances-sys-settings}

Sie müssen die folgenden Systemeinstellungen angeben, wenn Sie einen neuen vSphere-Cluster bestellen.

### Clustername
{: #vs_orderinginstances-cluster-name}

Der Clustername muss innerhalb Ihres Kontos eindeutig sein.

## Lizenzierungseinstellungen
{: #vs_orderinginstances-licensing-settings}

Wählen Sie die VMware-Komponenten aus, die mit Ihrem Cluster bestellt werden sollen, und geben Sie die Lizenzierungsoption für die Komponenten an.

### Komponentenpakete für IBM Business Partner-Benutzer
{: #vs_orderinginstances-component-bundles-for-bp-users}

IBM Business Partner-Benutzer können bei der Bestellung eines neuen vSphere-Clusters ein Komponentenlizenzpaket auswählen. Folgende Pakete sind verfügbar:

Table 1. VSphere-Cluster-Komponentenpakete für IBM Business Partner

| Paket | Komponenten                   |
|:------------------------- |:----------------------- |
| Standard with Management | vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, vRealize Operations Enterprise |
| Advanced                 | vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, vCloud Director, NSX Base |
| Advanced with Networking | vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, NSX Advanced |
| Advanced with Networking and Management | vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, vRealize Operations Enterprise, vCloud Director, NSX Enterprise |

Die folgenden VMware-Komponenten können Sie ebenfalls in Ihre Bestellung einbeziehen:
* VMware vSAN
* VMware Site Recovery Manager
* VMware vRealize Automation Enterprise

Die BYOL-Option (Bring Your Own License) steht für IBM Business Partner-Benutzer nicht zur Verfügung.
{:note}

### Einzelne Komponenten für Benutzer ohne Business Partner-Status
{: #vs_orderinginstances-individual-components-for-non-bp-users}

Wenn Sie nicht Den IBM Business Partner-Status haben, können Sie für Ihren vSphere Cluster folgende Komponenten auswählen:
* VMware vSphere Enterprise Plus 6.7 U1 oder 6.5 U2
* VMware vCenter Server
* VMware NSX
* VMware vSAN
* VMware Site Recovery Manager
* VMware vRealize Automation Enterprise
* VMware vRealize Operation Enterprise
* VMware vRealize Log Insight

Die Komponente "VMware vSAN" ist nicht verfügbar, wenn Sie VMware vSphere Enterprise Plus 6.0 bestellen. Falls Sie Ihre eigene Lizenz für VMware vSphere Enterprise Plus 6.0 verwenden wollen, wird in Ihrem Namen ein Ticket der {{site.data.keyword.cloud_notm}}-Infrastruktur geöffnet. Mit dem Ticket wird die Ersetzung der vSphere-Lizenzen für die bestellten {{site.data.keyword.baremetal_short}}-Instanzen durch die von Ihnen bereitgestellten Lizenzen angefordert.
{:note}

### Lizenzierungsoptionen
{: #vs_orderinginstances-licensing-options}

Zur Lizenzierung der ausgewählten VMware-Komponenten gibt es die folgenden Optionen:
* **Lizenz in Kauf einbeziehen**: In diesem Fall wird eine neue Lizenz für die VMware-Komponente in Ihrem Namen erworben. Es wird eine kombinierte VMware-Lizenz generiert, die mit der Clustergröße der Bestellung übereinstimmt.
* **Lizenz selbst bereitstellen**: In diesem Fall verwenden Sie Ihre eigene Lizenz für die VMware-Komponente.

Falls Sie den Kauf einer Lizenz auswählen (vSphere Enterprise Plus und vCenter Server ausgenommen) und Sie mehrere ESXi-Server bestellen, wird automatisch in Ihrem Namen ein {{site.data.keyword.cloud_notm}}-Ticket geöffnet, um die Lizenzschlüssel zu kombinieren. Sie müssen sich selbst um die weitere Verfolgung des Tickets kümmern, damit sichergestellt ist, dass Sie ausschließlich die vom DevOps-Team generierten Lizenzschlüssel verwenden.

Die Verwendung von einzelnen Lizenzschlüsseln zusammen mit den kombinierten Lizenzschlüsseln erfüllt nicht die Zahlungsvoraussetzungen für die Lizenzen, die Sie benötigen.
{:important}

## Einstellungen für Bare Metal Server
{: #vs_orderinginstances-bare-metal-settings}

### Standort des Rechenzentrums
{: #vs_orderinginstances-dc-location}

Wählen Sie das {{site.data.keyword.CloudDataCent_notm}} aus, das als Host für den Cluster verwendet werden soll.

**Hinweise:**
* Falls Sie eine vSAN-Komponente auswählen, wird die Liste der Standorte nach SSD-Verfügbarkeit gefiltert.
* Broadwell-Bare-Metal-Server sind für den Rechenzentrumstandort **FRA05-Frankfurt** nicht verfügbar.
* SAP-zertifizierte und Broadwell-Bare-Metal-Server sind für den Rechenzentrumstandort **LON05 - London** nicht verfügbar.

### Skylake
{: #vs_orderinginstances-skylake}

Wenn Sie **Skylake** auswählen, dann können Sie die Kombination aus CPU und RAM für den Bare Metal Server entsprechend Ihren Anforderungen auswählen. Welche Optionen verfügbar sind, ist davon abhängig, ob Sie die Komponente "VMware vSAN" ausgewählt haben.

Tabelle 2. Optionen für Skylake {{site.data.keyword.baremetal_short}}

| CPU-Modelloptionen        | RAM-Optionen       |
|:------------- |:------------- |
| Dual Intel Xeon Silver 4110-Prozessor / 16 Kerne insgesamt, 2,1 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon Gold 5120-Prozessor / 28 Kerne insgesamt, 2,2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon Gold 6140-Prozessor / 36 Kerne insgesamt, 2,3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |

### SAP-zertifiziert
{: #vs_orderinginstances-sap}

Die Registerkarte **SAP-zertifiziert** ist nicht verfügbar, wenn Sie zuvor VMware vSAN ausgewählt haben. Wenn Sie **SAP-zertifiziert** auswählen, dann können Sie die CPU- oder RAM-Einstellungen nicht ändern.

Wählen Sie gemäß Ihren Anforderungen eine Bare Metal Server-Konfiguration aus:
  * Dual Intel Xeon Gold 6140-Prozessor / 36 Kerne insgesamt, 2,3 GHzDual / 192 GB RAM
  * Dual Intel Xeon Gold 6140-Prozessor / 36 Kerne insgesamt, 2,3 GHzDual / 384 GB RAM
  * Dual Intel Xeon Gold 6140-Prozessor / 36 Kerne insgesamt, 2,3 GHzDual / 768 GB RAM
  * Dual Intel Xeon E5-2690 v4-Prozessor / 28 Kerne insgesamt, 2,6 GHz / 512 GB RAM
  * Quad Intel Xeon E7-8890 v4-Prozessor / 96 Kerne insgesamt, 2,2 GHz / 1024 GB RAM
  * Quad Intel Xeon E7-8890 v4-Prozessor / 96 Kerne insgesamt, 2,2 GHz / 2048 GB RAM
  * Quad Intel Xeon E7-8890 v4-Prozessor / 96 Kerne insgesamt, 2,2 GHz / 4096 GB RAM

### Broadwell
{: #vs_orderinginstances-broadwell}

Wenn Sie **Broadwell** auswählen, dann können Sie die Kombination aus CPU und RAM für den Bare Metal Server entsprechend Ihren Anforderungen auswählen. Welche Optionen verfügbar sind, ist davon abhängig, ob Sie die Komponente "VMware vSAN" ausgewählt haben.

Tabelle 3. Optionen für Broadwell {{site.data.keyword.baremetal_short}}

| CPU-Modelloptionen        | RAM-Optionen       |
|:------------- |:------------- |
| Quad Intel Xeon E7-4820 v4 / 40 Kerne insgesamt, 2,0 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |
| Quad Intel Xeon E7-4850 v4 / 64 Kerne insgesamt, 2,1 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |

### Bare Metal Server-Anzahl
{: #vs_orderinginstances-bare-metal-number}

Die Anzahl der ESXi-Server, die Sie zum vSphere-Cluster hinzufügen wollen. Alle ESXi-Server verfügen über dieselbe Konfiguration.
* Falls Sie die Komponente "VMware NSX" ausgewählt haben, sind mindestens drei Server erforderlich.
* Falls Sie die Komponente "VMware vSAN" ausgewählt haben, sind mindestens vier Server erforderlich.

## Speichereinstellungen
{: #vs_orderinginstances-storage-settings}

Bei Bestellungen ohne vSAN werden ESXi-Server mit einem Chassis für zwölf Platten und zwei Platten für das ESXi-Betriebssystem (OS) bestellt.

Bei Bestellungen mit vSAN werden ESXi-Server mit einem Chassis für zwölf Platten und vier Platten bestellt (zwei Platten für das ESXi-Betriebssystem und zwei für das Caching reservierte Platten). Diese Einstellungen sind standardmäßig konfiguriert und können nicht geändert werden. Sie können weitere Kapazitätsplatten bestellen, indem Sie **Plattentyp und -größe für vSAN-Kapazitätsplatten** und **Anzahl der vSAN-Kapazitätsplatten** auswählen.

Wenn Sie für den Cluster die Komponente "VMware vSAN" ausgewählt haben, müssen Sie folgende Einstellungen angeben.
* **Plattentyp und Größe für vSAN-Kapazitätsplatten**: Wählen Sie die für die Kapazitätsplatten benötigte Option aus.
* **Anzahl der vSAN-Kapazitätsplatten**: Geben Sie die Anzahl der hinzuzufügenden Kapazitätsplatten an.
* Wenn Sie über den Grenzwert von acht Stück hinaus Kapazitätsplatten hinzufügen möchten, müssen Sie das Feld für **Hohe Leistung mit Intel Optane** auswählen. Diese Option stellt zwei zusätzliche Kapazitätsplattenpositionen für eine Gesamtzahl von 10 Kapazitätsplatten bereit und ist für Workloads nützlich, die eine geringere Latenzzeit und einen höheren Durchsatz an E/A-Operationen pro Sekunde erfordern.

  Die Option **Hohe Leistung mit Intel Optane** ist nur für die Skylake-CPU-Modelle verfügbar.
  {:note}

* Überprüfen Sie die Werte für **Plattentyp für vSAN-Cacheplatten** und **Anzahl der vSAN-Cacheplatten**. Diese Werte hängen davon ab, ob Sie das Feld **Hohe Leistung mit Intel Optane** ausgewählt haben.

## Netzschnittstelleneinstellungen
{: #vs_orderinginstances-network-interface-settings}

Sie müssen die folgenden Netzschnittstelleneinstellungen angeben, wenn Sie einen neuen vSphere-Cluster bestellen.

### Hostnamenspräfix
{: #vs_orderinginstances-host-name-prefix}

Der Hostname wird für alle Bare Metal Server-Bestellungen verwendet. Es wird empfohlen, den Hostnamen für alle Management-VMs wie vCenter Server oder NSX zu verwenden.

Das Hostnamenspräfix muss die folgenden Anforderungen erfüllen:
* Der Name muss mit einem alphanumerischen Zeichen beginnen und enden.
* Es sind nur alphanumerische Zeichen und Bindestriche (-) zulässig.
* Die maximale Länge beträgt 10 Zeichen.

### Unterdomänenbezeichnung
{: #vs_orderinginstances-subdomain-label}

Die Unterdomänenbezeichnung muss die folgenden Anforderungen erfüllen:
*  Es sind nur alphanumerische Zeichen und Bindestriche (-) zulässig.
*  Die Unterdomänenbezeichnung muss mit einem alphanumerischen Zeichen beginnen und enden.
*  Die maximale Länge der Unterdomänenbezeichnung beträgt 10 Zeichen.

### Domänenname
{: #vs_orderinginstances-domain-name}

Der Domänenname wird für alle {{site.data.keyword.baremetal_short}}-Instanzen verwendet und muss die folgenden Anforderungen erfüllen:
* Der Name muss aus zwei oder mehr Zeichenfolgen bestehen, die jeweils durch einen Punkt (.) voneinander getrennt sind.
* Es sind nur alphanumerische Zeichen und Bindestriche (-) zulässig.
* Jede Zeichenfolge muss mit einem alphabetischen Zeichen beginnen und mit einem alphanumerischen Zeichen enden. Außerdem darf die letzte Zeichenfolge nur Buchstaben enthalten.
* Die Länge der letzten Zeichenfolge muss zwischen 2 und 24 Zeichen betragen.
* Die Länge der anderen Zeichenfolgen muss zwischen 1 und 63 Zeichen liegen.
* Die maximale Länge des Domänennamens beträgt 189 Zeichen.

### Öffentliches oder privates Netz
{: #vs_orderinginstances-public-private-network}

Die Einstellungen für die Aktivierung der Netzschnittstellenkarte (NIC - Network Interface Card) basieren darauf, ob Sie **Öffentliches und privates Netz** oder **Nur privates Netz** auswählen.

### VLANs
{: #vs_orderinginstances-vlans}

Die Netzeinstellungen basieren auf Ihrer Auswahl von entweder **Neue VLANs bestellen** oder **Vorhandene VLANs auswählen**.

Für Ihre Clusterbestellung sind 1 öffentliches VLAN und 2 private VLANs erforderlich. Die zwei privaten VLANs werden in jedem Bare Metal Server zusammengelegt.

#### Neue VLANs bestellen
{: #vs_orderinginstances-new-vlans}

Wählen Sie diese Option aus, um ein neues öffentliches VLANs und zwei neue private VLANs zu bestellen.

#### Vorhandene VLANs auswählen
{: #vs_orderinginstances-existing-vlans}

Abhängig vom ausgewählten {{site.data.keyword.CloudDataCent_notm}} sind möglicherweise vorhandene öffentliche und private VLANs verfügbar.

  Wenn Sie vorhandene öffentliche und private VLANs wiederverwenden wollen, dann geben Sie die VLANs und Teilnetze an:
  * **Öffentliches VLAN** - Wird für den Zugriff auf öffentliche Netze verwendet.
  * **Privates VLAN** - Wird für die Konnektivität zwischen den Rechenzentren und Services in {{site.data.keyword.cloud_notm}} verwendet.
  * **Sekundäres privates VLAN** - Wird für VMware-Funktionen wie z. B. vSAN verwendet.
  * **Primäres Teilnetz** - Wird physischen Hosts für den Zugriff auf öffentliche Netze zugewiesen.
  * **Primäres privates Teilnetz** - Wird physischen Hosts für den Managementdatenverkehr zugewiesen.

**Wichtig:**
* Stellen Sie sicher, dass die Firewallkonfiguration bei den ausgewählten VLANs den Managementdatenverkehr nicht sperrt.
* Stellen Sie sicher, dass sich alle von Ihnen ausgewählten VLANs in demselben Pod befinden. ESXi-Server können nicht in VLANs mit unterschiedlichen Pods bereitgestellt werden.

#### HA-Paar von FortiGate Physical Appliance 300 Series
{: #vs_orderinginstances-fortigate-physical-appliance}

Sie können außerdem auswählen, ob das HA-Paar von FortiGate Physical Appliance 300 Series zum Sichern der Cloudumgebung enthalten sein soll. Weitere Informationen enthält der Abschnitt [FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} - Übersicht](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_considerations).

## Bestellübersicht
{: #vs_orderinginstances-order-summary}

Auf Basis der ausgewählten Konfiguration werden die geschätzten Kosten sofort generiert und im rechten Fenster **Bestellübersicht** angezeigt. Klicken Sie auf **Preisdetails**, um ein PDF-Dokument mit der Kostenübersicht für die {{site.data.keyword.vmwaresolutions_short}}-Ressourcen zu generieren.

Sie können die bereitgestellten Ressourcen auch durch Klicken auf **Zur Schätzung hinzufügen** zum {{site.data.keyword.cloud_notm}}-Schätztool hinzufügen. Dies ist nützlich, wenn Sie die Kosten für die ausgewählten {{site.data.keyword.vmwaresolutions_short}}-Ressourcen zusammen mit anderen {{site.data.keyword.cloud_notm}}-Ressourcen schätzen möchten, die Sie für den Kauf in Betracht ziehen könnten.

## Vorgehensweise zum Bestellen von vSphere-Cluster
{: #vs_orderinginstances-procedure}

1. Klicken Sie im {{site.data.keyword.cloud_notm}}-Katalog im linken Navigationsfenster auf **VMware** und anschließend im Abschnitt **Virtuelle Rechenzentren** auf **VMware vSphere**.
2. Klicken Sie auf der Seite **VMware vSphere on IBM Cloud** auf **Erstellen**.  
   Vergewissern Sie sich, dass Sie sich auf der Registerkarte **Neue erstellen** befinden und dass in der Liste **Clusterkonfigurationen** der Eintrag **Neuer Cluster** angezeigt wird.
3. Geben Sie den Clusternamen ein.
4. Wählen Sie die VMware-Komponenten aus:
  * Wenn Sie ein IBM Business Partner sind, wählen Sie ein Lizenzpaket sowie beliebige zusätzliche VMware-Komponenten aus.
  * Wenn Sie nicht den Status eines IBM Business Partners haben, wählen Sie die Komponente und Edition (soweit verfügbar) aus und geben Sie die Lizenzoption an.
  Wenn Sie für VMware vSphere Enterprise Plus eine eigene Lizenz verwenden wollen (BYOL = Bring Your Own License), dann wird automatisch ein {{site.data.keyword.cloud_notm}}-Ticket für Sie geöffnet, um die standardmäßigen vSphere-Lizenzen für die bestellten {{site.data.keyword.baremetal_short}}-Instanzen anzufordern, die durch die von Ihnen bereitgestellten Lizenzen ersetzt werden sollen.   

    **Wichtig:** Sie sind selbst für die Verfolgung des Tickets verantwortlich und müssen sicherzustellen, dass Sie die vSphere-Lizenz auf den neu bestellten ESXi-Servern ersetzen. Auf diese Weise wird die Stornierung der Gebühr für die zunächst in der {{site.data.keyword.cloud_notm}}-Infrastruktur bereitgestellte vSphere-Lizenz von der {{site.data.keyword.cloud_notm}}-Infrastruktur bewilligt. Informationen zum Ersetzen Ihrer ESXi-vSphere-Lizenz finden Sie auf der Seite [Configure License Settings for an ESXi Host](https://docs.vmware.com/en/VMware-vSphere/6.0/com.vmware.vsphere.vcenterhost.doc/GUID-1B128360-0060-40F2-A6F0-43CD2534B034.html){:new_window}.
5. Geben Sie die Bare Metal Server-Einstellungen an:
   1. Wählen Sie das {{site.data.keyword.CloudDataCent_notm}} als Host für den Cluster aus.
   2. Wählen Sie die Bare Metal Server-Konfiguration aus.
      * Wenn Sie **Skylake** oder **Broadwell** auswählen, dann müssen Sie das CPU-Modell und die RAM-Größe angeben.
      * Wenn Sie **SAP-zertifiziert** auswählen, müssen Sie eine der voreingestellten Konfigurationen auswählen.
   3. Geben Sie die Anzahl der Bare Metal Server an.
6. Wenn Sie die Komponente **VMware vSAN** ausgewählt haben, müssen Sie die vSAN-Speicherkonfiguration ausführen. Geben Sie die Plattentypen für die Kapazitäts- und Cacheplatten sowie die Anzahl der Platten an. Falls Sie mehr Speicher benötigen, müssen Sie das Feld für **Hohe Leistung mit Intel Optane** auswählen.
7. Geben Sie die Netzschnittstelleneinstellungen an:
   1. Geben Sie das Hostnamenspräfix, die Unterdomänenbezeichnung und den Domänennamen ein.
   2. Wählen Sie die Netzeinstellung für entweder **Öffentliches und privates Netz** oder **Nur privates Netz** aus.
   3. Wählen Sie die Netzschnittstelle aus, die verwendet werden soll.
    * Falls Sie neue öffentliche und private VLANs bestellen wollen, klicken Sie auf **Neue VLANs bestellen**.
    * Wenn Sie die vorhandenen öffentlichen und privaten VLANs wiederverwenden möchten, sofern diese verfügbar sind, dann klicken Sie auf **Vorhandene VLANs auswählen** und geben Sie die VLANs und optional die Teilnetze an.
    4. Geben Sie an, ob das HA-Paar von FortiGate Physical Appliance 300 Series zum Sichern der Cloudumgebung angewendet werden soll.  
8. Überprüfen Sie im Fenster **Bestellübersicht** die Clusterkonfiguration und die geschätzten Kosten.
   * Wenn Sie die Konfiguration als Vorlage speichern wollen, ohne eine Bestellung aufzugeben, klicken Sie auf **Konfiguration speichern**.
   * Wenn Sie die Bestellung aufgeben wollen, dann vergewissern Sie sich, dass das zu belastende Konto korrekt ist, überprüfen und akzeptieren Sie die Bedingungen und klicken Sie dann auf **Bereitstellung**.

   Nur die {{site.data.keyword.baremetal_short}}-Instanzen werden installiert. Für die Installation und Konfiguration verschiedener Komponenten nach der Clusterbereitstellung (z. B. VMware vCenter, VMware NSX, VMware vSAN) sind Sie selbst zuständig.
   {:note}

### Ergebnisse nach der Bestellung von vSphere-Clustern
{: #vs_orderinginstances-results}

Wenn Sie die Clusterkonfiguration als Vorlage gespeichert haben, erhalten Sie in der Konsole eine Benachrichtigung, dass die Konfiguration erfolgreich gespeichert wurde. Die Vorlage ist danach in der Liste **Clusterkonfigurationen** enthalten.

Falls Sie eine Bestellung aufgegeben haben, beginnt die Bereitstellung des Clusters automatisch und Sie empfangen eine E-Mail-Bestätigung, dass die Bestellung bearbeitet wird. Sobald der Cluster einsatzbereit ist, werden Sie per E-Mail benachrichtigt.

Die vSphere-Cluster werden im Gegensatz zu den vCenter Server-Instanzen auf der Seite **Ressourcen** nicht angezeigt.
{:note}

## Zugehörige Links
{: #vs_orderinginstances-related}

* [Auf vorhandenen Konfigurationen basierenden vSphere-Cluster bestellen](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderingbasedonexistingconfig)
* [Vorhandene Cluster skalieren](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_scalingexistingclusters)
* [Außerhalb der Konsole erstellte Cluster skalieren](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderingforclustersoutside)
