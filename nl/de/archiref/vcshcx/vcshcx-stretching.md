---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-16"

---

# Netzerweiterung und Migration virtueller Maschinen
{: #vcshcx-stretching}

## Netzerweiterung
{: #vcshcx-network-stretching}

### Konzepte und bewährte Verfahren für die Netzerweiterung
{: #vcshcx-stretching-best-practices-network}

Was die Brücke des clientseitigen Netzes zum cloudseitigen VXLAN zusammenhält, ist ein hoch entwickeltes VPN mit mehreren Tunneln, das aus proprietärer HCX-Technologie besteht. Es basiert nicht auf NSX, arbeitet aber mit NSX zusammen und erweitert dessen Funktionalität. Dieser Prozess wird von der clientseitigen vCenter-Webbenutzerschnittstelle (UI) gesteuert, automatisiert die Bereitstellung und führt die beiden Endpunkte auf der Client- und der Cloudseite aus. Die Auswahl des zu erweiternden Netzes geschieht einzeln oder stapelweise.

Zusätzlich erhält NSX im Rahmen des Workflows zur Netzerweiterung auf Cloudseite den Befehl, ein VXLAN zu erstellen, das anschließend mit einer Schnittstelle verbunden wird, die auf der angegebenen cloudseitigen L3-Einheit (DLR oder ESG in nicht verbundenem Zustand) und der cloudseitigen L2C-Appliance erstellt wird.

Wenn Sie eine bestimmte Anwendung migrieren, müssen zumeist alle Netze, die von den entsprechenden virtuellen Maschinen (VMs) verwendet werden, über die ganze {{site.data.keyword.cloud}}-Instanz erweitert werden.

Warum "zumeist" und nicht immer? Es kann von Vorteil sein, bestimmten Datenverkehr von der Clientseite zu trennen, nachdem die VM migriert wurde. Beispiel: Backup-Clients für Gast-VMs, die bei der Verschiebung in die Cloud eine hohe Bandbreitennutzung verursachen könnten. Der Client für die Gastmaschine ist bei der VM-Migration nicht erforderlich, da er automatisch von einem moderneren Backup auf Blockebene auf Cloudseite übernommen wird.

Anstatt dass auf jede VM einzeln zugegriffen wird, um den Zeitplan für die Clientsicherung der Gastmaschine abzuschalten, führt die fehlende Verbindung des Client-Backup-Netzadapters (wenn ein Backup-Netz verwendet wird) zum Fehlschlagen des Backups. Diese Situation besteht vorübergehend, bis alle VMs nach der Migration erreichbar sind, um den Backup-Client der Gastmaschine zu inaktivieren.

Die Bandbreite eines einzelnen L2C beträgt theoretisch 4 Gb/s, dies kann jedoch die Grenze für alle erweiterten Netze innerhalb eines einzigen L2C-Paares sein und ist über ein einzelnes erweitertes Netz nicht zu erreichen. Ein einzelnes erweitertes Netz kann ungefähr 1 Gb/s erreichen, da ihm genügend Underlay-Bandbreite zugewiesen und die Latenzzeit mit < ca. 10 ms niedrig ist.

### Prozess zur Erweiterung eines Netzes
{: #vcshcx-stretching-process-stretch}

Zum Erweitern eines Netzes (VLAN oder VXLAN) mit HCX führen Sie die folgenden Schritte über die vCenter-Webbenutzerschnittstelle auf Clientseite aus.

1. Für eine individuelle Auswahl von Portgruppen navigieren Sie zur Registerkarte **Netze** in der vCenter-Webbenutzerschnittstelle, klicken Sie mit der rechten Maustaste auf das zu erweiternde Netz und wählen Sie **Hybriditäts-Aktionen-> Netze in die Cloud erweitern** aus.
2. Wählen Sie die cloudseitige L3-Einheit aus, zu der eine Verbindung hergestellt werden soll, sowie die zu verwendende L2C-Appliance. Geben Sie das aktuelle Standardgateway und die Teilnetzmaske im CIDR-Format ein.
3. Klicken Sie unten in der Anzeige auf **Erweiterung**, um den Workflow für die Netzerweiterung zu starten.

Der Netzfortschritt wird im Teilfenster für vCenter-Client-Tasks überwacht.

### Option "Proximity Routing"
{: #vcshcx-stretching-prox-routing}

Ohne jede Art von Routenoptimierung werden erweiterte Netze für beliebigen L3-Zugriff zur Clientseite zurück geleitet. Diese Anrufdurchleitung führt zu einem ineffizienten Verkehrsmuster, da Pakete zwischen Client (Quelle) und Cloud hin- und hergesendet werden müssen, selbst in Fällen, wo sich sowohl die Quell- als auch die Ziel-VMs in der Cloud befinden. Die Funktion des Proximity-Routings von HCX wurde in Hinblick auf dieses Problem und auch zur Vermeidung von lokalem Datenverkehr-Egress entwickelt.

## vMotion
{: #vcshcx-stretching-vmotion}

Die vMotion-Funktionalität in HCX erweitert die vSphere vMotion-Funktionalität zur Arbeit über unterschiedliche Versionen von vSphere, SSO-Domänen und Typen von Netzkonnektivität im ganzen Internet hinweg. HCX setzt voraus, dass das Netz, das es für diese Verbindung verwendet, nicht sicher ist, und verschiebt sämtlichen Datenverkehr unabhängig vom Typ der Konnektivität durch verschlüsselte Tunnel.

### Konzepte und bewährte Verfahren für vMotion
{: #vcshcx-stretching-best-practices-vmotion}

HCX ist im Wesentlichen ein vMotion-Zweiwege-Proxy. Jede Instanz von HCX emuliert einen einzigen ESXi-Host innerhalb des vSphere-Rechenzentrums, außerhalb von Clustern, die selbst eine "Front" der Paketkomponente Cloud-Gateway (CGW) darstellen. Für jeden HCX-Standort wird ein Proxy-Host angezeigt, der mit dem aktuell angezeigten Standort verknüpft ist. Wenn eine vMotion für einen fernen Host initiiert wird, migriert der lokale ESXi-Host diese VM mittels vMotion auf den lokalen Proxy-ESXi-Host, der die Front des CGW bildet, das ebenfalls einen verschlüsselten Tunnel mit dem CGW auf der fernen Seite aufrechterhält.

Gleichzeitig wird eine vMotion vom fernen ESXi-Proxy-Host zu dem physischen ESXi-Zielhost von vSphere initialisiert, da Daten vom Quell-CGW über den Tunnel empfangen werden. Wenn vMotion verwendet wird, wird im Gegensatz zur Massenmigrationsoption nur eine einzige VM-Migrationsoperation ausgeführt. Aus diesem Grund wird für große Anzahlen von zu migrierenden VMs empfohlen, dies nur dort einzusetzen, wo es keine Ausfallzeiten geben darf oder das Risiko eines Neustarts der VM besteht. Allerdings kann die VM wie bei der Standard-vMotion während des Prozesses aktiv sein.

Es wurde beobachtet, dass eine einzelne vMotion bis zu ca. 1,7 Gb/s im LAN und 300 bis 400 Mbit/s im WAN über das WAN-Optimierungsprogramm erreicht. Dies bedeutet nicht, dass 1,7 Gb/s im LAN gleich 400 Mb/s im WAN sind, sondern dies sind die festgestellten Maximalwerte in den einzelnen beobachteten Umgebungen. Die Umgebung, in der dies beobachtet wurde, bestand aus einem LAN-vMotion-Netz mit 10 GB, einem Internet-Uplink von 1 GB, der mit dem Produktions-Webdatenverkehr gemeinsam genutzt wird.

vMotion kann in folgenden Fällen verwendet werden:
- Die VM bereitet Schwierigkeiten beim Abschalten oder Starten oder die Betriebszeit kann sich ausdehnen und könnte eine riskante Abschaltung nach sich ziehen.
- Jede Clustertypanwendung, für die Platten-UUIDs wie z. B. Oracle Rac-Cluster erforderlich sind. vMotion ändert die Platten-UUIDs auf dem Ziel nicht.
- Sie möchten eine einzelne VM so schnell wie möglich verschieben.
- Eine geplante Migration ist nicht erforderlich.

### Operation
{: #vcshcx-stretching-operation}

Verwenden Sie das Snap-in-Portal für die HCX-Webbenutzerschnittstelle oder die vSphere Web Client-Kontextmenüerweiterungsmenüs, um eine cloudumfassende vMotion zu initiieren. In beiden Fällen wird derselbe Migrationsassistent aufgerufen. Bei den Kontextmenüs ist nur eine einzige VM für Migrationsoperationen ausgewählt. Beim Portal können mehrere VMs ausgewählt werden.

Die umgekehrte Migration von VMs ist nur über das Webbenutzerschnittstellenportal möglich, in dem der HCX-Migrationsassistent das Kontrollkästchen **Umgekehrte Migration** anbietet.

## Massenmigration
{: #vcshcx-stretching-bulk-mig}

### Konzepte und bewährte Verfahren für die Massenmigration
{: #vcshcx-stretching-best-practices-bulk-mig}

Die Massenmigrationsfunktion von HCX verwendet die vSphere-Replikation, um Plattendaten zu migrieren, während die VM auf der Zielinstanz von vSphere HCX neu erstellt wird. Bei der Migration einer VM wird der folgende Workflow verwendet:
- Erstellung einer neuen VM auf der Zielseite und den entsprechenden virtuellen Platten.
- Replikation der VM-Daten auf der neuen VM. Die Replikation wird gestartet, sobald der Assistent abgeschlossen ist, unabhängig von der Zeitplanung für das Umschalten.
- Abschalten der ursprünglichen VM.
- Während des Abschaltzeitraums erfolgt die endgültige Replikation aller Änderungsdaten.
- Einschalten der neuen VM auf der Zielseite.
- Umbenennen und Verschieben der ursprünglichen VM in den verschobenen Cloud-Ordner.

Die Massenmigration bietet gegenüber vMotion folgende Vorteile:
- Gleichzeitige Migration mehrerer VMs.
- Konsistentere Bandbreitennutzung. vMotion kann Schwankungen der Bandbreitennutzung erzeugen, die als Lastspitzen und -täler innerhalb der Netzüberwachungstools oder der Benutzerschnittstelle des WAN-Optimierungsprogramms erkennbar wären.
- Mit der Massenmigration wird eine höhere Gesamtnutzung einer Netzbandbreitenkapazität erhalten, als eine einzelne vMotion bieten könnte.
- Die Massenmigration kann geplant werden, um während eines geplanten Ausfallfensters zu den neu migrierten VMs umzuschalten.
- VMs, die aktuell virtuelle CPU-Funktionen verwenden, die sich von der Cloudseite unterscheiden - hier würde eine vMotion fehlschlagen -, wird die Migration ermöglicht.

Folgende Nachteile hat die Massenmigration gegenüber vMotion:
- Einzelne VMs werden sehr viel langsamer migriert als mit vMotion.
- Die VM erfährt eine kurze Ausfallzeit, während die neue Klon-VM auf der Zielseite erstellt wird.
- VMs, die von der Plattenbestellung und von Platten-UUIDs (Oracle RAC) abhängig sind, können Probleme aufweisen und ihre Platten werden möglicherweise anders angezeigt, wenn die UUIDs geändert werden, wodurch sich die Betriebssystempfade in die Einheiten der virtuellen Platte ändern können.

## Bewährte Verfahren für den Migrationstyp
{: #vcshcx-stretching-mig-type-best-practices}

### Cluster mit gemeinsam genutzter Platte
{: #vcshcx-stretching-shared-disk-clusters}

Oracle RAC-, MS Exchange- und MS-SQL-Cluster sind Beispiele für Anwendungen, in denen zwei oder mehr VMs an einem Cluster teilnehmen, der eine gemeinsam genutzte Platte für alle VMs oder Clusterknoten erfordert. Das Flag "VMware multi-writer" muss auf allen VM-Knoten für Platten aktiviert werden, die Teil des Anwendungsclusters sind (virtuelle Nicht-BS-Platten). VMs mit aktiviertem Flag "multi-writer" für virtuelle Platten werden nicht unterstützt.

Migration eines für eine virtuelle Multi-Writer-Platte aktivierten Clusters:
- Verwendet vMotion, während die ursprünglichen VM-Platten- und UUID-Zuordnungen beibehalten werden.
- Der Cluster bleibt während der Migration in einem herabgesetzten Zustand (Einzelknoten).
- Der Cluster erfährt eine Ausfallzeit vor dem Start der Migration und nach Abschluss der Migration, um die Multi-Writer-Konfiguration über mehrere Cluster-VM-Knoten neu zu assemblieren.

Führen Sie folgende Schritte aus, um einen für eine Multi-Writer-Platte aktivierten Cluster zu migrieren:
1. Fahren Sie den Cluster und alle Knoten gemäß bewährtem Verfahren für die jeweilige Anwendung herunter.
2. Vermerken Sie die Plattenreihenfolge, wenn die Anwendung dies erfordert, in jeder Knoten-VM für die für Multi-Writer konfigurierten virtuellen Platten.
3. Bei Oracle und jeder anderen Anwendung, die die Funktion für virtuelle Platten-UUID verwendet, melden Sie sich an einem bestimmten ESXi-Host an und führen Sie den Befehl `vmkfstools -J getuuid /vmfs/volumes/datastore/VM/vm.vmdk` aus, um die UUIDs der Dateien für die einzelnen virtuellen Platten abzurufen, die das Flag "multi-writer" für den Cluster erfordern. Dies ist notwendig, wenn nach bewährtem Verfahren die Plattenbestellungen daran ausgerichtet werden, wie der Pfad im Betriebssystem angezeigt wird. vMotion kann die Platten (disk1, disk2, disk3) neu anordnen, die UUIDs bleiben jedoch unverändert. Anhand der vermerkten Informationen für die Zuordnung der UUID zur Platte können Sie die Platten-Benennungsreihenfolge neu erstellen. Nach Abschluss der Migration gegebenenfalls die iSCSI-ID. Die Anwendung sollte mit beiden Verfahren funktionieren. Dies wird verwendet, wenn eine Oracle-Instanz über viele virtuelle Platten verfügt, die für die Fehlerbehebung der Anwendung zugeordnet sind.
4. Entfernen Sie die virtuellen Platten aus allen Cluster-VM-Knoten, mit Ausnahme der als primär erachteten virtuellen Platten.
5. Entfernen Sie das Flag "multi-writer" aus dem primären VM-Clusterknoten, der aktuell der einzige Eigner der Clusterplatten sein sollte.
6. Stellen Sie den primären Clusterknoten wieder her, falls dies für minimale Ausfallzeiten erforderlich ist.
7. Migrieren Sie alle Clusterknoten mit vMotion. Migrieren Sie zuerst den primären Cluster. Alle anderen Knoten werden nach Ausschalten des Servers migriert.
8. Nachdem der Knoten, der Eigner der primären Platte ist, die Migration abgeschlossen hat, schalten Sie ihn ab.
9. Falls erforderlich, ordnen Sie die Plattenreihenfolge mit der richtigen Platten-UUID und iSCSI-ID erneut zu. Für die Funktion der Anwendung ist keine erneute Zuordnung erforderlich.
10. Aktivieren Sie nochmals das Flag "multi-writer" auf dem Primärknoten.
11. Starten Sie den Primärknoten und die Prüfoperation.
12. Ordnen Sie die Platte/das Flag "multi-writer" für alle anderen Clusterknoten-VMs zu und schalten Sie sie ein.
13. Überprüfen Sie den Betrieb der übrigen Clusterknoten.

### Allgemeine VMs
{: #vcshcx-stretching-general-vms}

Nachdem die Zuverlässigkeit der Funktion von HCX gesichert ist, muss die Massenmigration verwendet werden. Die Massenmigration ist erforderlich, wenn redundante Anwendungen betroffen sind. Ein Beispiel sind Web-Server sowie Fälle, wo viele Hunderte oder Tausende VMs migriert werden sollen.

### VMs, die direkt angeschlossenes NAS verwenden
{: #vcshcx-stretching-vms-direct-nas}

NFS wird in der Regel verwendet, um Daten, wie z. B. Web-Server-Inhalt, über viele Server hinweg gemeinsam zu nutzen. iSCSI kann über VM-Knoten angewandt werden, die aus einem Anwendungscluster wie E-Mail oder RDBMS bestehen, und ist typischerweise Latenz-sensitiver als NFS.

Für beide Fälle gilt: Wenn die Latenzzeit für das {{site.data.keyword.CloudDataCent_notm}} niedrig gehalten werden kann (< ungefähr 7 ms für iSCSI und was die Anwendung für NFS toleriert) und unter der Voraussetzung, dass die Anwendung mit einer Bandbreite von ungefähr 1 Gb/s oder weniger betrieben werden kann, kann das NAS-Netz mit HCX an einen {{site.data.keyword.cloud_notm}}-Ort erweitert werden. Danach können die VMs normal migriert bzw. mittels vMotion mit HCX verschoben werden.

Nach der Migration können iSCSI-Datenträger mit dem Betriebssystem in eine andere lokale Cloud-Speicherlösung gespiegelt werden und NFS-Daten können in jede beliebige Cloud-Lösung repliziert werden.Hierzu gibt es folgende Aspekte:
- Latenzzeit (iSCSI oder Anwendungstoleranz für NFS)
- Bandbreite (ca. 1 Gb/s pro erweitertes Netz)
- Underlay-Verbindungsbandbreite

Stellen Sie nach dem Migrationslebenszyklus sicher, dass Sie mit Entwicklungs- oder Staging-Anwendungen testen, bevor Sie es mit der Produktion versuchen. QoS kann für den Underlay-Tunnelverkehr ('udp' 500/4500) zwischen den L2C-HCX-Appliances eingesetzt werden, die Latenzzeiten-sensitive erweiterte L2-Netze tragen.

## Netz-Swing
{: #vcshcx-stretching-network-swing}

Wenn das Ziel die Evakuierung des Rechenzentrums nach {{site.data.keyword.cloud_notm}} ist, dann besteht der nächste Schritt bis zum letzten Schritt vor dem Entfernen des HCX-Netzes im Netz-Swing. Durch den Netz-Swing wird eine Migration des Netzteilnetzes erreicht, in dem die aus dem Quell-Rechenzentrum in ein NSX-Overlay-Netz in {{site.data.keyword.cloud_notm}} migrierten VMs enthalten sind.

Der Swing des Netzes beinhaltet folgende Schritte:
- Stellen Sie sicher, dass das Netz aus allen Workloads entfernt wird und alle nicht mit VMs vernetzten Einheiten entweder in ein anderes Netz verschoben, funktional in die Cloud migriert oder nicht mehr unterstützt werden.
- Stellen Sie sicher, dass die NSX-Topologie oder die {{site.data.keyword.cloud_notm}} unterstützende Netztopologie abgeschlossen ist, sodass sie den Netz-Swing unterstützt. Zum Beispiel dynamische Routing-Protokolle und Firewalls.
- Führen Sie einen Workflow zum Rückgängigmachen der Erweiterung des HCX-Netzes in der Benutzerschnittstelle aus und wählen Sie die entsprechende Routing-NSX-Einheit aus, um das Standardgateway für nicht erweiterte Netze zu übernehmen.
- Führen Sie alle externen Routing-Änderungen aus, zu denen folgende gehören können: Einfügen geänderter Routings für migrierte Netze, Entfernen von Routen zum Quellenstandort in das migrierte Netz sowie bei Bedarf Sicherstellen eines Routings zu diesem migrierten Teilnetz über das WAN für nicht migrierte Anwendungen.
- Anwendungseignertest für migrierte Anwendungen von allen möglichen Zugriffspunkten aus: Internet, Intranet und VPN.

Überlegungen zum Netz-Swing einer bestimmten Anwendung, deren VMs vollständig in die Cloud migriert wurden: Wenn Sie eine Vyatta auf der Seite des privaten Netzes verwenden, um Routen in Ihre MPLS-Cloud und -Tunnel zu den Edge-Routing-Einheiten in MPLS einzufügen, um den {{site.data.keyword.cloud_notm}}-IP-Bereich zu vermeiden. Sie haben Ihr Konto mit {{site.data.keyword.cloud_notm}} VRF eingerichtet. Einige der Anwendungen befinden sich hinter einer virtuellen IP (vIP) mit Netzlastausgleich. Diese vIPs befinden sich in Ihrem eigenen Teilnetz, das sich auf einem virtuellen F5 hinter der Vyatta befindet. Wenngleich das Mitteilen spezifischer Routings nach MPLS für Netze, für die ein Swing über HCX nach {{site.data.keyword.cloud_notm}} ausgeführt wurde, bei anderen Netzen gut funktioniert, funktioniert dies nicht für einzelne vIPs, da eine /32-Route eingefügt wird.

Als Lösung ist es üblich, dass WAN-Provider die /32-Routen herausfiltern, die mitgeteilt werden. Finden Sie gemeinsam mit dem WAN-Provider einen Weg, dies zu ermöglichen.

Folgende Aspekte und Auswirkungen sind zu beachten:
- Anwendungen, die Teilnetz, vLAN und VXLAN gemeinsam nutzen, müssen gemeinsam verschoben werden.
- Anwendungen hinter einer Lastausgleichsfunktion, die eine interne umleitbare IP verwendet, können Routing-Änderungen erfordern, wenn sie nicht zusammen verschoben werden können oder sollen. Dies kann beispielsweise der Fall sein, wenn das Risiko als zu hoch empfunden wird, zu viele Anwendungen an einer Swing-Ausführung zu beteiligen.
- VMware-Administratoren, Netzadministratoren (einschließlich Kunden-/WAN-Provider) und Eigner von Anwendungen müssen beteiligt sein. Dies gilt auch dann, wenn es nicht geplant ist, dass sich die Änderungen auf ein bestimmtes System oder eine bestimmte Netzwerkausrüstung auswirken.

## Zugehörige Links
{: #vcshcx-stretching-related}

* [Übersicht über vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs/vcs-hybridity-intro.html)   
