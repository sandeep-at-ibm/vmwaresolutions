---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-31"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Neue vSphere-Cluster bestellen

Zur Bereitstellung einer hochanpassungsfähigen virtualisierten VMware-Plattform müssen Sie einen VMware vSphere on {{site.data.keyword.cloud}}-Cluster bestellen. In diesem Abschnitt ist beschrieben, wie Sie einen neuen vSphere-Cluster definieren.

In dieser Prozedur werden Sie durch die Auswahl von VMware-Komponenten, {{site.data.keyword.cloud_notm}} Bare Metal Server-Einstellungen, Speichereinstellungen und Optionen für den Netzbetrieb geführt, um einen neuen Cluster zu erstellen. Nachdem Sie die Bestellung aufgegeben haben, wird die Clusterkonfiguration gespeichert, damit Sie den Cluster später ausgehend von dieser Konfiguration wie benötigt skalieren können. Nach der Bestellung können Sie den VMware-Cluster manuell gemäß Ihren Anforderungen konfigurieren.

## Voraussetzungen

Stellen Sie sicher, dass Sie die folgenden Tasks ausgeführt haben:
*  Sie haben die Berechtigungsnachweise für die {{site.data.keyword.cloud_notm}}-Infrastruktur auf der Seite **Einstellungen** konfiguriert. Weitere Informationen finden Sie unter [Benutzerkonten und Einstellungen verwalten](../vmonic/useraccount.html).
*  Sie haben sich mit den Voraussetzungen und Hinweisen im Abschnitt [Voraussetzungen und Planung für vSphere-Cluster](vs_planning.html) vertraut gemacht.

## Systemeinstellungen

Sie müssen die folgenden Systemeinstellungen angeben, wenn Sie einen neuen vSphere-Cluster bestellen.

### Clustername

Der Clustername muss innerhalb Ihres Kontos eindeutig sein.

## Lizenzierungseinstellungen

Wählen Sie die VMware-Komponenten aus, die mit Ihrem Cluster bestellt werden sollen, und geben Sie die Lizenzierungsoption für die Komponenten an.

### Komponentenpakete für IBM Business Partner-Benutzer

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

Wenn Sie nicht Den IBM Business Partner-Status haben, können Sie für Ihren vSphere Cluster folgende Komponenten auswählen:
* VMware vSphere Enterprise Plus
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

Zur Lizenzierung der ausgewählten VMware-Komponenten gibt es die folgenden Optionen:
* **Lizenz in Kauf einbeziehen**: In diesem Fall wird eine neue Lizenz für die VMware-Komponente in Ihrem Namen erworben. Es wird eine kombinierte VMware-Lizenz generiert, die mit der Clustergröße der Bestellung übereinstimmt.
* **Lizenz selbst bereitstellen**: In diesem Fall verwenden Sie Ihre eigene Lizenz für die VMware-Komponente.

Falls Sie den Kauf einer Lizenz auswählen (vSphere Enterprise Plus und vCenter Server ausgenommen) und Sie mehrere ESXi-Server bestellen, wird automatisch in Ihrem Namen ein {{site.data.keyword.cloud_notm}}-Ticket geöffnet, um die Lizenzschlüssel zu kombinieren. Sie müssen sich selbst um die weitere Verfolgung des Tickets kümmern, damit sichergestellt ist, dass Sie ausschließlich die vom DevOps-Team generierten Lizenzschlüssel verwenden.

Die Verwendung von einzelnen Lizenzschlüsseln zusammen mit den kombinierten Lizenzschlüsseln erfüllt nicht die Zahlungsvoraussetzungen für die Lizenzen, die Sie benötigen.
{:important}

## Einstellungen für Bare Metal Server

### Standort des Rechenzentrums

Wählen Sie das {{site.data.keyword.CloudDataCent_notm}} aus, das als Host für den Cluster verwendet werden soll.

**Hinweise:**
* Falls Sie eine vSAN-Komponente auswählen, wird die Liste der Standorte nach SSD-Verfügbarkeit gefiltert.
* Das Rechenzentrum FRA05 bietet keine Unterstützung für den Broadwell-Bare-Metal-Server.
* Das Rechenzentrum FRA05 bietet keine Unterstützung für SAP-zertifizierte und Broadwell-Bare-Metal-Server.

### Skylake

Wenn Sie **Skylake** auswählen, dann können Sie die Kombination aus CPU und RAM für den Bare Metal Server entsprechend Ihren Anforderungen auswählen. Welche Optionen verfügbar sind, ist davon abhängig, ob Sie die Komponente "VMware vSAN" ausgewählt haben.

Tabelle 2. Optionen für Skylake {{site.data.keyword.baremetal_short}}

| CPU-Modelloptionen        | RAM-Optionen       |
|:------------- |:------------- |
| Dual Intel Xeon Silver 4110-Prozessor / 16 Kerne insgesamt, 2,1 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon Gold 5120-Prozessor / 28 Kerne insgesamt, 2,2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon Gold 6140-Prozessor / 36 Kerne insgesamt, 2,3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |

