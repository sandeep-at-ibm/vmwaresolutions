---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-28"

---

# Cluster für Cloud Foundation-Instanzen hinzufügen, anzeigen und löschen

Die ESXi-Server, die Sie bei der Bestellung einer Instanz konfiguriert haben, werden unter einem Standardcluster gruppiert. Der Standardclustername lautet wie folgt:
* Bei in V2.1 oder höheren Releases bereitgestellten Instanzen: **MGMT-Cluster-`<subdomain_label>`**
* Bei in V2.0 oder älteren Releases bereitgestellten Instanzen: **SDDC-Cluster**

Sie können eigene Cluster zu Ihren VMware Cloud Foundation-Instanzen hinzufügen, um die Rechen- und Speicherkapazität zu erweitern. In einem Cluster können Sie ESXi-Server verwalten, um eine bessere Ressourcenzuordnung und hohe Verfügbarkeit zu erreichen. Die hinzugefügten Cluster können aus Ihren Instanzen gelöscht werden, wenn sie nicht mehr benötigt werden.

**Verfügbarkeit:**
* Die Funktion zum Hinzufügen von Clustern steht nur für Instanzen zur Verfügung, die in V2.0 oder höheren Releases bereitgestellt (oder für die Upgrades auf diese Releases durchgeführt) wurden.
* Die Funktion zum Löschen von Clustern steht nur für Instanzen zur Verfügung, die in V2.3 oder höheren Releases bereitgestellt (oder für die Upgrades auf diese Releases durchgeführt) wurden.  

## Cluster zu Cloud Foundation-Instanzen hinzufügen

Sie können bis zu fünf Cluster zu einer Cloud Foundation-Instanz hinzufügen.

### Systemeinstellungen

Wenn Sie einen Cluster zu einer Cloud Foundation-Instanz hinzufügen, müssen Sie die folgenden Einstellungen angeben.

#### Clustername

Der Clustername muss die folgenden Anforderungen erfüllen:
* Es sind nur alphanumerische Zeichen und Bindestriche (-) zulässig.
* Der Clustername muss mit einem alphanumerischen Zeichen beginnen und enden.
* Die maximale Länge des Clusternamens beträgt 30 Zeichen.
* Der Clustername muss innerhalb der Cloud Foundation-Instanz eindeutig sein.

#### Standort des Rechenzentrums

