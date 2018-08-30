---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-17"

---

# Cluster für VMware Federal-Instanzen hinzufügen, anzeigen und löschen

Die ESXi-Server, die Sie bei der Bestellung einer Instanz konfiguriert haben, werden standardmäßig unter **cluster1** gruppiert.

Sie können Cluster zu Ihren VMware Federal-Instanzen hinzufügen, um die Rechen- und Speicherkapazität zu erweitern. In einem Cluster können Sie ESXi-Server verwalten, um eine bessere Ressourcenzuordnung und hohe Verfügbarkeit zu erreichen. Die hinzugefügten Cluster können aus Ihren Instanzen gelöscht werden, wenn sie nicht mehr benötigt werden.

**Verfügbarkeit**: Die Funktion zum Hinzufügen und Löschen von Clustern steht nur für Instanzen zur Verfügung, die in V2.3 oder höheren Releases bereitgestellt (oder für die Upgrades auf diese Releases durchgeführt) wurden.

## Cluster zu VMware Federal-Instanzen hinzufügen

Sie können bis zu zehn Cluster zu einer Instanz hinzufügen. Wenn Sie einen Cluster für eine VMware Federal-Instanz hinzufügen, müssen Sie die folgenden Einstellungen angeben.

### Systemeinstellungen

Wenn Sie einen Cluster für eine VMware Federal-Instanz hinzufügen, müssen Sie die folgenden Einstellungen angeben.

#### Clustername

Der Clustername muss die folgenden Anforderungen erfüllen:
* Es sind nur alphanumerische Zeichen und Bindestriche (-) zulässig.
* Der Clustername muss mit einem alphanumerischen Zeichen beginnen und enden.
* Die maximale Länge des Clusternamens beträgt 30 Zeichen.
* Der Clustername muss innerhalb der VMware Federal-Instanz eindeutig sein.

#### Standort des Rechenzentrums

Als Rechenzentrum des Clusters wird standardmäßig das Rechenzentrum der VMware Federal-Instanz festgelegt.

### Einstellungen für Bare Metal Server

#### Angepasst

Geben Sie das CPU-Modell und den RAM (Arbeitsspeicher) für den Bare Metal Server an. Die verfügbaren Optionen können je nach der Version, in der Ihre Instanz ursprünglich bereitgestellt wurde, variieren.

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

Für einen Cluster werden mindestens 2 {{site.data.keyword.baremetal_short}}-Instanzen benötigt.

Für VMware Federal-Instanzen, die in V2.3 oder höher bereitgestellt werden, können Sie bis zu 59 {{site.data.keyword.baremetal_short}}-Instanzen für einen Cluster hinzufügen und gleichzeitig jeweils 1 bis 59 ESXi-Server hinzufügen.

Nach der Implementierung können Sie bis zu vier weitere Cluster erstellen. Für die vSAN-Speichereinstellungen werden für den ersten Cluster und die Cluster nach der Bereitstellung 4 Server benötigt.

### Speichereinstellungen

Die Speichereinstellungen sind von der Auswahl der Bare Metal Server-Konfiguration und des Speichertyps abhängig.

#### vSAN-Speicher

Geben Sie für vSAN die folgenden Speicheroptionen an:

* **Plattentyp und -größe für vSAN-Kapazitätsplatten**: Wählen Sie die Kapazität aus, die Ihrem Bedarf an gemeinsam genutzten Speicher entspricht.
* **Anzahl der vSAN-Kapazitätsplatten**: Wählen Sie die Anzahl der Platten für den gemeinsam genutzten vSAN-Speicher aus, die Sie hinzufügen wollen. Die Plattenanzahl muss 2, 4, 6 oder 8 sein.
* Wählen Sie die VMware vSAN 6.6-Lizenzedition (Advanced oder Enterprise) aus.

Falls Ihr erster Cluster den Typ "vSAN" aufwies, verwenden alle zusätzlichen vSAN-Cluster dieselbe vSAN-Lizenz und dieselbe Konfiguration wie der erste vSAN-Cluster. Dies gilt auch dann, wenn für einen (ersten oder zusätzlichen) Cluster in der Instanz die Bereitstellung von vSAN ausgewählt wurde. Beim ersten Mal wird von Ihnen die vSAN-Lizenz und die Edition angefordert. Bei der nächsten Auswahl von vSAN für einen zusätzlichen Cluster wird Ihre anfänglich getroffene Auswahl wiederverwendet.

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
  | 10 IOPS/GB | Diese Option ist für die aufwändigsten Workloadtypen wie beispielsweise die Analyse gedacht. Anwendungsbeispiele sind Hochtransaktionsdatenbanken und andere leistungskritische Datenbanken. Diese Leistungsstufe ist auf eine maximale Kapazität von 4 TB pro Dateifreigabe begrenzt.|

