---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-22"

keywords: IBM Spectrum Protect Plus, SPP configuration, order SPP

subcollection: vmware-solutions


---

{:external: target="_blank" .external}

# IBM Spectrum Protect Plus on IBM Cloud bestellen
{: #spp_ordering}

Sie können den Service "{{site.data.keyword.IBM}} Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}}" durch Bestellen einer neuen Instanz, die den Service beinhaltet, oder durch Hinzufügen des Service zu Ihrer vorhandenen Instanz bestellen.

## IBM Spectrum Protect Plus on IBM Cloud für eine neue Instanz bestellen
{: #spp_ordering-new}

Sie können mithilfe einer der folgenden Methoden eine neue Instanz mit IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} bestellen:
* Wählen Sie beim Bestellen einer neuen Instanz über die {{site.data.keyword.vmwaresolutions_short}}-Konsole **IBM Spectrum Protect Plus on IBM Cloud** im Abschnitt **Services** aus.
* Klicken Sie im {{site.data.keyword.cloud_notm}}-Katalog im linken Navigationsfenster auf das Symbol **VMware** und anschließend im Abschnitt **VMware Services** auf die Karte **IBM Spectrum Protect Plus on IBM Cloud**. Geben Sie die Serviceeinstellungen an und wählen Sie **Zu neuer Instanz hinzufügen** aus.

## IBM Spectrum Protect Plus on IBM Cloud für eine vorhandene Instanz bestellen
{: #spp_ordering-existing}

Sie können den Service "IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}" mit einer der folgenden Methoden zu einer vorhandenen Instanz hinzufügen:
* Zeigen Sie über die {{site.data.keyword.vmwaresolutions_short}}-Konsole die Instanz an, für die der Service hinzugefügt werden soll, klicken Sie im linken Navigationsfenster auf **Services** und anschließend auf **Hinzufügen**.
* Klicken Sie im {{site.data.keyword.cloud_notm}}-Katalog im linken Navigationsfenster auf das Symbol **VMware** und anschließend im Abschnitt **VMware Services** auf die Karte **IBM Spectrum Protect Plus on IBM Cloud**. Geben Sie die Serviceeinstellungen an und wählen Sie **Zu vorhandener Instanz hinzufügen** aus.

## IBM Spectrum Protect Plus on IBM Cloud - Servicekonfiguration
{: #spp_ordering-config}

Geben Sie beim Bestellen des Service die folgenden Einstellungen an.

### Anzahl der Datenträger
{: #spp_ordering-config-number-vol}

Die Ihren Speicheranforderungen entsprechende Anzahl von Datenträgern.

### Speichergröße pro Datenträger
{: #spp_ordering-config-size}

Die Speicherkapazität pro Datenträger.

### Speicherleistung
{: #spp_ordering-config-performance}

Die E/A-Operationen pro Sekunde (Input/Output Operations Per Second, IOPS) und pro GB basierend auf Ihren Workloadanforderungen.
* Falls Sie Lizenzen für IBM Spectrum Protect Plus bestellen möchten, geben Sie die **Anzahl zu lizenzierender VMs** auf der Registerkarte **Lizenzen bestellen** an.
* Falls Sie eine eigene Lizenz verwenden möchten (Bring Your Own License, BYOL), klicken Sie auf die Registerkarte **IBM Spectrum Protect Plus-Lizenzen** und anschließend auf **Lizenzdateien hinzufügen**, um Ihre eigenen IBM Spectrum Protect Plus-Lizenzdateien hochzuladen.

## Bereitstellungsprozess für IBM Spectrum Protect Plus on IBM Cloud
{: #spp_ordering-deploy}

Die Bereitstellung von IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} ist automatisiert. Unabhängig davon, ob Sie eine Instanz mit enthaltenem Service bestellen oder den Service zu einem späteren Zeitpunkt in Ihrer Instanz bereitstellen, werden vom {{site.data.keyword.vmwaresolutions_short}}-Automatisierungsprozess die folgenden Schritte ausgeführt:

1. Aus der {{site.data.keyword.cloud_notm}}-Infrastruktur wird basierend auf den von Ihnen angegebenen Einstellungen Endurance-NFS-Speicher für das IBM Spectrum Protect Plus-Sicherungsrepository bestellt.
2. Aus der {{site.data.keyword.cloud_notm}}-Infrastruktur wird basierend auf den von Ihnen angegebenen Einstellungen eine Anzahl von Lizenzen für IBM Spectrum Protect Plus bestellt. Die Lizenzen werden in Schritten von Lizenzpaketen für je 10 virtuelle Maschinen (VMs) bestellt. Grundlage ist die Anzahl der virtuellen Maschinen, die Sie für die Lizenzierung angegeben haben, als Sie den Service "IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}" bestellt haben. Falls Sie eine eigene bestehende IBM Spectrum Protect Plus-Lizenz verwenden möchten, wird keine Lizenzbestellung aus der {{site.data.keyword.cloud_notm}}-Infrastruktur aufgegeben.
3. Der für diesen Service bestellte NFS-Speicher wird an alle ESXi-Server im Standardcluster der Instanz angehängt. Dabei werden auch die richtigen statischen Routen auf jedem ESXi-Server zum privaten Teilnetz des Speichers hinzugefügt.
4. In vCenter Server werden NFS-Datenspeicher für alle NFS-Speicherdatenträger erstellt, die an die ESXi-Server angehängt sind.
5. Die IBM Spectrum Protect Plus-VMs werden im Standardcluster der Instanz bereitgestellt, aktiviert und konfiguriert.
6. Der NFS-Speicher, der für diesen Service bestellt wurde, wird an die virtuelle Maschine von IBM Spectrum Protect Plus angehängt und das Sicherungsrepository wird konfiguriert.
7. Der Hostname und die IP-Adresse der virtuellen Maschine von IBM Spectrum Protect Plus werden beim DNS-Server der Instanz registriert.

## Zugehörige Links
{: #spp_ordering-related}

* [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} - Übersicht](/docs/services/vmwaresolutions/services?topic=vmware-solutions-spp_considerations)
* [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} Preventive Service Planning](https://www-01.ibm.com/support/docview.wss?uid=swg22012650){:external}
* [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} verwalten](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingspp)
* [Services für vCenter Server-Instanzen bestellen, anzeigen und entfernen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [IBM Spectrum Protect Plus-Dokumentation](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html){:external}
* [Kontaktaufnahme mit dem IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
