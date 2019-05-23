---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-09"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Zerto on IBM Cloud bestellen
{: #zerto_ordering}

Sie können den Service "Zerto on {{site.data.keyword.cloud}}" durch Bestellen einer neuen Instanz, die den Service beinhaltet, oder durch Hinzufügen des Service zu Ihrer vorhandenen Instanz bestellen.

## Zerto on IBM Cloud für eine neue Instanz bestellen
{: #zerto_ordering-new}

Sie können mithilfe einer der folgenden Methoden eine neue Instanz mit Zerto on {{site.data.keyword.cloud_notm}} bestellen:
* Wählen Sie beim Bestellen einer neuen Instanz von der {{site.data.keyword.vmwaresolutions_short}}-Konsole **Zerto on IBM Cloud** im Abschnitt **Services** aus.
* Wählen Sie im {{site.data.keyword.cloud_notm}}-Katalog **Zerto on IBM Cloud** aus, geben Sie die Serviceeinstellungen an und wählen Sie **Zu neuer Instanz hinzufügen** aus.

## Zerto on IBM Cloud für eine vorhandene Instanz bestellen
{: #zerto_ordering-existing}

Sie können den Service "Zerto on {{site.data.keyword.cloud_notm}}" mit einer der folgenden Methoden zu einer vorhandenen Instanz hinzufügen:
* Zeigen Sie über die {{site.data.keyword.vmwaresolutions_short}}-Konsole die Instanz an, für die der Service hinzugefügt werden soll, klicken Sie im linken Navigationsfenster auf **Services** und anschließend auf **Hinzufügen**.
* Wählen Sie im {{site.data.keyword.cloud_notm}}-Katalog **Zerto on IBM Cloud** aus, geben Sie die Serviceeinstellungen an und wählen Sie **Zu vorhandener Instanz hinzufügen** aus.

Wenn Sie Zerto for {{site.data.keyword.cloud_notm}} zu einer vCenter Server-Instanz hinzufügen, die einen ESXi-Server im Wartungsmodus enthält, müssen Sie die Konsole von Zerto Virtual Manager (ZVM) und die bereits ausgefüllte IP-Adresse von Zerto Virtual Replication Appliance (VRA) verwenden, um die virtuelle VRA-Maschine (VM) manuell bereitzustellen.
{:note}

## Zerto on IBM Cloud nur für private Instanzen bestellen
{: #zerto_ordering-private-only}

Wenn Sie Zerto on {{site.data.keyword.cloud_notm}} nur einer rein privaten Instanz hinzufügen möchten, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:
* Sie sind dafür verantwortlich, Ihren eigenen Proxy-Server für die Verbindung zum Internet einzurichten. Weitere Informationen finden Sie in der Veröffentlichung zur [öffentlichen Netzkonnektivität](/docs/services/vmwaresolutions/services?topic=vmware-solutions-design_virtualinfrastructure#public-network-connectivity).
* Sie müssen auch die Call-Home-Funktion für Zerto konfigurieren. Weitere Informationen finden Sie in der Veröffentlichung zur [Zerto-Berichtserstellung für Unternehmensumgebungen (Call-Home)](https://www.zerto.com/myzerto/knowledge-base/zerto-reporting-for-enterprise-environments-call-home/){:new_window}.

## Zugehörige Links
{: #zerto_ordering-related}

* [Zerto on {{site.data.keyword.cloud_notm}} - Übersicht](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr)
* [Zerto on {{site.data.keyword.cloud_notm}} verwalten](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingzertodr)
* [Verwaltete Services für Zerto on {{site.data.keyword.cloud_notm}} anfordern](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_zerto_services)
* [Website "zerto.com"](https://www.zerto.com){:new_window}
* [Technische Dokumentation zu Zerto (englisch)](https://www.zerto.com/myzerto/technical-documentation/){:new_window}
