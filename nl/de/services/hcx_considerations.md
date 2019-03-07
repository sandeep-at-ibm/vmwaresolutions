---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# VMware HCX on IBM Cloud - Spezifikationen und Aspekte
{: #vmware-hcx-on-ibm-cloud-overview}

Der Service "HCX on {{site.data.keyword.cloud}}" kann die Netze von lokalen Rechenzentren nahtlos in die {{site.data.keyword.cloud_notm}} erweitern. Dies ermöglicht die Migration von virtuellen Maschinen in die und aus der {{site.data.keyword.cloud_notm}}, ohne dass hierzu eine Konvertierung oder Änderung erforderlich ist.

Dieser Service ist nur für Instanzen von VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle verfügbar, die in V2.3 (und höher) bereitgestellt werden.
{:note}

Sie können für Ihre vorhandene vCenter Server-Instanz ein Upgrade auf eine vCenter Server with Hybridity Bundle-Instanz durchführen. Weitere Informationen zum Durchführen eines Upgrades für Ihre Instanz und zum Bereitstellen des Service "HCX on {{site.data.keyword.cloud_notm}}" finden Sie unter [Vorgehensweise zum Durchführen eines Upgrades auf eine vCenter Server with Hybridity Bundle-Instanz](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_applyingupdates#procedure-to-upgrade-to-the-vcenter-server-with-hybridity-bundle-instance).

Eine vCenter Server-Instanz mit HCX on {{site.data.keyword.cloud_notm}} ist auf drei simultane Verbindungen von lokalen Standorten begrenzt.
{:note}

## Technische Spezifikationen für HCX on IBM Cloud
{: #technical-specifications-for-hcx-on-ibm-cloud}

Mit dem Service "HCX on {{site.data.keyword.cloud_notm}}" werden die folgenden Komponenten bestellt und einbezogen.

Lokale HCX-Instanzen schließen nur Lizenzierung und Aktivierung ein.
{:note}

### Ein Aktiv/Passiv-Paar von VMware NSX Edge Services Gateways für das HCX-Management
{: #hcx_considerations-nsx}

* CPU: 6 vCPU
* RAM: 8 GB
* Festplatte: 3 GB VMDK

### HCX-Management-Appliance - virtuelle Maschine
{: #hcx_considerations-vm}

* CPU: 4 vCPU
* RAM: 12 GB
* Festplatte: 60 GB VMDK

Weitere HCX-Appliances werden bei der Konfiguration wie für die L2-Konnektivität, die WAN-Optimierung und Gateway-Verbindungen erforderlich bereitgestellt.

### Vernetzung
{: #hcx_considerations-networking}

* 1 öffentliches portierbares Teilnetz mit 16 IP-Adressen
* 2 private portierbare Teilnetze mit 64 IP-Adressen
* 8 IP-Adressen aus dem privaten portierbaren vMotion-Teilnetz

## Hinweise zur Installation von HCX on IBM Cloud
{: #hcx_considerations-install}

Lesen Sie die folgenden Hinweise, bevor Sie versuchen, HCX on {{site.data.keyword.cloud_notm}} zu installieren.

### Anforderungen an die Anzahl der ESXi-Server
{: #hcx_considerations-esxi-servers}

Der Service "HCX on {{site.data.keyword.cloud_notm}}" kann nicht in einer Instanz installiert werden, für die der Standardcluster mehr als 51 ESXi-Server umfasst. Da HCX on {{site.data.keyword.cloud_notm}} acht IP-Adressen im vMotion-Teilnetz aus dem Standardcluster benötigt, sind keine IP-Adressen im vMotion-Teilnetz für HCX on {{site.data.keyword.cloud_notm}} verfügbar, wenn die Anzahl der ESXi-Server 51 überschreitet.

### Anforderungen an Firewallregeln
{: #hcx_considerations-firewall}

Bevor Sie den Service "HCX on {{site.data.keyword.cloud_notm}}" installieren, müssen Sie eine Firewallregel zu vorhandenen Firewalls hinzufügen, um den gesamten abgehenden HTTPS-Datenverkehr zuzulassen, damit die virtuelle Appliance für den HCX-Manager sich selbst registrieren kann. Nachdem die Installation des HCX-Managers abgeschlossen ist, können Sie die Firewallregel entfernen. Darüber hinaus müssen Sie Firewallregeln konfigurieren, damit HCX ordnungsgemäß funktionieren kann. Weitere Informationen finden Sie in *Anhang A - Portzugriffsvoraussetzungen* unter der [Architektur von HCX on {{site.data.keyword.cloud_notm}}](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf).

## Hinweise zum Entfernen von HCX on IBM Cloud
{: #considerations-when-removing-hcx-on-ibm-cloud}

Lesen Sie die folgenden Hinweise, bevor Sie den Service "HCX on {{site.data.keyword.cloud_notm}}" entfernen:
* Stellen Sie sicher, dass die Verbindungen und erweiterten Netze zwischen dem lokalen Quellenstandort und den {{site.data.keyword.cloud_notm}}-Zielstandorten entfernt wurden. Verwenden Sie zum Entfernen der Verbindungen und erweiterten Netze die HCX-Benutzerschnittstelle in der lokalen Instanz von VMware vSphere Web Client.
* Stellen Sie sicher, dass die Standortpaarungen zwischen dem lokalen Quellenstandort und den {{site.data.keyword.cloud_notm}}-Zielstandorten entfernt wurden. Verwenden Sie zum Entfernen der Standortpaarungen die HCX-Benutzerschnittstelle in der lokalen Instanz von VMware vSphere Web Client.
* Das Entfernen von HCX on {{site.data.keyword.cloud_notm}} ist nicht automatisiert. Die folgenden Prozeduren müssen für das erfolgreiche Entfernen dieses Service durchgeführt werden:
   * Die für den cloudseitigen HCX-Manager bestellte HCX-Lizenz muss inaktiviert werden.
   * Der HCX-Manager muss gelöscht werden.
   * Die für HCX reservierten vMotion-IP-Adressen müssen freigegeben werden.
   * Alle HCX-bezogenen Ressourcenpools (sofern leer) müssen entfernt werden.
   * Alle HCX-bezogenen Ordner (sofern leer) müssen entfernt werden.
   * Die HCX-Management-Edge-Appliances müssen gelöscht werden.

## Zugehörige Links
{: #hcx_considerations-related}

* [HCX on {{site.data.keyword.cloud_notm}} bestellen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_ordering)
* [HCX on {{site.data.keyword.cloud_notm}} verwalten](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghcx)
* [Glossar der HCX-Begriffe](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_glossary)
* [Kontaktaufnahme mit dem IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [VMware Hybrid Cloud Extension - Übersicht](https://cloud.vmware.com/vmware-hcx)
* [Dokumentation zu VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx/resources)
