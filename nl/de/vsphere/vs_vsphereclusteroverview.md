---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-29"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Übersicht über VMware vSphere on IBM Cloud

Bei VMware vSphere on {{site.data.keyword.cloud}} handelt es sich um eine optimierte Bestellplattform für VMware. Mit dieser Plattform können Sie Ihre eigene von IBM gehostete VMware-Umgebung aufbauen, indem Sie die VMware-kompatible Hardware anpassen und bestellen, die Sie für die von Ihnen ausgewählten VMware-Komponenten benötigen.

In der {{site.data.keyword.vmwaresolutions_short}}-Konsole wird die Hardware automatisch abhängig von den ausgewählten VMware-Komponenten gefiltert. Wenn Sie beispielsweise einen neuen VMware vSAN-Cluster mit reinem Flashspeicher erstellen, wird nur solche Hardware angezeigt, die anhand des [VMware Compatibility Guide](https://www.vmware.com/resources/compatibility/search.php) validiert wurde. Darüber hinaus sind mindestens vier ESXi-Server erforderlich.

{{site.data.keyword.cloud_notm}} automatisiert weder Installation und Konfiguration noch Inbetriebnahme der optionalen VMware-Komponenten. Die Plattform stattet Sie mit einem hohen Maß an Flexibilität hinsichtlich des Designs und Aufbaus Ihrer gehosteten VMware-Umgebung beim Integrieren der VMware-kompatiblen Hardware aus.

Verwenden Sie dieses Produktangebot, um einen neuen Cluster aus ESXi-Servern zu erstellen oder einen vorhandenen Cluster aus ESXi-Servern in einem {{site.data.keyword.CloudDataCent_notm}} zu skalieren. Abhängig von den VMware-Komponenten, die Sie auswählen, können Sie mit nur einem einzigen ESXi-Server beginnen und den Cluster später nach Bedarf skalieren.

## Technische Spezifikationen für VMware vSphere on IBM Cloud-Cluster

Überprüfen Sie die Komponenten von VMware vSphere on {{site.data.keyword.cloud_notm}}.

Verfügbarkeit und Preisgestaltung standardisierter Hardwarekonfigurationen können abhängig vom {{site.data.keyword.CloudDataCent_notm}}, das für die Bereitstellung ausgewählt wird, variieren.
{:note}

### VMware-Komponenten

Wählen Sie für folgende VMware-Komponenten (von IBM bereitgestellt oder eigene) Lizenzen aus:
* VMware vSphere Enterprise Plus 6.0u2, 6.5u1 oder 6.5u2
* Folgende VMware-Komponenten sind optional:
   * VMware vCenter Server Standard
   * VMware NSX (Base, Advanced oder Enterprise)
   * VMware vSAN (Advanced oder Enterprise)
   * VMware Site Recovery Manager
   * VMware vRealize Automation Enterprise
   * VMware vRealize Operations Enterprise
   * VMware vRealize Log Insight

### Bare Metal Server

Wählen Sie eine oder mehrere {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}-Instanzen mit dem von Ihnen ausgewählten CPU-Modell und der ausgewählten RAM-Größe aus:
* 2-CPU Intel Broadwell Generation (Intel Xeon E5-2600 v4 Series)
* 2-CPU Intel Skylake Generation (Intel Xeon 4100/5100/6100 Series)

Die verfügbaren Optionen sind davon abhängig, ob Sie die Komponente "VMware vSAN" ausgewählt haben.

Zusätzlich folgende Platten- und Netzspezifikationen:
* 10-Gbps-Uplinks für öffentliche und private Netze
* 1 RAID-Plattencontroller

### Vernetzung

* 1 öffentliches VLAN (Virtual LAN) und zwei private VLANs
* (Optional) 1 HA-Paar von FortiGate Security Appliance-Einheiten

### Speicher

Vom Benutzer angepasster Speicher für vSAN-Konfiguration bei Auswahl der Komponente "VMware vSAN":
* Speicherplattenoptionen (960 GB SSD SED, 1.9 TB SSD SED oder 3.8 TB SSD SED)
* Optionen für die Plattenmenge (2, 4, 6 oder 8)

  Zusätzlich werden auch zwei Cacheplatten mit 960 GB pro Host bestellt.

  3,8-TB-Solid-State-Platten (SSD) sind unterstützt, wenn sie in einem Rechenzentrum allgemein verfügbar gemacht werden.
  {:note}
* Option für "Hohe Leistung mit Intel Optane", die zwei zusätzliche Kapazitätsplattenpositionen für eine Gesamtzahl von 10 Kapazitätsplatten bereitstellt. Diese Option hängt vom CPU-Modell ab.

## Technische Spezifikationen für vSphere-Clustererweiterungsknoten

Jeder vSphere-Clustererweiterungsknoten stellt folgende Komponenten in Ihrem {{site.data.keyword.slportal}}-Konto mit den entsprechenden anfallenden Gebühren bereit.

### Hardware für Erweiterungsknoten

1 {{site.data.keyword.cloud_notm}} Bare Metal Server mit der unter [Technische Spezifikationen für VMware vSphere on {{site.data.keyword.cloud_notm}}-Instanzen](vs_vsphereclusteroverview.html#technical-specifications-for-vmware-vsphere-on-ibm-cloud-clusters) aufgeführten Hardwarekonfiguration.

### Vernetzung für Erweiterungsknoten

1 {{site.data.keyword.cloud_notm}} Bare Metal Server mit der unter [Technische Spezifikationen für VMware vSphere on {{site.data.keyword.cloud_notm}}-Instanzen](vs_vsphereclusteroverview.html#technical-specifications-for-vmware-vsphere-on-ibm-cloud-clusters) aufgeführten Netzkonfiguration.

### VMware-Komponenten für Erweiterungsknoten

* 1 {{site.data.keyword.cloud_notm}} Bare Metal Server mit VMware vSphere Enterprise Plus 6.0u2 oder 6.5u1  
* Optionale VMware-Komponenten, die unter [Technische Spezifikationen für VMware vSphere on {{site.data.keyword.cloud_notm}}](vs_vsphereclusteroverview.html#technical-specifications-for-vmware-vsphere-on-ibm-cloud-clusters) aufgeführt sind.

Sie dürfen die ESXi-Server, die optionalen VMware-Komponenten und die zusätzliche Hardware, die bestellt und Ihrem {{site.data.keyword.cloud_notm}}-Konto übergeben wurden, nur im {{site.data.keyword.slportal}} verwalten. Nachdem Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole einen neuen Cluster erstellt haben, können Sie die Konsole erneut aufrufen, um den neuen Cluster unter Verwendung der gespeicherten Konfiguration zu skalieren. Weitere Informationen finden Sie unter [Vorhandene vSphere-Cluster skalieren](vs_scalingexistingclusters.html).
{:important}

### Zugehörige Links

* [VMware vSphere-Softwareteileliste](vs_bom.html)
* [vSphere-Cluster planen](vs_planning.html)
* [vSphere-Cluster bestellen](vs_orderinginstances.html)
* [Vorhandene vSphere-Cluster skalieren](vs_scalingexistingclusters.html)
