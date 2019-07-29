---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-17"

subcollection: vmware-solutions


---

# Glossar der HCX-Komponenten und -Begriffe
{: #hcxclient-components}

HCX besteht aus einer Cloud-Seite (Ziel/VCD-Umgebung) und mindestens einem Client (Quelle). Pro vCenter muss eine Instanz von HCX bereitgestellt werden, selbst wenn die vCenter-Instanzen, in denen HCX implementiert ist, in derselben SSO-Domäne auf der Client- oder Cloudseite verbunden sind. Konfigurationen, die von HCX unterstützt werden, sind Eins-zu-eins-, Eins-zu-viele-, Viele-zu-eins- und Viele-zu-viele.

## Zielseite und Clientseite
{: #hcxclient-components-cloud-client-side}

Von HCX wird das Konzept einer Cloudseite (Ziel/VCD-Umgebung) und einer Clientseite (Quelle) verwendet.

- Zielseite - Der HCX-Cloud-Manager wird vorab mit Netz- und Rechenprofilen bereitgestellt und konfiguriert, die für die Erstellung eines Servicenetzes verwendet werden können.  
- Die Clientseite besteht aus beliebigen vSphere-Instanzen, die die Voraussetzungen für die Installation und den Betrieb erfüllen. Die Clientseite von HCX ist der Master, der die cloudseitige Slaveinstanz über das Snap-in ihrer vCenter-Web-Client-Benutzerschnittstelle steuert.

## HCX-Manager
{: #hcxclient-components-hcx-manager}

- Die Cloudseite - Der HCX-Cloud-Manager ist für die Empfangsbereitschaft gegenüber eingehendem Datenverkehr für Registrierung, Management und Steuerung auf Clientseite konfiguriert.
- Die Clientseite - Der HCX-Enterprise Manager ist eine clientseitige spezifische OVA-Imagedatei, die UI-Funktionalität für das Management und den Betrieb von HCX bereitstellt. Der clientseitige HCX-Manager ist verantwortlich für die Registrierung beim cloudseitigen HCX-Manager und die Erstellung einer Managementebene zwischen Client- und Cloudseite. Darüber hinaus ist er zuständig für die Bereitstellung eines Servicenetzes auf Clientseite sowie für Anweisungen an die Cloudseite, dasselbe zu tun.

## Komponenten des Servicenetzes
{: #hcxclient-components-fleet}

Die Komponenten des Servicenetzes sind zuständig für die Erstellung der Daten- und der Steuerebene zwischen Client- und Cloudseite. Sie werden als virtuelle Maschinen (VMs) in spiegelgleichen Paaren bereitgestellt; das Servicenetz besteht aus den folgenden Komponenten:

- Interconnect Appliance (HCX-IX) - Von der Verbindungsappliance werden verschlüsselte Tunnel erstellt, von denen vMotion-Datenverkehr und Replikationsdatenverkehr (Massenmigrationsdatenverkehr) unterstützt wird.
- WAN Optimizer Appliance (HCX-WAN) - HCX enthält eine optional bereitgestellte Silver Peak™ WAN-Optimierungs-Appliance. Diese wird als VM-Appliance bereitgestellt. Nach der Bereitstellung wird der CGW-Tunnelverkehr so umgeleitet, dass er das WAN-Optimierungsprogramm durchläuft. Da das WAN-Optimierungsprogramm den Datenverkehr über das WAN (typischerweise ist ein Verhältnis von 3:1 bis 6:1 zu beobachten) deutlich verringert und gleichzeitig die Zuverlässigkeit der Verbindung erhöht, wird empfohlen, das WAN-Optimierungsprogramm immer zusammen mit dem CGW bereitzustellen. Der zusätzliche Vorteil der Bereitstellung des WAN-Optimierungsprogramms bezieht sich auch auf die Begrenzung der WAN-Bandbreite, die vom Datenverkehr der VM-Migration genutzt wird. Die Managementschnittstelle des WAN-Optimierungsprogramms ist standardmäßig nicht konfiguriert.
- Network Extension (HCX-NE) - Bietet Erweiterungsfunktionen für Layer-2-Netze und ermöglicht Migrationen zwischen lokalen Standorten und der vSphere-Umgebung; hierfür müssen den virtuellen Maschinen erneut IP-Adressen zugeordnet werden.
- Proxy-ESXi-Host - Wenn HCX-IX für die Verbindung mit dem cloudseitigen HCX-Standort konfiguriert wird, wird in vCenter außerhalb der Cluster ein Proxy-ESXi-Host angezeigt. Dieser ESXi-Host verfügt über dieselbe Management- und vMotion-IP-Adresse wie die entsprechende HCX-IX-Appliance. Dadurch kann die vSphere-Umgebung sowohl auf Clientseite als auch auf Cloudseite so funktionieren, als ob sie eine lokale vMotion-Umgebung ausführt. Die Vorteile dieser Methode sind folgende:
  - Die Management-IP-Bereiche auf beiden Seiten können sich überlappen, ohne ihre Funktionalität zu verlieren.
  - Die Cloudseite bietet keine vSphere-Einsicht in die Clientseite, wodurch sich die Sicherheit erhöht.

## HCX-Benutzerportale
{: #hcxclient-components-hcx-user-portals}

- Client-Webbenutzerschnittstelle: Das Webportal des HCX-Clients ist die Hauptbenutzerschnittstelle für HCX. Sobald der clientseitige HCX-Manager installiert ist, wird er als Snap-in für die vCenter-Webbenutzerschnittstelle angezeigt. Er steuert die HCX-Registrierung bei der fernen Cloud (Standortpaarung), die Bereitstellung der Paketkomponente, die Netzerweiterung und die VM-Migration in und aus der Cloud.
- Cloudseitige Benutzerschnittstelle: Die cloudseitige HCX-Benutzerschnittstelle ist über die öffentliche Registrierungs-URL für die HCX-Clientregistrierung zugänglich. Standardmäßig werden die cloudseitigen Berechtigungsnachweise des vCenter-Administrators (`administrator@vsphere.local`) verwendet. In der Regel wird sie für das Upgrade der Installation und zum Ändern einiger Netzkonfigurationen verwendet.

## Zugehörige Links
{: #hcxclient-components-related}

* [Portzugriffsvoraussetzungen für VMware HCX on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-port-req)
* [Installationsumgebung vorbereiten](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [Bereitstellung des HCX-Clients](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [Lokales HCX-Servicenetz](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [VMware Hybrid Cloud-Migrationen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [Überwachung von Parametern und Komponenten](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [Fehlerbehebung für HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)
