---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

subcollection: vmwaresolutions


---
# Installationsumgebung vorbereiten
{: #hcx-archi-prep-install}

Für die Installation von VMware HCX on IBM Cloud gelten die folgenden Softwarevoraussetzungen:
* vSphere 5.5 Update 3 oder vSphere 6.0 Update 2 oder höher.
* Wird NSX verwendet, dann Version 6.2.2 oder höher. NSX ist für die Richtlinienmigration erforderlich.
* Um cloudumfassende vMotion verwenden zu können, gelten für Clouds dieselben Affinitätsbeschränkungen, wie sie lokal gelten. Weitere Informationen finden Sie unter [VMware EVC und CPU-Kompatibilität - Häufig gestellte Fragen](http://bit.ly/2vK6Sp5).

## Netzkonnektivität konfigurieren
{: #hcx-archi-prep-install-config-net}

HCX muss das öffentliche Internet und Privatleitungen traversieren sowie Verbindungen zu Rechenzentrumskomponenten wie Netzwerke, Switches und Portgruppen herstellen.
* [Portzugriffsvoraussetzungen](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-port-req) listet Ports auf, die geöffnet werden müssen, damit die virtuellen HCX-Appliances erfolgreich installiert werden können.
* Sowohl die lokale vSphere-Umgebung als auch die VCF/VCS HCX Cloud-Umgebung müssen die Uhrzeitsynchronisation "Network Time Protocol" (NTP) zwischen lokalen vSphere-Einheiten und den VCF/VCS HCX-Einheiten zulassen. UDP-Port 123 muss für virtuelle HCX-Appliances und -Netze zugänglich sein.

## Lokale Umgebung
{: #hcx-archi-prep-install-on-prem-env}

Stellen Sie vor der Installation von HCX sicher, dass Ihre Umgebung die Tasks unterstützen kann, die Sie ausführen möchten. Die lokale Umgebung muss die folgenden Tasks unterstützen, damit HCX installiert werden kann.
* Virtual Center mit vSphere 5.5 Update 3 oder 6.0 Update 2.
* Die vMotion- und Richtlinienmigrationsfunktionen erfordern NSX Version 6.2.2 oder höher.
* Ein vSphere-Servicekonto, dem die Systemrolle des vCenter Server-Administrators zugewiesen ist.
* In vCenter ausreichend Plattenspeicherplatz für die zu installierenden HCX-Appliances.
* Ausreichende IP-Adressen für die bei der Installation bereitgestellten lokalen VMs.
* Die Ports und Firewalls sind wie in den Portzugriffsvoraussetzungen beschrieben geöffnet.
* Wenn der SSO-Server (Single Sign-on) ein ferner Server ist, muss die URL von vCenter, dem externen SSO-Server oder dem Platform Services Controller (PSC), auf dem der externe Suchservice ausgeführt wird, angegeben werden. Wenn der HCX-Manager bei vCenter registriert ist, muss diese URL angegeben werden.
* Wenn eine vCenter-Instanz über keine eigene interne Instanz des Suchservice verfügt, kann dies einen der folgenden Gründe haben:
  * vCenter 6.0 Update 2 führt einen externen Platform Services Controller aus.
  * vCenter befindet sich im Verbindungsmodus (in dem die sekundäre vCenter-Instanz den SSO-Service der primären vCenter-Instanz oder eines externen SSO-Service verwendet).

## Layer-2-Installationsumgebung überprüfen
{: #hcx-archi-prep-install-verify-layer-2-inst}

Für die Erweiterung des Layer-2-Netzes müssen folgende Voraussetzungen erfüllt sein:
* vSphere Enterprise Plus Edition
* vSphere vCenter muss zur Unterstützung der Layer-2-Erweiterung folgende Voraussetzungen erfüllen:
  * vSphere Enterprise Plus-Lizenz
  * Muss über einen vSphere Distributed Switch (vDS) verfügen. Der verteilte Switch ist mit vSphere Enterprise Plus Edition verfügbar.
  * Nach der Installation muss die lokale Service-Appliance für den Layer-2-Konzentrator über Zugriff auf einen vNIC-Port und eventuell zu erweiternde VLANs verfügen.
  * Wenn das Netz über das öffentliche Internet oder ein virtuelles privates Netz (auf einem alternativen Pfad) erweitert werden soll, benötigt die virtuelle L2C-Maschine in VCF/VCS eine IP-Adresse. Die ferne IP-Adresse ist erforderlich, um den Layer-2-Konzentrator zu konfigurieren.
  * Wenn mehrere Layer-2-Konzentratoren gewünscht sind, muss jeder über eine IP-Adresse verfügen, lokal wie auch in der Cloud.

## Zugehörige Links
{: #hcx-archi-prep-install-related}

* [Installation und Konfiguration von HCX für die Quelle](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-install-cfg-src)
* [VMware EVC und CPU-Kompatibilität - Häufig gestellte Fragen](http://bit.ly/2vK6Sp5)
