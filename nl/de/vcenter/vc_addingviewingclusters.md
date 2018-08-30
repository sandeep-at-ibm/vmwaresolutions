---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-02"

---

# Cluster für vCenter Server-Instanzen hinzufügen, anzeigen und löschen

Die ESXi-Server, die Sie bei der Bestellung einer Instanz konfiguriert haben, werden standardmäßig unter **cluster1** gruppiert.

Sie können eigene Cluster zu Ihren VMware vCenter Server-Instanzen hinzufügen, um die Rechen- und Speicherkapazität zu erweitern. In einem Cluster können Sie ESXi-Server verwalten, um eine bessere Ressourcenzuordnung und hohe Verfügbarkeit zu erreichen. Die hinzugefügten Cluster können aus Ihren Instanzen gelöscht werden, wenn sie nicht mehr benötigt werden.

**Verfügbarkeit**: Die Funktion zum Löschen von Clustern steht nur für Instanzen zur Verfügung, die in V2.3 oder höheren Releases bereitgestellt (oder für die Upgrades auf diese Releases durchgeführt) wurden.

## Cluster zu vCenter Server-Instanzen hinzufügen

Die Anzahl der Cluster, die zu einer Instanz hinzugefügt werden können, hängt von der Instanzversion ab:
* Für Instanzen, die in V2.2 oder höheren Releases bereitgestellt (oder für die Upgrades auf diese Releases durchgeführt) wurden, können Sie bis zu 10 Cluster hinzufügen.
* Für Instanzen, die in V2.2 oder älteren Releases bereitgestellt wurden, können Sie bis zu 5 Cluster hinzufügen.

### Systemeinstellungen

Wenn Sie einen Cluster für eine vCenter Server-Instanz hinzufügen, müssen Sie die folgenden Einstellungen angeben.

#### Clustername

Der Clustername muss die folgenden Anforderungen erfüllen:
* Es sind nur alphanumerische Zeichen und Bindestriche (-) zulässig.
* Der Clustername muss mit einem alphanumerischen Zeichen beginnen und enden.
* Die maximale Länge des Clusternamens beträgt 30 Zeichen.
* Der Clustername muss innerhalb der vCenter Server-Instanz eindeutig sein.

#### Standort des Rechenzentrums

