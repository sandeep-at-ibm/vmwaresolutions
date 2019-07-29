---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-13"

keywords: vCenter Server NSX-T add cluster, view cluster vCenter Server NSX-T, delete cluster vCenter Server NSX-T

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Cluster für vCenter Server with NSX-T-Instanzen hinzufügen, anzeigen und löschen
{: #vc_nsx-t_addingviewingcluster}

Die ESXi-Server, die Sie bei der Bestellung einer Instanz konfiguriert haben, werden standardmäßig unter **cluster1** gruppiert.

Sie können eigene Cluster zu VMware vCenter Server with NSX-T-Instanzen hinzufügen, um die Rechen- und Speicherkapazität zu erweitern. In einem Cluster können Sie ESXi-Server verwalten, um eine bessere Ressourcenzuordnung und hohe Verfügbarkeit zu erreichen. Löschen Sie die hinzufügten Cluster aus Ihrer Instanz, wenn sie nicht mehr benötigt werden.

## Cluster zu vCenter Server-Instanzen hinzufügen
{: #vc_nsx-t_addingviewingclusters-adding}

### Vor dem Hinzufügen von Clustern
{: #vc_nsx-t_addingviewingclusters-before-add}

* Fügen Sie Cluster nach Möglichkeit über die {{site.data.keyword.vmwaresolutions_full}}-Konsole hinzu, da Änderungen, die Sie am VMware vSphere Web Client vornehmen, nicht mit der {{site.data.keyword.vmwaresolutions_short}}-Konsole synchronisiert werden. Fügen Sie daher Cluster nur für On-Premise-Cluster oder Cluster hinzu, die Sie nicht in der {{site.data.keyword.vmwaresolutions_short}}-Konsole verwalten können/möchten.
* Die Anzahl der Cluster, Hosts und virtuellen Maschinen (VMs) legt die maximale Begrenzung für die Anzahl der Cluster fest, die Sie hinzufügen können. Sie müssen die Richtlinien und Grenzwerte für die VMware-Dimensionierung für Ihre Implementierung beibehalten. Weitere Informationen zu maximalen Grenzwerten finden Sie in [VMware Configuration Maximums](https://configmax.vmware.com/home){:new_window}.

### Systemeinstellungen
{: #vc_nsx-t_addingviewingclusters-adding-sys-settings}

Wenn Sie einen Cluster für eine vCenter Server with NSX-T-Instanz hinzufügen, müssen Sie die folgenden Einstellungen angeben.

#### Clustername
{: #vc_nsx-t_addingviewingclusters-adding-cluster-name}

Der Clustername muss die folgenden Anforderungen erfüllen:
* Es sind nur alphanumerische Zeichen und Bindestriche (-) zulässig.
* Der Clustername muss mit einem alphanumerischen Zeichen beginnen und enden.
* Die maximale Anzahl an Zeichen beträgt 30.
* Der Clustername muss innerhalb der vCenter Server-Instanz eindeutig sein.

#### Standort des Rechenzentrums
{: #vc_nsx-t_addingviewingclusters-adding-dc-location}

Der Standort des {{site.data.keyword.CloudDataCent}}s für den Cluster wird standardmäßig auf das {{site.data.keyword.CloudDataCent_notm}} der vCenter Server-Instanz gesetzt. Sie können den Cluster in einem anderen {{site.data.keyword.CloudDataCent_notm}} als die bereitgestellte Instanz bereitstellen, müssen aber sicherstellen, dass die Netzlatenz zwischen den beiden {{site.data.keyword.CloudDataCents_notm}} weniger als 150 Millisekunden beträgt. Zur Überprüfung der Netzlatenz können Sie ein Tool wie [Looking Glass](/docs/infrastructure/network-tools?topic=network-tools-about-looking-glass#about-looking-glass) verwenden.

Wenn Sie den Cluster in einem anderen {{site.data.keyword.CloudDataCent_notm}}- oder {{site.data.keyword.cloud_notm}}-Infrastrukturpod bereitstellen, werden drei weitere VLANs zur Verwendung mit den bestellten {{site.data.keyword.baremetal_short}}-Instanzen bestellt.

### Einstellungen für Bare Metal Server
{: #vc_nsx-t_addingviewingclusters-bare-metal-settings}

Sie können **Skylake** oder **Broadwell** auswählen.

#### Skylake
{: #vc_nsx-t_addingviewingclusters-adding-skylake}

Für die Einstellung **Skylake** stehen Ihnen Optionen für **CPU-Modell** und **RAM** zur Verfügung. Die verfügbaren Optionen können je nach der Version, in der Ihre Instanz ursprünglich bereitgestellt wurde, variieren.

Tabelle 1. Optionen für Skylake {{site.data.keyword.baremetal_short}}

| CPU-Modelloptionen        | RAM-Optionen       |
|:------------- |:------------- |
| Dual Intel Xeon Silver 4110-Prozessor / 16 Kerne insgesamt, 2,1 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon Gold 5120-Prozessor / 28 Kerne insgesamt, 2,2 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon Gold 6140-Prozessor / 36 Kerne insgesamt, 2,3 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |

#### Broadwell
{: #vc_nsx-t_addingviewingclusters-adding-broadwell}

Für die Einstellung **Broadwell** steht eine Reihe von Optionen für **CPU-Modell** und **RAM** zur Verfügung. Die verfügbaren Optionen können je nach der Version, in der Ihre Instanz ursprünglich bereitgestellt wurde, variieren.

Tabelle 2. Optionen für Broadwell {{site.data.keyword.baremetal_short}}

| CPU-Modelloptionen        | RAM-Optionen       |
|:------------- |:------------- |
| Quad Intel Xeon E7-4820 v4 / 40 Kerne insgesamt, 1,9 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |
| Quad Intel Xeon E7-4850 v4 / 64 Kerne insgesamt, 2,2 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |

#### Bare Metal Server-Anzahl
{: #vc_nsx-t_addingviewingclusters-adding-bare-metal-number}

* Alle Server, die Sie bestellen, haben die gleiche Konfiguration.
* Für vSAN-Speicher können Sie zwischen 4 und 59 Server bestellen.
* Für NFS-Speicher können Sie zwischen 2 und 59 Server bestellen. Für die Auslastung im Produktionsbetrieb werden jedoch mindestens drei Server empfohlen. Weitere Informationen finden Sie im Abschnitt [Ist eine vCenter Server-Instanz mit zwei Knoten hoch verfügbar?](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq#is-a-two-node-vcenter-server-instance-highly-available-).

### Speichereinstellungen
{: #vc_nsx-t_addingviewingclusters-adding-storage-settings}

Die Speichereinstellungen sind von der Auswahl der Bare Metal Server-Konfiguration und des Speichertyps abhängig.

#### vSAN-Speicher
{: #vc_nsx-t_addingviewingclusters-adding-vsan-storage}

Geben Sie die folgenden vSAN-Optionen an:
* **Plattentyp und Größe für vSAN-Kapazitätsplatten**: Wählen Sie die für die Kapazitätsplatten benötigte Option aus.
* **Anzahl der vSAN-Kapazitätsplatten**: Geben Sie die Anzahl der hinzuzufügenden Kapazitätsplatten an.
* Wenn Sie über den Grenzwert von zehn Stück hinaus Kapazitätsplatten hinzufügen möchten, müssen Sie das Feld für **Hohe Leistung mit Intel Optane** auswählen. Diese Option stellt zwei zusätzliche Kapazitätsplattenpositionen für eine Gesamtzahl von 12 Kapazitätsplatten bereit und ist für Workloads nützlich, die eine geringere Latenzzeit und einen höheren Durchsatz an E/A-Operationen pro Sekunde erfordern.

  Die Option **Hohe Leistung mit Intel Optane** ist nur für die Skylake-CPU-Modelle verfügbar.
  {:note}

* Überprüfen Sie die Werte für **Plattentyp für vSAN-Cacheplatten** und **Anzahl der vSAN-Cacheplatten**. Diese Werte hängen davon ab, ob Sie das Feld **Hohe Leistung mit Intel Optane** ausgewählt haben.
* **vSAN-Lizenz**: Verwenden Sie die von IBM bereitgestellte VMware-Lizenz für die vSAN-Komponente, indem Sie **In Kauf einbeziehen** auswählen, oder verwenden Sie eine eigene Lizenz (Bring Your Own License, BYOL), indem Sie **Lizenz selbst bereitstellen** auswählen und Ihren eigenen Lizenzschlüssel eingeben.

Wenn Ihr erster Cluster ein vSAN-Cluster war, verwenden alle zusätzlichen vSAN-Cluster dieselbe vSAN-Lizenz und dieselbe Konfiguration wie der erste vSAN-Cluster. Dies gilt auch dann, wenn für einen (ersten oder zusätzlichen) Cluster in der Instanz die Bereitstellung von vSAN ausgewählt wurde. Beim ersten Mal wird von Ihnen die vSAN-Lizenz (eigene oder gekaufte Lizenz) und die Edition angefordert. Wenn Sie das nächste Mal vSAN für einen neuen Cluster auswählen, wird Ihre anfänglich getroffene Auswahl wiederverwendet.

#### NFS-Speicher
{: #vc_nsx-t_addingviewingclusters-adding-nfs-storage}

Wenn Sie **NFS-Speicher** auswählen, können Sie gemeinsam genutzten Speicher auf Dateiebene für Ihre Instanz hinzufügen, wobei für alle gemeinsam genutzten Ressourcen dieselben Einstellungen verwendet werden; alternativ können Sie für die einzelnen gemeinsam genutzten Dateiressourcen jeweils unterschiedliche Konfigurationseinstellungen angeben. Geben Sie die folgenden NFS-Optionen an:

Die Anzahl der gemeinsam genutzten Dateiressourcen muss zwischen 1 und 32 liegen.
{:note}

* **Gemeinsam genutzte Ressourcen einzeln konfigurieren**: Wählen Sie diese Option aus, um für jede einzelne gemeinsam genutzte Dateiressource unterschiedliche Konfigurationseinstellungen anzugeben.
* **Anzahl der gemeinsam genutzten Ressourcen**: Geben Sie bei Verwendung derselben Konfigurationseinstellung für alle gemeinsam genutzten Dateiressourcen die Anzahl der gemeinsam genutzten Dateiressourcen für den gemeinsam genutzten NFS-Speicher an, die Sie hinzufügen möchten.
* **Größe**: Wählen Sie die Kapazität aus, die Ihrem Bedarf an gemeinsam genutzten Speicher entspricht.
* **Leistung**: Wählen Sie basierend auf Ihren Workloadanforderungen die pro GB geltende Anzahl von E/A-Operationen pro Sekunde aus.
* **NFS hinzufügen**: Wählen Sie diese Option aus, um einzelne gemeinsam genutzte Dateiressourcen mit anderen Konfigurationseinstellungen hinzuzufügen.

Tabelle 3. Optionen für die NFS-Leistungsstufe

| Option        | Details       |
  |:------------- |:------------- |
  | 0,25 IOPS/GB | Diese Option ist für Workloads vorgesehen, die nicht häufig verwendet werden. Zu den Beispielanwendungen gehören: durch Vaulting geschützte Daten, das Hosting großer Datenbanken mit übernommenen Daten oder Images von virtuellen Platten des virtuellen Speichersystems als Sicherung. |
  | 2 IOPS/GB | Diese Option ist für die meisten allgemeinen Workloads geeignet. Anwendungsbeispiele sind das Hosting von kompakten Datenbanken, die Sicherung von Webanwendungen oder Plattenimages von virtuellen Maschinen (VM) für einen Hypervisor. |
  | 4 IOPS/GB | Diese Option ist für Workloads mit höherer Intensität geeignet, die zu einem bestimmten Zeitpunkt einen hohen Prozentsatz an aktiven Daten aufweisen. Anwendungsbeispiele sind transaktionsorientierte Datenbanken. |
  | 10 IOPS/GB | Diese Option ist für die aufwändigsten Workloadtypen wie beispielsweise die Analyse gedacht. Anwendungsbeispiele sind Hochtransaktionsdatenbanken und andere leistungskritische Datenbanken. Diese Leistungsstufe ist auf eine maximale Kapazität von 4 TB pro gemeinsam genutzte Dateiressource begrenzt. |

### Lizenzierungseinstellungen
{: #vc_nsx-t_addingviewingclusters-adding-licensing-settings}

Geben Sie die Lizenzierungsoption für die Komponente "VMware vSphere" im Cluster an:
* Für Benutzer der Kategorie "Business Partner" ist die vSphere-Lizenz (Enterprise Plus Edition) enthalten und wird in Ihrem Namen erworben.
* Für Nicht-Business-Partner-Benutzer können die von IBM bereitgestellten VMware-Lizenzen für diese Komponente benutzt werden. Wählen Sie hierzu **In Kauf einbeziehen** aus. Alternativ hierzu können Sie auch eine eigene Lizenz (Bring Your Own License; BYOL) verwenden, indem Sie **Lizenz selbst bereitstellen** auswählen und den eigenen Lizenzschlüssel angeben.

### Netzschnittstelleneinstellungen
{: #vc_nsx-t_addingviewingclusters-adding-network-interface-settings}

Die Einstellungen für die Aktivierung der Netzschnittstellenkarte (NIC - Network Interface Card) basieren darauf, ob Sie **Öffentliches und privates Netz** oder **Nur privates Netz** auswählen.

### Bestellübersicht
{: #vc_nsx-t_addingviewingclusters-adding-order-summary}

Auf Basis der für den Cluster ausgewählten Konfiguration werden die geschätzten Kosten sofort generiert und im rechten Fenster **Bestellübersicht** angezeigt. Klicken Sie auf **Preisdetails**, um ein PDF-Dokument mit der Kostenübersicht für die {{site.data.keyword.vmwaresolutions_short}}-Ressourcen zu generieren.

Sie können die bereitgestellten Ressourcen auch durch Klicken auf **Zur Schätzung hinzufügen** zum {{site.data.keyword.cloud_notm}}-Schätztool hinzufügen. Dies ist nützlich, wenn Sie die Kosten für die ausgewählten {{site.data.keyword.vmwaresolutions_short}}-Ressourcen zusammen mit anderen {{site.data.keyword.cloud_notm}}-Ressourcen schätzen möchten, die Sie für den Kauf in Betracht ziehen könnten.

## Vorgehensweise zum Hinzufügen von Clustern zu vCenter Server with NSX-T-Instanzen
{: #vc_nsx-t_addingviewingclusters-adding-procedure}

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Ressourcen**.
2. Klicken Sie in der Tabelle **vCenter Server-Instanzen** auf die Instanz, zu der Cluster hinzugefügt werden sollen.

   Vergewissern Sie sich, dass sich die Instanz im Status **Bereit** befindet. Andernfalls können Sie keine Cluster zur Instanz hinzufügen.
   {:note}
3. Klicken Sie im linken Navigationsfenster auf **Infrastruktur** und anschließend in der rechten oberen Ecke der Tabelle **CLUSTER** auf **Hinzufügen**.
4. Geben Sie auf der Seite **Cluster hinzufügen** den Clusternamen ein.
5. Wenn Sie für den Cluster ein anderes {{site.data.keyword.CloudDataCent_notm}} als Host verwenden möchten als das, in dem die Instanz gehostet wird, aktivieren Sie unter **Bare Metal Server** das Kontrollkästchen **Anderen Standort auswählen** und wählen Sie dann das gewünschte {{site.data.keyword.CloudDataCent_notm}} als Host für die Instanz aus.
6. Führen Sie die Bare-Metal-Konfiguration durch. Geben Sie das **CPU-Modell**, die **RAM**-Größe und die **Anzahl der {{site.data.keyword.baremetal_short}}** an.
7. Führen Sie die Speicherkonfiguration durch.
  * Wenn Sie **vSAN-Speicher** auswählen, geben Sie die Plattentypen für die Kapazitäts- und Cacheplatten, die Anzahl der Platten und die vSAN-Lizenzedition an. Falls Sie mehr Speicher benötigen, müssen Sie das Feld für **Hohe Leistung mit Intel Optane** auswählen.
  * Wenn Sie **NFS-Speicher** auswählen und für alle gemeinsam genutzten Dateiressourcen dieselben Einstellungen konfigurieren möchten, geben Sie die **Anzahl der gemeinsam genutzten Ressourcen**, die **Leistung**und die **Größe (GB)** an.
  * Wenn Sie **NFS-Speicher** auswählen und alle gemeinsam genutzten Dateiressourcen einzeln hinzufügen und konfigurieren möchten, wählen Sie **Gemeinsam genutzte Ressourcen einzeln konfigurieren** aus. Klicken Sie anschließend auf das Symbol **+** neben der Bezeichnung **Gemeinsam genutzten Speicher hinzufügen** und wählen Sie für jede Dateifreigabe die Optionen **Leistung** und **Größe (GB)** aus. Sie müssen mindestens eine gemeinsam genutzte Dateiressource auswählen.
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
   3. Klicken Sie auf den Link bzw. die Links für die Bedingungen, die für Ihre Bestellung gelten, und bestätigen Sie, dass Sie mit diesen Bedingungen einverstanden sind, bevor Sie den Cluster hinzufügen.
   4. Klicken Sie auf **Bereitstellung**.

### Ergebnisse nach Hinzufügen von Clustern zu vCenter Server with NSX-T-Instanzen
{: #vc_nsx-t_addingviewingclusters-adding-results}

1. Die Bereitstellung des Clusters wird automatisch gestartet und der Status des Clusters ändert sich in **Wird initialisiert**. Sie können den Status der Bereitstellung überprüfen, indem Sie den Bereitstellungsverlauf über die Seite **Zusammenfassung** der Instanz anzeigen.
2. Sobald der Cluster einsatzbereit ist, ändert sich sein Status in **Bereit**. Der neu hinzugefügte Cluster wird mit vSphere High Availability (HA) und vSphere Distributed Resource Scheduler (DRS) aktiviert.

Der Clustername kann nicht geändert werden. Wenn Sie den Clusternamen ändern, kann die Operation zum Hinzufügen oder Entfernen von ESXi-Servern im Cluster fehlschlagen.
{:important}

## Vorgehensweise zum Anzeigen von Clustern in vCenter Server with NSX-T-Instanzen
{: #vc_nsx-t_addingviewingclusters-viewing-procedure}

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Ressourcen**.
2. Klicken Sie in der Tabelle **vCenter Server-Instanzen** auf eine Instanz, um die Cluster in dieser Instanz anzuzeigen.
3. Klicken Sie im linken Navigationsfenster auf **Infrastruktur**. Prüfen Sie in der Tabelle **CLUSTER** die Zusammenfassung für die Cluster:
  * **Name**: Der Name des Clusters.
  * **ESXi-Server**: Die Anzahl der ESXi-Server im Cluster.
  * **CPU**: Die CPU-Spezifikation der ESXi-Server im Cluster.
  * **Angepasste vSAN-Platten**: Die Anzahl der vSAN-Platten im Cluster, einschließlich des Plattentyps und der Kapazität.
  * **Speicher**: Die Gesamtspeichergröße der ESXi-Server im Cluster.
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
4. Klicken Sie auf einen Clusternamen, um die Details zum ESXi-Server, zum Speicher und zur Netzschnittstelle anzuzeigen:

Tabelle 4. Details zum ESXi-Server

| Element        | Beschreibung       |  
|:------------- |:------------- |
| Name | Der Name des ESXi-Servers weist das folgende Format auf:<br> `<host_prefix><n>.<subdomain_label>.<root_domain>` <br> Hierbei gilt Folgendes:<br> `host_prefix` ist das Hostnamenspräfix,<br> `n` ist die Folgenummer des Servers,<br> `subdomain_label` ist die Unterdomänenbezeichnung und<br> `root_domain` ist der Rootdomänenname |
| Version | Die Version des ESXi-Servers. |
| Berechtigungsnachweise | Der Benutzername und das Kennwort für den Zugriff auf den ESXi-Server. |
| Private IP | Die private IP-Adresse des ESXi-Servers. |
| Status | Der Status des ESXi-Servers, der einen der folgenden Werte aufweisen kann:<br> **Hinzugefügt** Der ESXi-Server wurde hinzugefügt und kann verwendet werden.<br> **Wird hinzugefügt** Der ESXi-Server wird gerade hinzugefügt.<br> **Wird gelöscht** Der ESXi-Server wird gerade gelöscht. |

Tabelle 5. Speicherdetails

| Element        | Beschreibung       |  
|:------------- |:------------- |
| Name | Der Name des Datenspeichers. |
| Größe | Die Kapazität des Speichers. |
| IOPS/GB | Die Leistungsstufe des Speichers. |
| NFS-Protokoll | Die NFS-Version des Speichers. |

Tabelle 6. Netzschnittstelle - VLAN-Details

| Element        | Beschreibung       |  
|:------------- |:------------- |
| VLAN-Nummer | Die eindeutige VLAN-Nummer.  |
| Beschreibung | Die Beschreibung des VLAN.  |
| Standort | Der Standort des Rechenzentrums. |
| Primäre Route | Die primäre Route des VLAN. |

Klicken Sie auf **Ressourcen anzeigen**, um auf die VLAN-Details zuzugreifen.

Tabelle 7. Netzschnittstelle - Teilnetzdetails

| Element        | Beschreibung       |  
|:------------- |:------------- |
| Name | Der Teilnetzname. Klicken Sie auf den Namen, um auf die Teilnetzdetails zuzugreifen. |
| Typ | Der Typ des Teilnetzes: primär oder portierbar. |
| Beschreibung | Die Beschreibung des Teilnetzes. |

Tabelle 8. Netzschnittstelle - IP-Details

| Element        | Beschreibung       |  
|:------------- |:------------- |
| IP | Die IP-Adresse. |
| Status | Der Status der IP-Adresse. |
| Beschreibung |Die Beschreibung der IP-Adresse.  |

## Cluster aus vCenter Server with NSX-T-Instanzen löschen
{: #vc_nsx-t_addingviewingclusters-deleting}

Wird ein Cluster nicht mehr benötigt, kann er aus einer Instanz gelöscht werden.

### Vorbereitende Schritte für die Löschung
{: #vc_nsx-t_addingviewingclusters-deleting-prereq}

* Löschen Sie Cluster nach Möglichkeit über die {{site.data.keyword.vmwaresolutions_full}}-Konsole, da Änderungen, die Sie am VMware vSphere Web Client vornehmen, nicht mit der {{site.data.keyword.vmwaresolutions_short}}-Konsole synchronisiert werden. Löschen Sie daher Cluster nur für On-Premise-Cluster oder Cluster, die Sie nicht in der {{site.data.keyword.vmwaresolutions_short}}-Konsole verwalten können/möchten.
* Es kann immer nur ein Cluster gleichzeitig gelöscht werden. Beim Löschen von mehreren Clustern müssen Sie nacheinander löschen. Warten Sie, bis der vorherige Cluster gelöscht wurde, bevor Sie den nächsten Cluster löschen.
* Stellen Sie sicher, dass alle Knoten in einem Cluster eingeschaltet und betriebsbereit sind, bevor Sie den Cluster löschen.
* Wenn Sie einen Cluster löschen, werden auch alle VMs des Clusters gelöscht und können nicht wiederhergestellt werden. Sollen die VMs beibehalten werden, dann müssen Sie sie auf andere Cluster migrieren.
* Der Standardcluster kann nicht gelöscht werden.

### Vorgehensweise zum Löschen von Clustern aus vCenter Server with NSX-T-Instanzen
{: #vc_nsx-t_addingviewingclusters-deleting-procedure}

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Ressourcen**.
2. Klicken Sie in der Tabelle **vCenter Server-Instanzen** auf die Instanz, aus der Cluster gelöscht werden sollen.

   Vergewissern Sie sich, dass sich die Instanz im Status **Bereit** befindet. Andernfalls können Sie keine Cluster aus der Instanz löschen.
   {:note}

3. Klicken Sie im linken Navigationsfenster auf **Infrastruktur**. Suchen Sie in der Tabelle **CLUSTER** den Cluster, der gelöscht werden soll, und klicken Sie dann auf das Symbol **Löschen** in der Spalte **Aktionen**.
4. Vergewissern Sie sich, dass die Migration der VMs auf andere Cluster (sofern erforderlich) durchgeführt wurde und dass der Cluster tatsächlich gelöscht werden soll.

## Zugehörige Links
{: #vc_nsx-t_addingviewingclusters-related}

* [vCenter Server-Instanzen anzeigen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_viewinginstances)
* [Kapazität für vCenter Server with NSX-T-Instanzen erweitern und verringern](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_addingremovingservers)
