---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-26"

---

# Übersicht über VMware HCX on IBM Cloud

Der Service "HCX on {{site.data.keyword.cloud}}" kann die Netze von lokalen Rechenzentren nahtlos in die {{site.data.keyword.cloud_notm}} erweitern. Dies ermöglicht die Migration von virtuellen Maschinen in die und aus der {{site.data.keyword.cloud_notm}}, ohne dass hierzu eine Konvertierung oder Änderung erforderlich ist.

**Verfügbarkeit**: Dieser Service ist nur für Instanzen von VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle verfügbar, die in V2.3 und höheren Releases bereitgestellt werden.

Sie können für Ihre vorhandene vCenter Server-Instanz ein Upgrade auf eine vCenter Server with Hybridity Bundle-Instanz durchführen. Weitere Informationen zum Upgrade Ihrer Instanz und zur Bereitstellung des Service "HCX on {{site.data.keyword.cloud_notm}}" finden Sie unter [Upgrade auf vCenter Server with Hybridity Bundle-Instanz durchführen](../vcenter/vc_applyingupdates.html#applying-updates-to-vcenter-server-instances.html#upgrading-to-the-vcenter-server-with-hybridity-bundle-instance).

**Hinweis:** Eine vCenter Server-Instanz mit HCX on {{site.data.keyword.cloud_notm}} ist auf drei simultane Verbindungen von lokalen Standorten begrenzt.

## Technische Spezifikationen für HCX on IBM Cloud

Mit dem Service "HCX on {{site.data.keyword.cloud_notm}}" werden die folgenden Komponenten bestellt und einbezogen.

**Hinweis:** Lokale HCX-Instanzen schließen nur Lizenzierung und Aktivierung ein.

### Ein Aktiv/Passiv-Paar von VMware NSX Edge Services Gateways für das HCX-Management

* CPU: 6 vCPU
* RAM: 8 GB
* Festplatte: 3 GB VMDK

### HCX-Management-Appliance - virtuelle Maschine

* CPU: 4 vCPU
* RAM: 12 GB
* Festplatte: 60 GB VMDK

Weitere HCX-Appliances werden bei der Konfiguration wie für die L2-Konnektivität, die WAN-Optimierung und Gateway-Verbindungen erforderlich bereitgestellt.

### Vernetzung

* 1 öffentliches portierbares Teilnetz mit 16 IP-Adressen
* 2 private portierbare Teilnetze mit 64 IP-Adressen
* 8 IP-Adressen aus dem privaten portierbaren vMotion-Teilnetz

### Lizenzen und Gebühren

* Basislizenzgebühr: Erforderliche Gebühr für den Service
* Gebühr für verwaltete VM: Pro VM berechnet, die monatlich migriert wird

## Hinweise zur Installation von HCX on IBM Cloud

Lesen Sie die folgenden Hinweise, bevor Sie versuchen, HCX on {{site.data.keyword.cloud_notm}} zu installieren.

### Anforderungen an die Anzahl der ESXi-Server

Der Service "HCX on {{site.data.keyword.cloud_notm}}" kann nicht in einer Instanz installiert werden, für die der Standardcluster mehr als 51 ESXi-Server umfasst. Da HCX on {{site.data.keyword.cloud_notm}} acht IP-Adressen im vMotion-Teilnetz aus dem Standardcluster benötigt, sind keine IP-Adressen im vMotion-Teilnetz für HCX on {{site.data.keyword.cloud_notm}} verfügbar, wenn die Anzahl der ESXi-Server 51 überschreitet.

### Anforderungen an Firewallregeln

Bevor Sie den Service "HCX on {{site.data.keyword.cloud_notm}}" installieren, müssen Sie eine Firewallregel zu vorhandenen Firewalls hinzufügen, um den gesamten abgehenden HTTPS-Datenverkehr zuzulassen, damit die virtuelle Appliance für den HCX-Manager sich selbst registrieren kann. Nachdem die Installation des HCX-Managers abgeschlossen ist, können Sie die Firewallregel entfernen. Darüber hinaus müssen Sie Firewallregeln konfigurieren, damit HCX ordnungsgemäß funktionieren kann. Weitere Informationen finden Sie in *Anhang A - Portzugriffsvoraussetzungen* unter der [Architektur von HCX on {{site.data.keyword.cloud_notm}}](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf).

## Hinweise zum Entfernen von HCX on IBM Cloud

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

### Zugehörige Links

* [HCX on {{site.data.keyword.cloud_notm}} bestellen](hcx_ordering.html)
* [HCX on {{site.data.keyword.cloud_notm}} verwalten](managinghcx.html)
* [Glossar der HCX-Begriffe](hcx_glossary.html)
* [Kontaktaufnahme mit dem IBM Support](../vmonic/trbl_support.html)
* [VMware Hybrid Cloud Extension overview](https://cloud.vmware.com/vmware-hcx)
* [VMware Hybrid Cloud Extension documentation](https://hcx.vmware.com/#vm-documentation)
