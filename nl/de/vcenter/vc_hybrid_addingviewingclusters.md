---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-19"

---

# Cluster für vCenter Server with Hybridity Bundle-Instanzen hinzufügen, anzeigen und löschen

Die ESXi-Server, die Sie bei der Bestellung einer Instanz konfiguriert haben, werden standardmäßig unter **cluster1** gruppiert.

Sie können Cluster zu Ihrer VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle-Instanz hinzufügen, um die Rechen- und Speicherkapazität zu erweitern. In einem Cluster können Sie ESXi-Server verwalten, um eine bessere Ressourcenzuordnung und hohe Verfügbarkeit zu erreichen. Die hinzugefügten Cluster können aus Ihrer Instanz gelöscht werden, wenn sie nicht mehr benötigt werden.

## Cluster zu vCenter Server with Hybridity Bundle-Instanzen hinzufügen

Sie können bis zu 10 Cluster zu Ihrer vCenter Server with Hybridity Bundle-Instanz hinzufügen.

### Systemeinstellungen

Wenn Sie einen Cluster für eine vCenter Server with Hybridity Bundle-Instanz hinzufügen, müssen Sie die folgenden Einstellungen angeben.

#### Clustername

Der Clustername muss die folgenden Anforderungen erfüllen:
* Es sind nur alphanumerische Zeichen und Bindestriche (-) zulässig.
* Der Clustername muss mit einem alphanumerischen Zeichen beginnen und enden.
* Die maximale Länge des Clusternamens beträgt 30 Zeichen.
* Der Clustername muss innerhalb der vCenter Server with Hybridity Bundle-Instanz eindeutig sein.

#### Standort des Rechenzentrums