Der Standort des {{site.data.keyword.CloudDataCent}}s für den Cluster wird standardmäßig auf das {{site.data.keyword.CloudDataCent_notm}} der vCenter Server-Instanz gesetzt. Sie können den Cluster in einem anderen {{site.data.keyword.CloudDataCent_notm}} als die bereitgestellte Instanz bereitstellen, müssen aber sicherstellen, dass die Netzlatenz zwischen den beiden {{site.data.keyword.CloudDataCents_notm}} weniger als 150 Millisekunden beträgt. Zur Überprüfung der Netzlatenz können Sie ein Tool wie [SoftLayer IP Backbone Looking Glass](http://lg.softlayer.com/){:new_window} verwenden.

Wenn Sie den Cluster in einem anderen {{site.data.keyword.CloudDataCent_notm}}- oder {{site.data.keyword.cloud_notm}}-Infrastrukturpod bereitstellen, werden drei zusätzliche VLANs zur Verwendung mit den bestellten {{site.data.keyword.baremetal_short}}-Instanzen bestellt.

### Einstellungen für Bare Metal Server

Sie können entweder **Vorkonfiguriert** oder **Angepasst** auswählen.

#### Vorkonfiguriert

Für die Einstellung **Vorkonfiguriert** können Sie abhängig von Ihren Anforderungen eine **Bare Metal Server-Konfiguration** auswählen:
* S (Klein): Dual Intel Xeon E5-2620 v4 / 16 Kerne insgesamt, 2,1 GHz / 128 GB RAM / 2 Platten
* M (Mittel): Dual Intel Xeon E5-2650 v4 / 24 Kerne insgesamt, 2,2 GHz / 256 GB RAM / 2 Platten
* L (Groß): Dual Intel Xeon E5-2690 v4 / 28 Kerne insgesamt, 2,6 GHz / 512 GB RAM / 2 Platten

#### Angepasst

Für die Einstellung **Angepasst** steht eine Reihe von Optionen für **CPU-Modell** und **RAM** zur Verfügung. Die verfügbaren Optionen können je nach der Version, in der Ihre Instanz ursprünglich bereitgestellt wurde, variieren.

Tabelle 1. Optionen für angepasste {{site.data.keyword.baremetal_short}}-Instanzen

| CPU-Modelloptionen        | RAM-Optionen       |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4 / 16 Kerne insgesamt, 2,1 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2650 v4 / 24 Kerne insgesamt, 2,2 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2690 v4 / 28 Kerne insgesamt, 2,6 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon Silver 4110-Prozessor / 16 Kerne insgesamt, 2,1 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon Gold 5120-Prozessor / 28 Kerne insgesamt, 2,2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon Gold 6140-Prozessor / 36 Kerne insgesamt, 2,3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |

#### Bare Metal Server-Anzahl

Für einen Cluster werden mindestens zwei {{site.data.keyword.baremetal_short}}-Instanzen benötigt.

Für vCenter Server-Instanzen, die in V2.1 oder einem höheren Release bereitgestellt werden, können Sie bis zu 59 {{site.data.keyword.baremetal_short}}-Instanzen für einen Cluster hinzufügen und gleichzeitig jeweils 1 bis 59 ESXi-Server hinzufügen.

Für vCenter Server-Instanzen, die in V2.0 oder früheren Releases bereitgestellt wurden, können Sie bis zu 32 {{site.data.keyword.baremetal_short}}-Instanzen für einen Cluster hinzufügen. Für die Anzahl der {{site.data.keyword.baremetal_short}}-Instanzen, die Sie jeweils hinzufügen können, gilt Folgendes:
* Bei Konfigurationen des Typs **S (Klein)**, **M (Mittel)** und **L (Groß)** können Sie gleichzeitig 1 bis 10 ESXi-Server hinzufügen.
* Bei Bare Metal Server-Konfigurationen des Typs **Angepasst** können Sie gleichzeitig 1 bis 20 ESXi-Server hinzufügen.

Nach der Implementierung können Sie bis zu vier weitere Cluster erstellen. Wenn Sie die Bare Metal Server-Konfiguration **Angepasst** mit VMware vSAN-Speicher auswählen, werden für den ersten Cluster und die Cluster nach der Bereitstellung 4 Server benötigt.

### Speichereinstellungen

Die Speichereinstellungen sind von der Auswahl der Bare Metal Server-Konfiguration und des Speichertyps abhängig.

#### vSAN-Speicher

vSAN ist nur für die angepasste Bare-Metal-Konfiguration verfügbar. Sie können den VMware vSAN-Speicher anpassen, indem Sie die Anzahl der vSAN-Kapazitätsplatten (2, 4, 6 oder 8), den Plattentyp und die Größe angeben, die Ihren Speicheranforderungen entsprechen, und außerdem die vSAN-Lizenzierungsoption.

Wenn Ihr erster Cluster ein vSAN-Cluster war, verwenden alle zusätzlichen vSAN-Cluster dieselbe vSAN-Lizenz und dieselbe Konfiguration wie der erste vSAN-Cluster. Dies gilt auch dann, wenn für einen (ersten oder zusätzlichen) Cluster in der Instanz die Bereitstellung von vSAN ausgewählt wurde. Beim ersten Mal wird von Ihnen die vSAN-Lizenz (eigene oder gekaufte Lizenz) und die Edition angefordert. Bei der nächsten Auswahl von vSAN für einen zusätzlichen Cluster wird Ihre anfänglich ausgewählte Lizenz wiederverwendet.

#### NFS-Speicher

Wenn Sie **NFS-Speicher** auswählen, können Sie gemeinsam genutzten Speicher auf Dateiebene für Ihre Instanz hinzufügen, wobei für alle Dateifreigaben dieselben Einstellungen verwendet werden. Alternativ können Sie für die einzelnen Dateifreigaben jeweils unterschiedliche Konfigurationseinstellungen angeben. Geben Sie die folgenden NFS-Optionen an:

**Hinweis:** Die Anzahl der Dateifreigaben muss zwischen 1 und 32 liegen.

* **Dateifreigaben einzeln konfigurieren**: Wählen Sie diese Option aus, um für jede einzelne Dateifreigabe unterschiedliche Konfigurationseinstellungen anzugeben.
* **Anzahl der Dateifreigaben**: Geben Sie bei Verwendung derselben Konfigurationseinstellung für jede Dateifreigabe die Anzahl der Dateifreigaben für den gemeinsam genutzten NFS-Speicher an, die Sie hinzufügen möchten.
* **Größe**: Wählen Sie die Kapazität aus, die Ihrem Bedarf an gemeinsam genutzten Speicher entspricht.
* **Leistung**: Wählen Sie basierend auf Ihren Workloadanforderungen die E/A-Operationen pro Sekunde (Input/output Operations Per Second, IOPS) pro GB aus.
* **NFS hinzufügen**: Wählen Sie diese Option aus, um einzelne Dateifreigaben hinzuzufügen, für die unterschiedliche Konfigurationseinstellungen verwendet werden.

Tabelle 2. Optionen für die NFS-Leistungsstufe

| Option        | Details       |
  |:------------- |:------------- |
  | 2 IOPS/GB | Diese Option ist für die meisten allgemeinen Workloads geeignet. Anwendungsbeispiele sind das Hosting von kompakten Datenbanken, die Sicherung von Webanwendungen oder Plattenimages von virtuellen Maschinen für einen Hypervisor. |
  | 4 IOPS/GB | Diese Option ist für Workloads mit höherer Intensität geeignet, die zu einem bestimmten Zeitpunkt einen hohen Prozentsatz an aktiven Daten aufweisen. Anwendungsbeispiele sind transaktionsorientierte Datenbanken. |
  | 10 IOPS/GB | Diese Option ist für die aufwändigsten Workloadtypen wie beispielsweise die Analyse gedacht. Anwendungsbeispiele sind Hochtransaktionsdatenbanken und andere leistungskritische Datenbanken. Diese Leistungsstufe ist auf eine maximale Kapazität von 4 TB pro Dateifreigabe begrenzt. |

### Lizenzierungseinstellungen

Geben Sie die Lizenzierungsoption für die Komponente "VMware vSphere" im Cluster an:
* Für Benutzer der Kategorie "Business Partner" ist die vSphere-Lizenz (Enterprise Plus Edition) enthalten und wird in Ihrem Namen erworben.
* Für Nicht-Business-Partner-Benutzer können die von IBM bereitgestellten VMware-Lizenzen für diese Komponente benutzt werden. Wählen Sie hierzu **In Kauf einbeziehen** aus. Alternativ hierzu können Sie auch eine eigene Lizenz (Bring Your Own License; BYOL) verwenden, indem Sie **Lizenz selbst bereitstellen** auswählen und den eigenen Lizenzschlüssel angeben.

### Bestellübersicht

Auf Basis der für den Cluster ausgewählten Konfiguration werden die geschätzten Kosten sofort generiert und im rechten Fenster **Bestellübersicht** angezeigt.

## Vorgehensweise zum Hinzufügen von Clustern zu vCenter Server-Instanzen

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Bereitgestellte Instanzen**.
2. Klicken Sie in der Tabelle **vCenter Server-Instanzen** auf die Instanz, zu der Cluster hinzugefügt werden sollen.

   **Hinweis**: Vergewissern Sie sich, dass sich die Instanz im Status **Bereit** befindet. Andernfalls können Sie keine Cluster zur Instanz hinzufügen.

3. Klicken Sie im linken Navigationsfenster auf **Infrastruktur** und anschließend in der rechten oberen Ecke der Tabelle **CLUSTER** auf **Hinzufügen**.
4. Geben Sie auf der Seite **Cluster hinzufügen** den Clusternamen ein.
5. Wenn Sie für den Cluster ein anderes {{site.data.keyword.CloudDataCent_notm}} als Host verwenden möchten als das, in dem die Instanz gehostet wird, aktivieren Sie unter **Bare Metal Server** das Kontrollkästchen **Anderen Standort auswählen** und wählen Sie dann das gewünschte {{site.data.keyword.CloudDataCent_notm}} als Host für die Instanz aus.
6. Führen Sie die Bare-Metal-Konfiguration durch.
   * Wenn Sie **Vorkonfiguriert** ausgewählt haben, geben Sie die **Bare Metal Server-Konfiguration** und die **Anzahl der {{site.data.keyword.baremetal_short}}-Instanzen** an. Wenn Sie vSAN als Speicherlösung verwenden möchten, beachten Sie, dass mindestens 4 {{site.data.keyword.baremetal_short}}-Instanzen erforderlich sind.
   * Wenn Sie **Angepasst** ausgewählt haben, geben Sie das **CPU-Modell**, die Größe des **RAM** und die **Anzahl der {{site.data.keyword.baremetal_short}}-Instanzen** an.
7. Führen Sie die Speicherkonfiguration durch.
  * Wenn Sie **vSAN-Speicher** ausgewählt haben, geben Sie **Plattentyp und -größe für vSAN-Kapazitätsplatten** und **Anzahl der vSAN-Kapazitätsplatten** sowie die Methode an, mit der die **vSAN-Lizenz** bereitgestellt werden soll.
  * Wenn Sie **NFS-Speicher** ausgewählt haben und für alle Dateifreigaben dieselben Einstellungen hinzufügen und konfigurieren wollen, geben Sie die **Anzahl der Dateifreigaben**, **Größe** und **Leistung** an.
  * Wenn Sie **NFS-Speicher** ausgewählt haben und Dateifreigaben einzeln hinzufügen und bearbeiten möchten, wählen Sie **Dateifreigaben einzeln konfigurieren** aus, klicken Sie neben der Bezeichnung **NFS hinzufügen** auf das Symbol **+** und wählen Sie dann für jede Dateifreigabe jeweils **Größe** und **Leistung** aus. Sie müssen mindestens eine Dateifreigabe auswählen.
8. Geben Sie an, wie der vSphere-Lizenzschlüssel bereitgestellt wird:
  * Für Benutzer der Kategorie "Business Partner" ist die vSphere-Lizenz (Enterprise Plus Edition) enthalten und wird in Ihrem Namen erworben.
  * Für Nicht-Business-Partner-Benutzer können Sie eine der folgenden Optionen auswählen:
      * Wenn Sie neue Lizenzen für sich erwerben lassen möchten, wählen Sie **In Kauf einbeziehen** für die Komponente aus.
      * Wenn Sie Ihre eigene VMware-Lizenz für die Komponente verwenden möchten, wählen Sie die Option **Lizenz selbst bereitstellen** aus und geben Sie den zugehörigen Lizenzschlüssel ein.
9. Überprüfen Sie im Fenster **Bestellübersicht** die Clusterkonfiguration, bevor Sie den Cluster hinzufügen.
   1. Überprüfen Sie die Einstellungen für den Cluster.
   2. Überprüfen Sie die geschätzten Kosten des Clusters. Klicken Sie auf **Preisdetails**, um eine PDF-Datei mit der Zusammenfassung zu generieren. Ihre Bestellübersicht können Sie speichern oder drucken, indem Sie rechts oben im PDF-Fenster auf das Symbol **Drucken** bzw. **Herunterladen** klicken.
   3. Klicken Sie auf den Link bzw. die Links für die Bedingungen, die für Ihre Bestellung gelten, und vergewissern Sie sich, dass Sie mit diesen Bedingungen einverstanden sind, bevor Sie den Cluster hinzufügen.
   4. Klicken Sie auf **Bereitstellung**.

### Ergebnisse nach Hinzufügen von Clustern zu vCenter Server-Instanzen

1. Die Bereitstellung des Clusters wird automatisch gestartet und der Status des Clusters ändert sich in **Wird initialisiert**. Sie können den Status der Bereitstellung überprüfen, indem Sie den Bereitstellungsverlauf über die Seite **Zusammenfassung** der Instanz anzeigen.
2. Sobald der Cluster einsatzbereit ist, ändert sich sein Status in **Bereit**. Der neu hinzugefügte Cluster wird mit vSphere High Availability (HA) und vSphere Distributed Resource Scheduler (DRS) aktiviert.

**Wichtig**: Der Clustername kann nicht geändert werden. Wenn Sie den Clusternamen ändern, kann die Operation zum Hinzufügen oder Entfernen von ESXi-Servern im Cluster fehlschlagen.

## Cluster in vCenter Server-Instanzen anzeigen

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Bereitgestellte Instanzen**.
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
4. Klicken Sie auf einen Clusternamen, um die Details zu ESXi-Servern und Speicher anzuzeigen:

  * ESXi-Serverdetails:
     * **Name**: Der Name des ESXi-Servers im Format `<host_prefix><n>.<subdomain_label>.<root_domain>`, wobei Folgendes gilt:

       `host_prefix` ist das Hostnamenspräfix,

       `n` ist die Folgenummer des Servers,

       `subdomain_label` ist die Unterdomänenbezeichnung und

       `root_domain` ist der Rootdomänenname.

     * **Version**: Die Version des ESXi-Servers.
     * **Berechtigungsnachweise**: Der Benutzername und das Kennwort für den Zugriff auf den ESXi-Server.
     * **Private IP**: Die private IP-Adresse des ESXi-Servers.
     * **Status**: Der Status des ESXi-Servers, der einen der folgenden Werte aufweisen kann:
        <dl class="dl">
        <dt class="dt dlterm">Hinzugefügt</dt>
        <dd class="dd">Der ESXi-Server wurde hinzugefügt und kann verwendet werden. </dd>
        <dt class="dt dlterm">Wird hinzugefügt</dt>
        <dd class="dd">Der ESXi-Server wird gerade hinzugefügt. </dd>
        <dt class="dt dlterm">Wird gelöscht</dt>
        <dd class="dd">Der ESXi-Server wird gerade gelöscht.</dd>
        </dl>
  * Speicherdetails:
    * **Name**: Der Name des Datenspeichers.
    * **Größe**: Die Kapazität des Speichers.
    * **IOPS/GB**: Die Leistungsstufe des Speichers.
    * **NFS-Protokoll**: Die NFS-Version des Speichers.

## Cluster aus vCenter Server-Instanzen löschen

Wird ein Cluster nicht mehr benötigt, kann er aus einer Instanz gelöscht werden.

### Vorbereitende Schritte für die Löschung

* Gehen Sie wie folgt vor, um Cluster aus Instanzen zu löschen, die in V2.3 oder höheren Releases bereitgestellt werden.
* Für Cluster, die in Instanzen mit V2.2 oder älteren Releases bereitgestellt wurden, müssen Sie ein Upgrade der Instanz auf V2.3 durchführen, um die Cluster löschen zu können, die Sie zu der Instanz hinzugefügt haben.
* Es kann immer nur ein Cluster gleichzeitig gelöscht werden. Zum Löschen mehrerer Cluster müssen Sie die entsprechenden Cluster nacheinander löschen und dabei abwarten, bis der vorherige Cluster gelöscht wurde, bevor Sie versuchen, den nächsten Cluster zu löschen.
* Vergewissern Sie sich, dass alle Knoten in einem Cluster eingeschaltet und betriebsbereit sind, bevor Sie den Cluster löschen.
* Wenn Sie einen Cluster löschen, dann werden auch alle VMs (virtuellen Maschinen) des Clusters gelöscht und können nicht wiederhergestellt werden. Sollen die VMs beibehalten werden, dann müssen Sie sie auf andere Cluster migrieren.
* Der Standardcluster kann nicht gelöscht werden.

## Vorgehensweise zum Löschen von Clustern aus vCenter Server-Instanzen

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Bereitgestellte Instanzen**.
2. Klicken Sie in der Tabelle **vCenter Server-Instanzen** auf die Instanz, aus der Cluster gelöscht werden sollen.

   **Hinweis**: Vergewissern Sie sich, dass sich die Instanz im Status **Bereit** befindet. Andernfalls können Sie keine Cluster aus der Instanz löschen.

3. Klicken Sie im linken Navigationsfenster auf **Infrastruktur**. Suchen Sie in der Tabelle **CLUSTER** den Cluster, der gelöscht werden soll, und klicken Sie dann auf das Symbol **Löschen** in der Spalte **Aktionen**.
4. Vergewissern Sie sich, dass die Migration der virtuellen Maschinen (VMs) auf andere Cluster (sofern erforderlich) durchgeführt wurde und dass der Cluster tatsächlich gelöscht werden soll.

### Zugehörige Links

* [vCenter Server-Instanzen anzeigen](vc_viewinginstances.html)
* [Kapazität für vCenter Server-Instanzen erweitern und verringern](vc_addingremovingservers.html)
