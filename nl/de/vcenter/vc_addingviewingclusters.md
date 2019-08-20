---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-06"

keywords: vCenter Server add cluster, view cluster vCenter Server, delete cluster vCenter Server

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Cluster für vCenter Server-Instanzen hinzufügen, anzeigen und löschen
{: #vc_addingviewingclusters}

Sie können eigene Cluster zu Ihren VMware vCenter Server-Instanzen hinzufügen, um die Rechen- und Speicherkapazität zu erweitern. In einem Cluster können Sie ESXi-Server verwalten, um eine bessere Ressourcenzuordnung und hohe Verfügbarkeit zu erreichen. Löschen Sie die hinzufügten Cluster aus Ihrer Instanz, wenn sie nicht mehr benötigt werden.

Die Funktion zum Löschen von Clustern steht nur für Instanzen zur Verfügung, die in V2.3 oder höher bereitgestellt (oder für die Upgrades auf diese Releases durchgeführt) wurden.
{:note}

## Cluster zu vCenter Server-Instanzen hinzufügen
{: #vc_addingviewingclusters-adding}

### Vor dem Hinzufügen von Clustern
{: #vc_addingviewingclusters-before-add}

* Fügen Sie Cluster nach Möglichkeit über die {{site.data.keyword.vmwaresolutions_full}}-Konsole hinzu, da Änderungen, die Sie am VMware vSphere Web Client vornehmen, nicht mit der {{site.data.keyword.vmwaresolutions_short}}-Konsole synchronisiert werden. Fügen Sie daher Cluster nur für On-Premise-Cluster oder Cluster hinzu, die Sie nicht in der {{site.data.keyword.vmwaresolutions_short}}-Konsole verwalten können/möchten.
* Für Instanzen, die in (oder einem Upgrade auf) V2.5 und höher implementiert wurden, legt die Anzahl der Cluster, Hosts und VMs die maximale Begrenzung für die Anzahl der Cluster fest, die Sie hinzufügen können. Sie müssen die Richtlinien und Grenzwerte für die VMware-Dimensionierung für Ihre Implementierung beibehalten. Weitere Informationen zu maximalen Grenzwerten finden Sie in [VMware Configuration Maximums](https://configmax.vmware.com/home){:external}.
* Für Instanzen, die in V2.2, 2.3 oder 2.4, bereitgestellt (oder für die Upgrades auf diese Releases durchgeführt) wurden, können Sie bis zu 10 Cluster hinzufügen.
* Für Instanzen, die in V2.1 oder früher bereitgestellt wurden, können Sie bis zu fünf Cluster hinzufügen.

### Systemeinstellungen
{: #vc_addingviewingclusters-adding-sys-settings}

Wenn Sie einen Cluster für eine vCenter Server-Instanz hinzufügen, müssen Sie die folgenden Einstellungen angeben.

#### Clustername
{: #vc_addingviewingclusters-adding-cluster-name}

Der Clustername muss die folgenden Anforderungen erfüllen:
* Es sind nur Kleinbuchstaben, Ziffern und Gedankenstriche (-) zulässig.
* Der Clustername muss mit einem Kleinbuchstaben beginnen.
* Der Clustername muss entweder auf einen Kleinbuchstaben oder auf eine Ziffer enden.
* Die maximale Länge des Clusternamens beträgt 30 Zeichen.
* Der Clustername muss innerhalb der vCenter Server-Instanz eindeutig sein.

#### Standort des Rechenzentrums
{: #vc_addingviewingclusters-adding-dc-location}

Der Standort des {{site.data.keyword.CloudDataCent}}s für den Cluster wird standardmäßig auf das {{site.data.keyword.CloudDataCent_notm}} der vCenter Server-Instanz gesetzt. Sie können den Cluster in einem anderen {{site.data.keyword.CloudDataCent_notm}} als die bereitgestellte Instanz bereitstellen, müssen aber sicherstellen, dass die Netzlatenz zwischen den beiden {{site.data.keyword.CloudDataCents_notm}} weniger als 150 Millisekunden beträgt. Zur Überprüfung der Netzlatenz können Sie ein Tool wie [Looking Glass](/docs/infrastructure/network-tools?topic=network-tools-about-looking-glass#about-looking-glass) verwenden.

Wenn Sie den Cluster in einem anderen {{site.data.keyword.CloudDataCent_notm}}- oder {{site.data.keyword.cloud_notm}}-Infrastrukturpod bereitstellen, werden drei weitere VLANs zur Verwendung mit den bestellten {{site.data.keyword.baremetal_short}}-Instanzen bestellt.

### Einstellungen für Bare Metal Server
{: #vc_addingviewingclusters-bare-metal-settings}

Sie können **Skylake**, **Cascade**, **SAP-zertifiziert** oder **Broadwell** auswählen. Die Optionen können je nach der Version, in der Ihre Instanz ursprünglich bereitgestellt wurde, variieren.

#### Skylake
{: #vc_addingviewingclusters-adding-skylake}

Für die Einstellung **Skylake** stehen Ihnen Optionen für **CPU-Modell** und **RAM** zur Verfügung. Die verfügbaren Optionen können je nach der Version, in der Ihre Instanz ursprünglich bereitgestellt wurde, variieren.

| CPU-Modelloptionen        | RAM-Optionen       |
|:------------- |:------------- |
| Dual Intel Xeon Silver 4110-Prozessor / 16 Kerne insgesamt, 2,1 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon Gold 5120-Prozessor / 28 Kerne insgesamt, 2,2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon Gold 6140-Prozessor / 36 Kerne insgesamt, 2,3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
{: caption="Tabelle 1. Optionen für Skylake {{site.data.keyword.baremetal_short}}" caption-side="top"}

#### Cascade
{: #vc_addingviewingclusters-adding-cascade}

Für die Einstellung **Cascade** stehen Ihnen Optionen für **CPU-Modell** und **RAM** zur Verfügung.

Cascade-{{site.data.keyword.baremetal_short}} stehen nur für VMware vSphere Enterprise Plus 6.7u2-Instanzen zur Verfügung.
{:note}

| CPU-Modelloptionen        | RAM-Optionen       |
|:------------- |:------------- |
|Dual Intel Xeon Gold 4210-Prozessor / 20 Kerne insgesamt, 2,3 GHz| 64 GB, 96 GB, 128 GB, 192 GB, 768 GB, 1,5 TB |
|Dual Intel Xeon Gold 5218-Prozessor / 32 Kerne insgesamt, 2,3 GHz| 64 GB, 96 GB, 128 GB, 192 GB, 768 GB, 1,5 TB |
|Dual Intel Xeon Gold 6248-Prozessor / 40 Kerne insgesamt, 2,5 GHz| 64 GB, 96 GB, 128 GB, 192 GB, 768 GB, 1,5 TB |
{: caption="Tabelle 2. Optionen für Cascade-{{site.data.keyword.baremetal_short}}" caption-side="top"}

#### SAP-zertifiziert
{: #vc_addingviewingclusters-adding-sap}

Wenn Sie **SAP-zertifiziert** auswählen, dann können Sie die CPU- oder RAM-Einstellungen nicht ändern.

Wählen Sie gemäß Ihren Anforderungen eine Bare Metal Server-Konfiguration aus:
* Dual Intel Xeon Gold 6140-Prozessor / 36 Kerne insgesamt, 2,3 GHz Dual / 192 GB RAM
* Dual Intel Xeon Gold 6140-Prozessor / 36 Kerne insgesamt, 2,3 GHz Dual / 384 GB RAM
* Dual Intel Xeon Gold 6140-Prozessor / 36 Kerne insgesamt, 2,3 GHz Dual / 768 GB RAM
* Dual Intel Xeon E5-2690 v4-Prozessor / 28 Kerne insgesamt, 2,6 GHz / 512 GB RAM
* Quad Intel Xeon E7-8890 v4-Prozessor / 96 Kerne insgesamt, 2,2 GHz / 1024 GB RAM
* Quad Intel Xeon E7-8890 v4-Prozessor / 96 Kerne insgesamt, 2,2 GHz / 2048 GB RAM
* Quad Intel Xeon E7-8890 v4-Prozessor / 96 Kerne insgesamt, 2,2 GHz / 4096 GB RAM

#### Broadwell
{: #vc_addingviewingclusters-adding-broadwell}

Für die Einstellung **Broadwell** steht eine Reihe von Optionen für **CPU-Modell** und **RAM** zur Verfügung. Die verfügbaren Optionen können je nach der Version, in der Ihre Instanz ursprünglich bereitgestellt wurde, variieren.

| CPU-Modelloptionen        | RAM-Optionen       |
|:------------- |:------------- |
| Quad Intel Xeon E7-4820 v4 / 40 Kerne insgesamt, 1,9 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |
| Quad Intel Xeon E7-4850 v4 / 64 Kerne insgesamt, 2,2 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |
{: caption="Tabelle 3. Optionen für Broadwell {{site.data.keyword.baremetal_short}}" caption-side="top"}

#### Bare Metal Server-Anzahl
{: #vc_addingviewingclusters-adding-bare-metal-number}

* Alle Server, die Sie bestellen, haben die gleiche Konfiguration.
* Für vSAN-Speicher können Sie zwischen 4 und 59 Server bestellen.
* Für NFS-Speicher können Sie zwischen 2 und 59 Server bestellen. Für die Auslastung im Produktionsbetrieb werden jedoch mindestens drei Server empfohlen. Weitere Informationen finden Sie im Abschnitt [Ist eine vCenter Server-Instanz mit zwei Knoten hoch verfügbar?](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq#is-a-two-node-vcenter-server-instance-highly-available-).

### Speichereinstellungen
{: #vc_addingviewingclusters-adding-storage-settings}

Die Speichereinstellungen sind von der Auswahl der Bare Metal Server-Konfiguration und des Speichertyps abhängig.

#### vSAN-Speicher
{: #vc_addingviewingclusters-adding-vsan-storage}

Geben Sie die folgenden vSAN-Optionen an:
* **Plattentyp und Größe für vSAN-Kapazitätsplatten**: Wählen Sie die für die Kapazitätsplatten benötigte Option aus.
* **Anzahl der vSAN-Kapazitätsplatten**: Geben Sie die Anzahl der hinzuzufügenden Kapazitätsplatten an.
* Wenn Sie über den Grenzwert von zehn Stück hinaus Kapazitätsplatten hinzufügen möchten, müssen Sie das Feld für **Hohe Leistung mit Intel Optane** auswählen. Diese Option stellt zwei zusätzliche Kapazitätsplattenpositionen für eine Gesamtzahl von 12 Kapazitätsplatten bereit und ist für Workloads nützlich, die eine geringere Latenzzeit und einen höheren Durchsatz an E/A-Operationen pro Sekunde erfordern.

  Die Option **Hohe Leistung mit Intel Optane** ist nur für die Skylake- und Cascade-CPU-Modelle verfügbar.
  {:note}

* Überprüfen Sie die Werte für **Plattentyp für vSAN-Cacheplatten** und **Anzahl der vSAN-Cacheplatten**. Diese Werte hängen davon ab, ob Sie das Feld **Hohe Leistung mit Intel Optane** ausgewählt haben.
* **vSAN-Lizenz**: Verwenden Sie die von IBM bereitgestellte VMware-Lizenz für die vSAN-Komponente, indem Sie **In Kauf einbeziehen** auswählen, oder verwenden Sie eine eigene Lizenz (Bring Your Own License, BYOL), indem Sie **Lizenz selbst bereitstellen** auswählen und Ihren eigenen Lizenzschlüssel eingeben.

Wenn Ihr erster Cluster ein vSAN-Cluster war, verwenden alle zusätzlichen vSAN-Cluster dieselbe vSAN-Lizenz und dieselbe Konfiguration wie der erste vSAN-Cluster. Dies gilt auch dann, wenn für einen (ersten oder zusätzlichen) Cluster in der Instanz die Bereitstellung von vSAN ausgewählt wurde. Beim ersten Mal wird von Ihnen die vSAN-Lizenz (eigene oder gekaufte Lizenz) und die Edition angefordert. Wenn Sie das nächste Mal vSAN für einen neuen Cluster auswählen, wird Ihre anfänglich getroffene Auswahl wiederverwendet.

#### NFS-Speicher
{: #vc_addingviewingclusters-adding-nfs-storage}

Wenn Sie **NFS-Speicher** auswählen, können Sie gemeinsam genutzten Speicher auf Dateiebene für Ihre Instanz hinzufügen, wobei für alle gemeinsam genutzten Ressourcen dieselben Einstellungen verwendet werden; alternativ können Sie für die einzelnen gemeinsam genutzten Dateiressourcen jeweils unterschiedliche Konfigurationseinstellungen angeben. Geben Sie die folgenden NFS-Optionen an:

Die Anzahl der gemeinsam genutzten Dateiressourcen muss zwischen 1 und 32 liegen.
{:note}

* **Gemeinsam genutzte Ressourcen einzeln konfigurieren**: Wählen Sie diese Option aus, um für jede einzelne gemeinsam genutzte Dateiressource unterschiedliche Konfigurationseinstellungen anzugeben.
* **Anzahl der gemeinsam genutzten Ressourcen**: Geben Sie bei Verwendung derselben Konfigurationseinstellung für alle gemeinsam genutzten Dateiressourcen die Anzahl der gemeinsam genutzten Dateiressourcen für den gemeinsam genutzten NFS-Speicher an, die Sie hinzufügen möchten.
* **Größe**: Wählen Sie die Kapazität aus, die Ihrem Bedarf an gemeinsam genutzten Speicher entspricht.
* **Leistung**: Wählen Sie basierend auf Ihren Workloadanforderungen die pro GB geltende Anzahl von E/A-Operationen pro Sekunde aus.
* **NFS hinzufügen**: Wählen Sie diese Option aus, um einzelne gemeinsam genutzte Dateiressourcen mit anderen Konfigurationseinstellungen hinzuzufügen.

Details der Leistungsstufe:

| Option        | Details       |
|:------------- |:------------- |
| 0,25 IOPS/GB | Diese Option ist für Workloads vorgesehen, die nicht häufig verwendet werden. Zu den Beispielanwendungen gehören: durch Vaulting geschützte Daten, das Hosting großer Datenbanken mit übernommenen Daten oder Images von virtuellen Platten des virtuellen Speichersystems als Sicherung. |
| 2 IOPS/GB | Diese Option ist für die meisten allgemeinen Workloads geeignet. Anwendungsbeispiele sind das Hosting von kompakten Datenbanken, die Sicherung von Webanwendungen oder Plattenimages von virtuellen Maschinen (VM) für einen Hypervisor. |
| 4 IOPS/GB | Diese Option ist für Workloads mit höherer Intensität geeignet, die zu einem bestimmten Zeitpunkt einen hohen Prozentsatz an aktiven Daten aufweisen. Anwendungsbeispiele sind transaktionsorientierte Datenbanken. |
| 10 IOPS/GB | Diese Option ist für die aufwändigsten Workloadtypen wie beispielsweise die Analyse gedacht. Anwendungsbeispiele sind Hochtransaktionsdatenbanken und andere leistungskritische Datenbanken. Diese Leistungsstufe ist auf eine maximale Kapazität von 4 TB pro gemeinsam genutzte Dateiressource begrenzt. |
{: caption="Tabelle 4. Optionen für die NFS-Leistungsstufe" caption-side="top"}

### Lokale Platten
{: #vc_addingviewingclusters-adding-local-disks}

Die Option für lokale Festplatten steht nur für die Bare-Metal-Konfiguration des **SAP-zertifizierten** Quad Intel Xeon E7-8890 v4-Prozessors zur Verfügung. Geben Sie die folgenden Optionen an:
* **Plattenanzahl**: Wählen Sie die Anzahl der Platten aus, die hinzugefügt werden sollen.
* **Plattentyp**: Wählen Sie eine Option für den Plattentyp aus, den Sie benötigen.

### Lizenzierungseinstellungen
{: #vc_addingviewingclusters-adding-licensing-settings}

Geben Sie die Lizenzierungsoption für die Komponente "VMware vSphere" im Cluster an:
* Für Benutzer der Kategorie "Business Partner" ist die vSphere-Lizenz (Enterprise Plus Edition) enthalten und wird in Ihrem Namen erworben.
* Für Nicht-Business-Partner-Benutzer können die von IBM bereitgestellten VMware-Lizenzen für diese Komponente benutzt werden. Wählen Sie hierzu **In Kauf einbeziehen** aus. Alternativ hierzu können Sie auch eine eigene Lizenz (Bring Your Own License; BYOL) verwenden, indem Sie **Lizenz selbst bereitstellen** auswählen und den eigenen Lizenzschlüssel angeben.

### Netzschnittstelleneinstellungen
{: #vc_addingviewingclusters-adding-network-interface-settings}

Wenn Sie einen Cluster für eine vCenter Server-Instanz hinzufügen, müssen Sie die folgenden Netzschnittstelleneinstellungen angeben.

#### Öffentliches oder privates Netz

Die Einstellungen für die Aktivierung der Netzschnittstellenkarte (NIC - Network Interface Card) basieren darauf, ob Sie **Öffentliches und privates Netz** oder **Nur privates Netz** auswählen. Die folgenden Add-on-Services benötigen öffentliche NICs und sind nicht verfügbar, wenn Sie die private Option auswählen:

* F5 on {{site.data.keyword.cloud_notm}}
* FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}
* FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}

#### VLANs
{: #vc_orderinginstance-vlans}

Die Netzeinstellungen basieren auf Ihrer Auswahl von entweder **Neue VLANs bestellen** oder **Vorhandene VLANs auswählen**.

Für Ihre Instanzbestellung sind 1 öffentliches VLAN und 2 private VLANs erforderlich. Die zwei privaten VLANs werden in jedem Bare Metal Server zusammengelegt.

##### Neue VLANs bestellen
{: #vc_orderinginstance-new-vlans}

Wählen Sie diese Option aus, um ein neues öffentliches VLANs und zwei neue private VLANs zu bestellen.

##### Vorhandene VLANs auswählen
{: #vc_orderinginstance-existing-vlans}

Abhängig vom ausgewählten {{site.data.keyword.CloudDataCent_notm}} sind möglicherweise vorhandene öffentliche und private VLANs verfügbar.

Wenn Sie vorhandene öffentliche und private VLANs wiederverwenden wollen, dann geben Sie die VLANs und Teilnetze an:
* **Öffentliches VLAN** - Wird für den Zugriff auf öffentliche Netze verwendet.
* **Privates VLAN** - Wird für die Konnektivität zwischen den Rechenzentren und Services in {{site.data.keyword.cloud_notm}} verwendet.
* **Sekundäres privates VLAN** - Wird für VMware-Funktionen wie z. B. vSAN verwendet.
* **Primäres Teilnetz** - Wird physischen Hosts für den Zugriff auf öffentliche Netze zugewiesen.
* **Primäres privates Teilnetz** - Wird physischen Hosts für den Managementdatenverkehr zugewiesen.

Stellen Sie sicher, dass die Firewallkonfiguration bei den ausgewählten VLANs den Managementdatenverkehr nicht sperrt. Stellen Sie außerdem sicher, dass sich alle von Ihnen ausgewählten VLANs in demselben Pod befinden. ESXi-Server können nicht in VLANs mit unterschiedlichen Pods bereitgestellt werden.
{:important}

### Bestellübersicht
{: #vc_addingviewingclusters-adding-order-summary}

Auf Basis der für den Cluster ausgewählten Konfiguration werden die geschätzten Kosten sofort generiert und im rechten Fenster **Bestellübersicht** angezeigt. Klicken Sie auf **Preisdetails**, um ein PDF-Dokument mit der Kostenübersicht für die {{site.data.keyword.vmwaresolutions_short}}-Ressourcen zu generieren.

Sie können die bereitgestellten Ressourcen auch durch Klicken auf **Zur Schätzung hinzufügen** zum {{site.data.keyword.cloud_notm}}-Schätztool hinzufügen. Dies ist nützlich, wenn Sie die Kosten für die ausgewählten {{site.data.keyword.vmwaresolutions_short}}-Ressourcen zusammen mit anderen {{site.data.keyword.cloud_notm}}-Ressourcen schätzen möchten, die Sie für den Kauf in Betracht ziehen könnten.

## Vorgehensweise zum Hinzufügen von Clustern zu vCenter Server-Instanzen
{: #vc_addingviewingclusters-adding-procedure}

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Ressourcen**.
2. Klicken Sie in der Tabelle **vCenter Server-Instanzen** auf die Instanz, zu der Cluster hinzugefügt werden sollen.

   Vergewissern Sie sich, dass sich die Instanz im Status **Bereit** befindet. Andernfalls können Sie keine Cluster zur Instanz hinzufügen.
   {:note}
3. Klicken Sie im linken Navigationsfenster auf **Infrastruktur** und anschließend in der rechten oberen Ecke der Tabelle **CLUSTER** auf **Hinzufügen**.
4. Geben Sie auf der Seite **Cluster hinzufügen** den Clusternamen ein.
5. Wenn Sie für den Cluster ein anderes {{site.data.keyword.CloudDataCent_notm}} als Host verwenden möchten als das, in dem die Instanz gehostet wird, aktivieren Sie unter **Bare Metal Server** das Kontrollkästchen **Anderen Standort auswählen** und wählen Sie dann das gewünschte {{site.data.keyword.CloudDataCent_notm}} als Host für die Instanz aus.
6. Führen Sie die Bare-Metal-Konfiguration durch.
   * Wenn Sie **Skylake**, **Cascade** oder **Broadwell** ausgewählt haben, geben Sie das **CPU-Modell**, die **RAM**-Größe und die **Anzahl der {{site.data.keyword.baremetal_short}}** an.
   * Wenn Sie **SAP-zertifiziert** ausgewählt haben, geben Sie das CPU-Modell an.
7. Führen Sie die Speicherkonfiguration durch.
  * Wenn Sie **vSAN-Speicher** auswählen, geben Sie die Plattentypen für die Kapazitäts- und Cacheplatten, die Anzahl der Platten und die vSAN-Lizenzedition an. Falls Sie mehr Speicher benötigen, müssen Sie das Feld für **Hohe Leistung mit Intel Optane** auswählen.
  * Wenn Sie **NFS-Speicher** auswählen und für alle gemeinsam genutzten Dateiressourcen dieselben Einstellungen konfigurieren möchten, geben Sie die **Anzahl der gemeinsam genutzten Ressourcen**, die **Leistung**und die **Größe (GB)** an.
  * Wenn Sie **NFS-Speicher** auswählen und alle gemeinsam genutzten Dateiressourcen einzeln hinzufügen und konfigurieren möchten, wählen Sie **Gemeinsam genutzte Ressourcen einzeln konfigurieren** aus. Klicken Sie anschließend auf das Symbol **+** neben der Bezeichnung **Gemeinsam genutzten Speicher hinzufügen** und wählen Sie für jede Dateifreigabe die Optionen **Leistung** und **Größe (GB)** aus. Sie müssen mindestens eine gemeinsam genutzte Dateiressource auswählen.
  * Wenn Sie **Lokale Platten** auswählen, geben Sie die Plattenanzahl und den Plattentyp an.
8. Geben Sie die Netzschnittstelleneinstellungen an.
8. Geben Sie an, wie der vSphere-Lizenzschlüssel bereitgestellt wird:
  * Für Benutzer der Kategorie "Business Partner" ist die vSphere-Lizenz (Enterprise Plus Edition) enthalten und wird in Ihrem Namen erworben.
  * Für Benutzer, bei denen es sich nicht um Business Partner handelt, können Sie eine der folgenden Optionen auswählen:
      * Wenn Sie neue Lizenzen für sich erwerben lassen möchten, wählen Sie **In Kauf einbeziehen** für die Komponente aus.
      * Wenn Sie Ihre eigene VMware-Lizenz für die Komponente verwenden möchten, wählen Sie die Option **Lizenz selbst bereitstellen** aus und geben Sie den Lizenzschlüssel ein.
9. Wählen Sie die Netzeinstellung für entweder **Öffentliches und privates Netz** oder **Nur privates Netz** aus.
10. Überprüfen Sie im Fenster **Bestellübersicht** die Clusterkonfiguration, bevor Sie den Cluster hinzufügen.
   1. Überprüfen Sie die Einstellungen für den Cluster.
   2. Überprüfen Sie die geschätzten Kosten des Clusters. Klicken Sie auf **Preisdetails**, um eine PDF-Datei mit der Zusammenfassung zu generieren. Ihre Bestellübersicht können Sie speichern oder drucken, indem Sie rechts oben im PDF-Fenster auf das Symbol **Drucken** bzw. **Herunterladen** klicken.
   3. Klicken Sie auf den Link bzw. die Links für die Bedingungen, die für Ihre Bestellung gelten, und vergewissern Sie sich, dass Sie mit diesen Bedingungen einverstanden sind, bevor Sie den Cluster hinzufügen.
   4. Klicken Sie auf **Bereitstellung**.

### Ergebnisse nach Hinzufügen von Clustern zu vCenter Server-Instanzen
{: #vc_addingviewingclusters-adding-results}

1. Die Bereitstellung des Clusters wird automatisch gestartet und der Status des Clusters ändert sich in **Wird initialisiert**. Sie können den Status der Bereitstellung überprüfen, indem Sie den Bereitstellungsverlauf über die Seite **Zusammenfassung** der Instanz anzeigen.
2. Sobald der Cluster einsatzbereit ist, ändert sich sein Status in **Bereit**. Der neu hinzugefügte Cluster wird mit vSphere High Availability (HA) und vSphere Distributed Resource Scheduler (DRS) aktiviert.

Der Clustername kann nicht geändert werden. Wenn Sie den Clusternamen ändern, kann die Operation zum Hinzufügen oder Entfernen von ESXi-Servern im Cluster fehlschlagen.
{:important}

## Vorgehensweise zum Anzeigen von Clustern in vCenter Server-Instanzen
{: #vc_addingviewingclusters-viewing-procedure}

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Ressourcen**.
2. Klicken Sie in der Tabelle **vCenter Server-Instanzen** auf eine Instanz, um die Cluster in dieser Instanz anzuzeigen.
3. Klicken Sie im linken Navigationsfenster auf **Infrastruktur**. Prüfen Sie in der Tabelle **CLUSTER** die Zusammenfassung für die Cluster:
  * **Name**: Der Name des Clusters.
  * **ESXi-Server**: Die Anzahl der ESXi-Server im Cluster.
  * **Speicher**: Der Speichertyp, der vom Cluster verwendet wird.
  * **Standort des Rechenzentrums**: Das {{site.data.keyword.CloudDataCent_notm}}, in dem der Cluster gehostet wird.
  * **Pod**: Der Pod, in dem der Cluster bereitgestellt wird.
  * **Status**: Der Status des Clusters. Der Status kann einen der folgenden Werte aufweisen:
    <dl class="dl">
        <dt class="dt dlterm">Wird initialisiert</dt>
        <dd class="dd">Der Cluster wird gerade erstellt und konfiguriert.</dd>
        <dt class="dt dlterm">Wird geändert</dt>
        <dd class="dd">Der Cluster wird gerade geändert.</dd>
        <dt class="dt dlterm">Bereit</dt>
        <dd class="dd">Der Cluster ist zur Verwendung bereit.</dd>
        <dt class="dt dlterm">Wird gelöscht</dt>
        <dd class="dd">Der Cluster wird gerade gelöscht.</dd>
        <dt class="dt dlterm">Gelöscht</dt>
        <dd class="dd">Der Cluster wurde gelöscht.</dd>
    </dl>
  * **Aktionen**: Klicken Sie auf das Symbol **Löschen**, um den Cluster zu löschen.
4. Klicken Sie auf einen Clusternamen, um die Details zum ESXi-Server, zum Speicher und zur Netzschnittstelle anzuzeigen.

Details des ESXi-Servers anzeigen:

| Element        | Beschreibung       |  
|:------------- |:------------- |
| Name | Der Name des ESXi-Servers hat das Format `<data_center>-<host_prefix><n>.<subdomain_label>.<root_domain>`, wobei `n` die Folgenummer des ESXi-Servers ist. |
| Version | Die Version des ESXi-Servers. |
| Berechtigungsnachweise | Der Benutzername und das Kennwort für den Zugriff auf den ESXi-Server. |
| Private IP | Die private IP-Adresse des ESXi-Servers. |
| Status | Der Status des ESXi-Servers, der einen der folgenden Werte aufweisen kann:<br> **Hinzugefügt** Der ESXi-Server wurde hinzugefügt und kann verwendet werden.<br> **Wird hinzugefügt** Der ESXi-Server wird gerade hinzugefügt.<br> **Wird gelöscht** Der ESXi-Server wird gerade gelöscht. |
{: caption="Tabelle 5. Details zum ESXi-Server" caption-side="top"}

ESXi-Server zum Anzeigen weiterer Details erweitern:

| Element        | Beschreibung       |  
|:------------- |:------------- |
| CPU | Die CPU-Spezifikation der ESXi-Server im Cluster. |
| Speicher | Die Gesamtspeichergröße der ESXi-Server im Cluster. |
| Angepasste vSAN-Platten | Die Anzahl der vSAN-Platten im Cluster, einschließlich des Plattentyps und der Kapazität. |
| vSAN-Cacheplatten | Der Typ und die Anzahl der vSAN-Cacheplatten. |
| Netzbetrieb |Die Einstellungen für die Aktivierung der Netzschnittstellenkarte (NIC) entweder des öffentlichen und privaten Netzes oder nur des privaten Netzes. |
{: caption="Tabelle 6. Weitere Details zum ESXi-Server" caption-side="top"}

Speicherdetails anzeigen:

| Element        | Beschreibung       |  
|:------------- |:------------- |
| Name | Der Name des Datenspeichers. |
| Größe | Die Kapazität des Speichers. |
| IOPS/GB | Die Leistungsstufe des Speichers. |
| NFS-Protokoll | Die NFS-Version des Speichers. |
{: caption="Tabelle 7. Speicherdetails" caption-side="top"}

Details der Netzschnittstelle anzeigen:

| Element        | Beschreibung       |  
|:------------- |:------------- |
| VLAN-Nummer | Die eindeutige VLAN-Nummer.  |
| Beschreibung | Die Beschreibung des VLAN.  |
| Standort | Der Standort des Rechenzentrums. |
| Primäre Route | Die primäre Route des VLAN. |
{: caption="Tabelle 8. Netzschnittstelle - VLAN-Details" caption-side="top"}

Klicken Sie auf **Ressourcen anzeigen**, um auf die VLAN-Details zuzugreifen.

Details des Teilnetzes anzeigen:

| Element        | Beschreibung       |  
|:------------- |:------------- |
| Name | Der Teilnetzname. Klicken Sie auf den Namen, um auf die Teilnetzdetails zuzugreifen. |
| Typ | Der Typ des Teilnetzes: primär oder portierbar. |
| Beschreibung | Die Beschreibung des Teilnetzes. |
{: caption="Tabelle 9. Netzschnittstelle - Teilnetzdetails" caption-side="top"}

Details der IP-Adressen anzeigen:

| Element        | Beschreibung       |  
|:------------- |:------------- |
| IP | Die IP-Adresse. |
| Status | Der Status der IP-Adresse. |
| Beschreibung |Die Beschreibung der IP-Adresse.  |
{: caption="Tabelle 10. Netzschnittstelle - IP-Details" caption-side="top"}

## Cluster aus vCenter Server-Instanzen löschen
{: #vc_addingviewingclusters-deleting}

Wird ein Cluster nicht mehr benötigt, kann er aus einer Instanz gelöscht werden.

### Vor dem Löschen von Clustern
{: #vc_addingviewingclusters-deleting-prereq}

* Gehen Sie wie folgt vor, um Cluster aus Instanzen zu löschen, die in V2.3 oder höher bereitgestellt werden.
* Für Cluster, die in Instanzen der Version 2.2 oder älter bereitgestellt wurden, müssen Sie ein Upgrade der Instanz auf Version 2.3 durchführen, wenn Sie die Cluster löschen möchten, die Sie der Instanz hinzugefügt haben.
* Löschen Sie Cluster nach Möglichkeit über die {{site.data.keyword.vmwaresolutions_full}}-Konsole, da Änderungen, die Sie am VMware vSphere Web Client vornehmen, nicht mit der {{site.data.keyword.vmwaresolutions_short}}-Konsole synchronisiert werden. Löschen Sie daher Cluster nur für On-Premise-Cluster oder Cluster, die Sie nicht in der {{site.data.keyword.vmwaresolutions_short}}-Konsole verwalten können/möchten.
* Es kann immer nur ein Cluster gleichzeitig gelöscht werden. Beim Löschen von mehreren Clustern müssen Sie nacheinander löschen. Warten Sie, bis der vorherige Cluster gelöscht wurde, bevor Sie den nächsten Cluster löschen.
* Stellen Sie sicher, dass alle Knoten in einem Cluster eingeschaltet und betriebsbereit sind, bevor Sie den Cluster löschen.
* Wenn Sie einen Cluster löschen, werden auch alle VMs des Clusters gelöscht und können nicht wiederhergestellt werden. Sollen die VMs beibehalten werden, dann müssen Sie sie auf andere Cluster migrieren.
* Der Standardcluster kann nicht gelöscht werden.

Für die Bestellung des VMware HCX on {{site.data.keyword.cloud_notm}}-Service ist eine Verpflichtung über 12 Monate erforderlich. Wenn Sie einen Cluster vor dem Ende des 12-monatigen Verpflichtungszeitraums löschen, wird Ihr Konto weiterhin für die HCX-Komponenten belastet. Das Ablaufdatum der 12-monatigen Verpflichtung ist auf der Detailseite von HCX on {{site.data.keyword.cloud_notm}} verfügbar. Weitere Informationen zum Anzeigen von Servicedetails finden Sie unter [Services für vCenter Server-Instanzen bestellen, anzeigen und entfernen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_addingremovingservices#vc_addingremovingservices-viewing-procedure).
{:important}

### Vorgehensweise zum Löschen von Clustern aus vCenter Server-Instanzen
{: #vc_addingviewingclusters-deleting-procedure}

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Ressourcen**.
2. Klicken Sie in der Tabelle **vCenter Server-Instanzen** auf die Instanz, aus der Cluster gelöscht werden sollen.

   Vergewissern Sie sich, dass sich die Instanz im Status **Bereit** befindet. Andernfalls können Sie keine Cluster aus der Instanz löschen.
   {:note}

3. Klicken Sie im linken Navigationsfenster auf **Infrastruktur**. Suchen Sie in der Tabelle **CLUSTER** den Cluster, der gelöscht werden soll, und klicken Sie dann auf das Symbol **Löschen** in der Spalte **Aktionen**.
4. Vergewissern Sie sich, dass die Migration der VMs auf andere Cluster (sofern erforderlich) durchgeführt wurde und dass der Cluster tatsächlich gelöscht werden soll.

## Zugehörige Links
{: #vc_addingviewingclusters-related}

* [vCenter Server-Instanzen anzeigen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_viewinginstances)
* [Kapazität für vCenter Server-Instanzen erweitern und verringern](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers)
