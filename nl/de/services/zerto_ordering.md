---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-28"

keywords: Zerto, Zerto replication billing, order Zerto

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Zerto on IBM Cloud bestellen
{: #zerto_ordering}

Sie können den Service "Zerto on {{site.data.keyword.cloud}}" durch Bestellen einer neuen Instanz, die den Service beinhaltet, oder durch Hinzufügen des Service zu Ihrer vorhandenen Instanz bestellen.

## Abrechnung für Zerto-Replikation
{: #zerto_ordering-billing}

Die Metriken von virtuellen Maschinen, die unter Verwendung von Zerto repliziert werden, werden von Zerto und {{site.data.keyword.cloud_notm}} gemessen. Ihre Rechnung für diese Nutzung wird über ein gebührenpflichtiges {{site.data.keyword.cloud_notm}}-Konto und nicht ein {{site.data.keyword.cloud_notm}}-Infrastrukturkonto abgerechnet.

Stellen Sie vor dem Bestellen von Zerto on {{site.data.keyword.cloud_notm}} sicher, dass Ihr {{site.data.keyword.cloud_notm}}-Konto ein Abrechnungskonto ist und dass es mit dem {{site.data.keyword.cloud_notm}}-Infrastrukturkonto verknüpft ist, in dem Ihre Instanz bereitgestellt wird.

Falls Sie über eine Zerto on {{site.data.keyword.cloud_notm}}-Installation der Version 3.0 oder einer früheren Version verfügen, werden die Replikationskosten Ihrer virtuellen Maschinen weiterhin über die Abrechnung der {{site.data.keyword.cloud_notm}}-Infrastruktur in Rechnung gestellt. Wenn Ihre Konten- und Abrechnungseinstellungen die oben aufgelisteten Anforderungen erfüllen, können Sie zur Zerto-Abrechnungsmethode wechseln.

Sie werden in der {{site.data.keyword.vmwaresolutions_short}}-Konsole aufgefordert, den {{site.data.keyword.cloud_notm}}-Infrastrukturplan in einen kostenpflichtigen Plan umzuwandeln und für Ihr {{site.data.keyword.cloud_notm}}-Konto ein Upgrade auf ein gebührenpflichtiges Konto durchzuführen (sofern erforderlich).

* Informationen zu kostenlosen Konten und gebührenpflichtigen Konten finden Sie unter [Kontotypen](/docs/account?topic=account-accounts).
* Informationen zu einem Upgrade auf ein gebührenpflichtiges Konto finden Sie unter [Upgrade für Konto durchführen](/docs/account?topic=account-upgrading-account).
* Informationen zum Verknüpfen von {{site.data.keyword.cloud_notm}} mit Ihren {{site.data.keyword.cloud_notm}}-Infrastrukturkonten finden Sie unter [Zur IBMid wechseln und Konten verknüpfen](/docs/account?topic=account-unifyingaccounts).

## Zerto on IBM Cloud für eine neue Instanz bestellen
{: #zerto_ordering-new}

Sie können mithilfe einer der folgenden Methoden eine neue Instanz mit Zerto on {{site.data.keyword.cloud_notm}} bestellen:
* Wählen Sie beim Bestellen einer neuen Instanz von der {{site.data.keyword.vmwaresolutions_short}}-Konsole **Zerto on IBM Cloud** im Abschnitt **Services** aus.
* Klicken Sie im {{site.data.keyword.cloud_notm}}-Katalog im linken Navigationsfenster auf das Symbol **VMware** und anschließend im Abschnitt **VMware Services** auf die Karte **Zerto on IBM Cloud**. Geben Sie die Serviceeinstellungen an und wählen Sie **Zu neuer Instanz hinzufügen** aus.

## Zerto on IBM Cloud für eine vorhandene Instanz bestellen
{: #zerto_ordering-existing}

Sie können den Service "Zerto on {{site.data.keyword.cloud_notm}}" mit einer der folgenden Methoden zu einer vorhandenen Instanz hinzufügen:
* Zeigen Sie über die {{site.data.keyword.vmwaresolutions_short}}-Konsole die Instanz an, für die der Service hinzugefügt werden soll, klicken Sie im linken Navigationsfenster auf **Services** und anschließend auf **Hinzufügen**.
* Klicken Sie im {{site.data.keyword.cloud_notm}}-Katalog im linken Navigationsfenster auf das Symbol **VMware** und anschließend im Abschnitt **VMware Services** auf die Karte **Zerto on IBM Cloud**. Geben Sie die Serviceeinstellungen an und wählen Sie **Zu vorhandener Instanz hinzufügen** aus.

Wenn Sie Zerto on {{site.data.keyword.cloud_notm}} zu einer vCenter Server-Instanz hinzufügen, die über einen ESXi-Server im Wartungsmodus verfügt, müssen Sie die Konsole von Zerto Virtual Manager (ZVM) und die bereits ausgefüllte IP-Adresse von Zerto Virtual Replication Appliance (VRA) verwenden, um die virtuelle VRA-Maschine (VM) manuell bereitzustellen.
{:note}

## Zerto on IBM Cloud nur für private Instanzen bestellen
{: #zerto_ordering-private-only}

Wenn Sie Zerto on {{site.data.keyword.cloud_notm}} nur einer rein privaten Instanz hinzufügen möchten, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:
* Sie sind dafür verantwortlich, Ihren eigenen Proxy-Server für die Verbindung zum Internet einzurichten. Weitere Informationen finden Sie in der Veröffentlichung zur [öffentlichen Netzkonnektivität](/docs/services/vmwaresolutions/services?topic=vmware-solutions-design_virtualinfrastructure#public-network-connectivity).
* Sie müssen auch die Call-Home-Funktion für Zerto konfigurieren. Weitere Informationen finden Sie in der Veröffentlichung zur [Zerto-Berichtserstellung für Unternehmensumgebungen (Call-Home)](https://www.zerto.com/myzerto/knowledge-base/zerto-reporting-for-enterprise-environments-call-home/){:external}.

## Zugehörige Links
{: #zerto_ordering-related}

* [Zerto on {{site.data.keyword.cloud_notm}} - Übersicht](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr)
* [Zerto on {{site.data.keyword.cloud_notm}} verwalten](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingzertodr)
* [Verwaltete Services für Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_zerto_services)
* [Website "zerto.com"](https://www.zerto.com){:external}
* [Technische Dokumentation zu Zerto (englisch)](https://www.zerto.com/myzerto/technical-documentation/){:external}
