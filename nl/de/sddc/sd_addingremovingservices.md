---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-06"

subcollection: vmwaresolutions


---

# Services für Cloud Foundation-Instanzen bestellen, anzeigen und entfernen
{: #sd_addingremovingservices}

Sie können Services für Ihre VMware Cloud Foundation-Instanzen bestellen, beispielsweise eine Disaster-Recovery-Lösung. Sobald Sie diese Services nicht mehr benötigen, können Sie sie aus Ihren Instanzen entfernen.

## Verfügbare Services für Cloud Foundation-Instanzen
{: #sd_addingremovingservices-available-services}

In der folgenden Tabelle sind die Services aufgeführt, die für Cloud Foundation-Instanzen verfügbar sind, sowie die installierten Serviceversionen.

Tabelle 1. Verfügbare Services für Cloud Foundation-Instanzen

| Servicename | Aktuelle Serviceversion | Instanzversion |
|----------------------------------------------------------------------------------------|------------------|
| [F5 on {{site.data.keyword.cloud}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_considerations) | BIG-IP VE V14.1.0.2 | V1.9 und höher |
| [FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_considerations)       | 300 Series | V1.8 und höher |
| [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_considerations) | 6.0.3 | V2.0 und höher |
| [HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_considerations)              | 5.4.2 | V2.3 und höher |
| [HyTrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_considerations)              | 4.2.1 | V2.3 und höher |
| [HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htkc_considerations) | 4.2 | V2.5 und höher |
| [IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-spp_considerations)  | 10.1.2 | V2.2 und höher |
| [KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations) |  2.0 | Nicht zutreffend |
| [Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_considerations) | 9.5u4 | V1.8 und höher |
| [Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr) | 6.5 Update 3 | V1.2 und höher |

## Vorgehensweise zum Hinzufügen von Services zu Cloud Foundation-Instanzen
{: #sd_addingremovingservices-adding-procedure}

Klicken Sie zum Hinzufügen eines Service zu Ihrer Cloud Foundation-Instanz auf den entsprechenden Service-Link in der vorherigen Tabelle, um die Hinweise zu dem Service zu prüfen und die bereitgestellten Komponenten zu überprüfen. Befolgen Sie anschließend die Anweisungen im Abschnitt zum Bestellen von Services, um den Service Ihrer Instanz hinzuzufügen.

### Ergebnisse der Serviceinstallation
{: #sd_addingremovingservices-adding-results}

Nachdem die Installation des Service erfolgreich abgeschlossen wurde, werden Sie per E-Mail benachrichtigt und der Service wird auf der Seite **Services** der Instanz mit dem Status **Installiert** angezeigt.

## Vorgehensweise zum Anzeigen von Services für Cloud Foundation-Instanzen
{: #sd_addingremovingservices-viewing-procedure}

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Ressourcen**.
2. Klicken Sie in der Tabelle **Cloud Foundation-Instanzen** auf die Instanz, für die Sie Services anzeigen wollen.
3. Klicken Sie im linken Navigationsfenster auf **Services**.
4. Klicken Sie auf der Seite **Services** auf einen Service, um die zugehörigen Informationen, beispielsweise den Servicestatus und andere Details, zu prüfen.
5. Je nach dem angezeigten Service können Sie über die in den Servicedetails bereitgestellten Berechtigungsnachweise auf die Servicekonsolen zugreifen und den Service von hier aus verwalten.

## Vorgehensweise zum Entfernen von Services für Cloud Foundation-Instanzen
{: #sd_addingremovingservices-removing-procedure}

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Ressourcen**.
2. Klicken Sie in der Tabelle **Cloud Foundation-Instanzen** auf die Instanz, für die Sie Services entfernen wollen.
3. Klicken Sie im linken Navigationsfenster auf **Services**.
4. Suchen Sie auf der Seite **Services** die Serviceinstanz, die entfernt werden soll, und klicken Sie anschließend auf das Symbol **Löschen**.
5. Prüfen Sie die gegebenenfalls im Fenster **Service löschen** angezeigten Hinweise oder Warnungen. Wählen Sie **Zur Kenntnis genommen** aus und klicken Sie auf **Löschen**.

### Ergebnisse der Servicelöschung
{: #sd_addingremovingservices-removing-results}

Nachdem Ihre Anforderung zum Entfernen des Service akzeptiert wurde, ändert sich der Servicestatus in **Wird entfernt**.

Nachdem die Entfernung des Service erfolgreich abgeschlossen wurde, werden Sie per E-Mail benachrichtigt und der Service wird von der Seite **Services** der Instanz entfernt.

Die entfernten Services werden Ihnen bis zum Ende des {{site.data.keyword.cloud_notm}}-Abrechnungszyklus berechnet.
{:note}

## Zugehörige Links
{: #sd_addingremovingservices-related}

* [Häufig gestellte Fragen](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
