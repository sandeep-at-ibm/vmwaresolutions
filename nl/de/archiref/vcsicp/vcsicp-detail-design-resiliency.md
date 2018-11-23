---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-06"

---

# Sicherung, Disaster-Recovery und Skalierbarkeit

## Sicherung und Disaster-Recovery

###	VCS-Sicherung

Als Teil von {{site.data.keyword.vmwaresolutions_full}} wird die Veeam-Sicherungssoftware optional auf einer {{site.data.keyword.cloud_notm}} VSI (Virtual Server Instance) unter Verwendung von {{site.data.keyword.cloud_notm}} Endurance-Speicher außerhalb des VMware-Clusters bereitgestellt. Diese Software dient dazu, Sicherungskopien für die Managementkomponenten in dieser Lösung zu erstellen.

### NSX-Sicherung

Eine ordnungsgemäße Sicherung aller NSX-Komponenten ist von entscheidender Bedeutung, um den Betriebszustand eines Systems wiederherzustellen, wenn ein Fehler aufgetreten ist. Es reicht nicht aus, die NSX-VMs zu sichern. Für eine ordnungsgemäße Sicherung muss die NSX-Sicherungsfunktion innerhalb von NSX Manager verwendet werden. Dazu ist es erforderlich, dass ein FTP- oder SFTP-Server für das Repository der NSX-Sicherungsdaten angegeben wird.
Die NSX-Manager-Sicherung umfasst die gesamte NSX-Konfiguration, einschließlich Controller, logischer Switching- und Routing-Entitäten, Sicherheitsfunktionen, Firewallregeln und aller anderen Komponenten, die Sie in der NSX Manager-UI oder -API konfigurieren. Die vCenter-Datenbank und die zugehörigen Elemente wie die virtuellen Switches müssen separat gesichert werden. Das Sichern der NSX-Konfiguration sollte zusammen mit einer vCenter-Sicherung vorgenommen werden.

###	Sicherung und Disaster-Recovery für IBM Cloud Private

Sicherungen für eine ICP-Bereitstellung sind von entscheidender Bedeutung, um den Betriebszustand eines Systems wiederherzustellen, wenn ein Fehler aufgetreten ist. Bei der traditionellen VM-Sicherung können Probleme auftreten. Auf jedem ICP-Masterknoten wird 'etcd' ausgeführt und die Dokumentation zu 'etcd' weist deutlich darauf hin, dass keine traditionelle VM-Sicherung zur Wiederherstellung verwendet werden soll.

Mit {{site.data.keyword.cloud_notm}} Private auf Plattformebene müssen Sie die folgenden Komponenten sichern:

-	**Etcd** - wird zum Speichern von Kubernetes-Ressourcen sowie von Calico-Statusinformationen verwendet.
-	**Docker-Registry** - private Image-Registry, die zum Speichern von Container-Image-Dateien in einem Image-Repository verwendet wird.
-	**MongoDB** - Datenbank, die von Messservice, Helm-Repository-Server, Helm-API-Server, LDAP-Konfiguration, Tenant (Namespace) und Rollenkonfigurationen (Team/Benutzer/Benutzergruppe) verwendet wird.
-	**MariaDB** - Datenbank, die von OIDC verwendet wird.
-	**Elasticsearch** - speichert die System- und Anwendungsprotokolle.
-	**Prometheus** - speichert Daten für die Überwachung.
-	**Persistenter Speicher** - wird für Management-Services verwendet, die den persistenten Datenträger und den Speicheranbieter von ICP oder Kubernetes nutzen. Sie können die Technologie für Sicherung und Wiederherstellung verwenden, die vom Speicheranbieter zur Verfügung gestellt wird. Ein ähnlicher Prozess kann auch auf die Benutzeranwendung erweitert werden.

###	Sicherung und Disaster-Recovery für CAM
Sicherungen für eine CAM-Bereitstellung sind von entscheidender Bedeutung, um den Betriebszustand eines Systems wiederherzustellen, wenn ein Fehler aufgetreten ist. Für die CAM-Sicherung ist es erforderlich, dass der Kunde die folgenden Komponenten sichert:
-	**Mongo Database** – Wichtigste Datenbank von CAM.
-	**Maria Database** - Wird von CAM Blueprint Designer verwendet.
-	**NFS/GlusterFS** - CAM-Daten befinden sich auf vier persistenten Datenträgern.

### Sicherung und Disaster-Recovery für IKS
Sicherungen der etcd-Datenbank werden dem Kunden als Teil des verwalteten Service zur Verfügung gestellt. Alle Anwendungsdaten müssen von Ihnen selbst gesichert werden.

## Skalierbarkeit

