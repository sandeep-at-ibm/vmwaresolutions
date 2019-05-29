---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-06"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Übersicht über IBM Spectrum Protect Plus on IBM Cloud
{: #spp_considerations}

Der Service "{{site.data.keyword.IBM}} Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}" bietet eine effiziente und skalierbare Datensicherungs-, Datenwiederverwendungs- und Datenwiederherstellungslösung für virtuelle Umgebungen. Er kann als eigenständige Lösung implementiert oder in Ihre IBM Spectrum Protect-Umgebung integriert werden, um Kopien für die Langzeitspeicherung und Datengovernance auszulagern.

Dieser Service ist nur für Instanzen verfügbar, auf denen vSphere 6.5 ausgeführt wird und die in V2.2 (oder höher) bereitgestellt werden oder für die ein Upgrade auf diese Versionen durchgeführt wurde. Die aktuell installierte Version von {{site.data.keyword.IBM}} Spectrum Protect Plus ist V10.1.3.
{:note}

## Technische Spezifikationen für IBM Spectrum Protect Plus on IBM Cloud
{: #spp_considerations-specs}

Mit dem Service "IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}" werden die folgenden Komponenten bestellt und einbezogen:

### vCenter-Ressourcen
{: #spp_considerations-vcenter}

* Server-VM mit dem IBM Spectrum Protect Plus-Server
   * Betriebssystem Linux 3.10.0-693.11.1.el7.x86_64
   * 4 Kerne mit 2,0 GHz
   * 32 GB RAM
   * 370 GB Plattenspeicher
* Sekundäre VM mit vSnap-Server und VADP-Proxy für IBM Spectrum Protect Plus
   * Betriebssystem Linux 3.10.0-693.11.1.el7.x86_64
   * CPU und RAM in der ausgewählten Speichergröße und entsprechend der Dimensionierungsanleitung in [IBM Spectrum Protect Plus Blueprint](https://www.ibm.com/developerworks/community/wikis/home?lang=en#!/wiki/Tivoli%20Storage%20Manager/page/IBM%20Spectrum%20Protect%20Plus%20Blueprints) konfiguriert
   * 150 GB Plattenspeicher

### Speicher für Sicherungen
{: #spp_considerations-backup-storage}

Anpassbarer Speicher für Sicherungen mit den folgenden Optionen:
* Anzahl Dateispeicher: 1 - 10
* Jede Endurance File Storage-Instanz: 500, 1000, 2000, 4000, 8000 oder 12000 GB
* Speicherleistung: 0,25, 2 oder 4 E/A-Operationen pro Sekunde und GB

Informationen zur Planung und Dimensionierung finden Sie unter [IBM Spectrum Protect Plus Blueprint and Sizing Tool](https://www.ibm.com/developerworks/community/wikis/home?lang=en#!/wiki/Tivoli%20Storage%20Manager/page/IBM%20Spectrum%20Protect%20Plus%20Blueprints).

### Speicher für Management
{: #spp_considerations-mgmt-storage}

Ein Endurance-Dateispeicher (File Storage) mit 1000 GB, 2 IOPS/GB, der die virtuelle Maschine (VM) für IBM Spectrum Protect Plus hostet und im selben Teilnetz wie der Sicherungsspeicher aktiv ist.

### Vernetzung
{: #spp_considerations-network}

Zwei portierbare private IP-Adressen.

### Lizenzen und Gebühren
{: #spp_considerations-license}

* IBM Spectrum Protect Plus (10 bis zu maximal 1000 VM-Lizenzen in 10er-Inkrementen)
* IBM Spectrum Protect Plus-Lizenz, die über die Konsole von {{site.data.keyword.vmwaresolutions_short}} angeboten wird (Anzahl von VMs in 10er-Paketen) oder als BYOL

## Hinweise zur Installation von IBM Spectrum Protect Plus on IBM Cloud
{: #spp_considerations-install}

Lesen Sie die folgenden Hinweise, bevor Sie den Service "IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}" installieren.

* Stellen Sie sicher, dass die CPU und der Speicher im Standardcluster Ihrer Instanz für die virtuelle Maschine von IBM Spectrum Protect Plus ausreichen.
* Stellen Sie sicher, dass die NFS-Mounts, die auf den ESXi-Servern verfügbar sind, auf der Basis der Version der ESXi-Server ausreichend sind.

  Instanzen, die in V2.2 oder höheren Releases bereitgestellt (oder auf diese Releases aktualisiert) werden, verfügen über eine Einstellung für den Parameter `NFS.MaxVolumes` in VMware. Dieser Parameter definiert die maximale Anzahl der NFS-Mounts auf einem ESXi-Server und kann je nach Version des ESXi-Servers auf maximal 256 gesetzt werden. Weitere Informationen finden Sie unter [Increasing the default value that defines the maximum number of NFS mounts on an ESXi/ESX host](https://kb.vmware.com/s/article/2239).

  Der Service "IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}" kann bis zu 11 der NFS-Datenträger auf jedem ESXi-Server im Standardcluster Ihrer Instanz verwenden. Darüber hinaus erstellt der Service transiente NFS-Mounts für Sicherungs- und Wiederherstellungszwecke. Daher müssen Sie die Anzahl der NFS-Mounts auf mindestens 64 setzen, um sicherzustellen, dass der Service installiert und erfolgreich ausgeführt werden kann.

## Hinweise zum Entfernen von IBM Spectrum Protect Plus on IBM Cloud
{: #spp_considerations-remove}

Lesen Sie die folgenden Hinweise, bevor Sie den Service "IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}" entfernen:
* Stellen Sie sicher, dass alle Sicherungsjobkonfigurationen zusammen mit den aktiven Sicherungs- oder Wiederherstellungsoperationen entfernt werden.
* Wenn Sie den Service entfernen, wird der Speicher für das Sicherungsrepository aus der virtuellen Maschine von IBM Spectrum Protect Plus entfernt und die Speicherbestellung wird storniert, wodurch die Sicherungsrepositorydaten permanent gelöscht werden.
* Wenn Sie den Service entfernen, wird der für den Service bestellte Sicherungsspeicher ebenfalls entfernt. Der Zugriff auf alle Sicherungen wird während des Entfernens des Service unmöglich.

## Zugehörige Links
{: #spp_considerations-related}

* [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} Preventive Service Planning](https://www-01.ibm.com/support/docview.wss?uid=swg22012650){:new_window}
* [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} verwalten](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingspp)
* [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} bestellen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-spp_ordering)
* [IBM Spectrum Protect Plus-Dokumentation](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html)
* [Kontaktaufnahme mit dem IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
