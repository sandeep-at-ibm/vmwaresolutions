---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

# Sicherung, Disaster-Recovery und Skalierbarkeit
{: #vcsicp-detail-design-resiliency}

## Sicherung und Disaster-Recovery
{: #vcsicp-detail-design-resiliency-backup-dr}

### Sicherung von VMware vCenter Server on IBM Cloud
{: #vcsicp-detail-design-resiliency-vcs-backup}

Als Teil von {{site.data.keyword.vmwaresolutions_full}} wird die Veeam-Sicherungssoftware optional auf einer {{site.data.keyword.cloud_notm}} VSI (Virtual Server Instance) bereitgestellt, die {{site.data.keyword.cloud_notm}} Endurance-Speicher außerhalb des VMware-Clusters verwendet. Diese Software dient dazu, Sicherungskopien für die Managementkomponenten in dieser Lösung zu erstellen.

### NSX-Sicherung
{: #vcsicp-detail-design-resiliency-nsx-backup}

Eine ordnungsgemäße Sicherung aller NSX-Komponenten ist von entscheidender Bedeutung, um den Betriebszustand eines Systems wiederherzustellen, wenn ein Fehler aufgetreten ist. Eine Sicherung allein der virtuellen NSX-Maschinen ist nicht ausreichend. Für eine ordnungsgemäße Sicherung muss stattdessen die NSX-Sicherungsfunktion innerhalb von NSX Manager verwendet werden. Hierzu muss ein FTP- oder SFTP-Server für das Repository der NSX-Sicherungsdaten angegeben sein.
Die NSX-Manager-Sicherung umfasst die gesamte NSX-Konfiguration, einschließlich Controller, logischer Switching- und Routing-Entitäten, Sicherheitsfunktionen, Firewallregeln und aller anderen Komponenten, die Sie in der Benutzerschnittstelle oder der API von NSX Manager konfigurieren. Die vCenter-Datenbank und die zugehörigen Elemente wie die virtuellen Switches müssen separat gesichert werden. Das Sichern der NSX-Konfiguration muss zusammen mit einer vCenter-Sicherung vorgenommen werden.

### Sicherung und Disaster-Recovery für IBM Cloud Private
{: #vcsicp-detail-design-resiliency-backup-dr-icp}

Sicherungen für eine {{site.data.keyword.icpfull_notm}}-Bereitstellung sind von entscheidender Bedeutung, um den Betriebszustand eines Systems wiederherzustellen, wenn ein Fehler aufgetreten ist. Neben einer traditionellen VM-Sicherung wird auf jedem {{site.data.keyword.icpfull_notm}}-Masterknoten "etcd" ausgeführt. Die Dokumentation zu "etcd" weist deutlich darauf hin, dass keine traditionelle VM-Sicherung zur Wiederherstellung verwendet werden soll.

Für {{site.data.keyword.icpfull_notm}} müssen Sie auf Plattformebene die folgenden Komponenten sichern:
- **Etcd** - Wird zum Speichern von Kubernetes-Ressourcen und von Calico-Statusinformationen verwendet.
- **Docker-Registry** - Private Image-Registry, die zum Speichern von Container-Image-Dateien in einem Image-Repository verwendet wird.
- **MongoDB** - Datenbank, die von Messservice, Helm-Repository-Server, Helm-API-Server, LDAP-Konfiguration, Tenant (Namespace) und Rollenkonfigurationen (Team/Benutzer/Benutzergruppe) verwendet wird.
- **MariaDB** - Datenbank, die von OIDC verwendet wird.
- **Elasticsearch** - Speichert die System- und Anwendungsprotokolle.
- **Prometheus** - Speichert Daten für die Überwachung.
- **Persistenter Speicher** - Wird für Management-Services verwendet, die den persistenten Datenträger und den Speicheranbieter von {{site.data.keyword.icpfull_notm}} oder Kubernetes verwenden. Sie können die Technologie für Sicherung und Wiederherstellung verwenden, die vom Speicheranbieter zur Verfügung gestellt wird. Ein ähnlicher Prozess kann auch auf die Benutzeranwendung erweitert werden.

### Sicherung und Disaster-Recovery für CAM
{: #vcsicp-detail-design-resiliency-backup-dr-cam}

Sicherungen für eine CAM-Bereitstellung sind von entscheidender Bedeutung, um den Betriebszustand eines Systems wiederherzustellen, wenn ein Fehler aufgetreten ist. Für die CAM-Sicherung ist es erforderlich, dass der Kunde die folgenden Komponenten sichert:
- Die **Mongo-Datenbank** ist die zentrale CAM-Datenbank.
- Die **Maria-Datenbank** wird von CAM Blueprint Designer verwendet.
- Unter **NFS/GlusterFS** befinden sich die CAM-Daten in vier persistenten Datenträgern.

### Sicherung und Disaster-Recovery für IBM Cloud Kubernetes-Service
{: #vcsicp-detail-design-resiliency-backup-dr-iks}

Sicherungen der etcd-Datenbank werden dem Kunden als Teil des verwalteten Service zur Verfügung gestellt. Alle Anwendungsdaten müssen von Ihnen selbst gesichert werden.

## Skalierbarkeit
{: #vcsicp-detail-design-resiliency-scalability}

### VCS-Skalierbarkeit
{: #vcsicp-detail-design-resiliency-vcs-scalability}

Nach der Erstbereitstellung der Hosts kann der Benutzer die Rechenkapazität aus dem {{site.data.keyword.cloud_notm}} for VMware-Portal heraus skalieren.

Für dieses Skalieren der Umgebung gibt es die folgenden Möglichkeiten:
- Hinzufügen neuer Standorte, die von separaten vCenter-Servern verwaltet werden
- Hinzufügen neuer Cluster
- Hinzufügen neuer Hosts zu einem vorhandenen Cluster

#### Bereitstellungen mit mehreren Standorten
{: #vcsicp-detail-design-resiliency-multi-site}

VMware on {{site.data.keyword.cloud_notm}} kann dank der weltweiten Verfügbarkeit von IBM Cloud-Rechenzentren und des integrierten Netzbackbones die Bereitstellung und Funktion verschiedener Anwendungsfälle in unterschiedlichsten Regionen unterstützen, und dies zu einem Bruchteil des Zeitaufwands, der ansonsten für den Neuaufbau einer solchen Infrastruktur erforderlich wäre.

#### Skalierung mit neuem Cluster
{: #vcsicp-detail-design-resiliency-scale-out-new}

Der Benutzer kann die Rechenkapazität auch dadurch skalieren, dass er einen neuen Cluster über die Konsole erstellt und Hosts bestellt; die neuen Hosts werden dem neuen Cluster dann automatisch hinzugefügt. Diese Option erstellt einen separaten Cluster in der Umgebung und gibt Benutzern die Möglichkeit, Management-Workloads physisch und logisch von Anwendungsworkloads zu trennen, Workloads basierend auf anderen Merkmalen (z. B. Microsoft SQL-Datenbankcluster) zu trennen und Anwendungen in hochverfügbaren Topologien bereitzustellen.

#### Skalierung vorhandener Cluster
{: #vcsicp-detail-design-resiliency-scale-out-existing}

Der Benutzer kann einen vorhandenen Cluster skalieren, indem er Hosts von der Konsole aus bestellt; die neuen Hosts werden dann automatisch zum Cluster hinzugefügt. Die Benutzer müssen die Reservierungsrichtlinie für Hochverfügbarkeit (HA) möglicherweise für den Cluster entsprechend den Reservierungsanforderungen anpassen.

### Skalierbarkeit von IBM Cloud Private
{: #vcsicp-detail-design-resiliency-icp-scalability}

Abhängig von den verfügbaren Rechenkapazitäten an den lokalen oder Cloudstandorten kann der Benutzer die Knotenarchitektur von dem zuerst bereitgestellten Bootknoten aus skalieren.

Für diese Skalierung der Umgebung gibt es die folgenden Möglichkeiten:
- Erweitern Sie die {{site.data.keyword.icpfull_notm}}-Workerknoten.
- Erweitern und verwenden Sie das {{site.data.keyword.containerlong_notm}}-Angebot.

#### Erweiterung von IBM Cloud Private
{: #vcsicp-detail-design-resiliency-icp-expansion}

Die {{site.data.keyword.icpfull_notm}}-Worker-VM-Knoten werden skaliert, um die Rechenressourcen oder Anwendung zu erweitern:
- Der Kunde richtet eine neue VM in demselben VXLAN ein, in dem {{site.data.keyword.icpfull_notm}} bereitgestellt wurde.
- Die Kunden können Workerknoten skalieren, indem sie eine neue VM einrichten, sich dann am Bootknoten anmelden und einen Befehl ausführen, um die neuen Knoten in den Cluster aufzunehmen.
- CAM kann verwendet werden, um das Einrichten der VM und das Ausführen der Befehle für die Aufnahme in den {{site.data.keyword.icpfull_notm}}-Cluster zu automatisieren.

###  Erweiterung für IBM Cloud Kubernetes-Service
{: #vcsicp-detail-design-resiliency-iks-expansion}

Benutzer können eine {{site.data.keyword.containerlong_notm}}-Umgebung über das {{site.data.keyword.cloud_notm}}-Portal bereitstellen, um eine Containerumgebung zu erweitern oder zu nutzen.

Verwenden Sie den folgenden Ordner für Anwendungsimplementierungen in {{site.data.keyword.containerlong_notm}}:
- {{site.data.keyword.containerlong_notm}}-Verbindungen oder -Services werden in CAM entwickelt und im {{site.data.keyword.icpfull_notm}}-Katalog veröffentlicht.
- Zukünftige Erweiterung des Multi-Cloud-Managers für das Management von {{site.data.keyword.containerlong_notm}}-Instanzen.
- Helm-Befehlszeilenschnittstelle.
- Verwenden von Clustern mit mehreren Zonen, um die Verfügbarkeit zu erhöhen.

## Zugehörige Links
{: #vcsicp-detail-design-resiliency-related}

* [Clusterknoten hinzufügen oder entfernen](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_2.1.0.3/installing/modify_cluster.html)
* [Workerknoten durch das Anpassen der Größe eines vorhandenen Workerpools](/docs/containers?topic=containers-clusters)
* [Vorgehensweise zum Sichern und Wiederherstellen von {{site.data.keyword.cloud_notm}} Private](https://medium.com/ibm-cloud/how-to-backup-and-restore-ibm-cloud-private-part-1-b6300dc1d7d8)
* [{{site.data.keyword.icpfull_notm}}-Backup GitHub](https://github.com/ibm-cloud-architecture/icp-backup/)
* [Übersicht über vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