Der Standort des {{site.data.keyword.CloudDataCent}}s für den Cluster wird standardmäßig auf das {{site.data.keyword.CloudDataCent_notm}} der Cloud Foundation-Instanz gesetzt. Sie können den Cluster in einem anderen {{site.data.keyword.CloudDataCent_notm}} als die bereitgestellte Instanz bereitstellen, müssen aber sicherstellen, dass die Netzlatenz zwischen den beiden {{site.data.keyword.CloudDataCents_notm}} weniger als 150 Millisekunden beträgt. Zur Überprüfung der Netzlatenz können Sie ein Tool wie [SoftLayer IP Backbone Looking Glass](http://lg.softlayer.com/){:new_window} verwenden.

Welche Rechenzentren für Sie verfügbar sind, richtet sich nach der Bare Metal Server-Konfiguration, die für die Bereitstellung ausgewählt wurde. Wurde die Konfiguration des Typs **Angepasst** ausgewählt, können Sie den Cluster auch in einem anderen {{site.data.keyword.cloud_notm}}-Infrastrukturpod bereitstellen, falls das ausgewählte Rechenzentrum weitere Pods enthält. Diese Konfiguration ist hilfreich, wenn der Standardpod der {{site.data.keyword.cloud_notm}}-Infrastruktur, in dem die erste Instanz bereitgestellt wird, seine maximale Kapazität erreicht hat.

**Hinweis:** Die standardisierten Bare Metal Server-Konfigurationen des Typs **S (Klein)** und **L (Groß)** verwenden einen Standardpod, der nicht geändert werden kann.

Wenn Sie den Cluster in einem anderen Rechenzentrum oder Pod bereitstellen, werden drei weitere VLANs für die Verwendung mit den bestellten {{site.data.keyword.baremetal_short}}-Instanzen bestellt.

### Einstellungen für Bare Metal Server

Sie können entweder **Angepasst** oder **Vorkonfiguriert** auswählen.

#### Angepasst

Für die Einstellung **Angepasst** steht eine Reihe von Optionen für **CPU-Modell** und **RAM** zur Verfügung. Die verfügbaren Optionen können je nach der Version, in der Ihre Instanz ursprünglich bereitgestellt wurde, variieren.

Tabelle 1. Optionen für angepasste {{site.data.keyword.baremetal_short}}-Instanzen

| CPU-Modelloptionen   | RAM-Optionen   |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4 / 16 Kerne insgesamt, 2,1 GHz | 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2650 v4 / 24 Kerne insgesamt, 2,2 GHz | 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2690 v4 / 28 Kerne insgesamt, 2,6 GHz | 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon Silver 4110-Prozessor / 16 Kerne insgesamt, 2,1 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon Gold 5120-Prozessor / 28 Kerne insgesamt, 2,2 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon Gold 6140-Prozessor / 36 Kerne insgesamt, 2,3 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |

#### Vorkonfiguriert

Für die Einstellung **Vorkonfiguriert** können Sie abhängig von Ihren Anforderungen eine **Bare Metal Server-Konfiguration** auswählen:
* S (Klein): Dual Intel Xeon E5-2650 v4 / 24 Kerne insgesamt, 2,2 GHz / 128 GB RAM / 12 Platten
* L (Groß): Dual Intel Xeon E5-2690 v4 / 28 Kerne insgesamt, 2,6 GHz / 512 GB RAM / 12 Platten

### vSAN-Speichereinstellungen

Für die Bare Metal Server-Konfigurationen vom Typ **Vorkonfiguriert** können die vSAN-Speichereinstellungen nicht geändert werden:
* Für die Konfiguration vom Typ **S (Klein)** werden zwei SSD-SED-Plattenlaufwerke mit jeweils 1,9 TB bestellt.
* Für die Konfiguration vom Typ **L (Groß)** werden vier SSD-SED-Plattenlaufwerke mit jeweils 3,8 TB bestellt.

Bei Bare Metal Server-Konfigurationen des Typs **Angepasst** können Sie den vSAN-Speicher durch Angeben der folgenden Einstellungen anpassen:

* **Plattentyp und Größe für vSAN-Kapazitätsplatten**: Wählen Sie die für die Kapazitätsplatten benötigte Option aus.
* **Anzahl der vSAN-Kapazitätsplatten**: Geben Sie die Anzahl der hinzuzufügenden Kapazitätsplatten an.
* Wenn Sie über den Grenzwert von acht Stück hinaus Kapazitätsplatten hinzufügen möchten, müssen Sie das Feld für **Hohe Leistung mit Intel Optane** auswählen. Diese Option stellt zwei zusätzliche Kapazitätsplattenpositionen für eine Gesamtzahl von 10 Kapazitätsplatten bereit und ist für Workloads nützlich, die eine geringere Latenzzeit und einen höheren Durchsatz an E/A-Operationen pro Sekunde erfordern. Die Option **Hohe Leistung mit Intel Optane** steht nur für die Dualprozessoren Intel Xeon Gold 5120 und 6140 zur Verfügung.
* Überprüfen Sie die Werte für **Plattentyp für vSAN-Cacheplatten** und **Anzahl der vSAN-Cacheplatten**. Diese Werte hängen davon ab, ob Sie das Feld **Hohe Leistung mit Intel Optane** ausgewählt haben.

### Lizenzierungseinstellungen

Sie können die Lizenzierungsoptionen für die VMware-Komponenten im Cluster einschließlich VMware vSphere und VMware vSAN angeben:
* Für Benutzer der Kategorie "IBM Business Partner" sind die vSphere-Lizenz (Enterprise Plus Edition) und die vSAN-Lizenz enthalten und werden in Ihrem Namen erworben. Für die vSAN-Lizenz muss allerdings die Edition angegeben werden.
* Für Benutzer, die keine IBM Business Partner sind, können die von IBM bereitgestellten VMware-Lizenzen für die Komponenten verwendet werden. Wählen Sie hierzu **In Kauf einbeziehen** aus. Alternativ hierzu können Sie auch eigene Lizenzen (Bring Your Own License; BYOL) für die Komponenten verwenden, indem Sie **Lizenz selbst bereitstellen** auswählen und die eigenen Lizenzschlüssel angeben.

## Vorgehensweise zum Hinzufügen von Clustern zu Cloud Foundation-Instanzen

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Bereitgestellte Instanzen**.
2. Klicken Sie in der Tabelle **Cloud Foundation-Instanzen** auf die Instanz, zu der Cluster hinzugefügt werden sollen.

   **Hinweis:** Vergewissern Sie sich, dass sich die Instanz im Status **Bereit** befindet. Andernfalls können Sie keine Cluster zur Instanz hinzufügen.

3. Klicken Sie im linken Navigationsfenster auf **Infrastruktur** und anschließend rechts oben in der Tabelle **CLUSTER** auf **Hinzufügen**.
4. Geben Sie auf der Seite **Cluster hinzufügen** den Clusternamen ein.
5. Wenn Sie für den Cluster ein anderes {{site.data.keyword.CloudDataCent_notm}} als Host verwenden möchten als das, in dem die Instanz gehostet wird, aktivieren Sie unter **Bare Metal Server** das Kontrollkästchen **Anderen Standort auswählen** und wählen Sie dann das gewünschte {{site.data.keyword.CloudDataCent_notm}} als Host für die Instanz aus.
6. Führen Sie die Bare-Metal-Konfiguration durch:
   * Wenn Sie **Angepasst** ausgewählt haben, geben Sie das **CPU-Modell** und die Größe des **RAM** an.
   * Wenn Sie **Vorkonfiguriert** ausgewählt haben, geben Sie die **Bare Metal Server-Konfiguration** an.
7. Führen Sie die Speicherkonfiguration durch:
   * Wenn Sie für die Bare Metal-Konfiguration die Option **Vorkonfiguriert** ausgewählt haben, können die Speichereinstellungen für die Bare-Metal-Serverkonfigurationen **S (Klein)** und **L (Groß)** nicht geändert werden.
   * Wenn Sie für die Bare Metal-Konfiguration die Option **Angepasst** ausgewählt haben, geben Sie die Plattentypen für die vSAN-Kapazitäts- und Cacheplatten sowie die Anzahl der Platten an. Falls Sie mehr Speicher benötigen, müssen Sie das Feld für **Hohe Leistung mit Intel Optane** auswählen.
8. Geben Sie an, wie Ihre Lizenzschlüssel bereitgestellt werden:
   * Für Benutzer der Kategorie "IBM Business Partner" sind die vSphere-Lizenz (Enterprise Plus Edition) und die vSAN-Lizenz enthalten und werden in Ihrem Namen erworben. Für die vSAN-Lizenz muss allerdings die Edition angegeben werden.
   * Für Benutzer, bei denen es sich nicht um IBM Business Partner handelt, können Sie eine der folgenden Optionen auswählen:
       * Wenn Sie neue Lizenzen für sich erwerben möchten, wählen Sie **In Kauf einbeziehen** für die Komponenten aus. Wählen Sie für VMware vSAN auch die Lizenzedition aus.
       * Wenn Sie Ihre eigene VMware-Lizenz für eine Komponente verwenden möchten, wählen Sie die Option **Lizenz selbst bereitstellen** aus und geben Sie den Lizenzschlüssel für die Komponente ein.
9. Überprüfen Sie im Fenster **Bestellübersicht** die Clusterkonfiguration, bevor Sie den Cluster hinzufügen.
   1. Überprüfen Sie die Einstellungen für den Cluster.
   2. Überprüfen Sie die geschätzten Kosten des Clusters. Klicken Sie auf **Preisdetails**, um eine PDF-Datei mit der Zusammenfassung zu generieren. Ihre Bestellübersicht können Sie speichern oder drucken, indem Sie rechts oben im PDF-Fenster auf das Symbol **Drucken** bzw. **Herunterladen** klicken.
   3. Klicken Sie auf den bzw. die Link(s) für die Bedingungen, die für Ihre Bestellung gelten, und vergewissern Sie sich, dass Sie mit diesen Bedingungen einverstanden sind, bevor Sie den Cluster hinzufügen.
   4. Klicken Sie auf **Bereitstellung**.

### Ergebnisse nach Hinzufügen von Clustern zu Cloud Foundation-Instanzen

1. Die Bereitstellung des Clusters wird automatisch gestartet und der Status des Clusters ändert sich in **Wird initialisiert**. Sie können den Status der Bereitstellung überprüfen, indem Sie den Bereitstellungsverlauf auf der Übersichtsseite für die Instanz anzeigen.
2. Sobald der Cluster einsatzbereit ist, ändert sich sein Status in **Bereit**. Der neu hinzugefügte Cluster wird mit vSphere High Availability (HA) und vSphere Distributed Resource Scheduler (DRS) aktiviert.

**Wichtig:** Der Clustername kann nicht geändert werden. Wenn Sie den Clusternamen ändern, kann die Operation zum Hinzufügen oder Entfernen von ESXi-Servern im Cluster fehlschlagen.

## Vorgehensweise zum Anzeigen von Clustern in Cloud Foundation-Instanzen

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Bereitgestellte Instanzen**.
2. Klicken Sie in der Tabelle **Cloud Foundation-Instanzen** auf eine Instanz, um die Cluster in dieser Instanz anzuzeigen.
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
4. Klicken Sie auf einen Clusternamen, um die Liste der ESXi-Server und die zugehörigen Informationen anzuzeigen:

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
   * Die Details der vSAN-Lizenz und der vSphere-Lizenz. Die Details der vSphere-Lizenz stehen nur zur Verfügung, wenn Sie bei der Clusterbestellung die Option zur Verwendung Ihrer eigenen VMware-Lizenz (BYOL – Bring Your Own License) ausgewählt haben.
       * **Lizenztyp**: Die vSAN-Lizenz oder die vSphere-Lizenz.
       * **Bestelltyp**: Die Lizenz wird vom Benutzer bereitgestellt (BYOL = Bring Your Own License) oder im Namen des Benutzers erworben.
       * **Lizenzedition**: Die Edition der Lizenz.
       * **Lizenzschlüssel**: Der Lizenzschlüssel.
       * **Gesamtkapazität (CPU)**: Die Gesamtkapazität oder die Anzahl der CPUs, die über die Lizenz bereitgestellt wird.
       * **Freie Kapazität (CPU)**: Die Kapazität, die über die Lizenz verfügbar ist.

## Cluster aus Cloud Foundation-Instanzen löschen

Wird ein Cluster nicht mehr benötigt, kann er aus einer Instanz gelöscht werden.

### Vorbereitende Schritte für die Löschung

* Gehen Sie wie folgt vor, um Cluster aus Instanzen zu löschen, die in V2.3 oder höheren Releases bereitgestellt werden.
* Für Cluster, die in Instanzen mit V2.2 oder älteren Releases bereitgestellt wurden, müssen Sie ein Upgrade der Instanz auf V2.3 durchführen, um die Cluster löschen zu können, die Sie zu der Instanz hinzugefügt haben.
* Es kann immer nur ein Cluster gleichzeitig gelöscht werden. Zum Löschen mehrerer Cluster müssen Sie die entsprechenden Cluster nacheinander löschen und dabei abwarten, bis der vorherige Cluster gelöscht wurde, bevor Sie versuchen, den nächsten Cluster zu löschen.
* Stellen Sie sicher, dass alle Knoten in einem Cluster eingeschaltet und betriebsbereit sind, bevor Sie den Cluster löschen.
* Wenn Sie einen Cluster löschen, werden auch alle VMs (virtuellen Maschinen) des Clusters gelöscht und können nicht wiederhergestellt werden. Sollen die VMs beibehalten werden, dann müssen Sie sie auf andere Cluster migrieren.
* Der Standardcluster kann nicht gelöscht werden.

## Vorgehensweise zum Löschen von Clustern aus Cloud Foundation-Instanzen

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Bereitgestellte Instanzen**.
2. Klicken Sie in der Tabelle **Cloud Foundation-Instanzen** auf die Instanz, aus der Cluster gelöscht werden sollen.

   **Hinweis:** Vergewissern Sie sich, dass sich die Instanz im Status **Bereit** befindet. Andernfalls können Sie keine Cluster aus der Instanz löschen.

3. Klicken Sie im linken Navigationsfenster auf **Infrastruktur**. Suchen Sie in der Tabelle **CLUSTER** den Cluster, der gelöscht werden soll, und klicken Sie dann auf das Symbol **Löschen**.
4. Vergewissern Sie sich, dass die Migration der VMs auf andere Cluster (sofern erforderlich) durchgeführt wurde und dass der Cluster tatsächlich gelöscht werden soll.

### Zugehörige Links

* [Cloud Foundation-Instanzen anzeigen](sd_viewinginstances.html)
* [Kapazität für Cloud Foundation-Instanzen erweitern und verringern](sd_addingremovingservers.html)