### Lizenzierungseinstellungen

	Von {{site.data.keyword.IBM}} bereitgestellte VMware-Lizenzen für folgende Ressourcen:
  * VMware vSphere Enterprise Plus 6.5u1
  * VMware vCenter Server 6.5
  * VMware NSX Service Providers Edition (Base, Advanced oder Enterprise) 6.4
  * (Für vSAN-Cluster) VMware vSAN Advanced oder Enterprise 6.6

### Bestellübersicht

Auf Basis der für den Cluster ausgewählten Konfiguration werden die geschätzten Kosten sofort generiert und im rechten Fenster **Bestellübersicht** angezeigt.

## Vorgehensweise zum Hinzufügen von Clustern zu VMware Federal-Instanzen

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_full}}-Konsole im linken Navigationsfenster auf **Bereitgestellte Instanzen**.
2. Klicken Sie in der Tabelle **vCenter Server-Instanz** auf die Instanz, zu der Cluster hinzugefügt werden sollen.

   **Hinweis**: Vergewissern Sie sich, dass sich die Instanz im Status **Bereit** befindet. Andernfalls können Sie keine Cluster zur Instanz hinzufügen.

3. Klicken Sie im linken Navigationsfenster auf **Infrastruktur** und anschließend in der rechten oberen Ecke der Tabelle **CLUSTER** auf **Hinzufügen**.
4. Geben Sie auf der Seite **Cluster hinzufügen** den Clusternamen ein.
5. Wählen Sie das **CPU-Modell**, die Menge des **RAM** und die **Anzahl der Bare Metal Server** für die Bare-Metal-Konfiguration aus.
6. Führen Sie die Speicherkonfiguration durch.
  * Wenn Sie **vSAN-Speicher** ausgewählt haben, geben Sie **Plattentyp und -größe für vSAN-Kapazitätsplatten** und **Anzahl der vSAN-Kapazitätsplatten** sowie die Methode an, mit der die **vSAN-Lizenz** bereitgestellt werden soll.
  * Wenn Sie **NFS-Speicher** ausgewählt haben und für alle Dateifreigaben dieselben Einstellungen hinzufügen und konfigurieren wollen, geben Sie die **Anzahl der Dateifreigaben**, **Größe** und **Leistung** an.
  * Wenn Sie **NFS-Speicher** ausgewählt haben und Dateifreigaben einzeln hinzufügen und bearbeiten möchten, wählen Sie **Dateifreigaben einzeln konfigurieren** aus, klicken Sie neben der Bezeichnung **NFS hinzufügen** auf das Symbol **+** und wählen Sie dann für jede Dateifreigabe jeweils **Größe** und **Leistung** aus. Sie müssen mindestens eine Dateifreigabe auswählen.
7. Wählen Sie die Lizenzedition für VMware vSAN für die Lizenzkonfiguration aus.
8. Überprüfen Sie im Fenster **Bestellübersicht** die Clusterkonfiguration, bevor Sie den Cluster hinzufügen.
   1. Überprüfen Sie die Einstellungen für den Cluster.
   2. Überprüfen Sie die geschätzten Kosten des Clusters. Klicken Sie auf **Preisdetails**, um eine PDF-Datei mit der Zusammenfassung zu generieren. Ihre Bestellübersicht können Sie speichern oder drucken, indem Sie rechts oben im PDF-Fenster auf das Symbol **Drucken** bzw. **Herunterladen** klicken.
   3. Klicken Sie auf den Link bzw. die Links für die Bedingungen, die für Ihre Bestellung gelten, und vergewissern Sie sich, dass Sie mit diesen Bedingungen einverstanden sind, bevor Sie den Cluster hinzufügen.
   4. Klicken Sie auf **Bereitstellung**.

## Ergebnisse nach Hinzufügen von Clustern zu VMware Federal-Instanzen

1. Die Bereitstellung des Clusters wird automatisch gestartet und der Status des Clusters ändert sich in **Wird initialisiert**. Sie können den Status der Bereitstellung überprüfen, indem Sie den Bereitstellungsverlauf über die Übersichtsseite für die Instanz anzeigen.
2. Sobald der Cluster einsatzbereit ist, ändert sich sein Status in **Bereit**. Der neu hinzugefügte Cluster wird mit vSphere High Availability (HA) und vSphere Distributed Resource Scheduler (DRS) aktiviert.

**Wichtig**: Der Clustername kann nicht geändert werden. Wenn Sie den Clusternamen ändern, kann die Operation zum Hinzufügen oder Entfernen von ESXi-Servern im Cluster fehlschlagen.

