---

copyright:

  years:  2019

lastupdated: "2019-06-17"

subcollection: vmware-solutions


---

# VMware Hybrid Cloud-Migrationen
{: #hcxclient-migrations}

Nach der Bereitstellung und Erweiterung des HCX-Servicenetzes und der HCX-Netzerweiterungen ist der nächste Schritt die Migration der virtuellen Maschinen.

Es gibt drei Migrationstypen:
  - vMotion
  - Massenmigration
  - Cold Migration

## Operation
{: #hcxclient-migrations-operation}

Verwenden Sie das Snap-in-Portal für die HCX-Webbenutzerschnittstelle oder die vSphere Web Client-Kontextmenüerweiterungsmenüs, um eine cloudumfassende vMotion zu initiieren. In beiden Fällen wird derselbe Migrationsassistent aufgerufen. Bei den Kontextmenüs ist nur eine einzige VM für Migrationsoperationen ausgewählt. Beim Portal können mehrere VMs ausgewählt werden.

Die umgekehrte Migration von VMs ist nur über das Webbenutzerschnittstellenportal möglich, in dem der HCX-Migrationsassistent das Kontrollkästchen **Umgekehrte Migration** anbietet.

## vMotion
{: #hcxclient-migrations-vmotion}

Die vMotion-Funktionalität in HCX erweitert die vSphere vMotion-Funktionalität zur Arbeit über unterschiedliche Versionen von vSphere, SSO-Domänen und Typen von Netzkonnektivität im ganzen Internet hinweg. Da von HCX vorausgesetzt wird, dass das Netz, das für diese Verbindung verwendet wird, nicht sicher ist, wird der gesamte Datenverkehr unabhängig vom Typ der Konnektivität über verschlüsselte Tunnel abgewickelt.

### Konzepte und bewährte Verfahren für vMotion
{: #hcxclient-migrations-best-practices-vmotion}

HCX ist im Wesentlichen ein vMotion-Zweiwege-Proxy. Jede Instanz von HCX emuliert einen einzigen ESXi-Host innerhalb des vSphere-Rechenzentrums, außerhalb von Clustern, die selbst eine "Front" der Paketkomponente Cloud-Gateway (CGW) darstellen. Für jeden HCX-Standort wird ein Proxy-Host angezeigt, der mit dem aktuell angezeigten Standort verknüpft ist. Wenn eine vMotion für einen fernen Host initiiert wird, migriert der lokale ESXi-Host diese VM mittels vMotion auf den lokalen Proxy-ESXi-Host, der die Front des CGW bildet, das ebenfalls einen verschlüsselten Tunnel mit dem CGW auf der fernen Seite aufrechterhält.

Gleichzeitig wird eine vMotion-Migration vom fernen ESXi-Proxy-Host zu dem physischen ESXi-Zielhost von vSphere initialisiert, während Daten vom Quell-CGW über den Tunnel empfangen werden. Wenn vMotion verwendet wird, wird im Gegensatz zur Massenmigrationsoption nur eine einzige VM-Migrationsoperation ausgeführt. Aus diesem Grund wird für große Anzahlen von zu migrierenden VMs empfohlen, vMotion nur dort einzusetzen, wo es keine Ausfallzeiten geben darf oder das Risiko eines Neustarts der VM besteht. Allerdings kann die VM wie bei der Standard-vMotion während des Prozesses aktiv sein.

Es wurde beobachtet, dass eine einzelne vMotion bis zu ca. 1,7 Gb/s im LAN und 300 bis 400 Mb/s im WAN über das WAN-Optimierungsprogramm erreicht. Dies bedeutet nicht, dass 1,7 Gb/s im LAN 400 Mb/s im WAN über das WAN-Optimierungsprogramm entsprechen, sondern dies sind die festgestellten Maximalwerte in bestimmten Umgebungen. Eine solche Umgebung bestand aus einem vMotion-Netz mit 10-GB-LAN und einem Internet-Uplink mit 1 GB, die gemeinsam mit dem Webdatenverkehr der Produktionsumgebung genutzt wurden.

Verwenden Sie vMotion in den folgenden Fällen:
- Die VM bereitet Schwierigkeiten beim Abschalten oder Starten oder die Betriebszeit kann sich ausdehnen und könnte eine riskante Abschaltung nach sich ziehen.
- Für jede Clusteranwendung, für die Platten-UUIDs erforderlich sind, z. B. Oracle RAC-Cluster. Beachten Sie, dass vMotion die Platten-UUIDs auf dem Ziel nicht ändert.
- Sie möchten eine einzelne VM so schnell wie möglich verschieben.
- Eine geplante Migration ist nicht erforderlich.

## Massenmigration
{: #hcxclient-migrations-bulk-mig}

### Konzepte und bewährte Verfahren für die Massenmigration
{: #hcxclient-migrations-best-practices-bulk-mig}

Die Massenmigrationsfunktion von HCX verwendet die vSphere-Replikation, um Plattendaten zu migrieren, während die VM auf der Zielinstanz von vSphere HCX neu erstellt wird. Bei der Migration einer VM wird der folgende Workflow verwendet:
- Erstellung einer neuen VM auf der Zielseite und den entsprechenden virtuellen Platten.
- Replikation der VM-Daten auf der neuen VM. Die Replikation wird gestartet, sobald der Assistent abgeschlossen ist, unabhängig von der Zeitplanung für das Umschalten.
- Abschalten der ursprünglichen VM.
- Während des Abschaltzeitraums erfolgt die endgültige Replikation aller Datenänderungen.
- Einschalten der neuen VM auf der Zielseite.
- Umbenennen und Verschieben der ursprünglichen VM in den Cloudordner, in den sie verschoben wurde.

Die Massenmigration bietet gegenüber vMotion folgende Vorteile:
- Gleichzeitige Migration mehrerer VMs.
- Konsistentere Bandbreitennutzung. vMotion kann Schwankungen der Bandbreitennutzung erzeugen, die als Lastspitzen und -täler innerhalb der Netzüberwachungstools oder der Benutzerschnittstelle des WAN-Optimierungsprogramms erkennbar wären.
- Mit der Massenmigration wird eine höhere Gesamtnutzung einer Netzbandbreitenkapazität erhalten, als eine einzelne vMotion bieten könnte.
- Die Massenmigration kann geplant werden, um während eines geplanten Ausfallfensters zu den neu migrierten VMs umzuschalten.
- Ermöglicht die Migration von VMs, die zurzeit andere virtuelle CPU-Features als die Cloudseite verwenden. Die vMotion-Migration könnte in diesen Fällen fehlschlagen.

Folgende Nachteile hat die Massenmigration gegenüber vMotion:
- Einzelne VMs werden sehr viel langsamer migriert als mit vMotion.
- Die VM erfährt eine kurze Ausfallzeit, während die neue Klon-VM auf der Zielseite erstellt wird.
- VMs, die von der Plattenbestellung und von Platten-UUIDs (Oracle RAC) abhängig sind, können Probleme aufweisen und ihre Platten werden möglicherweise anders angezeigt, wenn die UUIDs geändert werden, wodurch sich die Betriebssystempfade in die Einheiten der virtuellen Platte ändern können.

## Bewährte Verfahren für den Migrationstyp
{: #hcxclient-migrations-mig-type-best-practices}

### Cluster mit gemeinsam genutzter Platte
{: #hcxclient-migrations-shared-disk-clusters}

Oracle RAC-, MS Exchange- und MS-SQL-Cluster sind Beispiele für Anwendungen, in denen zwei oder mehr VMs an einem Cluster teilnehmen, der eine gemeinsam genutzte Platte für alle VMs oder Clusterknoten erfordert. Das VMware-Flag "multi-writer" muss auf allen VM-Knoten für Platten aktiviert werden, die Teil des Anwendungsclusters sind (virtuelle Nicht-BS-Platten). VMs, bei denen das Flag "multi-writer" für alle virtuellen Platten aktiviert ist, werden nicht unterstützt.

Migration eines für eine virtuelle Multi-Writer-Platte aktivierten Clusters:
- Verwendet vMotion, während die ursprünglichen VM-Platten- und UUID-Zuordnungen beibehalten werden.
- Der Cluster bleibt während der Migration in einem herabgesetzten Zustand (Einzelknoten).
- Der Cluster erfährt eine Ausfallzeit vor dem Start der Migration und nach Abschluss der Migration, um die Multi-Writer-Konfiguration über die Cluster-VMs hinweg neu zu erstellen.

Führen Sie folgende Schritte aus, um einen für eine Multi-Writer-Platte aktivierten Cluster zu migrieren:
1. Schalten Sie den Cluster und alle Knoten gemäß dem bewährten Verfahren für die jeweilige Anwendung aus.
2. Vermerken Sie die Plattenreihenfolge, wenn die Anwendung dies erfordert, in jeder Knoten-VM für die für Multi-Writer konfigurierten virtuellen Platten.
3. Bei Oracle und jeder anderen Anwendung, die die Funktion für virtuelle Platten-UUID verwendet, melden Sie sich an einem bestimmten ESXi-Host an und führen Sie den Befehl `vmkfstools -J getuuid /vmfs/volumes/datastore/VM/vm.vmdk` aus, um die UUIDs der Dateien für die einzelnen virtuellen Platten abzurufen, die das Flag "multi-writer" für den Cluster erfordern.
  Dies ist notwendig, wenn nach bewährtem Verfahren die Plattenbestellungen daran ausgerichtet werden, wie der Pfad im Betriebssystem angezeigt wird. vMotion kann die Platten (disk1, disk2, disk3) neu anordnen, die UUIDs bleiben jedoch unverändert.
  Wenn die Migration abgeschlossen ist, verwenden Sie die notierte UUID, um die Platteninformationen zuzuordnen sowie die Reihenfolge der Plattenbenennung und die SCSI-ID erneut zu erstellen, falls erforderlich. Die Anwendung sollte mit beiden Verfahren funktionieren. Dies wird verwendet, wenn eine Oracle-Instanz über viele virtuelle Platten verfügt, die für die Fehlerbehebung der Anwendung zugeordnet sind.
4. Entfernen Sie die virtuellen Platten aus allen Cluster-VMs mit Ausnahme der als primär erachteten VM.
5. Entfernen Sie das Flag "multi-writer" aus der primären Cluster-VM. Diese VM sollte zu diesem Zeitpunkt der einzige Eigner der Clusterplatten sein.
6. Schalten Sie den primären Cluster ein, falls dies für die minimale Ausfallzeit erforderlich ist.
7. Migrieren Sie alle Clusterknoten mit vMotion. Migrieren Sie zuerst den primären Cluster. Migrieren Sie alle anderen Knoten, nachdem sie ausgeschaltet wurden.
8. Nachdem der primäre Knoten, der Eigner der Platten ist, die Migration abgeschlossen hat, schalten Sie ihn aus.
9. Falls erforderlich, ordnen Sie die Plattenreihenfolge mit der richtigen Platten-UUID und iSCSI-ID erneut zu. Für die Funktion der Anwendung ist keine erneute Zuordnung erforderlich.
10. Aktivieren Sie das Flag "multi-writer" auf dem Primärknoten wieder.
11. Starten Sie den Primärknoten und überprüfen Sie seine Funktionsfähigkeit.
12. Ordnen Sie die Platten zu bzw. aktivieren Sie das Flag "multi-writer" auf allen anderen Cluster-VMs und schalten Sie sie ein.
13. Überprüfen Sie die Funktionsfähigkeit der übrigen Cluster.

### Allgemeine VMs
{: #hcxclient-migrations-general-vms}

Nachdem die Zuverlässigkeit der Funktion von HCX gesichert ist, muss die Massenmigration verwendet werden. Für redundante Anwendungen ist eine Massenmigration erforderlich. Ein Beispiel sind Web-Server sowie Fälle, wo viele Hunderte oder Tausende VMs migriert werden sollen.

### VMs, die direkt angeschlossenen NAS verwenden
{: #hcxclient-migrations-vms-direct-nas}

NFS wird in der Regel verwendet, um Daten, wie z. B. Web-Server-Inhalt, über viele Server hinweg gemeinsam zu nutzen. iSCSI kann über VM-Knoten verwendet werden, die aus einem Anwendungscluster bestehen, zum Beispiel E-Mails oder RDBMS; iSCSI ist typischerweise Latenz-sensitiver als NFS.

Für beide Fälle gilt: Wenn die Latenzzeit für das {{site.data.keyword.CloudDataCent_notm}} niedrig gehalten werden kann (< ungefähr 7 ms für iSCSI und was die Anwendung für NFS toleriert) und unter der Voraussetzung, dass die Anwendung mit einer Bandbreite von ungefähr 1 Gb/s oder weniger betrieben werden kann, kann das NAS-Netz mit HCX an einen {{site.data.keyword.cloud_notm}}-Ort erweitert werden. Danach können die virtuellen Maschinen normal migriert bzw. mittels vMotion mit HCX migriert werden.

Nach der Migration können iSCSI-Datenträger mit dem Betriebssystem in eine andere lokale Cloudspeicherlösung gespiegelt werden und NFS-Daten können in jede beliebige Cloudlösung repliziert werden. Hierzu gibt es folgende Aspekte:
- Latenzzeit (iSCSI oder Anwendungstoleranz für NFS)
- Bandbreite (ca. 1 Gb/s pro erweitertes Netz)
- Underlay-Verbindungsbandbreite

Führen Sie nach dem Migrationslebenszyklus Tests mit Entwicklungs- oder Staging-Anwendungen aus, bevor Sie die Produktionsumgebung migrieren. QoS kann für den Underlay-Tunnelverkehr ('udp' 500/4500) zwischen den L2C-HCX-Appliances eingesetzt werden, die latenzsensitive erweiterte L2-Netze unterstützen.

## Netz-Swing
{: #hcxclient-migrations-network-swing}

Wenn das Ziel die Evakuierung des Rechenzentrums nach {{site.data.keyword.cloud_notm}} ist, dann besteht der nächste Schritt bis zum letzten Schritt vor dem Entfernen des HCX-Netzes im Netz-Swing. Durch den Netz-Swing wird eine Migration des Netzteilnetzes erreicht, in dem die aus dem Quellrechenzentrum in ein NSX-Overlay-Netz in {{site.data.keyword.cloud_notm}} migrierten VMs enthalten sind.

Der Swing des Netzes beinhaltet folgende Schritte:
- Stellen Sie sicher, dass das Netz aus allen Workloads entfernt wird und alle Netzeinheiten, die keine VMs sind, entweder in ein anderes Netz verschoben, funktional in die Cloud migriert oder nicht mehr verwendet werden.
- Stellen Sie sicher, dass die NSX-Topologie oder die {{site.data.keyword.cloud_notm}} unterstützende Netztopologie abgeschlossen ist, sodass sie den Netz-Swing unterstützt. Zum Beispiel dynamische Routing-Protokolle und Firewalls.
- Führen Sie einen Workflow zum Rückgängigmachen der Erweiterung des HCX-Netzes in der Benutzerschnittstelle aus und wählen Sie die entsprechende Routing-NSX-Einheit aus, um die Steuerung über das Standardgateway des nicht erweiterten Netzes zu übernehmen.
- Führen Sie alle externen Routing-Änderungen aus, zu denen folgende gehören können: Einfügen geänderter Routings für migrierte Netze; Entfernen von Routen zum Quellenstandort aus dem migrierten Netz; Sicherstellen, dass die Weiterleitung zu dem migrierten Teilnetz über das WAN für nicht migrierte Anwendungen noch funktioniert.
- Anwendungseignertest für migrierte Anwendungen von allen möglichen Zugriffspunkten aus: Internet, Intranet und VPN.

Angenommen, Sie möchten einen Netz-Swing für eine bestimmte Anwendung ausführen, für die alle VMs in die Cloud migriert wurden. Beispiel:
- Sie verwenden eine Vyatta-Einheit auf der privaten Netzseite, um Routen in Ihre MPLS-Cloud einzufügen und Daten im Tunnelungsverfahren an die Edge-Routing-Einheiten in der MPLS-Cloud zu übertragen, so dass Sie den {{site.data.keyword.cloud_notm}}-IP-Bereich vermeiden können.
- Sie haben Ihr Konto mit {{site.data.keyword.cloud_notm}} VRF eingerichtet.
- Einige Anwendungen befinden sich hinter einer virtuellen IP (vIP) mit Netzlastausgleich. Diese vIPs befinden sich in Ihrem eigenen Teilnetz, das sich auf einem virtuellen F5 hinter der Vyatta befindet.

Wenngleich das Hinzufügen spezifischer Routings zu MPLS für Netze, für die über HCX ein Swing nach {{site.data.keyword.cloud_notm}} ausgeführt wurde, bei anderen Netzen gut funktioniert, funktioniert dies nicht für einzelne vIPs, da eine /32-Route hinzugefügt wird.

Als Lösung ist es üblich, dass WAN-Provider die /32-Routen herausfiltern, die hinzugefügt werden. Finden Sie gemeinsam mit dem WAN-Provider einen Weg, dies zu ermöglichen.

Folgende Aspekte und Auswirkungen sind zu beachten:
- Anwendungen, die Teilnetz, vLAN und VXLAN gemeinsam nutzen, müssen gemeinsam verschoben werden.
- Anwendungen hinter einer Lastausgleichsfunktion, die eine interne umleitbare IP verwendet, können Routing-Änderungen erfordern, wenn sie nicht zusammen verschoben werden können oder sollen. Dies kann beispielsweise der Fall sein, wenn das Risiko als zu hoch empfunden wird, zu viele Anwendungen an einer Swing-Ausführung zu beteiligen.
- VMware-Administratoren, Netzadministratoren (einschließlich Kunden und WAN-Provider) sowie Eigner von Anwendungen müssen einbezogen werden, selbst wenn das Vorhaben gemäß Plan keine Auswirkungen auf das jeweilige System oder Netzgerät hat.

## Zugehörige Links
{: #hcxclient-migrations-related}

* [Glossar der HCX-Komponenten und -Begriffe](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-components)
* [Installationsumgebung vorbereiten](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [Bereitstellung des HCX-Clients](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [Lokales HCX-Servicenetz](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [Überwachung von Parametern und Komponenten](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [Fehlerbehebung für HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)
