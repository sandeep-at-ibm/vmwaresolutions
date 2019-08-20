---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-09"

subcollection: vmware-solutions


---

# Installationsumgebung vorbereiten
{: #hcxclient-planning-prep-install}

Für die Installation von VMware HCX on IBM Cloud gelten die folgenden Softwarevoraussetzungen:
* vSphere 5.5 Update 3 oder vSphere 6.0u2 oder höher.
* Wird NSX verwendet, dann Version 6.2.2 oder höher. NSX ist für die Richtlinienmigration erforderlich.
* Um cloudumfassende vMotion verwenden zu können, gelten für Clouds dieselben Affinitätsbeschränkungen, wie sie lokal gelten. Weitere Informationen finden Sie unter [VMware EVC und CPU-Kompatibilität - Häufig gestellte Fragen](https://kb.vmware.com/s/article/1005764).

## Netzkonnektivität konfigurieren
{: #hcxclient-planning-config-net}

HCX muss das öffentliche Internet und Privatleitungen traversieren sowie Verbindungen zu Rechenzentrumskomponenten wie Netze, Switches und Portgruppen herstellen.
* Informationen zu den Ports, die geöffnet sein müssen, damit virtuelle HCX-Appliances erfolgreich installiert werden können, finden Sie unter [Portzugriffsvoraussetzungen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-port-req).
* Sowohl die lokale vSphere-Umgebung als auch die VCS HCX Cloud-Umgebung müssen die Uhrzeitsynchronisation "Network Time Protocol" (NTP) zwischen den lokalen vSphere-Geräten und den VCS HCX-Geräten zulassen. UDP-Port 123 muss für virtuelle HCX-Appliances und -Netze zugänglich sein.

## Lokale Umgebung
{: #hcxclient-planning-on-prem-env}

Stellen Sie vor der Installation von HCX sicher, dass Ihre Umgebung die Tasks unterstützen kann, die Sie ausführen möchten. Die lokale Umgebung muss die folgenden Tasks unterstützen, damit HCX installiert werden kann.
* Virtual Center mit vSphere 5.5 Update 3 oder 6.0u2.
* Die vMotion- und Richtlinienmigrationsfunktionen erfordern NSX Version 6.2.2 oder höher.
* Ein vSphere-Servicekonto, dem die Systemrolle des vCenter Server-Administrators zugewiesen ist.
* In vCenter ausreichend Plattenspeicherplatz für die zu installierenden HCX-Appliances.
* Ausreichende IP-Adressen für die bei der Installation bereitgestellten lokalen VMs.
* Die Ports und Firewalls sind wie in den Portzugriffsvoraussetzungen beschrieben geöffnet.
* Wenn der SSO-Server (Single Sign-on) ein ferner Server ist, muss die URL von vCenter, dem externen SSO-Server oder dem Platform Services Controller (PSC), auf dem der externe Suchservice ausgeführt wird, angegeben werden. Wenn der HCX-Manager bei vCenter registriert ist, muss diese URL angegeben werden.
* Wenn eine vCenter-Instanz über keine eigene interne Instanz des Suchservice verfügt, kann dies einen der folgenden Gründe haben:
  * vCenter 6.0u2 führt einen externen Platform Services Controller aus.
  * vCenter befindet sich im Verbindungsmodus (in dem die sekundäre vCenter-Instanz den SSO-Service der primären vCenter-Instanz oder eines externen SSO-Service verwendet).

## Layer-2-Installationsumgebung überprüfen
{: #hcxclient-planning-verify-layer-2-inst}

Für die Erweiterung des Layer-2-Netzes müssen folgende Voraussetzungen erfüllt sein:
* vSphere Enterprise Plus Edition
* vSphere vCenter muss zur Unterstützung der Layer-2-Erweiterung folgende Voraussetzungen erfüllen:
  * vSphere Enterprise Plus-Lizenz
  * Muss über einen vSphere Distributed Switch (vDS) verfügen. Der verteilte Switch ist mit vSphere Enterprise Plus Edition verfügbar.
  * Nach der Installation muss die lokale Service-Appliance für den Layer-2-Konzentrator über Zugriff auf einen vNIC-Port und eventuell zu erweiternde VLANs verfügen.
  * Wenn das Netz über das öffentliche Internet oder ein virtuelles privates Netz (auf einem alternativen Pfad) erweitert werden soll, benötigt die virtuelle L2C-Maschine in VCS eine IP-Adresse. Die ferne IP-Adresse ist erforderlich, um den Layer-2-Konzentrator zu konfigurieren.
  * Wenn mehrere Layer-2-Konzentratoren gewünscht sind, muss jeder über eine IP-Adresse verfügen, lokal wie auch in der Cloud.

## Vorplanung für die Bereitstellung
{: #hcxclient-planning-predepl}

Ein Großteil der Zeit, die eine Bereitstellung von HCX erfordert, wird für die Phase vor der Bereitstellung benötigt. Während die Ausführung von Migrationsprojekten für Informationssysteme oft Monate oder sogar Jahre dauert, ermöglicht HCX schnelle Migrationen; zudem steht die Netzkonnektivität zur Cloud sofort nach der Bereitstellung zur Verfügung.

Da die Bereitstellung von HCX für einen Kunden auf Unternehmensebene in der Regel Teams für Sicherheit, Netz, Speicher und vSphere-Infrastruktur umfasst, ist es sinnvoll, diese Teams nach Möglichkeit in den PoC einzubinden. Effektives Projektmanagement und eine frühzeitige Einbeziehung von Stakeholdern sind entscheidend, um die Bereitstellungsgeschwindigkeit und den Betrieb von HCX zu gewährleisten.

## Vermeidung von übermäßigem Analyseaufwand
{: #hcxclient-planning-avoiding}

Ein Großteil der Hindernisse und des Zeitaufwands für die Migration einer virtuellen Maschine (VM) oder Gruppe von VMs entsteht dadurch, dass Teile der Anwendungsumgebung geändert werden müssen, diese Änderungen ihrerseits gestaltet werden müssen und die Ausfallzeit zum Vornehmen dieser Änderungen geplant werden muss. Nachdem diese Änderungen vorgenommen wurden, lässt sich die Migration kaum noch abbrechen, weil dies zusätzlich zu übermäßigem Analyseaufwand führen würde. Der Versuch, alle Aspekte der Migration zu erfassen, die Teams zu koordinieren und die Unterstützung wichtiger Stakeholder zu gewinnen, kann das Projekt verzögern.

HCX ermöglicht die vSphere-übergreifende Instanzmigration einer VM oder Gruppe von VMs, die eine Teil- oder vollständige Verbundanwendung darstellen, ohne Änderungen an der Anwendung. Aus diesem Grund bedeutet der Abbruch einer Migration, dass die VMs zurückverschoben oder die Netze wieder erweitert werden müssen. Dadurch entfällt ein Großteil der Migrationsplanung, während eine gewisse Parallelität im Planungsprozess ermöglicht wird. Nach der Auswahl der Anwendungen zum Verschieben und Erstellen eines übergeordneten Netzdesigns können die Anwendungen mit der Migration mit minimaler Konfiguration in der Cloud-Instanz beginnen, während die endgültige Netzkonnektivität und das endgültige Design erarbeitet werden.

## Erweiterte Netze
{: #hcxclient-planning-stretched-net}

Die Komponenten des HCX-Produktpakets zur Netzerweiterung sind sehr stabil. Bei einem Kunden mit mehr als 20 VLANs, die in die {{site.data.keyword.cloud}} über ein WAN mit 1 Gb/s WAN erweitert werden, das gemeinsam mit anderen Datenverkehr- und HCX-Migrationstunneln genutzt wird, gibt es keine Anwendungsprobleme, die dem Netz zuzuschreiben sind. Die Netzverbindungen haben auf diese Weise eine Lebensdauer von mehr als 6 Monaten.

Weitere erweiterte Netze wurden ohne Probleme hinzugefügt und entfernt. Das Auswählen eines {{site.data.keyword.CloudDataCent_notm}} in der Nähe (<6 ms Latenzzeit für diesen einen Kunden) trägt ebenfalls zur Netzstabilität von erweiterten Netzen bei. Die langfristige Aufrechterhaltung von erweiterten Netzen sollte auf Ihr Design keine negativen Auswirkungen haben, vorausgesetzt, Sie verfügen über genügend Bandbreite und eine Latenzzeit, die für Ihre Anwendungen gering genug ist.

## Migrationslebenszyklus
{: #hcxclient-planning-mig-lifecycle}

In den folgenden Abschnitten werden die Phasen innerhalb eines typischen HCX-Migrationslebenszyklus beschrieben, mit Hinweisen darauf, an welchen Punkten die Arbeitsabläufe parallel ausgeführt werden können.

## vSphere-Bestand
{: #hcxclient-planning-vsphere-planning}

- Allgemeine Bewertung von VMs innerhalb einer zu migrierenden Anwendung. "Allgemein" impliziert die Kenntnis der an einer Anwendung beteiligten VMs, ohne sich in Details zu verlieren.
- Wenn Sie vorhaben, eine Vielzahl von VMs zu migrieren, und die Netzbandbreite zwischen Quellen- und Cloudstandorten begrenzt ist, gruppieren Sie die VMs weiter nach VLAN bzw. VXLAN, wenn an der Quelle NSX eingesetzt wird. Dies ermöglicht einen kaskadierenden HCX-Migrationsplan, der vorsieht, dass die VM-Gruppen nach VLAN migriert werden und die L2-Netze, in denen sie sich befinden, nur bis zu dem Punkt erweitert werden, an dem die VLANs freigegeben werden.

Dies bedeutet, dass für die Anfangsgruppe verwandter erweiterter L2-Netze die Erweiterung nur dann rückgängig gemacht werden kann, wenn das Design des cloudseitigen Netzes finalisiert und bereitgestellt wurde. Das Rückgängigmachen der Erweiterung impliziert, dass ein Swing dieses VXLAN-Datenverkehrs jetzt zu einer Weiterleitung durch die NSX-Infrastruktur der Cloud-Instanz führt.

## Baseline-Netzkonfiguration
{: #hcxclient-planning-baseline-net-config}

Erstellen Sie ein geschütztes Perimeternetz in der cloudseitigen vSphere-Instanz. Diese besteht in der Regel aus einem NSX-DLR oder einem Edge-Gerät. Wenn Sie HCX-Proximity-Routing verwenden, müssen Sie keine Firewallregeln oder Uplinktopologien erstellen, da es später oder gleichzeitig ohne Auswirkungen auf den erweiterten L2-Datenverkehr ausgeführt werden kann.

## Netzerweiterung
{: #hcxclient-planning-net-extension}

Das Erweitern des Netzes bedeutet lediglich, dass vorhandene VLANs oder VXLANs aus der vSphere-Quelllenumgebung, dargestellt durch eine virtuelle Switch-Port-Gruppe (vDS), auf ein NSX-VXLAN auf der Cloudseite von HCX erweitert werden.

## Vor-Tests
{: #hcxclient-planning-preflight-tests}

Bei den Vor-Tests wird eine HCX-Migration sowohl mit vMotion als auch mit der Massenmigrationsfunktion durchgeführt, um eine Basis-Übertragungsrate zu ermitteln.

## Migration von Nicht-Produktions-Apps
{: #hcxclient-planning-mig-non-prod-apps}

Die Migration von virtuellen Maschinen beginnt mit den geplanten Stadien für weniger kritische virtuelle Maschinen. Entwicklungs- und Testteams verwenden die Internetkonnektivität für Migration und erweiterten L2-Datenverkehr.

## Cloud-Netzdesign und -bereitstellung beginnen
{: #hcxclient-planning-cloud-net-begins}

Während die Migration fortgesetzt wird, werden cloudseitige Netz-Designs in der cloudseitigen vSphere-Instanz abgeschlossen und implementiert.

## Weitere Aspekte zur Netzkonnektivität
{: #hcxclient-planning-connect-considerations}

Während die Migration läuft, wird die private WAN-Netzkonnektivität bestellt, da es in der Regel einige Wochen bis Monate dauert, bis sie beim Cloud-Provider aufgebaut ist. Nach der Herstellung der privaten Netzkonnektivität kann HCX so konfiguriert werden, dass sowohl die dedizierte private Netzverbindung als auch das Internet für die Migration und den erweiterten L2-Datenverkehr verwendet werden.

## Physische Server
{: #hcxclient-planning-physical-servers}

Wenn das Ziel die Migration des Rechenzentrums in die Cloud ist, können alle physischen Server, die mit den VMs interagieren, daraufhin beurteilt werden, ob sie als VM (P2V) oder als Bare-Metal-VMs nach {{site.data.keyword.cloud_notm}} migriert werden oder ob sie an der Quelle verbleiben. Wenn der physische Server an der Quelle verbleiben soll und HCX nur während der Migration verwendet wird, bis ein dediziertes Netz eingerichtet wird, ist es wichtig zu wissen, ob es sich in einem Netz befindet, das mit HCX in die Cloud erweitert wird. In diesem Szenario lässt HCX die Migration nicht nur der virtuellen Maschinen, sondern auch des gesamten Teilnetzes in die Cloud zu.

Um HCX am Ende der Migration zu entfernen, darf das Teilnetz in der Quelle und im Ziel nicht vorhanden sein, wenn die Verbindung zwischen physischen Einheiten und den migrierten VMs beibehalten werden soll. Dies impliziert, dass alle physischen Einheiten, die am Quellenstandort verbleiben und in erweiterten L2-Netzen vorhanden sind, in ein anderes Netzteilnetz migriert werden müssen, das an die Cloudseite weitergeleitet werden kann. Eine Ausnahme ist es, wenn eine andere erweiterte L2-Technologie verwendet wird, wie zum Beispiel NSX-L2-VPN, um HCX-erweiterte L2-Endpunkte zu ersetzen.

## Produktions- und komplexe Anwendungen migrieren
{: #hcxclient-planning-mig-prod-complex-app}

VMs mit gemeinsam genutzten Multi-Writer-VMDKs, wie z. B. Oracle RAC oder MS Exchange/SQL-Cluster oder VMs mit Roheinheiten-Zuordnungen, sind Beispiele für VMs, die vor der Migration zusätzlicher Aufmerksamkeit bedürfen.

## Netz-Swing
{: #hcxclient-planning-net-swing}

Der Netz-Swing erfolgt nach Abschluss der Evakuierung der VMs in den Netzen der Quellenseite und nachdem das Netzdesign und die Netzimplementierung auf Cloudseite abgeschlossen sind. Wenn Sie HCX so konfigurieren, dass die Erweiterung der Netze im Zusammenhang mit den in Migrationsphasen abgearbeiteten VMs rückgängig gemacht wird, kann der Netzverkehr von den migrierten VMs unter Verwendung der cloudseitigen NSX-Infrastruktur weitergeleitet werden.

## Unterstützte Clientplattformen
{: #hcxclient-planning-client-platforms}

Für Netzerweiterungen werden nur solche Portgruppen unterstützt, die über einen virtuellen verteilten vSphere-Switch (virtual distributed switch, vDS) verfügen. Dies bedeutet auch, dass eigenständige ESXi-Hosts nicht unterstützt werden, da Sie nur dann über einen vDS verfügen können, wenn ESXi-Hosts von vCenter verwaltet werden.
- vSphere 5.1 (Befehlszeile nur für vCenter 5.1 über API)
- vSphere 5.5 (Webclient-Benutzerschnittstelle wird auf vCenter 5.5 Update 3 und höher unterstützt)
- vSphere 6.0
- vSphere 6.5 (vDS muss auf Version 6.0 vorhanden sein)

## Unterstützte Cloudplattformen
{: #hcxclient-planning-cloud-platforms}

Die HCX-Cloudseite wird von der {{site.data.keyword.cloud_notm}}-Automatisierung bereitgestellt.

## Konnektivitätsoptionen
{: #hcxclient-planning-connect-options}

### Standard-HCX-Konnektivität
{: #hcxclient-planning-standard-connect}

Von der {{site.data.keyword.vmwaresolutions_short}}-Automatisierung bereitgestellt, wird die HCX-Cloudseite standardmäßig für die Verbindung über das öffentliche Internet konfiguriert.

## Zugehörige Links
{: #hcxclient-planning-related}

* [Glossar der HCX-Komponenten und -Begriffe](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-components)
* [Bereitstellung des HCX-Clients](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [Lokales HCX-Servicenetz](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [VMware Hybrid Cloud-Migrationen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [Überwachung von Parametern und Komponenten](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [Fehlerbehebung für HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)