## Cluster in VMware Federal-Instanzen anzeigen

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Bereitgestellte Instanzen**.
2. Klicken Sie in der Tabelle **vCenter Server-Instanzen** auf eine Instanz, um die Cluster in dieser Instanz anzuzeigen.
3. Klicken Sie im linken Navigationsfenster auf **Infrastruktur**. Prüfen Sie in der Tabelle **CLUSTER** die Zusammenfassung für die Cluster:
   * **Name**: Der Name des Clusters.
   * **ESXi-Server**: Die Anzahl der ESXi-Server im Cluster.
   * **CPU**: Die CPU-Spezifikation der ESXi-Server im Cluster.
   * **Angepasste vSAN-Platten**: Die Anzahl der vSAN-Platten im Cluster, einschließlich des Plattentyps und der Kapazität.
   * **Speicher**: Die Gesamtspeichergröße der ESXi-Server im Cluster.
   * **Standort des Rechenzentrums**: Das Rechenzentrum, in dem der Cluster gehostet wird.
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
4. Klicken Sie auf einen Clusternamen, um die Details zum ESXi-Server, zum Speicher und zur Lizenz anzuzeigen.

### ESXi-Server

   * **Name**: Der Name des ESXi-Servers im Format `<host_prefix><n>.<subdomain_label>.<root_domain>`, wobei Folgendes gilt:

      `host_prefix` ist das Hostnamenspräfix,
       `n` ist die Folgenummer des ESXi-Servers,
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

### Speicher

   * **Name**: Der Name des Datenspeichers.
   * **Größe**: Die Kapazität des Speichers.
   * **IOPS/GB**: Die Leistungsstufe des Speichers.
   * **NFS/Portal**: Die NFS-Version des Speichers.
   * **Status**: Der Status des Speichers, der einen der folgenden Werte aufweisen kann:
        <dl class="dl">
        <dt class="dt dlterm">Hinzugefügt</dt>
        <dd class="dd">Der ESXi-Server wurde hinzugefügt und kann verwendet werden. </dd>
        <dt class="dt dlterm">Wird hinzugefügt</dt>
        <dd class="dd">Der ESXi-Server wird gerade hinzugefügt. </dd>
        <dt class="dt dlterm">Wird gelöscht</dt>
        <dd class="dd">Der ESXi-Server wird gerade gelöscht.</dd>
        </dl>

### Lizenzen

   * **Lizenz**: Der Lizenztyp.
   * **Bestelltyp**: Die Lizenz wurde von IBM oder vom Benutzer bereitgestellt.
   * **Lizenzedition**: Die Version und Edition der Lizenz.
   * **Lizenzschlüssel**: Der Lizenzschlüssel.
   * **Gesamtkapazität (CPU)**: Die Gesamtmenge der CPU-Kapazität für die Lizenz.
   * **Freie Kapazität (CPU)**: Die Menge an freier CPU-Kapazität für die Lizenz.

## Cluster aus VMware Federal-Instanzen löschen

Wird ein Cluster nicht mehr benötigt, kann er aus einer Instanz gelöscht werden.

**Hinweis**: Gehen Sie wie folgt vor, um Cluster aus Instanzen zu entfernen, die in V2.3 oder höheren Releases bereitgestellt (oder für die Upgrades auf diese Releases durchgeführt) wurden.

### Vorbereitende Schritte für die Löschung

* Gehen Sie wie folgt vor, um Cluster aus Instanzen zu löschen, die in V2.3 oder höheren Releases bereitgestellt werden.
* Für Cluster, die in Instanzen mit V2.2 oder älteren Releases bereitgestellt wurden, müssen Sie ein Upgrade der Instanz auf V2.3 durchführen, um die Cluster löschen zu können, die Sie zu der Instanz hinzugefügt haben.
* Es kann immer nur ein Cluster gleichzeitig gelöscht werden. Zum Löschen mehrerer Cluster müssen Sie die entsprechenden Cluster nacheinander löschen und dabei abwarten, bis der vorherige Cluster gelöscht wurde, bevor Sie versuchen, den nächsten Cluster zu löschen.
* Vergewissern Sie sich, dass alle Knoten in einem Cluster eingeschaltet und betriebsbereit sind, bevor Sie den Cluster löschen.
* Wenn Sie einen Cluster löschen, dann werden auch alle VMs (virtuellen Maschinen) des Clusters gelöscht und können nicht wiederhergestellt werden. Sollen die VMs beibehalten werden, dann müssen Sie sie auf andere Cluster migrieren.
* Der Standardcluster kann nicht gelöscht werden.

## Vorgehensweise zum Löschen von Clustern aus VMware Federal-Instanzen

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Bereitgestellte Instanzen**.
2. Klicken Sie in der Tabelle **vCenter Server-Instanzen** auf die Instanz, aus der Cluster gelöscht werden sollen.

   **Hinweis**: Vergewissern Sie sich, dass sich die Instanz im Status **Bereit** befindet. Andernfalls können Sie keine Cluster aus der Instanz löschen.

3. Klicken Sie im linken Navigationsfenster auf **Infrastruktur**. Suchen Sie in der Tabelle **CLUSTER** den Cluster, der gelöscht werden soll, und klicken Sie dann auf das Symbol **Löschen** in der Spalte **Aktionen**.

### Zugehörige Links

* [VMware Federal-Instanzen anzeigen](vc_fed_viewinginstance.html)
* [Kapazität für VMware Federal-Instanzen erweitern und verringern](vc_fed_addingremovingservers.html)
