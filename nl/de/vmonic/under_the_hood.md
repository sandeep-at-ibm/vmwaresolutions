---

copyright:

  years:  2019

lastupdated: "2019-06-28"

keywords: about vmware solutions, product overview, benefits

subcollection: vmware-solutions

---
{:external: target="_blank" .external}

# IBM Cloud for VMware Solutions: Werfen Sie einen Blick hinter die Kulissen
{: #under_the_hood}

## Virtualisierte VMware-Umgebungen bereitstellen und verwalten
{: #under_the_hood-deploy}

Machen Sie sich eingehend mit der Architektur von {{site.data.keyword.vmwaresolutions_full}} vertraut, einem {{site.data.keyword.cloud_notm}}-Angebot zum Bereitstellen und Verwalten von virtualisierten VMware-Umgebungen. In diesem Lernprogramm erhalten Sie einen Einblick in die Komponenten des Angebots, sodass Sie verstehen, wie diese zusammen funktionieren und so die Umgebung in der öffentlichen Cloud bereitstellen und verwalten.

## Zwei Unternehmen, eine optimierte Lösung
{: #under_the_hood-two-companies}

Benutzer stellen jetzt schon seit einiger Zeit virtualisierte VMware-Umgebungen in IBM Public Cloud bereit, entweder selbst oder mit Unterstützung professioneller Dienstleister. Im Februar 2016 haben [IBM und VMware eine Partnerschaft angekündigt](https://www-03.ibm.com/press/us/en/pressrelease/49154.wss){:external}, um den Prozess zur Bereitstellung von VMware-Software und VMware-Umgebungen in {{site.data.keyword.cloud_notm}} zu automatisieren. Einer der frühen Erfolge dieser Partnerschaft war die Möglichkeit, dass unterschiedliche VMware-Produktbereitstellungen und -Lizenzen in der {{site.data.keyword.vmwaresolutions_short}}-Konsole bestellt werden konnten und später [VMware Horizon Air](https://www-03.ibm.com/press/us/en/pressrelease/49932.wss){:external} in {{site.data.keyword.cloud_notm}} angeboten wurde. Darüber hinaus haben IBM und VMware gemeinsam eine [Standardreferenzarchitektur und eine Bereitstellungsanleitung für VMware](https://www.ibm.com/cloud/garage/architectures/virtualizationArchitecture){:external} in IBM Public Cloud erstellt.

Im Herbst 2016 haben IBM und VMware gemeinsam {{site.data.keyword.vmwaresolutions_short}} freigegeben. Diese Angebote basieren auf den Virtualisierungstechnologien von VMware, einschließlich virtualisierter Berechnung (VMware vSphere), Netzbetrieb (VMware NSX) und optional virtualisiertem Speicher (VMware vSAN). Diese Anwendungen werden treffender als softwaredefinierte Rechenzentren bezeichnet.

{{site.data.keyword.vmwaresolutions_short}} basiert auf der VMware-Technologie, was für die Bereitstellung und Verwaltung dieser softwaredefinierten Rechenzentren in IBM Public Cloud eine erhebliche Optimierung bedeutet. Mithilfe von {{site.data.keyword.vmwaresolutions_short}} ist es jetzt möglich, Teile der Standardreferenzarchitektur für {{site.data.keyword.cloud_notm}} nicht mehr manuell, sondern automatisch bereitzustellen. Umgebungen, deren Bereitstellung und Konfiguration früher Wochen dauerte, können jetzt in einigen Stunden bereitgestellt werden.

Da die Bereitstellung jetzt einfacher ist, können Sie sich auf das Implementieren von Lösungen auf der Basis von VMware konzentrieren, anstatt auf das Erstellen der Umgebung. Da Umgebungen schnell bereitgestellt werden können, können Sie sowohl Hybrid-Cloud-Lösungen mit übergreifender Verarbeitung für Ihre private Cloud und IBM Public Cloud als auch cloudnative Lösungen in IBM Public Cloud erstellen. Wenn Sie mehrere Bereitstellungen kombinieren, können Sie problemlos Disaster-Recovery oder Hochverfügbarkeitsfunktion zu Ihren Lösungen hinzufügen.

Nun werfen wir einen Blick hinter die Kulissen der {{site.data.keyword.vmwaresolutions_short}}-Architektur. Sie erhalten einen Einblick in die unterschiedlichen Komponenten, die Teil der Lösung sind, und erfahren, wie diese zusammen funktionieren, damit ein softwaredefiniertes Rechenzentrum in {{site.data.keyword.cloud_notm}} bereitgestellt und verwaltet werden kann. Außerdem erfahren Sie mehr über die Netztopologie und verschiedene Optionen, die Sie für die Verbindung zu Ihrer Umgebung verwenden können.

## Grundlagen von IBM Cloud for VMware Solutions

Ihre softwaredefinierten Rechenzentren werden über die [{{site.data.keyword.vmwaresolutions_short}}-Konsole](https://cloud.ibm.com/infrastructure/vmware-solutions/console){:external} bereitgestellt und verwaltet. An der Konsole melden Sie sich mit Ihrem IBMid-Konto an.

Mithilfe des VMware Solutions-Katalogs können Sie eine von mehreren Arten an Virtualisierungsumgebungen bereitstellen. Die besprochene Virtualisierungslösung ist *VMware vCenter Server on {{site.data.keyword.cloud_notm}}*, von der VMware vSphere Hypervisor, VMware vCenter Server, VMware NSX und optional VMware vSAN bereitgestellt werden. Sie können diese Umgebung auch mit weiteren Add-on-Services für Sicherungen, Disaster-Recovery, Migration, Sicherheit, Konformität und Netzbetrieb bereitstellen.

Bevor Sie eine vCenter Server-Instanz bestellen, müssen Sie den API-Schlüssel für die {{site.data.keyword.cloud_notm}}-Infrastruktur im VMware Solutions-Katalog konfigurieren. Klicken Sie hierzu im linken Menü der Konsole auf [Einstellungen](https://cloud.ibm.com/infrastructure/vmware-solutions/console/settings){:external} und geben Sie den Benutzernamen und den API-Schlüssel ein, wenn Sie zum Angeben der Berechtigungsnachweise für die {{site.data.keyword.cloud_notm}}-Infrastruktur aufgefordert werden. Vom System wird überprüft, ob Ihr API-Schlüssel und Ihr Konto die entsprechenden Berechtigungen und Einstellungen zum Bereitstellen der Instanz aufweisen.

Wenn Sie Ihre vCenter Server-Instanz bestellen, wählen Sie zuerst den Namen und die VMware vSphere-Version aus. Alle VMware-Instanzen werden zusammen mit den Microsoft Active Directory-Domänencontrollern bereitgestellt; für Single Sign-on (SSO) müssen Sie Ihre Instanz entweder als primäre oder sekundäre Site angeben. Eine primäre Instanz ist die erste oder einzige Instanz in einer Single-Sign-on-Domäne. Sie können weitere sekundäre Instanzen bereitstellen und sie derselben Single-Sign-on-Domäne einer vorhandenen primären Instanz zuordnen. Als Nächstes entscheiden Sie, ob Sie eigene VMware-Lizenzen verwenden bzw. welche Edition einer Lizenz Sie von {{site.data.keyword.cloud_notm}} mieten möchten. Zum Schluss wählen Sie die {{site.data.keyword.cloud_notm}}-Region und das Rechenzentrum für die Instanz sowie die Merkmale für CPU und Hauptspeicher der Hosts im Cluster aus.

Im nächsten Teil der Bestellseite geben Sie die Merkmale für Speicher und Netzbetrieb der Instanz an. Sie können zwischen vSAN- und NFS-Speicher für den Cluster wählen und haben die Möglichkeit, die Größe und Anzahl der vSAN-Flash-Platten und die vSAN-Lizenzedition bzw. die Größe, Anzahl und Leistung der NFS-Speicherdatenträger auszuwählen. Für den Netzbetrieb wählen Sie das Hostnamenspräfix für die Hosts und die Unterdomäne und die Domäne für den Cluster aus. Sie haben die Möglichkeit, die Active Directory-Controller als einzelne virtuelle {{site.data.keyword.cloud_notm}}-Serverinstanz oder als zwei virtuelle Maschinen im Cluster bereitzustellen, für die Sie die Lizenzierung und Aktivierung bereitstellen müssen.

Unten auf der vCenter Server-Bestellseite können Sie verschiedene Add-on-Services auswählen, die Sie für die VMware-Instanz bereitstellen können und die Ihrem {{site.data.keyword.cloud_notm}}-Konto in Rechnung gestellt werden. Für einige Services ist eine zusätzliche Konfiguration erforderlich, die Sie als Teil des Bestellformulars angeben.

Vom Bestellformular wird auf Basis der Auswahlen ein Schätzpreis berechnet und angezeigt. Sie können diese Schätzung sowie verschiedene Vertragsbedingungen überprüfen, bevor Sie Ihre Bestellung abgeben.

### Bereitstellungsoptionen
{: #under_the_hood-deploy-options}

Im vCenter Server-Bestellformular können Sie verschiedene Optionen für CPU, Hauptspeicher und Speicher für Ihre Instanz auswählen. Da regelmäßig neue Optionen verfügbar gemacht werden, ist es von Vorteil, den {{site.data.keyword.cloud_notm}}-Katalog auf die neuesten Verfügbarkeitsinformationen zu überprüfen.

Von {{site.data.keyword.cloud_notm}} wird die vCenter Server-Instanz mithilfe von drei VLANs bereitgestellt: einem öffentlichen und zwei privaten. Das öffentliche VLAN ist mit Dual 10 GbE-Schnittstellen verbunden und ist weitgehend für die Verwendung nach Ihrem Ermessen für öffentliche Verbindungen oder eine Tunnelung für Bereitstellungen eigener Workloads reserviert. Zur Bereitstellungszeit wird jedoch ein NSX Edge Services Gateway-Paar für das öffentliche VLAN bereitgestellt, damit von einigen Add-on-Services eine Verbindung zum öffentlichen Netz zu Lizenzierungs- und Rechnungsstellungszwecken hergestellt werden kann. Die privaten VLANs sind mit separaten Dual 10 GbE-Schnittstellen verbunden: Das erste private VLAN wird für die Managementkommunikation und NSX VTEP verwendet, das zweite für vMotion und den NFS-Speicherdatenverkehr.

VMware-Instanzen können in 35 unterschiedlichen {{site.data.keyword.CloudDataCents_notm}} bereitgestellt werden. Von {{site.data.keyword.cloud_notm}} werden von Zeit zu Zeit neue Rechenzentren bereitgestellt. Überprüfen Sie den {{site.data.keyword.cloud_notm}}-Katalog auf die neueste Liste der verfügbaren Standorte.

### Instanzbereitstellung
{: #under_the_hood-inst-deploy}

Wenn Sie eine neue VMware vCenter-Instanz bestellen, wählen Sie den Standort und die Spezifikation der Instanz aus. Anschließend werden von {{site.data.keyword.vmwaresolutions_short}} die vorher ausgewählten {{site.data.keyword.cloud_notm}}-Angaben für Benutzername und API-Schlüssel zum Orchestrieren des Bestellverfahrens, der Installation und der Konfiguration der Virtualisierungsumgebung verwendet. Dazu gehören:

1. Bestellung der VLANs und Teilnetze für den Netzbetrieb.
2. Bestellung von {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} mit installiertem vSphere Hypervisor.
3. Bereitstellung und Konfiguration von VMware vCenter Server mit integriertem Platform Services Controller, VMware NSX Manager, Controllern und Edge Services Gateways.
4. Bestellung und Konfiguration des Clusterspeichers, einschließlich VMware vSAN oder {{site.data.keyword.cloud_notm}}-Endurance-Speicher.
5. Bereitstellung einer IBM Managementkomponente mit der Bezeichnung IBM CloudDriver.
6. Bereitstellung und Konfiguration der Add-on-Services, die Sie für Ihre Instanz ausgewählt haben.
7. Validierung der Installation und Konfiguration der Umgebung.

Sie wählen das {{site.data.keyword.CloudDataCent_notm}} aus, in dem Sie Ihre Instanz bereitstellen möchten. Wenn die Hardware im ausgewählten {{site.data.keyword.CloudDataCent_notm}} verfügbar ist, dauert der Bereitstellungsprozess für die Instanz in der Regel weniger als 24 Stunden.

Wenn die Instanz bereitgestellt wurde und Sie über eine VPN-Verbindung zu Ihrem {{site.data.keyword.cloud_notm}}-Konto verfügen, können Sie direkt vom Web-Browser Ihrer Workstation eine Verbindung zum vCenter-Server aufbauen.

Auf die Komponenten Ihrer Instanz wird in der Regel über ihre Hostnamen und nicht über ihre IP-Adressen zugegriffen. Damit Sie eine Verbindung zu vCenter herstellen und sich an vCenter authentifizieren können, müssen Sie sicherstellen, dass der Hostname von vCenter und Platform Services Controller (PSC) von Ihrer Workstation aufgelöst werden kann; fügen Sie ihn hierzu zur Datei 'hosts' Ihrer Workstation wie in Liste 1 beschrieben hinzu. 1. Den Hostnamen und die IP-Adresse finden Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole in der Registerkarte **Zusammenfassung** für Ihre Instanz. Es kann auch sinnvoll sein, die Hostnamen und IP-Adressen für Ihre vSphere-Hosts zur Datei 'hosts' hinzuzufügen.

*Liste 1. Hostdatei*

<pre># vCenter und Platform Services Controller (PSC) am Standort Dallas
10.208.85.196  vcenter-dallas.dallas.example.com
# Hosts am Standort Dallas
10.208.85.171  host0.dallas.example.com
10.208.85.153  host1.dallas.example.com
10.208.85.137  host2.dallas.example.com</pre>

Wenn Ihre Instanz bereitgestellt wurde, können Sie sie in der Konsole verwalten. Hierfür stehen Ihnen folgende Managementfunktionen zur Verfügung:

* Knoten im Cluster bereitstellen oder aus dem Cluster entfernen
* Zusätzliche Cluster in demselben Rechenzentrum und Pod oder in alternativen Rechenzentren und Pods bereitstellen und entfernen
* Add-on-Services für Ihre Instanz bereitstellen und entfernen
* Upgrade für bestimmte Lizenzeditionen für die Instanz durchführen

Von der {{site.data.keyword.vmwaresolutions_short}}-Konsole wird eine Detailsicht jeder einzelnen vCenter Server-Instanz bereitgestellt. In der Registerkarte **Zusammenfassung** jeder einzelner Instanz befinden sich ein Link zur vCenter-Konsole und weitere Details zur Instanz und zu Managementkomponenten. In der Registerkarte **Infrastruktur** werden Details zu den Clustern, Hosts, Speicher und Netzbetrieb der Instanz angezeigt; außerdem können Sie Cluster, Hosts und Speicher hinzufügen oder entfernen. In der Registerkarte **Update und Patch** können Sie ein Upgrade für bestimmte Lizenzeditionen durchführen. In der Registerkarte **Services** können Sie die Add-on-Services anzeigen und verwalten, die für Ihre Instanz bereitgestellt werden. In der Registerkarte **Bereitstellungsverlauf** wird der Verlauf aller Aktionen angezeigt, die für die Instanz ausgeführt wurden.

## Komponenten von IBM Cloud for VMware Solutions
{: #under_the_hood-comp}

Die Bereitstellung und Verwaltung Ihrer Umgebung basiert auf dem Zusammenwirken unterschiedlicher Komponenten. Die meisten dieser Komponenten werden in Ihrem {{site.data.keyword.cloud_notm}}-Konto bereitgestellt. Da die Lösung vom Zusammenwirken aller dieser Komponenten abhängig ist, dürfen Sie keine dieser Komponenten auf Ihrem {{site.data.keyword.cloud_notm}}-Konto ändern oder stornieren. Die korrekte Vorgehensweise zum Entfernen einer aktiven Instanz ist die Verwendung der Konsole und nicht das Stornieren einzelner Komponenten.

Da es sich um eine integrierte Virtualisierungsumgebung handelt, werden die Kosten für die verschiedenen Virtualisierungskomponenten (zum Beispiel VMware-Lizenzen), Infrastrukturkomponenten (Bare-Metal-Server, VLANs, Teilnetze und Speicher) und Managementkomponenten in der Rechnung, die Sie von {{site.data.keyword.cloud_notm}} erhalten, einzeln aufgeführt.

### Die IBM Cloud for VMware Solutions-Konsole
{: #under_the_hood-console}

Sie melden sich an der [{{site.data.keyword.vmwaresolutions_short}}-Konsole](https://cloud.ibm.com/infrastructure/vmware-solutions/console){:external} an, um Instanzen zu erstellen und zu verwalten. Über diesen Teil der Lösung werden die ersten Bestellungen und die Bereitstellung für Ihre Umgebung ausgeführt, sie wird aber auch für die laufende Verwaltung der Umgebung verwendet. Von den bereitgestellten Instanzen wird über das {{site.data.keyword.cloud_notm}} Private-Netz mit der Konsole kommuniziert.

### Die Komponente IBM CloudBuilder
{: #under_the_hood-ibm-cb}

Wenn Sie eine neue Instanz bereitstellen, wird von der Konsole eine temporäre virtuelle Serverinstanz (VSI) in Ihrem {{site.data.keyword.cloud_notm}}-Konto bereitgestellt. Dieser virtuelle Server wird als IBM CloudBuilder bezeichnet. Damit werden die Installation und Konfiguration aller Komponenten der Instanz sowie die Validierung der Umgebung durchgeführt. Nach Abschluss der Bereitstellung wird CloudBuilder gelöscht.

### Die Komponente IBM CloudDriver
{: #under_the_hood-ibm-cd}

Analog zu CloudBuilder ist auch IBM CloudDriver eine temporäre virtuelle Serverinstanz (VSI), die im {{site.data.keyword.cloud_notm}}-Konto zum Ausführen von Aktionen für Ihre Instanz bereitgestellt wird. Sie wird nach Bedarf zum Konfigurieren oder Entfernen von Hosts, Clustern, Speicher oder Services in der Instanz bereitgestellt.

### VMware-Komponenten
{: #under_the_hood-vmware-comp}

Für alle Instanzen wird vSphere Hypervisor auf den Bare-Metal-Servern installiert. Anschließend wird von {{site.data.keyword.cloud_notm}} vCenter Server Appliance mit integriertem Platform Services Controller (PSC), NSX Manager, drei NSX-Controllern und zwei NSX Edge Services Gateway-Paaren im VMware-Management-Cluster bereitgestellt.

### Zusätzliche Komponenten
{: #under_the_hood-add-comp}

Abhängig von Ihrer Auswahl werden entweder eine Microsoft Windows-VSI oder zwei virtuelle Microsoft Windows-Maschinen neben dem oder im Cluster als Active Directory-Server für Managementkomponenten bereitgestellt. Optional können Sie eigene Active Directory-Server als zusätzliche Identitätsquellen für den Managementzugriff hinzufügen.

Unabhängig von der Bereitstellung der Geschäftskontinuität für eigene Workloads wird von {{site.data.keyword.cloud_notm}} dringend empfohlen, Sie die Managementkomponenten der Instanz zu sichern. In der {{site.data.keyword.vmwaresolutions_short}}-Konsole können Sie einen integrierten IBM Spectrum Protect Plus-Sicherungsserver oder einen Veeam Backup & Replication-Sicherungsserver zusammen mit Ihrer Instanz bereitstellen. Diese Sicherungsservices können als Teil einer [Gesamtsicherungslösung](/docs/services/vmwaresolutions?topic=vmware-solutions-solution_backingup) für Ihre Instanz verwendet werden.

### Lizenzen
{: #under_the_hood-licenses}

Von {{site.data.keyword.cloud_notm}} wird eine Reihe von VMware-Lizenzen (zum Beispiel vCenter Server und NSX) bereitgestellt, die in Ihrer Instanz installiert sind und Ihrem {{site.data.keyword.cloud_notm}}-Konto in Rechnung gestellt werden.

## Netzarchitektur von IBM Cloud for VMware Solutions
{: #under_the_hood-network}

Von Ihrer vCenter Server-Instanz wird eine Verbindung zu einem öffentlichen VLAN für Ihre bereitgestellten Workloads aufgebaut. Das öffentliche VLAN können Sie weitgehend nach eigenem Ermessen verwenden, mit dem öffentlichen VLAN ist jedoch auch ein NSX Edge Services Gateway-Paar verbunden, das bestimmten Add-on-Services die abgehende Kommunikation zu Lizenzierungs- und Abrechnungszwecken ermöglicht. Es ist möglich, eine Instanz ohne Verwendung des öffentlichen Netzes bereitzustellen; in diesem Fall werden nicht alle Add-on-Services unterstützt und Sie müssen möglicherweise einen Web-Proxy bereitstellen, damit bestimmte Add-on-Services verwendet werden können.

Die vCenter Server-Instanz verfügt über zwei private VLANs, die miteinander in der Schnittstelle des privaten Netzes für die Hypervisoren zusammengelegt werden. Das erste private VLAN wird für die Managementkonnektivität (zum Beispiel die vCenter-Kommunikation mit Hypervisoren) und von NSX für die Tunnelung des gesamten VXLAN-Datenverkehrs für die bereitgestellten Workloads verwendet. Das zweite private VLAN wird für vMotion und den Speicherdatenverkehr verwendet. Für den Speicherdatenverkehr können entweder NFS- oder vSAN-Protokolle verwendet werden.

Von {{site.data.keyword.cloud_notm}} werden bestimmte zusätzliche Services für diese privaten VLANs bereitgestellt. Von den Active Directory-Servern wird mit {{site.data.keyword.cloud_notm}}-DNS-Servern über das private Management-VLAN kommuniziert. Von den Hosts und anderen Komponenten wird mit {{site.data.keyword.cloud_notm}}-NTP-Servern über das private Management-VLAN kommuniziert. Von IBM CloudBuilder und CloudDriver wird mit der {{site.data.keyword.vmwaresolutions_short}}-Konsole auch über dieses VLAN kommuniziert. Von den Hosts wird die Verbindung zum {{site.data.keyword.cloud_notm}}-Endurance-Speicher über das private Speicher-VLAN hergestellt.

### Verbindung zur Instanz herstellen
{: #under_the_hood-connect-inst}

Sie können auf mehrere Arten eine Verbindung zu Ihren Instanzen aufbauen. Sie können direkt eine Verbindung zu privaten IP-Adressen in der Instanz (zum Beispiel vCenter) über das [{{site.data.keyword.cloud_notm}}-VPN](https://www.softlayer.com/VPN-Access){:external} herstellen. Sie können auch [{{site.data.keyword.cloud_notm}}-Netzappliances](https://www.ibm.com/cloud/network-appliances){:external} und [Hardware-Firewalls oder virtuelle Firewalls von {{site.data.keyword.cloud_notm}}](https://www.ibm.com/cloud/network-security), wie zum Beispiel FortiGate oder vSRX, für Ihr Konto bestellen. Von {{site.data.keyword.cloud_notm}} werden auch [direkte Links](https://www.ibm.com/cloud/direct-link){:external} zwischen Ihrem Netz und den VLANs in Ihrem {{site.data.keyword.cloud_notm}}-Konto bereitgestellt.

Für den Zugriff auf Ihre bereitgestellten virtuellen Maschinen können Sie öffentliche IP-Adressen direkt auf die virtuellen Maschinen anwenden. Sie können die {{site.data.keyword.cloud_notm}}-Netzappliancefunktionen und -Firewallfunktionen jedoch auch verwenden, um durch die Verwendung von NAT und Firewalls einen sichereren öffentlichen Zugriff auf die virtuellen Maschinen zu konfigurieren. Sie können auch NSX Edge-Server bereitstellen und diese Server verwenden, um eine VPN- oder NAT-Konnektivität für Ihre virtuellen Maschinen einzurichten.

## Fazit
{: #under_the_hood-conclusion}

In diesem Lernprogramm haben Sie sich mit den grundlegenden Funktionen von {{site.data.keyword.vmwaresolutions_short}} zum Bereitstellen und Verwalten standardisierter VMware-Virtualisierungsumgebungen in einer öffentlichen Cloud vertraut gemacht. Da Sie diese Umgebungen schneller als je zuvor bereitstellen können, können Sie sich darauf konzentrieren, Ihre Anwendungen und Lösungen auf dieser Basis bereitzustellen und die Clouds miteinander zum Bereitstellen von Disaster-Recovery und Hochverfügbarkeit zu verbinden.

Sie haben die verschiedenen Komponenten kennengelernt, die in Ihrem {{site.data.keyword.cloud_notm}}-Konto bereitgestellt und in den {{site.data.keyword.cloud_notm}}-Abrechnungen angezeigt werden und durch ihr Zusammenwirken die Ausführung der Umgebung ermöglichen. Schließlich haben Sie sich mit der Netzwerkarchitektur der Lösung und einigen Optionen zur Herstellung einer Verbindung zur Umgebung vertraut gemacht; hierfür wurden verschiedene sichere Konnektivitätsoptionen besprochen, damit die Kommunikation privat bleibt, alternativ wurde die Verwendung verschiedener Optionen für Verbindungen ins öffentliche Internet erläutert.

Jetzt wissen Sie über alles Bescheid, was Sie für den Einstieg benötigen. Fahren Sie fort und stellen Sie heute Ihre nächste VMware-Virtualisierungsumgebung in {{site.data.keyword.cloud_notm}} bereit.

## Zugehörige Links
{: #under_the_hood-related}

* [Einführung](/docs/services/vmwaresolutions?topic=vmware-solutions-getting-started)
* [VMware Solutions-Architektur](/docs/services/vmwaresolutions?topic=vmware-solutions-solution_overview)
