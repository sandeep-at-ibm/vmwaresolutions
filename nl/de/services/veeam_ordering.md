---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-22"

keywords: Veeam, Veeam configuration, order Veeam

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Veeam on IBM Cloud bestellen
{: #veeam_ordering}

Sie können den Service "Veeam on {{site.data.keyword.cloud}}" durch Bestellen einer neuen Instanz, die den Service beinhaltet, oder durch Hinzufügen des Service zu Ihrer vorhandenen Instanz bestellen.

## Veeam on IBM Cloud für eine neue Instanz bestellen
{: #veeam_ordering-new}

Sie können mithilfe einer der folgenden Methoden eine neue Instanz mit Veeam on {{site.data.keyword.cloud_notm}} bestellen:
* Wählen Sie beim Bestellen einer neuen Instanz von der {{site.data.keyword.vmwaresolutions_short}}-Konsole **Veeam on IBM Cloud** im Abschnitt **Services** aus.
* Klicken Sie im {{site.data.keyword.cloud_notm}}-Katalog im linken Navigationsfenster auf das Symbol **VMware** und anschließend im Abschnitt **VMware Services** auf die Karte **Veeam on IBM Cloud**. Geben Sie die Serviceeinstellungen an und wählen Sie **Zu neuer Instanz hinzufügen** aus.

## Veeam on IBM Cloud für eine vorhandene Instanz bestellen
{: #veeam_ordering-existing}

Sie können den Service "Veeam on {{site.data.keyword.cloud_notm}}" mit einer der folgenden Methoden zu einer vorhandenen Instanz hinzufügen:
* Zeigen Sie über die {{site.data.keyword.vmwaresolutions_short}}-Konsole die Instanz an, für die der Service hinzugefügt werden soll, klicken Sie im linken Navigationsfenster auf **Services** und anschließend auf **Hinzufügen**.
* Klicken Sie im {{site.data.keyword.cloud_notm}}-Katalog im linken Navigationsfenster auf das Symbol **VMware** und anschließend im Abschnitt **VMware Services** auf die Karte **Veeam on IBM Cloud**. Geben Sie die Serviceeinstellungen an und wählen Sie **Zu vorhandener Instanz hinzufügen** aus.

## Veeam on IBM Cloud - Servicekonfiguration
{: #veeam_ordering-config}

Geben Sie beim Bestellen des Service die folgenden Einstellungen an.

### Anzahl zu lizenzierender VMs
{: #veeam_ordering-config-vms}

Für die Lizenzverwaltung sind mindestens 10 VMs erforderlich.

### Speichergröße
{: #veeam_ordering-config-storage-size}

Die Kapazität, die Ihre Speicheranforderungen erfüllt. Hinweise zur Schätzung der Speichergröße finden Sie im Abschnitt zum [Schätzen der Repository-Kapazität](https://bp.veeam.expert/repository_server/repository_planning/repository_planning_sizing){:external}.

### Speicherleistung
{: #veeam_ordering-config-storage-performance}

Die E/A-Operationen pro Sekunde (Input/Output operations per second, IOPS) und pro GB basierend auf Ihren Workloadanforderungen.

## Zugehörige Links
{: #veeam_ordering-related}

* [Veeam on {{site.data.keyword.cloud_notm}} verwalten](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingveeam)
* [Services für vCenter Server-Instanzen bestellen, anzeigen und entfernen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [Verwaltete Services für Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_veeam_services)
* [Veeam-Website](https://www.veeam.com/){:external}
* [Veeam Help Center](https://www.veeam.com/documentation-guides-datasheets.html){:external}
