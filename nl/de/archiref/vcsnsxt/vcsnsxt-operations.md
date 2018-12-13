---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-08"

---

# Betriebsaspekte

## Sicherung

### VCS-Sicherung

Als Teil von {{site.data.keyword.vmwaresolutions_full}} wird die Veeam-Sicherungssoftware optional auf einer {{site.data.keyword.cloud_notm}} VSI (Virtual Server Instance) bereitgestellt. Dies erfolgt unter Verwendung des {{site.data.keyword.cloud_notm}} Endurance-Speichers außerhalb des VMware-Clusters. Diese Software dient dazu, Sicherungskopien für die Managementkomponenten in der Lösung zu erstellen. Ausführliche Informationen zum Produktangebot enthält der Abschnitt [Übersicht über Veeam on {{site.data.keyword.cloud_notm}}](../../services/veeam_considerations.html).

Die Sicherung aller NSX-Komponenten ist von entscheidender Bedeutung, um den Betriebszustand eines Systems wiederherzustellen, wenn ein Fehler aufgetreten ist. Es reicht nicht aus, die virtuellen NSX-Appliances zu sichern. Für eine wirksame Sicherung muss die NSX-Sicherungsfunktion innerhalb des NSX-Managers verwendet werden. Für diese Operation ist es erforderlich, dass ein FTP- oder SFTP-Server für das Repository der NSX-Sicherungsdaten angegeben ist.

