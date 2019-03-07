---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-16"

---

# Glossar der HCX-Komponenten und -Begriffe
{: #vcshcx-components}

HCX besteht aus einer Cloudseite (Ziel) und einem oder mehreren Clients (Quelle). Pro vCenter muss eine Instanz von HCX bereitgestellt werden, selbst wenn die vCenter-Instanzen, in denen HCX implementiert ist, in derselben SSO-Domäne auf der Client- oder Cloudseite verbunden sind. Konfigurationen, die von HCX unterstützt werden, sind Eins-zu-eins-, Eins-zu-viele-, Viele-zu-eins- und Viele-zu-viele.

## Cloudseite und Clientseite
{: #vcshcx-components-cloud-client-side}

HCX hat das Konzept der Cloudseite (Ziel) und der Clientseite (Quelle).
- Die Cloudseite besteht aus vCenter Server on	{{site.data.keyword.cloud}} mit Hybridity Bundle. Die Cloudseite von HCX ist die Slaveinstanz einer HCX-Client-zu-Cloud-Beziehung. Sie wird von der Clientseite gesteuert.
- Die Clientseite besteht aus beliebigen vSphere-Instanzen, die die Voraussetzungen für die Installation und den Betrieb erfüllen. Die Clientseite von HCX ist der Master, der die cloudseitige Slaveinstanz über das Snap-in ihrer vCenter-Web-Client-Benutzerschnittstelle steuert.

## HCX-Manager
{: #vcshcx-components-hcx-manager}

- Der cloudseitige HCX-Manager ist der erste Teil einer HCX-Installation, die auf Cloudseite durch die {{site.data.keyword.vmwaresolutions_short}}-Automatisierung bereitgestellt wird.
Es handelt sich dabei zunächst um eine einzelne, für die Cloudseite spezifische, bereitgestellte OVA-Imagedatei sowie um eine Firewall für die NSX Edge-Lastausgleichsfunktion, die spezifisch für die HCX-Rolle konfiguriert ist. Der HCX-Manager ist für die Empfangsbereitschaft gegenüber eingehendem Datenverkehr für Registrierung, Management und Steuerung auf Clientseite konfiguriert.
- Der clientseitige HCX-Manager ist eine clientseitige spezifische OVA-Imagedatei, die UI-Funktionalität für das Management und den Betrieb von HCX bereitstellt. Der clientseitige HCX-Manager ist verantwortlich für die Registrierung beim cloudseitigen HCX-Manager und die Erstellung einer Managementebene zwischen Client- und Cloudseite. Darüber hinaus ist er zuständig für die Bereitstellung von Paketkomponenten auf Clientseite sowie für Anweisungen an die Cloudseite, dasselbe zu tun.

## Paketkomponenten
{: #vcshcx-components-fleet}

Die HCX-Paketkomponenten sind zuständig für die Erstellung der Daten- und der Steuerebene zwischen Client- und Cloudseite. Als virtuelle Maschinen (VMs) in spiegelgleichen Paaren bereitgestellt, besteht das Paket aus den folgenden Komponenten:

- Cloud-Gateway (CGW): Das Cloud-Gateway ist eine optionale Komponente, die für die Erstellung von verschlüsselten Tunneln verantwortlich ist, die den vMotion- und den Replikations- (Massenmigrations-) Datenverkehr unterstützen. Pro verknüpften HCX-Standort gibt es nur ein Paar.
- Layer-2-Konzentrator (L2C): Der Layer-2-Konzentrator ist eine optionale Komponente, die für die Erstellung von verschlüsselten Tunneln für die Daten- und die Steuerebene entsprechend dem erweiterten Layer-2-Datenverkehr verantwortlich ist. Jedes L2C-Paar kann bis zu 4096 erweiterte Netze verarbeiten. Weitere L2C-Paare werden nach Bedarf bereitgestellt. Die Bandbreite ist auf ungefähr 4 Gb/s begrenzt. Wenn also die Kapazität der externen Bandbreite größer als 4 Gb/s ist, ermöglicht die Verwendung weiterer L2C-Paare eine bessere Nutzung des zugrundeliegenden Netzes.
- WAN-Optimierungsprpogramm: HCX enthält eine optional bereitgestellte Silver Peak™ WAN-Optimierungs-Appliance. Diese wird als VM-Appliance bereitgestellt. In dem Fall wird der CGW-Tunnelverkehr umgeleitet, sodass er das WAN-Optimierer-Paar durchquert.
Da das WAN-Optimierungsprogramm den Datenverkehr über das WAN (typischerweise ist ein Verhältnis von 3:1 bis 6:1 zu beobachten) deutlich verringert und gleichzeitig die Zuverlässigkeit der Verbindung erhöht, wird empfohlen, das WAN-Optimierungsprogramm immer zusammen mit dem CGW bereitzustellen. Der zusätzliche Vorteil der Bereitstellung des WAN-Optimierungsprogramms bezieht sich auch auf die Begrenzung der WAN-Bandbreite, die vom Datenverkehr der VM-Migration genutzt wird. Die Managementschnittstelle des WAN-Optimierungsprogramms ist standardmäßig nicht konfiguriert.
- Proxy-ESX-Host: Wenn das CGW für die Verbindung mit dem cloudseitigen HCX-Standort konfiguriert wird, erscheint in vCenter außerhalb jedes Clusters ein Proxy-ESXi-Host. Dieser ESXi-Host besitzt dieselbe Management- und vMotion-IP-Adresse wie die entsprechende CGW-Appliance. Dadurch kann die vSphere-Umgebung sowohl auf Clientseite als auch auf Cloudseite so funktionieren, als ob sie eine lokale vMotion-Umgebung ausführt. Die Vorteile dieser Methode sind folgende:
    - Die Management-IP-Bereiche auf beiden Seiten können sich überlappen, ohne ihre Funktionalität zu verlieren.
    - Die Cloudseite bietet keine vSphere-Einsicht in die Clientseite, wodurch sich die Sicherheit erhöht.

## HCX-Benutzerportale
{: #vcshcx-components-hcx-user-portals}

- Client-Webbenutzerschnittstelle: Das Webportal des HCX-Clients ist die Hauptbenutzerschnittstelle für HCX. Sobald der clientseitige HCX-Manager installiert ist, wird er als Snap-in für die vCenter-Webbenutzerschnittstelle angezeigt. Er steuert die HCX-Registrierung bei der fernen Cloud (Standortpaarung), die Bereitstellung der Paketkomponente, die Netzerweiterung und die VM-Migration in und aus der Cloud.

- Cloudseitige Benutzerschnittstelle: Die cloudseitige HCX-Benutzerschnittstelle ist über die öffentliche Registrierungs-URL für die HCX-Clientregistrierung zugänglich. Standardmäßig verwendet sie die cloudseitige vSphere-SSO-Anmeldung (` administrator@vsphere.local`). In der Regel wird sie für das Upgrade der Installation und zum Ändern einiger Netzkonfigurationen verwendet. Außerdem werden mit ihr auch virtuelle Netze innerhalb von HCX erstellt.

- Management-Benutzerschnittstelle für client-/cloudseitige HCX-Manager-Appliance: Der Zugriff auf die Appliance-Managementbenutzerschnittstelle für die Cloud- oder Clientseite erfolgt über die private IP-Adresse der VM, so wie sie in vCenter angezeigt wird.
`https://<hcxmanager_IP>:9443`. Die ID (meist "admin") und das Kennwort werden über das {{site.data.keyword.vmwaresolutions_short}}-Portal bereitgestellt. Die Managementbenutzerschnittstelle wird für Folgendes verwendet: zum Starten und Stoppen von HCX-Manager-Services, Konfigurieren der Protokollüberwachung, für grundlegende Netzkonfigurationen, manuelle Upgrades, Unterstützung der Protokollerfassung, wenn die Webbenutzerschnittstelle nicht funktioniert, Registrierung bei vSphere-Komponenten (vCenter, PSC, NSX-Manager) und Zertifikatsmanagement.

## Zugehörige Links
{: #vcshcx-components-related}

* [Übersicht über vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)   