### SAP-zertifiziert

Die Registerkarte **SAP-zertifiziert** ist nicht verfügbar, wenn Sie zuvor VMware vSAN ausgewählt haben. Wenn Sie **SAP-zertifiziert** auswählen, dann können Sie die CPU- oder RAM-Einstellungen nicht ändern.

Wählen Sie gemäß Ihren Anforderungen eine Bare Metal Server-Konfiguration aus:
  * Dual Intel Xeon Gold 6140-Prozessor / 36 Kerne insgesamt, 2,3 GHzDual / 192 GB RAM
  * Dual Intel Xeon Gold 6140-Prozessor / 36 Kerne insgesamt, 2,2 GHzDual / 384 GB RAM
  * Dual Intel Xeon Gold 6140-Prozessor / 36 Kerne insgesamt, 2,3 GHzDual / 768 GB RAM

### Broadwell

Wenn Sie **Broadwell** auswählen, dann können Sie die Kombination aus CPU und RAM für den Bare Metal Server entsprechend Ihren Anforderungen auswählen. Welche Optionen verfügbar sind, ist davon abhängig, ob Sie die Komponente "VMware vSAN" ausgewählt haben.

Tabelle 3. Optionen für Broadwell {{site.data.keyword.baremetal_short}}

| CPU-Modelloptionen        | RAM-Optionen       |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4 / 16 Kerne insgesamt, 2,1 GHz | 64 GB, 128 GB, 256 GB, 384 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2650 v4 / 24 Kerne insgesamt, 2,2 GHz | 64 GB, 128 GB, 256 GB, 384 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2690 v4 / 28 Kerne insgesamt, 2,6 GHz | 64 GB, 128 GB, 256 GB, 384 GB, 512 GB, 768 GB, 1,5 TB |

### Bare Metal Server-Anzahl

Die Anzahl der ESXi-Server, die Sie zum vSphere-Cluster hinzufügen wollen. Alle ESXi-Server verfügen über dieselbe Konfiguration.
* Falls Sie die Komponente "VMware NSX" ausgewählt haben, sind mindestens drei Server erforderlich.
* Falls Sie die Komponente "VMware vSAN" ausgewählt haben, sind mindestens vier Server erforderlich.

## Speichereinstellungen

Bei Bestellungen ohne vSAN werden ESXi-Server mit einem Chassis für zwölf Platten und zwei Platten für das ESXi-Betriebssystem (OS) bestellt.

Bei Bestellungen mit vSAN werden ESXi-Server mit einem Chassis für zwölf Platten und vier Platten bestellt (zwei Platten für das ESXi-Betriebssystem und zwei für das Caching reservierte Platten). Diese Einstellungen sind standardmäßig konfiguriert und können nicht geändert werden. Sie können weitere Kapazitätsplatten bestellen, indem Sie **Plattentyp und -größe für vSAN-Kapazitätsplatten** und **Anzahl der vSAN-Kapazitätsplatten** auswählen.

Wenn Sie für den Cluster die Komponente "VMware vSAN" ausgewählt haben, müssen Sie folgende Einstellungen angeben.
* **Plattentyp und Größe für vSAN-Kapazitätsplatten**: Wählen Sie die für die Kapazitätsplatten benötigte Option aus.
* **Anzahl der vSAN-Kapazitätsplatten**: Geben Sie die Anzahl der hinzuzufügenden Kapazitätsplatten an.
* Wenn Sie über den Grenzwert von acht Stück hinaus Kapazitätsplatten hinzufügen möchten, müssen Sie das Feld für **Hohe Leistung mit Intel Optane** auswählen. Diese Option stellt zwei zusätzliche Kapazitätsplattenpositionen für eine Gesamtzahl von 10 Kapazitätsplatten bereit und ist für Workloads nützlich, die eine geringere Latenzzeit und einen höheren Durchsatz an E/A-Operationen pro Sekunde erfordern. Die Option **Hohe Leistung mit Intel Optane** steht nur für die Dualprozessoren Intel Xeon Gold 5120 und 6140 zur Verfügung.
* Überprüfen Sie die Werte für **Plattentyp für vSAN-Cacheplatten** und **Anzahl der vSAN-Cacheplatten**. Diese Werte hängen davon ab, ob Sie das Feld **Hohe Leistung mit Intel Optane** ausgewählt haben.

## Netzschnittstelleneinstellungen

Sie müssen die folgenden Netzschnittstelleneinstellungen angeben, wenn Sie einen neuen vSphere-Cluster bestellen.

### Hostnamenspräfix

Der Hostname wird für alle Bare Metal Server-Bestellungen verwendet. Es wird empfohlen, den Hostnamen für alle Management-VMs wie vCenter Server oder NSX zu verwenden.