### VCS-Skalierbarkeit

Nach der Erstbereitstellung der Hosts hat der Benutzer die Möglichkeit, die Rechenkapazität aus dem {{site.data.keyword.cloud_notm}} for VMware-Portal heraus zu skalieren.

Für dieses Skalieren der Umgebung gibt es die folgenden Möglichkeiten:
- Hinzufügen neuer Standorte, die von separaten vCenter-Servern verwaltet werden
- Hinzufügen neuer Cluster
- Hinzufügen neuer Hosts zu einem vorhandenen Cluster

####	Bereitstellungen mit mehreren Standorten
VMware on {{site.data.keyword.cloud_notm}} kann dank der weltweiten Verfügbarkeit von IBM Cloud-Rechenzentren und des integrierten Netzbackbones die Bereitstellung und Funktion verschiedener Anwendungsfälle in unterschiedlichsten Regionen unterstützen, und dies zu einem Bruchteil des Zeitaufwands, der ansonsten für den Neuaufbau einer solchen Infrastruktur erforderlich wäre.

####	Skalierung mit neuem Cluster
Der Benutzer kann die Rechenkapazität auch dadurch skalieren, dass er einen neuen Cluster über die Konsole erstellt und Hosts bestellt; die neuen Hosts werden dem neuen Cluster dann automatisch hinzugefügt. Diese Option erstellt einen separaten Cluster in der Umgebung und gibt Benutzern die Möglichkeit, Management-Workloads physisch und logisch von Anwendungsworkloads zu trennen, Workloads basierend auf anderen Merkmalen (z. B. Microsoft SQL-Datenbankcluster) zu trennen und Anwendungen in hochverfügbaren Topologien bereitzustellen.

####	Skalierung vorhandener Cluster
Der Benutzer kann einen vorhandenen Cluster skalieren, indem er Hosts von der Konsole aus bestellt; die neuen Hosts werden dann automatisch zum Cluster hinzugefügt. Die Benutzer müssen die Reservierungsrichtlinie für Hochverfügbarkeit (HA) möglicherweise für den Cluster entsprechend den Reservierungsanforderungen anpassen.

### ICP-Skalierbarkeit
Abhängig von den verfügbaren Rechenkapazitäten an den lokalen oder Cloudstandorten hat der Benutzer die Möglichkeit, die Knotenarchitektur von dem zuerst bereitgestellten Bootknoten aus zu skalieren.

Für diese Skalierung der Umgebung gibt es die folgenden Möglichkeiten:
- Erweiterung der ICP-Workerknoten
- Erweiterung und Nutzung des IKS-Angebots

####	ICP-Erweiterung
Die ICP-Worker-VM-Knoten werden skaliert, um die Rechenressourcen/Anwendung zu erweitern:
  - Der Kunde richtet eine neue virtuelle Maschine in demselben VXLAN ein, in dem ICP bereitgestellt wurde.
  - Die Kunden können Workerknoten skalieren, indem sie neue virtuelle Maschinen einrichten, sich dann am Bootknoten anmelden und einen Befehl ausführen, um die neuen Knoten in den Cluster aufzunehmen.
  - CAM kann verwendet werden, um das Einrichten der VM und das Ausführen der Befehle für die Aufnahme in den ICP-Cluster zu automatisieren.


###  IKS-Erweiterung
Benutzer können eine IKS-Umgebung über das {{site.data.keyword.cloud_notm}}-Portal bereitstellen, um eine Containerumgebung zu erweitern bzw. zu nutzen.

Anwendungsbereitstellungen in IKS können über folgende Schritte ausgeführt werden:
- IKS-Verbindung/-Services werden in CAM entwickelt und im ICP-Katalog veröffentlicht.
- Zukünftige Erweiterung des Multi-cloud Manager für das Management von IKS-Instanzen.
- Helm-Befehlszeile.
- Verwenden von Clustern mit mehreren Zonen, um die Verfügbarkeit zu erhöhen.

### Zugehörige Links
* [Clusterknoten hinzufügen oder entfernen](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_2.1.0.3/installing/modify_cluster.html)
* [Workerknoten durch das Anpassen der Größe eines vorhandenen Workerpools](../../../../containers/cs_clusters.html#resize_pool)
* [Vorgehensweise zum Sichern und Wiederherstellen von {{site.data.keyword.cloud_notm}} Private](https://medium.com/ibm-cloud/how-to-backup-and-restore-ibm-cloud-private-part-1-b6300dc1d7d8)
* [ICP Backup GitHub](https://github.com/ibm-cloud-architecture/icp-backup/)
* [Übersicht über VCS Hybridity Bundle](../vcs/vcs-hybridity-intro.html)
