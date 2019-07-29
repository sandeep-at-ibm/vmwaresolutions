---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-18"

keywords: Zerto, request Zerto Orchestrated, Zerto managed service

subcollection: vmware-solutions


---

# Verwaltete Services für Zerto on IBM Cloud anfordern
{: #managing_zerto_services}

Der Service "Zerto on {{site.data.keyword.cloud}}" stellt Replikations- und Disaster-Recovery-Funktionalität bereit. Diese Funktionalität kann in die Bereitstellungsangebote integriert werden, um Daten in Ihrer virtuellen VMware-Umgebung in {{site.data.keyword.cloud_notm}} zu schützen und wiederherzustellen.

Wenn Sie verwaltete Services für Zerto on {{site.data.keyword.cloud_notm}} anfordern, kann eine vollständig verwaltete Disaster-Recovery-Umgebung sowohl mit Disaster-Recovery-Software von Zerto als auch IBM Resiliency Services bereitgestellt werden, die Ihnen folgendermaßen von Nutzen sein kann:

Die folgenden Modelle für verwaltete Services für Zerto on {{site.data.keyword.cloud_notm}} sind verfügbar.

## IBM Orchestrated Managed Services for Zerto
{: #managing_zerto_services-orchestrated}

Dieses Modell ist geeignet, wenn Sie das Produktangebot "Zerto on {{site.data.keyword.cloud_notm}}" verwenden.

In diesem Modell wird der Service "{{site.data.keyword.cloud_notm}} Resiliency Orchestration" für Zerto on {{site.data.keyword.cloud_notm}} bereitgestellt. Dieses Modell ermöglicht einen unterbrechungsfreien Schutz von virtuellen Maschinen, Betriebssystemen und Daten in {{site.data.keyword.cloud_notm}} mit kontinuierlichen Disaster-Recovery-Tests, Sichtbarkeit von RTO (Recovery Time Objective; Zielsetzung für Wiederherstellungszeit) und RPO (Recovery Point Objective; Zielsetzung für Wiederherstellungspunkt) sowie Failover- und Failbackfunktionalität.

Alle Funktionen werden über das Dashboard von {{site.data.keyword.cloud_notm}} Resiliency Orchestration durch das IBM Resiliency Services Global Command Center verwaltet.

Weitere Informationen finden Sie unter [IBM Resiliency Orchestration](https://www.ibm.com/us-en/marketplace/disaster-recovery-orchestration).

## IBM Managed Services for Zerto (ohne Orchestration)
{: #managing_zerto_services-without-orchestrated}

In diesem Modell wird eine vollständig verwaltete Disaster-Recovery-Lösung für Zerto on {{site.data.keyword.cloud_notm}} bereitgestellt. Dieses Modell ist geeignet, wenn Sie einen verwalteten Service nur für Zerto Virtual Replication verwenden möchten, ohne den Service "{{site.data.keyword.cloud_notm}} Resiliency Orchestration" in der {{site.data.keyword.cloud_notm}} zu nutzen.

Weitere Informationen finden Sie unter [IBM Resiliency Disaster Recovery as a Service](https://www.ibm.com/us-en/marketplace/disaster-recovery-as-a-service#product-header-top).

## Vorgehensweise zum Anfordern von verwalteten Services für Zerto in IBM Cloud
{: #managing_zerto_services-procedure}

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Einführung**.
2. Blättern Sie auf der Seite abwärts und klicken Sie unter **Zusätzliche verwaltete Services bestellen** auf die Karte **Verwaltete Services für Zerto on IBM Cloud**.
3. Prüfen Sie auf der Seite **Zerto on IBM Cloud** die Beschreibung und die technischen Spezifikationen für Zerto on {{site.data.keyword.cloud_notm}} als verwalteten Service und klicken Sie anschließend auf **Erstellen**.
4. Geben Sie die Konfigurationseinstellungen entsprechend Ihren Anforderungen an oder übernehmen Sie die Standardwerte.
5. Klicken Sie auf **vCenter Server**, um den Service zu einer Ihrer Instanzen hinzuzufügen.
6. Um den Service während der Bestellung einer neuen Instanz hinzuzufügen, klicken Sie auf **Zu neuer Instanz hinzufügen**. Fahren Sie anschließend mit der Bestellung einer neuen [vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)- oder [vCenter Server with Hybridity](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance)-Instanz fort.
7. Um den Service zu einer bereits vorhandenen Instanz hinzuzufügen, müssen Sie auf **Zu bereitgestellter Instanz hinzufügen** klicken und dann die gewünschte Instanz in der Liste auswählen. Anschließend müssen Sie bestätigen, dass Sie mit der Bestellung fortfahren möchten, indem Sie auf **Bereitstellung** klicken.

## Zugehörige Links
{: #managing_zerto_services-related}

* [Services für vCenter Server-Instanzen bestellen, anzeigen und entfernen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [Kontaktaufnahme mit dem IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