Das Hostnamenspräfix muss die folgenden Anforderungen erfüllen:
* Der Name muss mit einem alphanumerischen Zeichen beginnen und enden.
* Es sind nur alphanumerische Zeichen und Bindestriche (-) zulässig.
* Die maximale Länge beträgt 10 Zeichen.

### Unterdomänenbezeichnung

Die Unterdomänenbezeichnung muss die folgenden Anforderungen erfüllen:
*  Es sind nur alphanumerische Zeichen und Bindestriche (-) zulässig.
*  Die Unterdomänenbezeichnung muss mit einem alphanumerischen Zeichen beginnen und enden.
*  Die maximale Länge der Unterdomänenbezeichnung beträgt 10 Zeichen.
*  Die Unterdomänenbezeichnung muss innerhalb Ihres Kontos eindeutig sein.

### Domänenname

Der Domänenname wird für alle {{site.data.keyword.baremetal_short}}-Instanzen verwendet und muss die folgenden Anforderungen erfüllen:
* Der Name muss aus zwei oder mehr Zeichenfolgen bestehen, die jeweils durch einen Punkt (.) voneinander getrennt sind.
* Es sind nur alphanumerische Zeichen und Bindestriche (-) zulässig.
* Jede Zeichenfolge muss mit einem alphabetischen Zeichen beginnen und mit einem alphanumerischen Zeichen enden. Außerdem darf die letzte Zeichenfolge nur Buchstaben enthalten.
* Die Länge der letzten Zeichenfolge muss zwischen 2 und 24 Zeichen betragen.
* Die Länge der anderen Zeichenfolgen muss zwischen 1 und 63 Zeichen liegen.
* Die maximale Länge des Domänennamens beträgt 189 Zeichen.

### Öffentliches oder privates Netz

Die Einstellungen für die Aktivierung der Netzschnittstellenkarte (NIC – Network Interface Card) basieren darauf, ob Sie **Öffentliches und privates Netz** oder **Nur privates Netz** auswählen. Die folgenden Add-on-Services benötigen öffentliche NICs und sind nicht verfügbar, wenn Sie die private Option auswählen:

* F5 on {{site.data.keyword.cloud_notm}}
* FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}
* FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}
* Zerto on {{site.data.keyword.cloud_notm}}

### VLANs

Die Netzeinstellungen basieren auf Ihrer Auswahl von entweder **Neue VLANs bestellen** oder **Vorhandene VLANs auswählen**.

Für Ihre Clusterbestellung sind 1 öffentliches VLAN und 2 private VLANs erforderlich. Die zwei privaten VLANs werden in jedem Bare Metal Server zusammengelegt.

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

**Wichtig:**
* Stellen Sie sicher, dass die Firewallkonfiguration bei den ausgewählten VLANs den Managementdatenverkehr nicht blockiert.
* Stellen Sie sicher, dass sich alle von Ihnen ausgewählten VLANs in demselben Pod befinden. ESXi-Server können nicht in VLANs mit unterschiedlichen Pods bereitgestellt werden.

#### HA-Paar von FortiGate Physical Appliance 300 Series

Sie können außerdem auswählen, ob das HA-Paar von FortiGate Physical Appliance 300 Series zum Sichern der Cloudumgebung enthalten sein soll. Weitere Informationen enthält der Abschnitt [Übersicht über FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](../services/fsa_considerations.html).

## Bestellübersicht

Auf Basis Ihrer Konfigurationen werden die geschätzten Kosten sofort generiert und im rechten Fenster **Bestellübersicht** angezeigt. Klicken Sie auf **Preisdetails**, um ein PDF-Dokument zu generieren, das die Kostenschätzungsdetails enthält.

## Vorgehensweise zum Bestellen von vSphere-Cluster

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
      * Wenn Sie **SAP-zertifiziert** auswählen, müssen Sie das CPU-Modell wählen.
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

### Ergebnisse

Wenn Sie die Clusterkonfiguration als Vorlage gespeichert haben, erhalten Sie in der Konsole eine Benachrichtigung, dass die Konfiguration erfolgreich gespeichert wurde. Die Vorlage ist danach in der Liste **Clusterkonfigurationen** enthalten.

Falls Sie eine Bestellung aufgegeben haben, beginnt die Bereitstellung des Clusters automatisch und Sie empfangen eine E-Mail-Bestätigung, dass die Bestellung bearbeitet wird. Sobald der Cluster einsatzbereit ist, werden Sie per E-Mail benachrichtigt.

Die vSphere-Cluster werden (anders als die vCenter Server- und Cloud Foundation-Instanzen) auf der Seite **Bereitgestellte Instanzen** nicht angezeigt.
{:note}

### Zugehörige Links

* [Auf vorhandenen Konfigurationen basierenden vSphere-Cluster bestellen](vs_orderingbasedonexistingconfig.html)
* [Vorhandene Cluster skalieren](vs_scalingexistingclusters.html)
* [Außerhalb der Konsole erstellte Cluster skalieren](vs_orderingforclustersoutside.html)
