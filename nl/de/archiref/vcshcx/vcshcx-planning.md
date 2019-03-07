---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-16"

---

# Vorplanung für die Bereitstellung
{: #vcshcx-planning}

Ein Großteil der Zeit, die eine Bereitstellung von HCX erfordert, wird für die Phase vor der Bereitstellung benötigt.
Während Migrationsprojekte für Informationssysteme oft viele Monate bis Jahre dauern, ermöglicht HCX den Migrationen und der Netzkonnektivität in die Cloud den sofortigen Start nach der Bereitstellung. Da die Bereitstellung von HCX für einen Kunden auf Unternehmensebene in der Regel Teams für Sicherheit, Netz, Speicher und vSphere-Infrastruktur umfasst, ist es sinnvoll, diese Teams nach Möglichkeit in den PoC einzubinden. Effektives Projektmanagement und eine frühzeitige Einbeziehung von Stakeholdern sind entscheidend, um die Bereitstellungsgeschwindigkeit und den Betrieb von HCX zu gewährleisten.

## Vermeidung von übermäßigem Analyseaufwand
{: #vcshcx-planning-avoiding}

Ein Großteil der Hindernisse und des Zeitaufwands für die Migration einer virtuellen Maschine (VM) oder Gruppe von VMs entsteht dadurch, dass Teile der Anwendungsumgebung geändert werden müssen, diese Änderungen ihrerseits gestaltet werden müssen und die Ausfallzeit zum Vornehmen dieser Änderungen geplant werden muss. Nachdem diese Änderungen vorgenommen wurden, lässt sich die Migration kaum noch abbrechen, weil dies zusätzlich zu übermäßigem Analyseaufwand führen würde. Der Versuch, alle Aspekte der Migration zu erfassen, die Teams zu koordinieren und wichtige Stakeholder während der Zeit bis zur Finalisierung des Plans zu ändern, kann das Projekt verzögern bzw. macht die schnelle vollständige Umsetzung des Projekts zwingend.

HCX ermöglicht die vSphere-übergreifende Instanzmigration einer VM oder Gruppe von VMs, die eine Teil- oder vollständige Verbundanwendung darstellen, ohne Änderungen an der Anwendung. Aus diesem Grund bedeutet der Abbruch einer Migration, dass die VMs zurückverschoben oder die Netze wieder erweitert werden müssen. Dadurch entfällt ein Großteil der Migrationsplanung, während eine gewisse Parallelität im Planungsprozess ermöglicht wird. Nach der Auswahl der Anwendungen zum Verschieben und Erstellen eines übergeordneten Netzdesigns können die Anwendungen mit der Migration mit minimaler Konfiguration in der Cloud-Instanz beginnen, während die endgültige Netzkonnektivität und das endgültige Design erarbeitet werden.

## Erweiterte Netze
{: #vcshcx-planning-stretched-net}

Die Komponenten des HCX-Produktpakets zur Netzerweiterung sind sehr stabil. Bei einem Kunden mit mehr als 20 VLANs, die in die {{site.data.keyword.cloud}} über ein WAN mit 1 Gb/s WAN erweitert werden, das gemeinsam mit anderen Datenverkehr- und HCX-Migrationstunneln genutzt wird, gibt es keine Anwendungsprobleme, die dem Netz zuzuschreiben sind.
Die Netzverbindungen haben auf diese Weise eine Lebensdauer von mehr als 6 Monaten.
Weitere erweiterte Netze wurden ohne Probleme hinzugefügt und entfernt.
Das Auswählen eines {{site.data.keyword.CloudDataCent_notm}} in unmittelbarer Nähe (< 6 ms Latenzzeit für diesen einen Kunden) trägt ebenfalls zur Netzstabilität von erweiterten Netzen bei. Die langfristige Aufrechterhaltung von erweiterten Netzen sollte auf Ihr Design keine negativen Auswirkungen haben, vorausgesetzt, Sie verfügen über genügend Bandbreite und eine Latenzzeit, die für Ihre Anwendungen gering genug ist.


## Migrationslebenszyklus
{: #vcshcx-planning-mig-lifecycle}

In den folgenden Abschnitten werden die Phasen innerhalb eines typischen HCX-Migrationslebenszyklus beschrieben, mit Hinweisen darauf, an welchen Punkten die Arbeitsabläufe parallel ausgeführt werden können.

## vSphere-Bestand
{: #vcshcx-planning-vsphere-planning}

- Verwenden Sie eine Anwendung wie z. B. [RVTOOLS](https://www.robware.net/rvtools/), um einen Speicherauszug des Bestands der vCenter-Quelleninstanz in Tabellenform zu erstellen.
- Allgemeine Bewertung von VMs innerhalb einer zu migrierenden Anwendung.
"Allgemein" impliziert die Kenntnis der an einer Anwendung beteiligten VMs, ohne sich in Details zu verlieren.
- Wenn Sie vorhaben, eine Vielzahl von VMs zu migrieren, und die Netzbandbreite zwischen Quellen- und Cloudstandorten begrenzt ist, gruppen Sie die VMs weiter nach VLAN bzw. VXLAN, wenn an der Quelle NSX eingesetzt wird. Dies ermöglicht einen kaskadierenden HCX-Migrationsplan in Fällen, wo VM-Gruppen nach VLAN migriert werden und die L2-Netze, auf denen sie sich befinden, nur bis zu dem Punkt erweitert werden, an dem die VLANs evakuiert werden. Dies bedeutet, dass für die Anfangsgruppe verwandter erweiterter L2-Netze die Erweiterung nur dann rückgängig gemacht werden kann, wenn das Design des cloudseitigen Netzes finalisiert und bereitgestellt wurde. Das Rückgängigmachen der Erweiterung impliziert, dass ein Swing dieses VXLAN-Datenverkehrs jetzt zu einer Weiterleitung durch die NSX-Infrastruktur der Cloud-Instanz führt.


## Baseline-Netzkonfiguration
{: #vcshcx-planning-baseline-net-config}

Erstellen Sie ein gehärtetes Perimeternetz in der cloudseitigen vSphere-Instanz. Diese besteht in der Regel aus einem NSX-DLR oder einem Edge-Gerät. Wenn Sie HCX-Proximity-Routing verwenden, müssen Sie keine Firewallregeln oder Uplinktopologien erstellen, da es später oder gleichzeitig ohne Auswirkungen auf den erweiterten L2-Datenverkehr ausgeführt werden kann.

## 	Netzerweiterung
{: #vcshcx-planning-net-extension}

Das Erweitern des Netzes bedeutet lediglich, dass vorhandene VLANs oder VXLANs aus der vSphere-Quelllenumgebung, dargestellt durch eine virtuelle Switch-Port-Gruppe (vDS), auf ein NSX-VXLAN auf der Cloudseite von HCX erweitert werden.

## Vor-Tests
{: #vcshcx-planning-preflight-tests}

Bei den Vor-Tests wird eine HCX-Migration sowohl mit vMotion als auch mit der Massenmigrationsfunktion durchgeführt, um eine Basis-Übertragungsrate zu ermitteln.

## Migration von Nicht-Produktions-Apps
{: #vcshcx-planning-mig-non-prod-apps}

An diesem Punkt beginnt die Migration von VMs mit den geplanten Wellen von weniger kritischen VMs. Für Entwicklung, Test usw. verwenden Sie die Internetkonnektivität für Migration und erweiterten L2-Datenverkehr.


## Cloud-Netzdesign und -bereitstellung beginnen
{: #vcshcx-planning-cloud-net-begins}

Während die Migration fortgesetzt wird, werden cloudseitige Netz-Designs in der cloudseitigen vSphere-Instanz abgeschlossen und implementiert.

## Weitere Aspekte zur Netzkonnektivität
{: #vcshcx-planning-connect-considerations}

Während die Migration läuft, wird die private WAN-Netzkonnektivität bestellt, da es in der Regel einige Wochen bis Monate dauert, bis sie beim Cloud-Provider aufgebaut ist. Nach der Herstellung der privaten Netzkonnektivität kann HCX so konfiguriert werden, dass sowohl die dedizierte private Netzverbindung als auch das Internet für die Migration und den erweiterten L2-Datenverkehr verwendet werden.

## Physische Server
{: #vcshcx-planning-physical-servers}

Wenn das Ziel die Migration des Rechenzentrums in die Cloud ist, können alle physischen Server, die mit den VMs interagieren, daraufhin beurteilt werden, ob sie als VM (P2V) oder als Bare-Metal-VMs nach {{site.data.keyword.cloud_notm}} migriert werden oder ob sie an der Quelle verbleiben. Wenn der physische Server an der Quelle verbleiben soll und HCX nur während der Migration verwendet wird, bis ein dediziertes Netz eingerichtet wird, ist es wichtig zu wissen, ob es sich in einem Netz befindet, das mit HCX in die Cloud erweitert wird. In diesem Szenario lässt HCX die Migration nicht nur der VMs, sondern auch des gesamten Teilnetzes in die Cloud zu. Um HCX am Ende der Migration zu entfernen, darf das Teilnetz in der Quelle und im Ziel nicht vorhanden sein, wenn die Verbindung zwischen physischen Einheiten und den migrierten VMs beibehalten werden soll. Dies impliziert, dass alle physischen Einheiten, die am Quellenstandort verbleiben und in erweiterten L2-Netzen vorhanden sind, in ein anderes Netzteilnetz migriert werden müssen, das an die Cloudseite weitergeleitet werden kann. Eine Ausnahme ist es, wenn eine andere erweiterte L2-Technologie verwendet wird, wie zum Beispiel NSX-L2-VPN, um HCX-erweiterte L2-Endpunkte zu ersetzen.

## Produktions- und komplexe Anwendungen migrieren
{: #vcshcx-planning-mig-prod-complex-app}

VMs mit gemeinsam genutzten Multi-Writer-VMDKs, wie z. B. Oracle RAC oder MS Exchange/SQL-Cluster oder VMs mit Roheinheiten-Zuordnungen, sind Beispiele für VMs, die vor der Migration zusätzlicher Aufmerksamkeit bedürfen.

## Netz-Swing
{: #vcshcx-planning-net-swing}

Der Netz-Swing erfolgt nach Abschluss der Evakuierung der VMs in den Netzen der Quellenseite und nachdem das Netzdesign und die Netzimplementierung auf Cloudseite abgeschlossen sind. Wenn Sie HCX konfigurieren, um die Erweiterung der Netze im Zusammenhang mit den abgeschlossenen VMs in Migrationswellen rückgängig zu machen, ermöglicht dies es den migrierten VMs, Netzverkehr unter Verwendung der cloudseitigen NSX-Infrastruktur umzuleiten.

## Unterstützte Clientplattformen
{: #vcshcx-planning-client-platforms}

Für Netzerweiterungen werden nur solche Portgruppen unterstützt, die über einen virtuellen verteilten vSphere-Switch (virtual distributed switch, vDS) verfügen. Dies bedeutet auch, dass eigenständige ESXi-Hosts nicht unterstützt werden, da Sie nur dann über einen vDS verfügen können, wenn ESXi-Hosts von vCenter verwaltet werden.
- vSphere 5.1 (Befehlszeile nur für vCenter 5.1 über API)
- vSphere 5.5 (Webclient-Benutzerschnittstelle wird auf vCenter 5.5 Update 3 und höher unterstützt)
- vSphere 6.0
- vSphere 6.5 (vDS muss auf Version 6.0 vorhanden sein)

## Unterstützte Cloudplattformen
{: #vcshcx-planning-cloud-platforms}

Die HCX-Cloudseite wird von der {{site.data.keyword.cloud_notm}}-Automatisierung bereitgestellt.

## Konnektivitätsoptionen
{: #vcshcx-planning-connect-options}

### Standard-HCX-Konnektivität
{: #vcshcx-planning-standard-connect}

Von der {{site.data.keyword.vmwaresolutions_short}}-Automatisierung bereitgestellt, wird die HCX-Cloudseite standardmäßig für die Verbindung über das öffentliche Internet konfiguriert.

### Optionale Konnektivität
{: #vcshcx-planning-optional-connect}

Die Verbindung über das private {{site.data.keyword.cloud_notm}}-Netz kann zum Zeitpunkt der Bestellung ausgewählt werden.

## Zugehörige Links
{: #vcshcx-planning-related}

* [Übersicht über vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)   
