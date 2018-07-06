---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-22"

---

# Überblick zu IBM Spectrum Protect Plus on IBM Cloud

Der Service "IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud}}" bietet eine effiziente und skalierbare Datensicherungs-, Datenwiederverwendungs- und Datenwiederherstellungslösung für virtuelle Umgebungen. Er kann als eigenständige Lösung implementiert oder in Ihre IBM Spectrum Protect Plus-Umgebung integriert werden, um Kopien für die Langzeitspeicherung und Datengovernance auszulagern.

**Verfügbarkeit:** Dieser Service ist nur für Instanzen verfügbar, auf denen vSphere 6.5 ausgeführt wird und die in V2.2 oder höheren Releases bereitgestellt werden oder für die ein Upgrade auf diese Releases durchgeführt wurde.

**Hinweise:**
* Wenn Sie den Service für Instanzen installieren, die in V2.4 oder einem höheren Release bereitgestellt werden, dann wird IBM Spectrum Protect Plus V10.1.1 Patch 1 installiert. Der Service stellt automatisch Wiederherstellungsunterstützung für Management-VMs bereit.
* Wenn Sie den Service für Instanzen installieren, die in V2.3 bereitgestellt werden, dann wird IBM Spectrum Protect Plus V10.1.1 installiert. Der Service unterstützt die automatische Sicherung von Management-VMs.
* Wenn Sie den Service für Instanzen installieren, die in V2.2 bereitgestellt werden, dann wird IBM Spectrum Protect Plus V10.1.0 installiert. Der Service bietet nur für die Workload-VMs Datenschutz.


## Komponenten von IBM Spectrum Protect Plus on IBM Cloud

Mit dem Service "IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}" werden die folgenden Komponenten bestellt und einbezogen:

### vCenter-Ressourcen

* Eine einzelne virtuelle Maschine (VM) für die Ausführung des IBM Spectrum Protect Plus-Servers
* 4 Kerne mit 2,0 GHz
* 32 GB RAM
* 370 GB Plattenspeicher

### Speicher für Sicherungen

Anpassbarer Speicher für Sicherungen mit den folgenden Optionen:
* File Storage-Anzahl: 1, 2, 3 oder 4
* Jede Endurance File Storage-Instanz: 500, 1000, 2000, 4000, 8000 oder 12000 GB
* Speicherleistung: 0,25, 2 oder 4 E/A-Operationen pro Sekunde und GB

### Speicher für Management

Eine Endurance File Storage-Instanz (500 GB, 2 E/A-Operationen pro Sekunde und GB) als Host für die virtuelle Maschine von IBM Spectrum Protect Plus mit Ausführung in demselben Teilnetz wie der für den Service bestellte Sicherungsspeicher.

### Netzbetrieb

Eine portierbare private IP-Adresse.

### Lizenzen und Gebühren

IBM Spectrum Protect Plus kann in der {{site.data.keyword.vmwaresolutions_short}}-Konsole für 10 bis maximal 1000 virtuelle Maschinen in Zehnerschritten lizenziert werden. Sie können auch Ihre eigene Lizenz verwenden (Bring Your Own License: BYOL) und die Lizenzdatei während des Installationsprozesses hochladen.

## Hinweise zur Installation von IBM Spectrum Protect Plus on IBM Cloud

Lesen Sie die folgenden Hinweise, bevor Sie den Service "IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}" installieren.

* Stellen Sie sicher, dass die CPU und der Speicher im Standardcluster Ihrer Instanz für die virtuelle Maschine von IBM Spectrum Protect Plus ausreichen.
* Stellen Sie sicher, dass die NFS-Mounts, die auf den ESXi-Servern verfügbar sind, auf der Basis der Version der ESXi-Server ausreichend sind.

  Cloud Foundation-Instanzen und vCenter Server-Instanzen, die in V2.2 oder höheren Releases bereitgestellt werden (oder für die ein entsprechendes Upgrade durchgeführt wurde), verfügen über eine Einstellung für den Parameter `NFS.MaxVolumes` in VMware. Dieser Parameter definiert die maximale Anzahl der NFS-Mounts auf einem ESXi-Server und kann je nach Version des ESXi-Servers auf maximal 256 gesetzt werden. Weitere Informationen finden Sie unter [Increasing the default value that defines the maximum number of NFS mounts on an ESXi/ESX host](https://kb.vmware.com/s/article/2239).

  Der Service "IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}" kann bis zu fünf der NFS-Datenträger auf jedem ESXi-Server im Standardcluster Ihrer Instanz belegen. Darüber hinaus erstellt der Service transiente NFS-Mounts für Sicherungs- und Wiederherstellungszwecke. Daher müssen Sie die Anzahl der NFS-Mounts auf mindestens 64 setzen, um sicherzustellen, dass der Service installiert und erfolgreich ausgeführt werden kann.

## Hinweise zum Entfernen von IBM Spectrum Protect Plus on IBM Cloud

Lesen Sie die folgenden Hinweise, bevor Sie den Service "IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}" entfernen:
* Stellen Sie sicher, dass alle Sicherungsjobkonfigurationen entfernt wurden und dass keine Sicherungs- oder Wiederherstellungsoperationen aktiv sind.
* Wenn Sie den Service entfernen, wird der Speicher für das Sicherungsrepository aus der virtuellen Maschine von IBM Spectrum Protect Plus entfernt und die Speicherbestellung wird storniert, wodurch die Sicherungsrepositorydaten permanent gelöscht werden.
* Wenn Sie den Service entfernen, wird der für den Service bestellte Sicherungsspeicher ebenfalls entfernt. Daher wird der Zugriff auf alle Sicherungen während des Entfernen des Service unmöglich.

## Zugehörige Links

* [IBM Spectrum Protect Plus on IBM Cloud Preventive Service Planning](http://www.ibm.com/support/docview.wss?uid=swg22012650)
* [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} verwalten](managingspp.html)
* [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} bestellen](spp_ordering.html)
* [IBM Spectrum Protect Plus documentation](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html)
* [Kontaktaufnahme mit dem IBM Support](../vmonic/trbl_support.html)
