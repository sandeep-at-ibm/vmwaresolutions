---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-05"

keywords: VMware HCX, HCX, tech specs HCX

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Übersicht über VMware HCX on IBM Cloud
{: #hcx_considerations}

Der Service "HCX on {{site.data.keyword.cloud}}" kann die Netze von lokalen Rechenzentren nahtlos in die {{site.data.keyword.cloud_notm}} erweitern. Dies ermöglicht die Migration von virtuellen Maschinen in die und aus der {{site.data.keyword.cloud_notm}}, ohne dass hierzu eine Konvertierung oder Änderung erforderlich ist. HCX erstellt eine Abstraktionsschicht, die Anwendungsmobilität und Hybridinfrastruktur durch sicher erweiterte Netze ermöglicht. Sie können Ihre VMware-Umgebung einfach von vSphere 5.1 auf die neueste vSphere-Version modernisieren, ohne Ihre bestehende Anwendung refraktorieren oder ändern müssen, da HCX diese nahtlose Transformation ermöglicht. Mit HCX können Sie Ihre IP-Teilnetzbereiche in {{site.data.keyword.cloud_notm}} bringen und die IP-Konsistenz durch eine Hybrid-Bereitstellung sicherstellen, während gleichzeitig hohe Sicherheit durch durchgängige Suite B-Verschlüsselungen gegeben ist.

HCX on {{site.data.keyword.cloud_notm}} setzt voraus, dass Sie entweder NSX Advanced oder Enterprise über {{site.data.keyword.cloud_notm}} oder eine äquivalente Version mittels BYOL (Bring Your Own License) nutzen. Für die Bestellung des VMware HCX on {{site.data.keyword.cloud_notm}}-Service ist eine Verpflichtung über 12 Monate erforderlich. Nach der Erstbereitstellung von HCX werden Ihnen 12 aufeinanderfolgende Monate in Rechnung gestellt. Alle zusätzlichen Knoten sind im anfänglichen Ablaufdatum für die Bereitstellung enthalten. Nach Ablauf der 12-monatigen Verpflichtung können Sie den HCX on {{site.data.keyword.cloud_notm}}-Service installieren und deinstallieren sowie Hosts und Cluster ohne Einschränkungen hinzufügen und entfernen. Ihr Konto wird dann auf monatlicher Basis belastet und kann jederzeit storniert werden.

Das Ablaufdatum der 12-monatigen Verpflichtung ist auf der Detailseite von HCX on {{site.data.keyword.cloud_notm}} verfügbar. Weitere Informationen zum Anzeigen von Servicedetails finden Sie unter [Services für vCenter Server-Instanzen bestellen, anzeigen und entfernen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_addingremovingservices#vc_addingremovingservices-viewing-procedure).
{:note}

Eine vCenter Server-Instanz mit HCX on {{site.data.keyword.cloud_notm}} ist auf drei simultane Verbindungen von lokalen Standorten begrenzt.

HCX on {{site.data.keyword.cloud_notm}} wird auf den folgenden Plattformen unterstützt:

* vSphere 5.1 (Befehlszeile nur für vCenter 5.1 über API)
* vSphere 5.5 (Webclient-Benutzerschnittstelle wird in vCenter 5.5u3 und höher unterstützt)
* vSphere 6.0
* vSphere 6.5 (vDS muss auf Version 6.0 vorhanden sein)
* vSphere 6.7

## Technische Spezifikationen für HCX on IBM Cloud
{: #hcx_considerations-specs}

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

Bevor Sie den Service "HCX on {{site.data.keyword.cloud_notm}}" installieren, müssen Sie eine Firewallregel zu vorhandenen Firewalls hinzufügen, um den gesamten abgehenden HTTPS-Datenverkehr zuzulassen, damit die virtuelle Appliance für den HCX-Manager sich selbst registrieren kann. Nachdem die Installation des HCX-Managers abgeschlossen ist, können Sie die Firewallregel entfernen. Darüber hinaus müssen Sie Firewallregeln konfigurieren, damit HCX ordnungsgemäß funktionieren kann. Weitere Informationen finden Sie unter [VMware HCX on {{site.data.keyword.cloud_notm}} - Portzugriffsvoraussetzungen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-port-req#hcx-archi-port-req).

## Hinweise zum Entfernen von HCX on IBM Cloud
{: #hcx_considerations-delete}

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
* [Geführte Demo zu VMware HCX on IBM Cloud: Informationen zur Migration einer VM mithilfe von HCX](https://www.ibm.com/cloud/garage/dte/producttour/vmware-hcx-ibm-cloud-guided-demo-learn-how-migrate-vm-using-hcx){:external}
* [Glossar der HCX-Begriffe](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_glossary)
* [Kontaktaufnahme mit dem IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Überblick über VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx){:external}
* [Dokumentation zu VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx/resources){:external}