Der Standort des {{site.data.keyword.CloudDataCent_notm}}s für den Cluster wird standardmäßig auf das {{site.data.keyword.CloudDataCent_notm}} der vCenter Server-Instanz gesetzt. Sie können den Cluster in einem anderen {{site.data.keyword.CloudDataCent_notm}} als die bereitgestellte Instanz bereitstellen, müssen aber sicherstellen, dass die Netzlatenz zwischen den beiden {{site.data.keyword.CloudDataCents_notm}} weniger als 150 Millisekunden beträgt. Zur Überprüfung der Netzlatenz können Sie ein Tool wie [SoftLayer IP Backbone Looking Glass](http://lg.softlayer.com/){:new_window} verwenden.

Wenn Sie den Cluster in einem anderen {{site.data.keyword.CloudDataCent_notm}}- oder {{site.data.keyword.cloud_notm}}-Infrastrukturpod bereitstellen, werden drei zusätzliche VLANs zur Verwendung mit den bestellten {{site.data.keyword.baremetal_short}}-Instanzen bestellt.

### Einstellungen für Bare Metal Server

#### Angepasst

Geben Sie das CPU-Modell und den RAM (Arbeitsspeicher) für den Bare Metal Server an. Die verfügbaren Optionen können je nach der Version, in der Ihre Instanz ursprünglich bereitgestellt wurde, variieren.

Tabelle 2. Optionen für angepasste Bare Metal Server-Instanzen

| CPU-Optionen        | RAM-Optionen       |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4 / 16 Kerne insgesamt, 2,1 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2650 v4 / 24 Kerne insgesamt, 2,2 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2690 v4 / 28 Kerne insgesamt, 2,6 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon Gold 6140-Prozessor / 36 Kerne insgesamt, 2,3 GHz | 96 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon Silver 4110-Prozessor / 16 Kerne insgesamt, 2,1 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon Gold 5120-Prozessor / 28 Kerne insgesamt, 2,2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon Gold 6140-Prozessor / 36 Kerne insgesamt, 2,3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |

#### Bare Metal Server-Anzahl

Für einen Cluster werden mindestens zwei {{site.data.keyword.baremetal_short}}-Instanzen benötigt.

Sie können bis zu 59 {{site.data.keyword.baremetal_short}}-Instanzen für einen Cluster und gleichzeitig 1 bis 59 ESXi-Server hinzufügen.

Nach der Implementierung können Sie bis zu vier weitere Cluster erstellen. Für VMware vSAN-Speicher werden für den ersten Cluster und die Cluster nach der Bereitstellung 4 Server benötigt.

### vSAN-Speichereinstellungen

VMware vSAN 6.6 ist Bestandteil der Bestellung Ihrer vCenter Server with Hybridity Bundle-Instanz. Für die Lizenzedition müssen Sie entweder **Advanced** oder **Enterprise** angeben.

* **Plattentyp und -größe für vSAN-Kapazitätsplatten**: Wählen Sie die Kapazität aus, die Ihrem Bedarf an gemeinsam genutzten Speicher entspricht.
* **Anzahl der vSAN-Kapazitätsplatten**: Wählen Sie die Anzahl der Platten für den gemeinsam genutzten vSAN-Speicher aus, die Sie hinzufügen wollen. Die Plattenanzahl muss 2, 4, 6 oder 8 sein.
* Wählen Sie die VMware vSAN 6.6-Lizenzedition (Advanced oder Enterprise) aus.

### Lizenzierungseinstellungen

Von IBM bereitgestellte VMware-Lizenzen für folgende Ressourcen:
  * VMware vSphere Enterprise Plus 6.5u1
  * VMware vCenter Server 6.5
  * VMware NSX Service Providers Edition (Advanced oder Enterprise) 6.4

### Bestellübersicht

Auf Basis der für den Cluster ausgewählten Konfiguration werden die geschätzten Kosten sofort generiert und im rechten Fenster **Bestellübersicht** angezeigt.

## Vorgehensweise zum Hinzufügen von Clustern zu vCenter Server with Hybridity Bundle-Instanzen

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Bereitgestellte Instanzen**.
2. Klicken Sie in der Tabelle **vCenter Server-Instanzen** auf die Instanz, um die Cluster in dieser Instanz anzuzeigen.

   **Hinweis**: Vergewissern Sie sich, dass sich die Instanz im Status **Bereit** befindet. Andernfalls können Sie keine Cluster zur Instanz hinzufügen.

3. Klicken Sie im linken Navigationsfenster auf **Infrastruktur** und anschließend in der rechten oberen Ecke der Tabelle **CLUSTER** auf **Hinzufügen**.
4. Geben Sie auf der Seite **Cluster hinzufügen** den Clusternamen ein.
5. Wenn Sie für den Cluster ein anderes {{site.data.keyword.CloudDataCent_notm}} als Host verwenden möchten als das, in dem die Instanz gehostet wird, aktivieren Sie unter **Bare Metal Server** das Kontrollkästchen **Anderen Standort auswählen** und wählen Sie dann das gewünschte {{site.data.keyword.CloudDataCent_notm}} als Host für die Instanz aus.
6. Wählen Sie das **CPU-Modell**, die Menge des **RAM** und die **Anzahl der Bare Metal Server** für die Bare-Metal-Konfiguration aus.
7.  Wählen Sie für die Speicherkonfiguration **vSAN-Speicher** und dann **Anzahl der vSAN-Kapazitätsplatten** und **Plattentyp und -größe für vSAN-Kapazitätsplatten** aus.
8. Wählen Sie die Lizenzedition für VMware vSAN für die Lizenzkonfiguration aus.
9. Überprüfen Sie im Fenster **Bestellübersicht** die Clusterkonfiguration, bevor Sie den Cluster hinzufügen.
   1. Überprüfen Sie die Einstellungen für den Cluster.
   2. Überprüfen Sie die geschätzten Kosten des Clusters. Klicken Sie auf **Preisdetails**, um eine PDF-Datei mit der Zusammenfassung zu generieren. Ihre Bestellübersicht können Sie speichern oder drucken, indem Sie rechts oben im PDF-Fenster auf das Symbol **Drucken** bzw. **Herunterladen** klicken.
   3. Klicken Sie auf den Link bzw. die Links für die Bedingungen, die für Ihre Bestellung gelten, und vergewissern Sie sich, dass Sie mit diesen Bedingungen einverstanden sind, bevor Sie den Cluster hinzufügen.
   4. Klicken Sie auf **Bereitstellung**.

### Ergebnisse nach Hinzufügen von Clustern zu vCenter Server with Hybridity Bundle-Instanzen

1. Die Bereitstellung des Clusters wird automatisch gestartet und der Status des Clusters ändert sich in **Wird initialisiert**. Sie können den Status der Bereitstellung überprüfen, indem Sie den Bereitstellungsverlauf über die Seite **Zusammenfassung** der Instanz anzeigen.
2. Sobald der Cluster einsatzbereit ist, ändert sich sein Status in **Bereit**. Der neu hinzugefügte Cluster wird mit vSphere High Availability (HA) und vSphere Distributed Resource Scheduler (DRS) aktiviert.

**Wichtig**: Der Clustername kann nicht geändert werden. Wenn Sie den Clusternamen ändern, kann die Operation zum Hinzufügen oder Entfernen von ESXi-Servern im Cluster fehlschlagen.

## Cluster in vCenter Server with Hybridity Bundle-Instanzen anzeigen

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Bereitgestellte Instanzen**.
2. Klicken Sie in der Tabelle **vCenter Server-Instanzen** auf die Instanz, um die Cluster in dieser Instanz anzuzeigen.
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

## Cluster aus vCenter Server with Hybridity Bundle-Instanzen löschen

Wird ein Cluster nicht mehr benötigt, kann er aus einer Instanz gelöscht werden.

### Vorbereitende Schritte für die Löschung

* Es kann immer nur ein Cluster gleichzeitig gelöscht werden. Zum Löschen mehrerer Cluster müssen Sie die entsprechenden Cluster nacheinander löschen und dabei abwarten, bis der vorherige Cluster gelöscht wurde, bevor Sie versuchen, den nächsten Cluster zu löschen.
* Vergewissern Sie sich, dass alle Knoten in einem Cluster eingeschaltet und betriebsbereit sind, bevor Sie den Cluster löschen.
* Wenn Sie einen Cluster löschen, dann werden auch alle VMs (virtuellen Maschinen) des Clusters gelöscht und können nicht wiederhergestellt werden. Sollen die VMs beibehalten werden, dann müssen Sie sie auf andere Cluster migrieren.
* Der Standardcluster kann nicht gelöscht werden.

## Vorgehensweise zum Löschen von Clustern aus vCenter Server with Hybridity Bundle-Instanzen

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Bereitgestellte Instanzen**.
2. Klicken Sie in der Tabelle **vCenter Server-Instanzen** auf die Instanz, aus der Cluster gelöscht werden sollen.

   **Hinweis**: Vergewissern Sie sich, dass sich die Instanz im Status **Bereit** befindet. Andernfalls können Sie keine Cluster aus der Instanz entfernen.

3. Klicken Sie im linken Navigationsfenster auf **Infrastruktur**. Suchen Sie in der Tabelle **CLUSTER** den Cluster, der gelöscht werden soll, und klicken Sie dann auf das Symbol **Löschen** in der Spalte **Aktionen**.

### Zugehörige Links

* [vCenter Server with Hybridity Bundle-Instanzen anzeigen](vc_hybrid_viewinginstances.html)
* [Kapazität für vCenter Server with Hybridity Bundle-Instanzen erweitern und verringern](vc_hybrid_addingremovingservers.html)
