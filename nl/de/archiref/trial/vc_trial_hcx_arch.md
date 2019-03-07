---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# HCX on IBM Cloud-Architekturdesign für Single-node Trial for vCenter Server on IBM Cloud
{: #vc_trial_hcx_arch}

VMware HCX on {{site.data.keyword.cloud}} mit Single-node Trial for VMware vCenter Server on {{site.data.keyword.cloud_notm}} ist ein neues Angebot, das eine nahtlose Verbindung zwischen {{site.data.keyword.vmwaresolutions_short}}-Instanzen und einem lokalen virtualisierten VMware-Rechenzentrum ermöglicht. Während die Empfehlung für vCenter Server mindestens drei Knoten beschreibt, bietet die Single-node Trial (Testversion für Einzelknoten) einen kostengünstigen Pfad zum Testen und Erleben der Vorteile einer Hybrid-Cloud-Implementierung.

{{site.data.keyword.vmwaresolutions_short}} schließt vollautomatisierte, schnelle Bereitstellungen von vCenter Server-Konfigurationen in {{site.data.keyword.cloud_notm}} ein. Das Angebot Single-node Trial for vCenter Server ergänzt die lokale Infrastruktur und ermöglicht die Ausführung vorhandener und zukünftiger Workloads ohne Konvertierung in {{site.data.keyword.cloud_notm}}. Das Angebot verwendet die gleichen Tools, Kenntnisse und Prozesse, die auch lokal verwendet werden. Weitere Informationen zu {{site.data.keyword.vmwaresolutions_short}}-Angeboten finden Sie im [IBM Architecture Center](https://www.ibm.com/cloud/garage/architectures/virtualizationArchitecture).

Der HCX on {{site.data.keyword.cloud_notm}}-Service führt vCenter Server-Instanzen mit vorhandenen lokalen virtualisierten Rechenzentren zusammen, indem er die Erstellung von nahtlosen Netzerweiterungen und die bidirektionale Migration von Workloads ermöglicht. HCX on IBM Cloud-Komponenten, die als virtuelle Maschinen (VMs) am {{site.data.keyword.cloud_notm}} VMware-Zielstandort bereitgestellt werden, ermöglichen die Einrichtung einer Verbindung zu den HCX on {{site.data.keyword.cloud_notm}}-Komponenten, die am gleichgeordneten lokalen Quellenstandort installiert sind.

Abbildung 1. HCX-Architektur

![HCX-Architektur](hcx-architecture.svg "HCX-Architektur")

Im Folgenden wird das Design der HCX on {{site.data.keyword.cloud_notm}}-Serviceimplementierung dargestellt. Beschrieben werden sowohl die Komponenten der {{site.data.keyword.vmwaresolutions_short}}-Instanz auf der Zielseite als auch die Komponenten, die lokal in der Quelle bereitgestellt sind.

## HCX on IBM Cloud - Übersicht
{: #vc_trial_hcx_arch-ovw}

{{site.data.keyword.cloud_notm}} integriert lokale vSphere vCenter-Netze nahtlos in {{site.data.keyword.vmwaresolutions_short}}-Bereitstellungen. Mit der hybriden Vernetzung werden lokale vSphere vCenter-Netze nach {{site.data.keyword.cloud_notm}} erweitert, was die bidirektionale Mobilität der VMs unterstützt.

HCX ist Eigner der Verfahren für Quellen- und Zielverschlüsselung, gewährleistet damit eine konsistente Sicherheit und stellt den Zugang für hybride Workflows wie VM-Migrationen und Netzerweiterungen bereit. Dieses Produktangebot schafft ein optimiertes, softwaredefiniertes WAN (Wide Area Network), um die Performance des erweiterten Netzes zu erhöhen, wodurch die Leistung annähernd die Geschwindigkeit eines LAN (Local Area Network) erreicht. HCX ermöglicht bidirektionale Workloads und die Migration von VMware NSX-Sicherheitsrichtlinien nach {{site.data.keyword.cloud_notm}}; es lässt sich in vSphere vCenter integrieren und wird von vSphere Web Client aus verwaltet.

### Layer-2-Netz-Erweiterung
{: #vc_trial_hcx_arch-layer-2-extension}

HCX ermöglicht es einer vorhandenen lokalen vSphere-Bereitstellung, ein Netz sicher von der lokalen vCenter-Instanz in ein {{site.data.keyword.CloudDataCent_notm}} zu erweitern, in dem VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} oder vCenter Server ausgeführt wird. Mit den folgenden Elementen wird diese Funktion aktiviert:

* HCX stellt eine Appliance mit dem Namen "Layer 2 Concentrator" (Layer-2-Konzentrator, L2C) bereit.
* Erweiterte Netze werden mit {{site.data.keyword.cloud_notm}}-NSX-Edge-Appliances verbunden, die in vCenter Server bereitgestellt sind.
* Es können mehrere Standard-Layer-2-Konzentratoren bereitgestellt werden, um Skalierbarkeit zu erzielen und den Durchsatz von Seiten der lokalen vCenter-Instanz zu erhöhen.
* Virtuelle Maschinen, die über das Cloud-Gateway und über ein erweitertes Layer-2-Netz migriert werden, können ihre IP- und MAC-Adressen beibehalten.

### Migration virtueller Maschinen
{: #vc_trial_hcx_arch-vm-mig}

HCX bietet die folgenden drei Methoden zur VM-Verschiebung:

* Migration mit geringer Ausfallzeit
* vSphere vMotion-Migration
* Cold Migration

#### Migration mit geringer Ausfallzeit
{: #vc_trial_hcx_arch-low-downtime-mig}

Die Migration mit geringer Ausfallzeit beruht auf der vSphere-Replikation, einer verteilten Technologie, die im VMware ESX- oder VMware ESXi-Hypervisor implementiert ist. Die lokale HCX-Bereitstellung erstellt ein Replikat einer Live-VM in {{site.data.keyword.cloud_notm}} und führt eine Umschaltung durch, um die Quellen-VM auszuschalten und die migrierte VM einzuschalten. Der Migrationspfad führt immer über das Cloud-Gateway. Die Übertragung kann über das Internet, ein erweitertes Layer-2-Netz oder eine Direktverbindung erfolgen. Eine VM kann mehr als einmal in jede Richtung migriert werden.

#### vSphere vMotion-Migration
{: #vc_trial_hcx_arch-vmotion-mig}

Sie können Live-VMs mithilfe der vSphere vMotion-Migration über ein Netz übertragen, das hin zu {{site.data.keyword.cloud_notm}} erweitert wurde. Die vMotion-Migration wird auch als "Migration ohne Ausfallzeit" oder "cloudumfassende vMotion" bezeichnet.

#### Cold Migration
{: #vc_trial_hcx_arch-cold-mig}

Mit einer Cold Migration können Sie eine ausgeschaltete VM über ein erweitertes Netz, das mit dem Layer-2-Konzentrator erstellt wurde, nach {{site.data.keyword.cloud_notm}} übertragen.

#### Merkmale, die allen Migrationsmethoden gemeinsam sind
{: #vc_trial_hcx_arch-common-feat}

Folgende Merkmale sind allen drei Migrationstypen gemeinsam:

* Die softwaredefinierte WAN-Optimierung, mit der sich Durchsatz und Geschwindigkeit der Migration erhöhen lassen.
* Die Möglichkeit, Ihre Migration für einen bestimmten Zeitpunkt festzulegen.
* Die Beibehaltung von Hostnamen, VM-Namen oder Beidem.

### Vernetzung
{: #vc_trial_hcx_arch-network}

Die folgenden Netzfunktionen sind in das Cloud-Gateway und die Layer-2-Konzentratoren integriert.

#### Intelligente Flussweiterleitung
{: #vc_trial_hcx_arch-intel-flow}

Die intelligente Flussweiterleitung wählt automatisch die beste Verbindung basierend auf dem Internet-Pfad aus und überflutet effizient die gesamte Verbindung, sodass die Workloads schnellstmöglich verschoben werden. Wenn größere Datenflüsse, wie z. B. Sicherung oder Replikation, eine CPU-Konkurrenzsituation verursachen, werden kleinere Datenflüsse zwecks einer verbesserten Leistung des interaktiven Datenverkehrs an weniger ausgelastete CPUs weitergeleitet.

#### Proximity Routing
{: #vc_trial_hcx_arch-prox-routing}

Das Proximity Routing stellt sicher, dass die Weiterleitung zwischen VMs, die mit erweiterten und weitergeleiteten Netzen verbunden sind (sowohl lokal als auch in der Cloud), symmetrisch ist. Diese Funktion setzt Advanced Networks Services mit dynamischem Routing voraus, das zwischen dem Kundenstandort und der Cloud konfiguriert ist.

Wenn Benutzer ihre Netze in die Cloud erweitern, wird die Layer-2-Konnektivität auf {{site.data.keyword.cloud_notm}}-Netze erweitert. Ohne Routenoptimierung jedoch müssen die Layer-3-Kommunikationsanforderungen zum lokalen weiterzuleitenden Ursprungsnetz zurückkehren. Diese Rückgabe wird als "Tromboning" oder "Hairpinning" bezeichnet. Das Tromboning ist ineffizient, da Pakete zwischen dem Ursprungsnetz und der Cloud hin- und hergesendet werden müssen, selbst wenn sich sowohl die Quellen- als auch die Ziel-VM in der Cloud befindet.

Wenn der Weiterleitungspfad statusabhängige Firewalls oder andere Inline-Geräte umfasst, die auf beide Seiten der Verbindung zugreifen können müssen, kann die Kommunikation fehlschlagen. Ein Fehlschlagen der VM-Kommunikation ohne Routenoptimierung tritt auf, wenn der Austrittspfad aus der Cloud entweder das erweiterte Layer-2-Netz oder das Netz mit Weiterleitung der Organisation ist. Dem lokalen Netz ist der "Direktaufruf" des erweiterten Netzes nicht bekannt. Dieses Problem wird als asymmetrisches Routing bezeichnet. Die Lösung besteht darin, Proximity Routing zu aktivieren, sodass dem lokalen Netz die Routen von {{site.data.keyword.cloud_notm}} mitgeteilt werden können.

Das Cloud-Gateway verwaltet einen Bestand an VMs in der Cloud. Es erkennt auch die folgenden VM-Status:

* Mit vMotion nach {{site.data.keyword.cloud_notm}} übertragen (Migration ohne Ausfallzeit)
* Mit hostbasierter Replikation in die Cloud migriert (Migration mit geringer Ausfallzeit)
* In der Cloud erstellt (in einem erweiterten Netz)

#### Sicherheit
{: #vc_trial_hcx_arch-sec}

Das Cloud-Gateway bietet Suite B-konformes AES-GCM mit IKEv2, AES-NI-Auslagerung und durchflussbasierter Zugangssteuerung. HCX ist außerdem Eigner der Verfahren für Quellen- und Zielverschlüsselung, gewährleistet damit eine konsistente Sicherheit und stellt den Zugang für hybride Workflows wie VM-Migrationen und die Netzerweiterungen bereit. Sicherheitsrichtlinien, die definiert und einer lokalen VM zugeordnet sind, können zusammen mit der VM nach {{site.data.keyword.cloud_notm}} migriert werden.

Für die Richtlinienmigration sind die folgenden Voraussetzungen erforderlich:

* Im lokalen Rechenzentrum muss NSX V6.2.2 oder höher aktiv sein.
* In vSphere handelt es sich bei der Sicherheitsrichtlinie um einen einzelnen NSX-Abschnitt, der eine Vielzahl von Regeln enthalten kann.
* Es kann eine Gruppe von IP- oder MAC-Adressen angegeben werden, die an der Richtlinie beteiligt sein sollen.
* Der Name der Gruppe von IP- bzw. MAC-Adressen darf 218 Zeichen nicht überschreiten.
* Unterstützte Regeln geben Layer-3-IP-Adressen bzw. -Gruppen von IP-Adressen oder aber Layer-2-MAC-Adressen bzw. -Gruppen von MAC-Adressen als Quelle oder Ziel an.

### HCX-Komponenten
{: #vc_trial_hcx_arch-hcx-comp}

Der VMware HCX on {{site.data.keyword.cloud_notm}}-Service stellt vier virtuelle Appliances bereit, die sowohl im lokalen Rechenzentrum als auch auf dem IBM Cloud-Ziel installiert und konfiguriert werden. Im Folgenden werden die vier erforderlichen virtuellen Appliances einzeln beschrieben. Optional können abhängig vom Implementierungsdesign Edge-Einheiten erforderlich sein.

#### HCX-Manager
{: #vc_trial_hcx_arch-hcx-manager}

Die virtuelle HCX-Manager-Appliance stellt eine Erweiterung in die lokale vCenter-Instanz dar. Die Appliance wird als VM bereitgestellt und die zugehörige Dateistruktur enthält die anderen virtuellen Hybrid-Services-Appliances. Der HCX-Manager überwacht die Bereitstellung und Konfiguration des Cloud-Gateways, der Layer-2-Konzentratoren und der virtuellen WAN-Optimierungs­Appliance, sowohl lokal als auch in {{site.data.keyword.cloud_notm}}.

#### Hybrid-Cloud-Gateway
{: #vc_trial_hcx_arch-hcg}

Das Hybrid-Cloud-Gateway (CGW) verwaltet einen sicheren Kanal zwischen der lokalen vSphere-Bereitstellung und {{site.data.keyword.cloud_notm}}. HCX verwendet eine starke Verschlüsselung, um eine Site-to-Site-Verbindung mit {{site.data.keyword.cloud_notm}} zu booten. Der sichere Kanal zwischen vSphere und {{site.data.keyword.cloud_notm}} verhindert Sicherheitsprobleme im Form einer "mittleren Meile" des Netzes. Das Cloud-Gateway umfasst auch die vSphere-Replikationstechnologie, mit der bidirektionale Migrationen durchgeführt werden können.

#### WAN-Optimierung
{: #vc_trial_hcx_arch-wan-opt}

Die WAN-Optimierungs-Appliance ist die Komponente, die WAN-Bedingungen setzt, um die Auswirkungen der Latenzzeit zu reduzieren. Zudem enthält sie eine vorwärtsgerichtete Fehlerkorrektur zur Behebung von Szenarios mit Paketverlusten und Deduplizierung von redundanten Datenverkehrsmustern. Diese reduzieren die Bandbreitennutzung und stellen die bestmögliche Nutzung der verfügbaren Netzkapazität zur Verfügung, um die Datenübertragung zu und von {{site.data.keyword.cloud_notm}} zu beschleunigen.

Die VM-Migration beruht auf der Kombination aus Cloud-Gateway und WAN-Optimierungs­Appliance, mit der eine beispiellose Mobilität zwischen der lokalen vSphere-Instanz und {{site.data.keyword.cloud_notm}} erreicht wird. Darüber hinaus profitiert die Layer-2-Erweiterung von der WAN-Optimierung, wenn der Datenpfad über das Cloud-Gateway weitergeleitet wird.
{:important}

#### Layer-2-Konzentratoren
{: #vc_trial_hcx_arch-layer-2-conc}

Die Layer-2-Konzentrator- (L2C-) Appliances ermöglichen die Erweiterung eines Layer-2-Netzes vom lokalen vSphere-Rechenzentrum nach {{site.data.keyword.cloud_notm}}.

Die Layer-2-Konzentratoren besitzen die folgenden Schnittstellen:

* **Interne Trunkschnittstelle:** Diese Schnittstelle bearbeitet den virtuellen Maschinen-Datenverkehr lokal für die erweiterten Netze mithilfe einer translationalen Brückenzuordnung zu einem entsprechenden nach {{site.data.keyword.cloud_notm}} erweiterten Netz.
* **Uplink-Schnittstelle:** HCX verwendet diese Schnittstelle, um eingekapselten Overlay-Datenverkehr an und von {{site.data.keyword.cloud_notm}} zu senden. Über die Uplink-Schnittstelle werden Anwendungsdaten gesendet.

### Bereitstellungsarchitektur
{: #vc_trial_hcx_arch-deployment}

Informationen zur Bereitstellung und zum Betrieb der HCX on {{site.data.keyword.cloud_notm}}-Bereitstellung finden Sie unter [VMware HCX on {{site.data.keyword.cloud_notm}}
Deployment and Operations](https://www.ibm.com/cloud/garage/files/VMware-HCX-on-IBM-Cloud-Deployment-and-Operations.pdf).
