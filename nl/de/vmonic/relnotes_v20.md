---

copyright:

  years:  2016, 2017

lastupdated: "2017-11-20"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Releaseinformationen für V2.0
{: #relnotes_v20}

Dieses Release stellt neue Funktionen, Komponentenaktualisierungen, Verbesserungen des Bedienungskomforts und Fehlerkorrekturen zur Verfügung. Eine Liste mit den in den unterschiedlichen Releases behobenen Problemen, den bekannten Problemen beim Produkt sowie Tipps für die Verwendung von {{site.data.keyword.vmwaresolutions_full}} finden Sie unter [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## FortiGate Virtual Appliance on IBM Cloud
{: #relnotes_v20-fva}

Der Service "FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}" ist jetzt für VMware Cloud Foundation- und VMware vCenter Server-Instanzen aus V2.0 und höher verfügbar. Dieser Service stellt ein Hochverfügbarkeitspaar (HA-Paar) von FortiGate Virtual Appliances für Ihre Umgebung bereit, mit dessen Hilfe Sie durch die Implementierung von kritischen Sicherheitsmaßnahmen in Ihrer virtuellen Infrastruktur Risiken verringern können.

Bestellen Sie Instanzen, die den Service "FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}" enthalten, oder fügen Sie diesen Service später Ihren vorhandenen Instanzen über die Registerkarte **Services** auf der Seite mit den Instanzdetails hinzu. Wählen Sie je nach Bedarf eine der drei Bereitstellungsgrößen und Lizenzierungsoptionen, die für diesen Service vorhanden sind. Verwalten und konfigurieren Sie nach der erfolgreichen Installation des Service Firewallregeln für FortiGate Virtual Appliances über die FortiGate-Konsole.

Weitere Informationen finden Sie in den folgenden Abschnitten:
* [Komponenten und Hinweise für FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_considerations)
* [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} verwalten](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingfortinetvm)

## Installation mehrerer Services für F5 on IBM Cloud und FortiGate Virtual Appliance on IBM Cloud
{: #relnotes_v20-multiple-services}

Sie können jetzt mehrere Instanzen der Services "F5 on {{site.data.keyword.cloud_notm}}" und "FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}" für eine Cloud Foundation-Instanz oder eine vCenter Server-Instanz installieren. Wenn Sie bei der Instanzbestellung den F5- oder den FortiGate-Service auswählen, müssen Sie einen Namen für die Serviceinstanz angeben, um sie von den zusätzlichen Serviceinstanzen zu unterscheiden, die Sie später installieren.

Nachdem die Instanzbereitstellung erfolgt ist, können Sie weitere Instanzen des F5- oder FortiGate-Service hinzufügen, indem Sie den Service auf der Registerkarte **Services hinzufügen** der Seite mit den Instanzdetails installieren. Sie können gleichzeitig jeweils nur eine einzige Serviceinstanz hinzufügen; der Prozess muss für jede Instanz, die Sie für einen Service hinzufügen wollen, wiederholt werden.

Weitere Informationen finden Sie unter [Services für vCenter Server-Instanzen bestellen, anzeigen und entfernen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices).

## Updates für FortiGate Security Appliance on IBM Cloud
{: #relnotes_v20-fsa}

Der Service "Fortinet on {{site.data.keyword.cloud_notm}}" wurde in diesem Release in "FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}" umbenannt. Das Paar aus FortiGate Security Appliances (FSAs) des Service ist so konfiguriert, dass es standardmäßig geschützt ist, wenn es in Ihrer Instanz bereitgestellt wird.
* Wenn Sie ein FSA-Paar als Teil einer neuen Cloud Foundation- oder vCenter Server-Instanz bereitstellen, werden die FSAs so konfiguriert, dass nur die erforderliche abgehende Kommunikation aus Ihrer Instanz in das öffentliche Netz zugelassen und jede andere Kommunikation zurückgewiesen wird.
* Wenn Sie ein FSA-Paar als Teil einer vorhandenen Cloud Foundation- oder vCenter Server-Instanz bereitstellen, werden die FSAs mit einer expliziten Regel so konfiguriert, dass die gesamte erforderliche abgehende Managementkommunikation aus Ihrer Instanz in das öffentliche Netz zugelassen wird. Außerdem werden die FSAs mit einer Regel so konfiguriert, dass die gesamte andere Kommunikation zulässig ist, um sicherzustellen, dass der Datenverkehr Ihrer vorhandenen Anwendungen nicht unterbrochen wird.

Sie müssen die FSA-Konfiguration in jedem Fall sorgfältig verwalten, damit nur die erforderliche Kommunikation zulässig ist und jede andere Kommunikation zurückgewiesen wird.

## Konsistenz des Formats für vollständig qualifizierte Domänennamen
{: #relnotes_v20-fqdn}

Der vollständig qualifizierte Domänenname (Fully Qualified Domain Name, FQDN) wird jetzt bei allen Instanzen konsistent dargestellt. Beim Aufgeben einer Bestellung können Sie Ihr eigenes Unterdomänen- und Hostnamenspräfix eingeben, um sicherzustellen, dass der Branchenstandard für das FQDN-Format eingehalten wird. Beispiel: `hostnamenspräfix<n>.unterdomänenpräfix.domänenname`.

Weitere Informationen finden Sie in den folgenden Abschnitten:
* [vCenter Server-Instanzen bestellen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [Neue vSphere-Cluster bestellen](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)

## Workload- und Speicherschätzungen bei einer Instanzbestellung
{: #relnotes_v20-estimates-order}

* Bei einer Bestellung von VMware vSphere on {{site.data.keyword.cloud_notm}} erhalten Sie eine Schätzung darüber, wie viele virtuelle Maschinen auf der bestellten Instanz ausgeführt werden können.
* Bei einer Bestellung von Cloud Foundation und vCenter Server erhalten Sie eine Schätzung der nutzbaren Speicherkapazität für die bestellte Instanz.

Weitere Informationen finden Sie in den folgenden Abschnitten:
* [vCenter Server-Instanzen bestellen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [Neue vSphere-Cluster bestellen](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)

## Updates für VMware Cloud Foundation-Instanzen
{: #relnotes_v20-vcf}

Im aktuellen Release werden die folgenden Komponentenupdates und Verbesserungen für neue Bereitstellungen angewendet:

* VMware vSphere Enterprise Plus 6.5u1 (5969303)
* VMware SDDC Manager 2.4
* VMware vCenter Server 6.5U1a
* VMware vSAN 6.6.1
* VMware NSX for vSphere 6.3.4
* VMware ESXi 6.5, Patch-Release ESXi650-201710401-BG. Updates für VIBs "esx-base", "esx-tboot", "vsan" und "vsanhealth" (2151061). Weitere Informationen zu Details über das Patch können Sie auf der Seite [VMware vCenter Server Appliance Photon OS Security Patches](https://docs.vmware.com/en/VMware-vSphere/6.5/rn/vcenter-server-appliance-photonos-security-patches.html){:new_window} nachlesen.

Bei vorhandenen Instanzen (aus Releases V1.9 und früher) ist ein Upgrade auf die in dieser Liste aufgeführten Komponentenversionen nicht möglich.
{:note}

### Clusterunterstützung für Cloud Foundation-Instanzen
{: #relnotes_v20-vcf-cluster}

Sie können jetzt ESXi-Server in Cloud Foundation-Instanzen, die in V2.0 und höher bereitgestellt werden, mithilfe von Clustern verwalten und so ein besseres Ressourcenmanagement und eine hohe Verfügbarkeit erreichen. Die ESXi-Server, die Sie bei der Bestellung einer Instanz konfiguriert haben, werden standardmäßig unter **SDDC-Cluster** gruppiert.

Auf der Registerkarte **Infrastruktur** der Seite mit den Instanzdetails können Sie die Clusterdetails anzeigen und für eine Instanz bis zu insgesamt fünf Cluster hinzufügen. Wenn Sie die Kapazität für eine Instanz erweitern oder verringern, können Sie auswählen, in welchem Cluster ESXi-Server hinzugefügt oder entfernt werden sollen.

### Unterstützung für angepassten vSAN-Speicher bei Cloud Foundation-Instanzen
{: #relnotes_v20-custom-vsan-vcf}

Sie können die vSAN-Speicherkonfiguration jetzt anpassen, indem Sie Anzahl und Größe der vSAN-Speicherlaufwerke bei der Bestellung Ihrer Instanz auswählen.

### Auswahl der VMware vSAN-Lizenzedition (Advanced oder Enterprise) für Cloud Foundation-Instanzen
{: #relnotes_v20-vsan-license}

Sie können jetzt bei der Bestellung einer Cloud Foundation-Instanz die gewünschte vSAN-Lizenzedition auswählen. Sie können entweder die Lizenz im Rahmen der Bestellung kaufen oder eine eigene Lizenz verwenden (Bring Your Own License, BYOL).

### Neue standardisierte IBM Bare Metal Server-Konfigurationen für Cloud Foundation-Instanzen
{: #relnotes_v20-vcf-bare-metal}

Die folgenden Einstellungen für Bare Metal Server-Konfigurationen sind jetzt verfügbar:
* S (Klein): Dual Intel Xeon E5-2650 v4 / 24 Kerne insgesamt, 2,2 GHz / 128 GB RAM / 12 Platten
* L (Groß): Dual Intel Xeon E5-2690 v4 / 28 Kerne insgesamt, 2,6 GHz / 512 GB RAM / 12 Platten

Im Chassis ist Platz für 12 Platten. Nicht alle Steckplätze sind belegt. Die Konfiguration **S (Klein)** stellt zwei Micron 5100 MAX-Laufwerke mit 1,9 TB bereit; die Konfiguration **L (Groß)** bietet vier Micron 5100 PRO-Laufwerke mit 3,8 TB.
{:note}

## Updates für VMware vCenter Server-Instanzen
{: #relnotes_v20-vcs}

Im aktuellen Release werden die folgenden Komponentenupdates für neue Bereitstellungen angewendet:

* VMware vSphere Enterprise Plus 6.5u1 (5969303)
* VMware vCenter Server 6.5U1a
* VMware vSAN 6.6.1
* VMware NSX for vSphere 6.3.4

Angepasste vCenter Server-Bestellungen mit der oder ohne die Komponente "VMware vSAN" enthalten immer einen Server mit einem Gehäuse für 12 Platten. Dieser Server führt in der PDF-Datei für die Preisschätzung zu etwas höheren Kosten für die {{site.data.keyword.baremetal_short}}-Instanzen bei einer Bestellung ohne vSAN.
{:note}

Weitere Informationen zu Komponenten enthält der Abschnitt [Übersicht über vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview).

### Unterstützung von Konfigurationen mit mehreren Standorten für vCenter Server-Instanzen
{: #relnotes_v20-vcs-multisite}

Sie können nun eine einzige vCenter Server-Instanz bereitstellen und zusätzlich auch sekundäre Instanzen bereitstellen, die an eine primäre Instanz angeschlossen sind. Das Konfigurationsmodell für mehrere Standorte verwendet eine Hub-Peripherie-Topologie mit einem primären Standort und maximal sieben sekundären Standorten.

Weitere Informationen finden Sie unter [Konfiguration mit mehreren Standorten für vCenter Server-Instanzen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_multisite).

### Unterstützung für angepassten vSAN-Speicher bei vCenter Server-Instanzen
{: #relnotes_v20-custom-vsan-vcs}

vSAN-Speicher ist jetzt sowohl für primäre als auch für sekundäre vCenter Server-Instanzen verfügbar. Die Verfügbarkeit besteht jedoch nur dann, wenn Sie eine angepasste Konfiguration auswählen. Die gewünschte vSAN-Lizenzedition (Advanced oder Enterprise) können Sie jetzt bei der Bestellung der vCenter Server-Instanz auswählen. Sie können entweder die Lizenz im Rahmen der Bestellung kaufen oder eine eigene Lizenz verwenden (Bring Your Own License, BYOL).

Weitere Informationen finden Sie unter [vCenter Server-Instanzen bestellen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance).

### Eigene Lizenzen für VMware vCenter Server-Instanzen verwenden (Bring Your Own License, BYOL)
{: #relnotes_v20-byol}

BYOL, also die Verwendung eigener Lizenzen, ist jetzt für vCenter Server-Instanzen verfügbar. Verwenden Sie eine oder mehrere Ihrer eigenen Lizenzen für vCenter Server, vSphere, vSAN und NSX VMware, wenn Sie vCenter Server-Instanzen bestellen.

Weitere Informationen finden Sie in den folgenden Abschnitten:
* [vCenter Server-Instanzen bestellen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [Neue vSphere-Cluster bestellen](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)

## Updates für VMware vSphere on IBM Cloud
{: #relnotes_v20-vss}

### Neue Plattentypen für Bare Metal Server-Systeme
{: #relnotes_v20-disk-type}

Bei der Komponente "VMware vSAN" sind jetzt die folgenden Plattentypen für {{site.data.keyword.baremetal_short}}-Systeme verfügbar:
* 960 GB SSD SED
* 1,9 TB SSD SED
* 3,8 TB SSD SED

**Hinweise**:
* 3,8-TB-SSD-SED-Laufwerke sind unterstützt, wenn sie allgemein in einem {{site.data.keyword.CloudDataCent_notm}} (Rechenzentrum) verfügbar gemacht werden.
* Bestellungen mit oder ohne die Komponente "VMware vSAN" enthalten immer einen Server mit einem Chassis für 12 Platten. Dieser Server führt in der PDF-Datei für die Preisschätzung zu etwas höheren Kosten für die {{site.data.keyword.baremetal_short}}-Instanzen bei einer Bestellung ohne vSAN.

Weitere Informationen finden Sie unter [Neue vSphere-Cluster bestellen](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances).

## Updates für NetApp ONTAP Select on IBM Cloud
{: #relnotes_v20-netapp}

### Neue Bare Metal Server-Optionen
{: #relnotes_v20-netapp-bare-metal}

Die folgenden Bare Metal Server-Konfigurationsoptionen sind jetzt verfügbar:
* **Hohe Leistung (M = Mittel)** - Premium-Lizenz / Dual Intel Xeon E5-2650 V4 (24 Kerne insgesamt, 2,2 GHz) / 128 GB RAM / Kapazität von 22 1,9-TB-SSD-Laufwerken pro Knoten / Effektive Kapazität eines Clusters mit 4 Knoten - 59 TB
* **Hohe Leistung (L = Groß)** - Premium-Lizenz / Dual Intel Xeon E5-2650 V4 (24 Kerne insgesamt, 2,2 GHz) / 128 GB RAM / Kapazität von 22 3,8-TB-SSD-Laufwerken pro Knoten / Effektive Kapazität eines Clusters mit 4 Knoten - 118 TB
* **Hohe Kapazität** - Standardlizenz / Dual Intel Xeon E5-2650 v4 (24 Kerne insgesamt, 2,2 GHz) / 64 GB RAM / Kapazität von zehn 4-TB-SATA-Laufwerken pro Knoten / Effektive Kapazität eines Clusters mit 4 Knoten - 60 TB

3,8-TB-SSD-Laufwerke sind unterstützt, wenn sie allgemein in einem {{site.data.keyword.CloudDataCent_notm}} (Rechenzentrum) verfügbar gemacht werden.
{:note}

Weitere Informationen finden Sie in den folgenden Abschnitten:
* [Übersicht über NetApp ONTAP Select](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_netappoverview)
* [NetApp ONTAP Select-Instanzen bestellen](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_orderinginstances)

## Neue und aktualisierte Dokumentation
{: #relnotes_v20-new-docs}

VMware Cloud Foundation-Benutzer können mithilfe von schrittweisen Anleitungen und der NSX-Plattform von VMware in der {{site.data.keyword.cloud_notm}} die Kommunikation für virtuelle Maschinen untereinander und mit dem Internet ermöglichen. Weitere Informationen finden Sie auf der Seite [Setting up NSX for workload VMs on VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} (VCF)](https://developer.ibm.com/recipes/tutorials/setting-up-nsx-for-workload-vms-on-vmware-cloud-foundation-on-ibm-cloud-vcf/){:new_window}.

## Updates und Erweiterungen der Benutzerschnittstelle
{: #relnotes_v20-ui}

* Die maximale Anzahl der ESXi-Server, die zu einem Cluster hinzugefügt werden können, beträgt jetzt 32 Server. Die maximale Anzahl an Clustern ist weiterhin fünf.
* Auf der Seite **Ressourcen** wird die Spalte **ESXi-Server** in den Tabellen mit der Instanzzusammenfassung durch die Spalte **Version** ersetzt. In dieser Spalte ist die Releaseversion angegeben, in der Instanzen bereitgestellt oder auf die sie aktualisiert wurden.
* Auf der Seite mit den Instanzdetails ist jetzt die Version von SDDC Manager für Cloud Foundation-Instanzen angegeben.
* Es sind verschiedene Fehlernachrichten und QuickInfos verfügbar, die Sie bei der Auswahl der geeigneten Einstellung in der Benutzerschnittstelle unterstützen.
