---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Stock Trader unter WebSphere Application Server in Stock Trader in Containern umwandeln

Der nächste Schritt im Modernisierungsprozess für Stock Trader ist die Umwandlung der Workloadausführung in virtuellen Maschinen (VMs) in eine Ausführung in Containern.

Zur Fortsetzung des Prozesses führen Todd und Jane Transformation Advisor aus, um die Workload von Stock Trader zu analysieren, gegebenenfalls komplexe Aspekte der Migration zu ermitteln und Änderungen zu empfehlen. Nachdem alles vorbereitet ist, stellen sie Stock Trader mithilfe von Transformation Advisor in Liberty-Containern bereit, die unter {{site.data.keyword.icpfull_notm}} ausgeführt werden.

## IBM Cloud Private vorbereiten

Todd muss zunächst {{site.data.keyword.icpfull_notm}} installieren. Da Todd über eine VMware on {{site.data.keyword.cloud_notm}}-Umgebung verfügt, beschließt er, das Produktangebot "{{site.data.keyword.cloud_notm}} Private Hosted" zu nutzen, das ihm eine vollständige {{site.data.keyword.icpfull_notm}}-Instanz zur Verfügung stellt, die auf virtuellen VMware-Maschinen in {{site.data.keyword.cloud_notm}} ausgeführt wird.

Das Standarddashboard bietet eine umfassende Benutzerschnittstelle für die Verwaltung des Kubernetes-Clusters, der Sicherheit, des Speichers und der Bereitstellung aus dem Katalog.

### Speicher vorbereiten

{{site.data.keyword.cloud_notm}} Private Hosted ist im Bereitstellungszustand mit GlusterFS konfiguriert und stellt Dateispeicher in virtuellen Maschinen als dedizierte GlusterFS-Knoten zur Verfügung. Besonders wertvoll an GlusterFS ist die Möglichkeit der dynamischen Bereitstellung. Todd kann auf Wunsch zusätzliche virtuelle Maschinen als NFS-Server einrichten.

Da Todd einen NFS-Server zur Verfügung haben möchte, hat er eine virtuelle Maschine namens "toddnfs" angegeben und die [hier](https://help.ubuntu.com/community/SettingUpNFSHowTo) beschriebenen Schritte ausgeführt.

Todd führt die folgenden Befehle aus, um einen neuen NFS-Server zu erstellen:

`ssh root@toodnfs.acme.com`

`apt-get install nfs-kernel-server`

`mkdir -p /shared`

`chown nobody:nogroup /shared`

`vi /etc/exports`

Anschließend fügt Todd die folgende Zeile hinzu:

`/shared \*(rw,no_subtree_check,async,insecure,no_root_squash)`

`systemctl restart nfs-kernel-server`

Danach führt Todd den folgenden Befehl auf jeder virtuellen Maschine aus, um NFS in jeder Worker-VM für {{site.data.keyword.icpfull_notm}} zu installieren:

`sudo apt-get update`

`sudo apt-get install nfs-common`

Todd führt anschließend den folgenden Befehl aus, um die installierte Version zu prüfen:

`apt-cache policy nfs-common`

Jedes Mal, wenn ein neuer NFS-Datenträger benötigt wird, führt Todd den folgenden Befehl aus, um bei Bedarf einen neuen NFS-Datenträger zu erstellen:

`cd /shared`

`mkdir -p <foldername>`

`chmod 777 <foldername>`

### Imagesicherheit vorbereiten

In {{site.data.keyword.icpfull_notm}} V3.1 wird die Sicherheit dadurch erweitert, dass eine Imagerichtlinie erstellt worden sein muss, bevor ein Image mit einer Pull-Operation in eine {{site.data.keyword.icpfull_notm}}-Instanz extrahiert werden kann. Die Erweiterung setzt voraus, dass Sie eine Imagerichtlinie für die Position der IBM Images (*dockerhub/ibmcom*) und im Docker-Speicher hinzufügen.

Die Richtlinie "ibmcloud-default-cluster-image-policy" wird standardmäßig bereitgestellt und deckt alle IBM Images unter "docker.io/ibmcom/\*" ab. Da sich Db2 und anderer IBM Inhalt im Docker-Speicher befinden, ist jedoch eine weitere Imagerichtlinie für den Docker-Speicher *docker.io/store/ibmcorp/* erforderlich.

Für bestimmte Inhalte ist zusätzlich ein Podsicherheitsrichtliniensatz erforderlich, der einen bestimmten Zugriff für den Pod ermöglicht. Beispielsweise macht Db2 eine Richtlinie für Clients erforderlich, die Db2 in einem anderen Namensbereich als "default" ausführen wollen.

Weitere Informationen finden Sie im [IBM Knowledge Center](https://www.ibm.com/support/knowledgecenter/SSBS6K_3.1.0/manage_cluster/enable_pod_security.html).

## Transformation Advisor und Microclimate bereitstellen

Nachdem Todd {{site.data.keyword.icpfull_notm}} in Betrieb genommen hat, installiert er Transformation Advisor zusammen mit Microclimate. Todd öffnet den [Katalog](https://www.ibm.com/cloud/private/developer) und zeigt den gesamten verfügbaren Inhalt an.

Todd sucht nach Transformation Advisor und Microclimate und installiert beides anhand der in der Readme-Datei bereitstehenden Anweisungen, wenn er auf das Helm-Diagramm klickt.

### Transformation Advisor ausführen

Zur Ausführung von Transformation Advisor hat Jane den Datenkollektor in der VM hinzugefügt, in der Stock Trader in WebSphere ausgeführt wird. Sie öffnet die Benutzerschnittstelle von [Transformation Advisor](https://developer.ibm.com/recipes/tutorials/using-the-transformation-advisor-on-ibm-cloud-private/), um die Ergebnisse anzuzeigen.

Jane hat auf Stock Trader geklickt; daraufhin wird für sie die Empfehlung angezeigt, jede WAR-Datei in Liberty auszuführen. Außerdem wird sie darüber informiert, dass ein Großteil der Migration einfach durchzuführen ist und nur eine einzige moderate Migration erforderlich sein wird. Nachdem Jane auf "Migrationsdetails" geklickt hat, werden die von Transformation Advisor zur Verfügung gestellten Bereitstellungsdateien angezeigt, die Jane zur Durchführung der Migration verwenden kann. Jane lädt die Binärdateien in Transformation Advisor hoch, wo anschließend die von Microclimate zur Verfügung gestellten APIs für die Bereitstellung der Liberty-Container verwendet werden.

Am Ende resultieren hieraus die folgenden Layoutoptionen für Stock Trader:
* Einzelner Liberty-Container, falls Jane eine Liberty-Laufzeit bereitstellt und ihre Anwendung "Stock Trader" in diesem einzelnen Container hinzufügt.
* Mehrere Liberty-Container, in diesem Fall ein Container für jede WAR-Datei gemäß der Empfehlung von Transformation Advisor für Stock Trader.

Todd hat die Datenquelle während des Transformationsschritts nicht geändert. Transformation Advisor übernimmt die Datenquellenkonfiguration aus WebSphere Application Server Network Deployment und fügt sie zur Datei "server.xml" des Liberty-Containers hinzu.
{:important}

### Zugehörige Links

* [Übersicht über vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs/vcs-hybridity-intro.html)
