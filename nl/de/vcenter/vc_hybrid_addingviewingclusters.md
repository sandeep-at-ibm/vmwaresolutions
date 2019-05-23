---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-18"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Cluster für vCenter Server with Hybridity Bundle-Instanzen hinzufügen, anzeigen und löschen
{: #vc_hybrid_addingviewingclusters}

Die ESXi-Server, die Sie bei der Bestellung einer Instanz konfiguriert haben, werden standardmäßig unter **cluster1** gruppiert.

Sie können Cluster zu Ihrer VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle-Instanz hinzufügen, um die Rechen- und Speicherkapazität zu erweitern. Verwalten Sie in einem Cluster ESXi-Server, um eine bessere Ressourcenzuordnung und hohe Verfügbarkeit zu erreichen. Löschen Sie die hinzufügten Cluster aus Ihrer Instanz, wenn sie nicht mehr benötigt werden.

## Cluster zu vCenter Server with Hybridity Bundle-Instanzen hinzufügen
{: #vc_hybrid_addingviewingclusters-adding}

### Vor dem Hinzufügen von Clustern
{: #vc_hybrid_addingviewingclusters-before-add}

* Fügen Sie Cluster nach Möglichkeit über die {{site.data.keyword.vmwaresolutions_full}}-Konsole hinzu, da Änderungen, die Sie am VMware vSphere Web Client vornehmen, nicht mit der {{site.data.keyword.vmwaresolutions_short}}-Konsole synchronisiert werden. Fügen Sie daher Cluster nur für On-Premise-Cluster oder Cluster hinzu, die Sie nicht in der {{site.data.keyword.vmwaresolutions_short}}-Konsole verwalten können/möchten.
* Für Instanzen, die in (oder einem Upgrade auf) V2.5 und höher implementiert wurden, legt die Anzahl der Cluster, Hosts und VMs die maximale Begrenzung für die Anzahl der Cluster fest, die Sie hinzufügen können. Sie müssen die Richtlinien und Grenzwerte für die VMware-Dimensionierung für Ihre Implementierung beibehalten. Weitere Informationen zu maximalen Grenzwerten finden Sie in [VMware Configuration Maximums](https://configmax.vmware.com/home){:new_window}.
* Für Instanzen, die in Version 2.3 und 2.4 bereitgestellt oder darauf aktualisiert wurden, können Sie bis zu 10 Cluster hinzufügen.

### Systemeinstellungen
{: #vc_hybrid_addingviewingclusters-adding-sys-settings}

Wenn Sie einen Cluster für eine vCenter Server with Hybridity Bundle-Instanz hinzufügen, müssen Sie die folgenden Einstellungen angeben.

#### Clustername
{: #vc_hybrid_addingviewingclusters-adding-cluster-name}

Der Clustername muss die folgenden Anforderungen erfüllen:
* Es sind nur alphanumerische Zeichen und Bindestriche (-) zulässig.
* Der Clustername muss mit einem alphanumerischen Zeichen beginnen und enden.
* Die maximale Länge des Clusternamens beträgt 30 Zeichen.
* Der Clustername muss innerhalb der vCenter Server with Hybridity Bundle-Instanz eindeutig sein.

#### Standort des Rechenzentrums
{: #vc_hybrid_addingviewingclusters-adding-dc-location}

Der Standort des {{site.data.keyword.CloudDataCent_notm}}s für den Cluster wird standardmäßig auf das {{site.data.keyword.CloudDataCent_notm}} der vCenter Server-Instanz gesetzt. Sie können den Cluster in einem anderen {{site.data.keyword.CloudDataCent_notm}} als die bereitgestellte Instanz bereitstellen, müssen aber sicherstellen, dass die Netzlatenz zwischen den beiden {{site.data.keyword.CloudDataCents_notm}} weniger als 150 Millisekunden beträgt. Verwenden Sie zum Überprüfen der Netzlatenz ein Tool wie [Looking Glass](/docs/infrastructure/network-tools?topic=network-tools-about-looking-glass#about-looking-glass).

Wenn Sie den Cluster in einem anderen {{site.data.keyword.CloudDataCent_notm}}- oder {{site.data.keyword.cloud_notm}}-Infrastrukturpod bereitstellen, werden drei weitere VLANs zur Verwendung mit den bestellten {{site.data.keyword.baremetal_short}}-Instanzen bestellt.

### Einstellungen für Bare Metal Server
{: #vc_hybrid_addingviewingclusters-adding-bare-metal}

Sie können **Skylake** oder **Broadwell** auswählen. Die Optionen können je nach der Version, in der Ihre Instanz ursprünglich bereitgestellt wurde, variieren.

#### Skylake
{: #vc_hybrid_addingviewingclusters-adding-skylake}

Wenn Sie **Skylake** auswählen, dann können Sie die Kombination aus CPU und RAM entsprechend Ihren Anforderungen auswählen.

Tabelle 1. Optionen für Skylake Bare Metal Server-Instanzen

| CPU-Modelloptionen        | RAM-Optionen       |
|:------------- |:------------- |
| Dual Intel Xeon Silver 4110-Prozessor / 16 Kerne insgesamt, 2,1 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon Gold 5120-Prozessor / 28 Kerne insgesamt, 2,2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon Gold 6140-Prozessor / 36 Kerne insgesamt, 2,3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |

#### Broadwell
{: #vc_hybrid_addingviewingclusters-adding-broadwell}

Wenn Sie **Broadwell** auswählen, dann können Sie die Kombination aus CPU und RAM entsprechend Ihren Anforderungen auswählen.

Tabelle 2. Optionen für Broadwell Bare Metal Server-Instanzen

| CPU-Modelloptionen        | RAM-Optionen       |
|:------------- |:------------- |
| Quad Intel Xeon E7-4820 v4 / 40 Kerne insgesamt, 1,9 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |
| Quad Intel Xeon E7-4850 v4 / 64 Kerne insgesamt, 2,2 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |

#### Bare Metal Server-Anzahl
{: #vc_hybrid_addingviewingclusters-adding-bare-metal-number}

* Alle Server, die Sie bestellen, haben die gleiche Konfiguration.
* Sie können zwischen 4 und 59 Server bestellen.

### vSAN-Speichereinstellungen
{: #vc_hybrid_addingviewingclusters-adding-vsan-storage-settings}

VMware vSAN 6.6 ist Bestandteil der Bestellung Ihrer vCenter Server with Hybridity Bundle-Instanz. Geben Sie die folgenden vSAN-Optionen an:
* **Plattentyp und Größe für vSAN-Kapazitätsplatten**: Wählen Sie die für die Kapazitätsplatten benötigte Option aus.
* **Anzahl der vSAN-Kapazitätsplatten**: Geben Sie die Anzahl der hinzuzufügenden Kapazitätsplatten an.
* Wenn Sie über den Grenzwert von zehn Stück hinaus Kapazitätsplatten hinzufügen möchten, müssen Sie das Feld für **Hohe Leistung mit Intel Optane** auswählen. Diese Option stellt zwei zusätzliche Kapazitätsplattenpositionen für eine Gesamtzahl von 12 Kapazitätsplatten bereit und ist für Workloads nützlich, die eine geringere Latenzzeit und einen höheren Durchsatz an E/A-Operationen pro Sekunde erfordern.

  Die Option **Hohe Leistung mit Intel Optane** ist nur für die Skylake-CPU-Modelle verfügbar.
  {:note}

* Überprüfen Sie die Werte für **Plattentyp für vSAN-Cacheplatten** und **Anzahl der vSAN-Cacheplatten**. Diese Werte hängen davon ab, ob Sie das Feld **Hohe Leistung mit Intel Optane** ausgewählt haben.
* **vSAN-Lizenz**: Wählen Sie die VMware vSAN 6.6-Lizenzedition (Advanced oder Enterprise) aus.

### Lizenzierungseinstellungen
{: #vc_hybrid_addingviewingclusters-adding-licensing-settings}

Von IBM bereitgestellte Lizenzen für folgende VMware-Komponenten:
  * vSphere Enterprise Plus 6.5u1
  * vCenter Server 6.5
  * NSX Service Providers 6.4 (Advanced oder Enterprise Edition)

### Netzschnittstelleneinstellungen
{: #vc_hybrid_addingviewingclusters-adding-network-interface-settings}

Die Einstellungen für die Netzschnittstellenkarte (NIC - Network Interface Card) basieren darauf, ob Sie **Öffentliches und privates Netz** oder **Nur privates Netz** auswählen. Die folgenden Add-on-Services benötigen öffentliche NICs und sind bei Auswahl der privaten Option nicht verfügbar:

* F5 on {{site.data.keyword.cloud_notm}}
* FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}
* FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}

### Bestellübersicht
{: #vc_hybrid_addingviewingclusters-adding-order-summary}

Auf Basis der für den Cluster ausgewählten Konfiguration werden die geschätzten Kosten sofort generiert und im rechten Fenster **Bestellübersicht** angezeigt.

## Vorgehensweise zum Hinzufügen von Clustern zu vCenter Server with Hybridity Bundle-Instanzen
{: #vc_hybrid_addingviewingclusters-adding-procedure}

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Ressourcen**.
2. Klicken Sie in der Tabelle **vCenter Server-Instanzen** auf die Instanz, um die Cluster in dieser Instanz anzuzeigen.

   Stellen Sie sicher, dass der Instanzstatus **Bereit** lautet. Andernfalls können Sie der Instanz keine Cluster hinzufügen.
   {:note}

3. Klicken Sie im linken Navigationsfenster auf **Infrastruktur** und anschließend in der rechten oberen Ecke der Tabelle **CLUSTER** auf **Hinzufügen**.
4. Geben Sie auf der Seite **Cluster hinzufügen** den Clusternamen ein.
5. Sie können den Cluster in einem anderen {{site.data.keyword.CloudDataCent_notm}} hosten, als das, in dem die Instanz gehostet wird. Aktivieren Sie dazu unter **Bare Metal Server** das Kontrollkästchen **Anderen Standort auswählen** und wählen Sie dann das gewünschte {{site.data.keyword.CloudDataCent_notm}} als Host für die Instanz aus.
6. Wählen Sie das **CPU-Modell**, die Menge des **RAM** und die **Anzahl der Bare Metal Server** für die Bare-Metal-Konfiguration aus.
7.  Wählen Sie den **vSAN-Speicher** aus und geben Sie die Plattentypen für die Kapazitäts- und Cacheplatten sowie die Anzahl der Platten an. Falls Sie mehr Speicher benötigen, müssen Sie das Feld für **Hohe Leistung mit Intel Optane** auswählen.
8. Wählen Sie die Lizenzedition für VMware vSAN für die Lizenzkonfiguration aus.
9. Wählen Sie die Netzeinstellung für entweder **Öffentliches und privates Netz** oder **Nur privates Netz** aus.
10. Überprüfen Sie im Fenster **Bestellübersicht** die Clusterkonfiguration, bevor Sie den Cluster hinzufügen.
   1. Überprüfen Sie die Einstellungen für den Cluster.
   2. Überprüfen Sie die geschätzten Kosten des Clusters. Klicken Sie auf **Preisdetails**, um eine PDF-Datei mit der Zusammenfassung zu generieren. Ihre Bestellübersicht können Sie speichern oder drucken, indem Sie rechts oben im PDF-Fenster auf das Symbol **Drucken** bzw. **Herunterladen** klicken.
   3. Klicken Sie auf den Link bzw. die Links für die Bedingungen, die für Ihre Bestellung gelten, und vergewissern Sie sich, dass Sie mit diesen Bedingungen einverstanden sind, bevor Sie den Cluster hinzufügen.
   4. Klicken Sie auf **Bereitstellung**.

### Ergebnisse nach Hinzufügen von Clustern zu vCenter Server with Hybridity Bundle-Instanzen
{: #vc_hybrid_addingviewingclusters-adding-results}

1. Die Bereitstellung des Clusters wird automatisch gestartet und der Status des Clusters ändert sich in **Wird initialisiert**. Sie können den Status der Bereitstellung überprüfen, indem Sie den Bereitstellungsverlauf über die Seite **Zusammenfassung** der Instanz anzeigen.
2. Sobald der Cluster einsatzbereit ist, ändert sich sein Status in **Bereit**. Der neu hinzugefügte Cluster wird mit vSphere High Availability (HA) und vSphere Distributed Resource Scheduler (DRS) aktiviert.

Der Clustername kann nicht geändert werden. Wenn Sie den Clusternamen ändern, kann die Operation zum Hinzufügen oder Entfernen von ESXi-Servern im Cluster fehlschlagen.
{:important}

## Vorgehensweise zum Anzeigen von Clustern in vCenter Server with Hybridity Bundle-Instanzen
{: #vc_hybrid_addingviewingclusters-viewing-procedure}

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Ressourcen**.
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
4. Klicken Sie auf einen Clusternamen, um die Details zu den ESXi-Servern, zum Speicher und zur Netzschnittstelle anzuzeigen:

  * ESXi-Serverdetails:
     * **Name**: Der Name des ESXi-Servers hat das Format `<host_prefix><n>.<subdomain_label>.<root_domain>`. Dabei gilt Folgendes:

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
  * Netzschnittstelle - VLAN-Details:
    * **VLAN-Nummer**: Die eindeutige VLAN-Nummer.
    * **Beschreibung**: Die Beschreibung des VLAN.
    * **Standort**: Der Standort des Rechenzentrums.
    * **Primäre Route**: Die primäre Route des VLAN.
    Klicken Sie auf **Ressourcen anzeigen**, um auf die VLAN-Details zuzugreifen.
  * Netzschnittstelle - Teilnetz-Details:
    * **Name**: Der Teilnetzname. Klicken Sie auf den Namen, um auf die Teilnetzdetails zuzugreifen.
    * **Typ**: Der Typ des Teilnetzes - primär oder portierbar.
    * **Beschreibung**: Die Beschreibung des Teilnetzes.
  * Netzschnittstelle - IP-Details:
    * **IP**: Die IP-Adresse.
    * **Status**: Der Status der IP-Adresse.
    * **Beschreibung**: Die Beschreibung der IP-Adresse.

## Cluster aus vCenter Server with Hybridity Bundle-Instanzen löschen
{: #vc_hybrid_addingviewingclusters-deleting}

Wird ein Cluster nicht mehr benötigt, kann er aus einer Instanz gelöscht werden.

### Vorbereitende Schritte für die Löschung
{: #vc_hybrid_addingviewingclusters-deleting-prereq}

* Löschen Sie Cluster nach Möglichkeit über die {{site.data.keyword.vmwaresolutions_full}}-Konsole, da Änderungen, die Sie am VMware vSphere Web Client vornehmen, nicht mit der {{site.data.keyword.vmwaresolutions_short}}-Konsole synchronisiert werden. Löschen Sie daher Cluster nur für On-Premise-Cluster oder Cluster, die Sie nicht in der {{site.data.keyword.vmwaresolutions_short}}-Konsole verwalten können/möchten.
* Es kann immer nur ein Cluster gleichzeitig gelöscht werden. Zum Löschen mehrerer Cluster müssen Sie die entsprechenden Cluster nacheinander löschen und dabei abwarten, bis der vorherige Cluster gelöscht wurde, bevor Sie den nächsten Cluster löschen.
* Stellen Sie sicher, dass alle Knoten in einem Cluster eingeschaltet und betriebsbereit sind, bevor Sie den Cluster löschen.
* Wenn Sie einen Cluster löschen, werden auch alle VMs (virtuellen Maschinen) des Clusters gelöscht und können nicht wiederhergestellt werden. Sollen die VMs beibehalten werden, dann müssen Sie sie auf andere Cluster migrieren.
* Der Standardcluster kann nicht gelöscht werden.

## Vorgehensweise zum Löschen von Clustern aus vCenter Server with Hybridity Bundle-Instanzen
{: #vc_hybrid_addingviewingclusters-deleting-procedure}

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Ressourcen**.
2. Klicken Sie in der Tabelle **vCenter Server-Instanzen** auf die Instanz, aus der Cluster gelöscht werden sollen.

   Vergewissern Sie sich, dass sich die Instanz im Status **Bereit** befindet. Andernfalls können Sie keine Cluster aus der Instanz entfernen.
   {:note}

3. Klicken Sie im linken Navigationsfenster auf **Infrastruktur**. Suchen Sie in der Tabelle **CLUSTER** den Cluster, der gelöscht werden soll, und klicken Sie dann auf das Symbol **Löschen** in der Spalte **Aktionen**.

## Zugehörige Links
{: #vc_hybrid_addingviewingclusters-related}

* [vCenter Server with Hybridity Bundle-Instanzen anzeigen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_viewinginstances)
* [Kapazität für vCenter Server with Hybridity Bundle-Instanzen erweitern und verringern](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservers)