Die NSX-Manager-Sicherung umfasst die gesamte NSX-Konfiguration, einschließlich Controller, logischer Switching- und Routing-Entitäten, Sicherheitsfunktionen, Firewallregeln und aller anderen Komponenten, die Sie in der Benutzerschnittstelle oder API des NSX-Managers konfigurieren. Die vCenter-Datenbank und die zugehörigen Elemente wie die virtuellen Switches müssen separat gesichert werden. Ausführliche Informationen finden Sie unter [Dateibasierte NSX-Sicherung](../solution/solution_backingup.html#nsx-file-based-backup). Das Sichern der NSX-Konfiguration sollte zusammen mit einer [dateibasierten vCenter-Sicherung](../solution/solution_backingup.html#vcenter-file-based-backup) vorgenommen werden.

### Sicherung und Disaster-Recovery für IBM Cloud Private

Sicherungen für eine ICP-Bereitstellung sind von entscheidender Bedeutung, um den Betriebszustand eines Systems wiederherzustellen, wenn ein Fehler aufgetreten ist. Bei der traditionellen VM-Sicherung können Probleme auftreten: Auf jedem ICP-Masterknoten wird ein Service *etcd* ausgeführt und die Dokumentation zu *etcd* weist deutlich darauf hin, dass keine traditionelle VM-Sicherung zur Wiederherstellung verwendet werden soll.

Für {{site.data.keyword.cloud_notm}} Private müssen Sie auf Plattformebene die folgenden Komponenten sichern.
- **etcd** - Wird zum Speichern von Kubernetes-Ressourcen und von Calico-Statusinformationen verwendet.
- **Docker-Registry** - Private Image-Registry, die zum Speichern von Container-Image-Dateien in einem Image-Repository verwendet wird.
- **MongoDB** - Datenbank, die von Messservice, Helm-Repository-Server, Helm-API-Server, LDAP-Konfiguration, Tenant (Namespace) und Rollenkonfigurationen (Team/Benutzer/Benutzergruppe) verwendet wird.
- **MariaDB** - Datenbank, die von OIDC verwendet wird.
-	**Elasticsearch** - Speichert die System- und Anwendungsprotokolle.
-	**Prometheus** - Speichert Daten für die Überwachung.
-	**Persistenter Speicher** - Wird für Management-Services verwendet, die den persistenten Datenträger und den Speicheranbieter von {{site.data.keyword.cloud_notm}} Private oder Kubernetes nutzen.

Sie können die Technologie für Sicherung und Wiederherstellung verwenden, die vom Speicheranbieter zur Verfügung gestellt wird. Ein ähnlicher Prozess kann auch auf die Benutzeranwendung erweitert werden. Weitere Informationen finden Sie im Blogbeitrag [How to back up and restore {{site.data.keyword.cloud_notm}} Private](https://medium.com/ibm-cloud/how-to-backup-and-restore-ibm-cloud-private-part-1-b6300dc1d7d8) oder auf der GitHub-Seite [icp-backup](https://github.com/ibm-cloud-architecture/icp-backup/).

### Sicherung und Disaster-Recovery für CAM

Sicherungen für eine CAM-Bereitstellung sind von entscheidender Bedeutung, um den Betriebszustand eines Systems wiederherzustellen, wenn ein Fehler aufgetreten ist. Für die CAM-Sicherung ist es erforderlich, dass der Kunde die folgenden Komponenten sichert:
-	**Mongo Database** - Hauptdatenbank von CAM.
-	**Maria Database** - Wird von CAM Blueprint Designer verwendet.
-	**NFS/GlusterFS** - CAM-Daten befinden sich auf vier persistenten Datenträgern.

### Sicherung und Disaster-Recovery für IKS

Eine Sicherung der etcd-Datenbank wird dem Kunden als Teil des verwalteten Service zur Verfügung gestellt. Für die Sicherung aller Anwendungsdaten ist der Kunde selbst zuständig.

## Skalierbarkeit

### VCS-Skalierbarkeit

Nach der Erstbereitstellung der Hosts können Benutzer die Rechenkapazität aus dem {{site.data.keyword.cloud_notm}} for VMware-Portal heraus skalieren.

Für dieses Skalieren der Umgebung gibt es die folgenden Möglichkeiten:
-	Hinzufügen neuer Standorte, die von separaten vCenter-Servern verwaltet werden
-	Hinzufügen neuer Cluster
-	Hinzufügen neuer Hosts zu einem vorhandenen Cluster

#### Bereitstellungen an mehreren Standorten

VMware on {{site.data.keyword.cloud_notm}} kann dank der weltweiten Verfügbarkeit von {{site.data.keyword.cloud_notm}}-Rechenzentren und des integrierten Netzbackbones die Bereitstellung und Funktion verschiedener Anwendungsfälle in unterschiedlichsten Regionen unterstützen, und dies zu einem Bruchteil des Zeitaufwands, der ansonsten für den Neuaufbau einer solchen Infrastruktur erforderlich wäre. Weitere Informationen enthält der Abschnitt [Konfiguration mit mehreren Standorten für vCenter Server on {{site.data.keyword.cloud_notm}}-Instanzen](../../vcenter/vc_multisite.html).

#### Skalierung mit neuem Cluster

Benutzer können die Rechenkapazität auch dadurch skalieren, dass sie durch die Bestellung der Hosts einen neuen Cluster in der Konsole erstellen; die neuen Hosts werden dann automatisch zum neuen Cluster hinzugefügt. Diese Option erstellt einen separaten Cluster in der Umgebung und gibt Benutzern die Möglichkeit, Management-Workloads physisch und logisch von Anwendungsworkloads zu trennen, Workloads basierend auf anderen Merkmalen (z. B. Microsoft SQL-Datenbankcluster) zu trennen und Anwendungen in hochverfügbaren Topologien bereitzustellen. Weitere Informationen finden Sie unter [vCenter Server-Instanzen bestellen](../../vcenter/vc_orderinginstance.html).

#### Skalierung vorhandener Cluster

Der Benutzer kann einen vorhandenen Cluster skalieren, indem er Hosts von der Konsole aus bestellt; die neuen Hosts werden dann automatisch zum Cluster hinzugefügt. Weitere Informationen finden Sie unter [Kapazität für vCenter Server-Instanzen erweitern und verringern](../../vcenter/vc_addingremovingservers.html). Möglicherweise müssen Sie die Reservierungsrichtlinie für Hochverfügbarkeit (HA) für den Cluster entsprechend den Reservierungsanforderungen anpassen.

### ICP- und IKS-Skalierbarkeit

Abhängig von den verfügbaren Rechenkapazitäten an den lokalen oder Cloudstandorten können Benutzer die Knotenarchitektur von dem zuerst bereitgestellten Bootknoten aus skalieren. Für diese Skalierung der Umgebung gibt es die folgenden Möglichkeiten:
-	Erweiterung der ICP-Workerknoten
-	Erweiterung und Nutzung des IKS-Angebots

#### ICP-Erweiterung

Die ICP-Worker-VM-Knoten werden skaliert, um die Rechenressourcen und Anwendung zu erweitern:
- Der Kunde richtet eine neue virtuelle Maschine in demselben VXLAN ein, in dem ICP bereitgestellt wurde.
- Die Kunden können Workerknoten skalieren, indem sie neue virtuelle Maschinen einrichten, sich dann am Bootknoten anmelden und einen Befehl ausführen, um die neuen Knoten in den Cluster aufzunehmen. Ausführliche Informationen finden Sie unter [Clusterknoten hinzufügen oder entfernen](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_2.1.0.3/installing/modify_cluster.html).
- CAM kann verwendet werden, um das Einrichten der VM und das Ausführen der Befehle für ihre Aufnahme in den ICP-Cluster zu automatisieren.

#### IKS-Erweiterung

Benutzer können eine IKS-Umgebung über das {{site.data.keyword.cloud_notm}}-Portal bereitstellen, um eine Containerumgebung zu erweitern und zu nutzen. Weitere Informationen enthält der Blogbeitrag [Hybrid enhancements across {{site.data.keyword.cloud_notm}} Private and {{site.data.keyword.cloud_notm}}](https://www.ibm.com/developerworks/community/blogs/5092bd93-e659-4f89-8de2-a7ac980487f0/entry/Hybrid_Enhancements_Across_IBM_Cloud_Private_and_IBM_Public_Cloud?lang=en_us).

Anwendungsbereitstellungen in IKS sind mit den folgenden Verfahren möglich:
-	IKS-Verbindungen und -Services werden in CAM entwickelt und im ICP-Katalog veröffentlicht.
-	Multi Cloud Manager, eine zukünftige Erweiterung für das Management von IKS-Instanzen.
-	Helm-Befehlszeile.

### Zugehörige Links

* [Übersicht über VCS Hybridity Bundle](../vcs/vcs-hybridity-intro.html)
