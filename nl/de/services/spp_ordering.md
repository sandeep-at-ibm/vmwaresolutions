---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-15"

---

# IBM Spectrum Protect Plus on IBM Cloud bestellen

Sie können den Service "IBM Spectrum Protect Plus on {{site.data.keyword.cloud}}" durch Bestellen einer neuen Instanz, die den Service beinhaltet, oder durch Hinzufügen des Service zu Ihrer vorhandenen Instanz bestellen.

## IBM Spectrum Protect Plus on IBM Cloud für eine neue Instanz bestellen

Sie können mithilfe einer der folgenden Methoden eine neue Instanz mit IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} bestellen:
* Wählen Sie beim Bestellen einer neuen Instanz über die {{site.data.keyword.vmwaresolutions_full}}-Konsole **IBM Spectrum Protect Plus on IBM Cloud** im Abschnitt **Services** aus.
* Wählen Sie im {{site.data.keyword.cloud_notm}}-Katalog **IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}-Service** aus, geben Sie die Serviceeinstellungen an und wählen Sie **Zu neuer Instanz hinzufügen** aus.

## IBM Spectrum Protect Plus on IBM Cloud für eine vorhandene Instanz bestellen

Sie können den Service "IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}" mit einer der folgenden Methoden zu einer vorhandenen Instanz hinzufügen:
* Zeigen Sie über die {{site.data.keyword.vmwaresolutions_short}}-Konsole die Instanz an, für die der Service hinzugefügt werden soll, klicken Sie im linken Navigationsfenster auf **Services** und anschließend auf **Service hinzufügen**.
* Wählen Sie im {{site.data.keyword.cloud_notm}}-Katalog **IBM Spectrum Protect Plus on IBM Cloud-Service** aus, geben Sie die Serviceeinstellungen an und wählen Sie **Zu vorhandener Instanz hinzufügen** aus.

## IBM Spectrum Protect Plus on IBM Cloud - Servicekonfiguration

Geben Sie beim Bestellen des Service die folgenden Einstellungen an.

### Anzahl der Datenträger

Die Ihren Speicheranforderungen entsprechende Anzahl von Datenträgern.

### Speichergröße pro Datenträger

Die Speicherkapazität pro Datenträger. Für das Management sind mindestens 500 GB pro Datenträger erforderlich.

### Speicherleistung

Die E/A-Operationen pro Sekunde (Input/Output Operations Per Second, IOPS) und pro GB basierend auf Ihren Workloadanforderungen.
* Falls Sie Lizenzen für IBM Spectrum Protect Plus bestellen möchten, geben Sie die **Anzahl zu lizenzierender VMs** auf der Registerkarte **Lizenzen bestellen** an. Für das Lizenzmanagement sind mindestens 10 virtuelle Maschinen (Virtual Machines, VMs) erforderlich.
* Falls Sie eine eigene Lizenz verwenden möchten (Bring Your Own License, BYOL), klicken Sie auf die Registerkarte **IBM Spectrum Protect Plus-Lizenzen** und anschließend auf **Lizenzdateien hinzufügen**, um Ihre eigenen IBM Spectrum Protect Plus-Lizenzdateien hochzuladen.

## Bereitstellungsprozess für IBM Spectrum Protect Plus on IBM Cloud

Die Bereitstellung von IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} ist automatisiert. Unabhängig davon, ob Sie eine Instanz mit enthaltenem Service bestellen oder den Service zu einem späteren Zeitpunkt in Ihrer Instanz bereitstellen, werden vom {{site.data.keyword.vmwaresolutions_short}}-Automatisierungsprozess die folgenden Schritte ausgeführt:

1. Aus der {{site.data.keyword.cloud_notm}}-Infrastruktur wird basierend auf den von Ihnen angegebenen Einstellungen Endurance-NFS-Speicher für das IBM Spectrum Protect Plus-Sicherungsrepository bestellt.
2. Aus der {{site.data.keyword.cloud_notm}}-Infrastruktur wird basierend auf den von Ihnen angegebenen Einstellungen eine Anzahl von Lizenzen für IBM Spectrum Protect Plus bestellt. Die Lizenzen werden in Schritten von Lizenzpaketen für je 10 virtuelle Maschinen bestellt. Grundlage ist die Anzahl der virtuellen Maschinen, die Sie für die Lizenzierung angegeben haben, als Sie den Service "IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}" bestellt haben. Falls Sie eine eigene bestehende IBM Spectrum Protect Plus-Lizenz verwenden möchten, wird keine Lizenzbestellung aus der {{site.data.keyword.cloud_notm}}-Infrastruktur aufgegeben.
3. Der für diesen Service bestellte NFS-Speicher wird an alle ESXi-Server im Standardcluster der Instanz angehängt. Dabei werden auch die richtigen statischen Routen auf jedem ESXi-Server zum privaten Teilnetz des Speichers hinzugefügt.
4. In vCenter Server werden NFS-Datenspeicher für alle NFS-Speicherdatenträger erstellt, die an die ESXi-Server angehängt sind.
5. Die virtuelle Maschine von IBM Spectrum Protect Plus wird im Standardcluster der Instanz bereitgestellt, aktiviert und konfiguriert.
6. Der NFS-Speicher, der für diesen Service bestellt wurde, wird an die virtuelle Maschine von IBM Spectrum Protect Plus angehängt und das Sicherungsrepository wird konfiguriert.
7. Der Hostname und die IP-Adresse der virtuellen Maschine von IBM Spectrum Protect Plus werden beim DNS-Server der Instanz registriert.
8. (Für Instanzen ab V2.3 und höher) In IBM Spectrum Protect Plus wird ein standardmäßiger Managementsicherungsjob erstellt. Weitere Informationen finden Sie unter [IBM Spectrum Protect Plus on IBM Cloud verwalten](managingspp.html).

## Zugehörige Links

* [Überblick zu IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](spp_considerations.html)
* [IBM Spectrum Protect Plus on IBM Cloud Preventive Service Planning](http://www.ibm.com/support/docview.wss?uid=swg22012650)
* [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} verwalten](managingspp.html)
* [Services für Cloud Foundation-Instanzen bestellen, anzeigen und entfernen](../sddc/sd_addingremovingservices.html)
* [Services für vCenter Server-Instanzen bestellen, anzeigen und entfernen](../vcenter/vc_addingremovingservices.html)
* [Services für vCenter Server with Hybridity Bundle-Instanzen bestellen, anzeigen und entfernen](../vcenter/vc_hybrid_addingremovingservices.html)
* [IBM Spectrum Protect Plus documentation](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html)
* [Kontaktaufnahme mit dem IBM Support](../vmonic/trbl_support.html)
