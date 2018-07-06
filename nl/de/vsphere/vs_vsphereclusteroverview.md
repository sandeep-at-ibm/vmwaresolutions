---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-22"

---

# Überblick zu VMware vSphere on IBM Cloud

VMware vSphere on {{site.data.keyword.cloud}} ist eine rationalisierte und optimierte Bestellplattform für VMware, mit deren Hilfe Sie Ihre eigene von IBM gehostete VMware-Umgebung aufbauen können, indem Sie die VMware-kompatible Hardware anpassen und bestellen, die auf den ausgewählten VMware-Komponenten basiert.

In der {{site.data.keyword.vmwaresolutions_short}}-Konsole wird die Hardware automatisch abhängig von den ausgewählten VMware-Komponenten gefiltert. Wenn Sie beispielsweise einen neuen VMware vSAN-Cluster mit All-Flash-Funktionalität erstellen, wird nur solche Hardware angezeigt, die anhand des [VMware Compatibility Guide](https://www.vmware.com/resources/compatibility/search.php) validiert wurde, und es sind mindestens vier ESXi-Server erforderlich.

Da VMware vSphere on {{site.data.keyword.cloud_notm}} weder Installation noch Konfiguration oder Inbetriebnahme der optionalen VMware-Komponenten automatisiert, besitzen Sie hinsichtlich des Designs und des Aufbaus Ihrer gehosteten VMware-Umgebung beim Integrieren der VMware-kompatiblen Hardware eine hohe Flexibilität.

Verwenden Sie dieses Produktangebot, um einen neuen Cluster aus ESXi-Servern zu erstellen oder einen vorhandenen Cluster aus ESXi-Servern in einem {{site.data.keyword.CloudDataCent_notm}} zu skalieren. Abhängig von den VMware-Komponenten, die Sie auswählen, können Sie mit nur einem einzigen ESXi-Server beginnen und den Cluster später nach Bedarf skalieren.

## Komponenten von VMware vSphere on IBM Cloud

Überprüfen Sie die Komponenten von VMware vSphere on {{site.data.keyword.cloud_notm}}.

**Hinweis**: Verfügbarkeit und Preisgestaltung standardisierter Hardwarekonfigurationen können abhängig vom {{site.data.keyword.CloudDataCent_notm}}, das für die Bereitstellung ausgewählt ist, variieren.

### VMware-Komponenten

Lizenzen (von IBM bereitgestellt oder eigene) für die folgenden VMware-Komponenten:
* VMware vSphere Enterprise Plus 6.0u2 oder 6.5u1
* Optionale VMware-Komponenten:
   * VMware vCenter Server Standard
   * VMware NSX (Base, Advanced oder Enterprise)
   * VMware vSAN (Advanced oder Enterprise)
   * VMware Site Recovery Manager
   * VMware vRealize Automation Enterprise
   * VMware vRealize Operations Enterprise
   * VMware vRealize Log Insight

### Bare Metal Server

Eine oder mehrere {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}-Instanzen mit dem ausgewählten CPU-Modell und der ausgewählten RAM-Größe:
* 2-CPU Intel Broadwell Generation (Intel Xeon E5-2600 v4 Series)
* 2-CPU Intel Skylake Generation (Intel Xeon 4100/5100/6100 Series)

Die verfügbaren Optionen sind davon abhängig, ob Sie die Komponente "VMware vSAN" ausgewählt haben.

Zusätzlich folgende Platten- und Netzspezifikationen:
* 10-Gbps-Uplinks für öffentliche und private Netze
* 1 RAID-Plattencontroller

### Netzbetrieb

* 3 VLANs (virtuelle LANs): 1 öffentliches VLAN und 2 private VLANs
* (Optional) 1 HA-Paar von FortiGate Security Appliance-Einheiten

### Speicher

Vom Benutzer angepasster Speicher für vSAN-Konfiguration bei Auswahl der Komponente "VMware vSAN":
* Optionen für Speicherplatten: 960 GB SSD SED, 1,9 TB SSD SED oder 3,8 TB SSD SED
* Optionen für die Plattenmenge: 2, 4, 6 oder 8

**Hinweis:** 3,8-TB-Solid-State-Platten (SSD) werden unterstützt, wenn sie allgemein in einem Rechenzentrum verfügbar gemacht werden.

## Komponenten von vSphere-Clustererweiterungsknoten

Jeder vSphere-Clustererweiterungsknoten stellt die folgenden Komponenten in Ihrem {{site.data.keyword.slportal}}-Konto mit den entsprechenden anfallenden Gebühren bereit.

### Hardware für Erweiterungsknoten

1 IBM Cloud Bare Metal Server mit der unter [Komponenten von VMware vSphere on IBM Cloud](../vsphere/vs_vsphereclusteroverview.html#components-of-vmware-vsphere-on-ibm-cloud) beschriebenen Hardwarekonfiguration.

### Netzbetrieb für Erweiterungsknoten

1 IBM Cloud Bare Metal Server mit der unter [Komponenten von VMware vSphere on IBM Cloud](../vsphere/vs_vsphereclusteroverview.html#components-of-vmware-vsphere-on-ibm-cloud) beschriebenen Netzkonfiguration.

### VMware-Komponenten für Erweiterungsknoten

* 1 IBM Cloud Bare Metal Server mit VMware vSphere Enterprise Plus 6.0u2 oder 6.5u1  
* Optionale VMware-Komponenten, die unter [Komponenten von VMware vSphere on IBM Cloud](../vsphere/vs_vsphereclusteroverview.html#components-of-vmware-vsphere-on-ibm-cloud) aufgeführt sind.

**Wichtig**: Sie dürfen die ESXi-Server, die optionalen VMware-Komponenten und die zusätzliche Hardware, die bestellt und Ihrem {{site.data.keyword.cloud_notm}}-Konto übergeben wurden, nur im {{site.data.keyword.slportal}} verwalten. Nachdem Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole einen neuen Cluster erstellt haben, können Sie die Konsole erneut aufrufen, um den neuen Cluster unter Verwendung der gespeicherten Konfiguration zu skalieren. Weitere Informationen finden Sie unter [Vorhandene vSphere-Cluster skalieren](vs_scalingexistingclusters.html).

## Zugehörige Links

* [VMware vSphere-Softwareteileliste](vs_bom.html)
* [vSphere-Cluster planen](vs_planning.html)
* [vSphere-Cluster bestellen](vs_orderinginstances.html)
* [Vorhandene vSphere-Cluster skalieren](vs_scalingexistingclusters.html)
